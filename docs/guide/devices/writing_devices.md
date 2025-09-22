# Writing/Creating a Device

## Introduction
Before you can use a device with MDSplus, you must write it. It may be helpful to think of this as a device driver, but this process goes beyond that since it will be partially dictated by the way you want your data tree to be structured. Unfortunately, users cannot simply reuse legacy devices from our archive because the code is so tightly coupled to the hardware. Examples will be provided below to help guide you through the steps for your own equipment.

Note that you do not need to write a device if you simply want to import data after the experiment is over: 

* Importing Data
    * Data transfer into MDSplus happens post-shot (not live)
    * Assumes that you have some other way of storing data during the experiment. Either your experiment is expected to generate a manageable amount of data for the memory buffers built in to your various hardware, or you have some other arrangement for temporary storage in the meantime.
    * After the experiment is over, you can use a python script (or whatever) to import your CSV/video file/whatever into MDSplus
    * For example: instead of a live camera feed during the experiment, you would take the video file after the fact and import that into MDSplus
    
* Writing a Device
    * Goal: capture data live during experiment

### Examples
* N-Chan Digitizer and a Camera
* Signal/Pulse Generators/Analog Output (AO)/Digital Output (DO)

## General steps
1. Design your node list
    * Configuration nodes, with defaults
    * Data nodes
    * Options for nodes
        * no_write_model
        * no_write_shot
        * write_once
        * etc.
    * Examples:
        * Example, Digitizer: {address, length, frequency, input_xx}
        * Example, Camera: {address, width, height, length, frames}
2. Write setup function
    * Connect to device
    * Configure settings
    * Arm? (prepare it for firing)

3. Choose 3A (streaming) or 3B (store)
    * 3A. Write Main Loop Function (Continuous/streaming data capture, while experiment is running)
        * take data from hardware
        * write data to MDS plus
        * loop back to top
        * "buffering": Pre/post/window

    * 3B. Write Store Function (transient or post-shot data capture). 
        * Some hardware can buffer data inside of it. This is important in case the device's data exceeds the rate that we can capture it.
        * post-shot or STORE phase: basically do the same as 3A, but only need to do once for all the data captured during.
        * pre/post/window

4. Tuning: adjusting until everything works well. "After all you're trying to make hardware do something" which is inherently difficult.

5. Usage. Explain that you can use your device manually or via dispatch functions. With examples (TODO: examples from Stephen, Fernando).

### Debugging
more to come

tips and tricks for debugging as you're writing

whatever Stephen and Fernando can remember

### Modifying
Remove and Re-add
### Threading
... TODO
### Running with MDSTCL
### Running the device with the Shot Cycle

## Examples
Here is how we would set up some hypothetical devices.

### 32-Channel Transient Digitizer
This would be an analog-to-digital converter that stores data internally in a ring-buffer, and will return the data after the shot is complete. This device would wait for a trigger, capture the remaining `POSTSAMPLES`, and then stop and wait to offload the data.

The following would be stored in `DIG_32_TR.py` and located on your `$MDS_PYDEVICE_PATH` (see Environment Variables [link]())

To start, the device must be a sublcass of `MDSplus.Device`.

```py
import MDSplus

# TODO: Rename?
class DIG_32_TR(MDSplus.Device):
```

1. Design your node list. (node names need to be 11 characters or less)

    ```py
    parts = [
        # For any notes about this specific device, e.g. location, usage, problems
        {
            'path': ':COMMENT',
            'type': 'text',
            'options': ('no_write_shot',),
        },
        # The IP Address or DNS Name to be able to connect to the device
        {
            'path': ':ADDRESS',
            'type': 'text',
            'options': ('no_write_shot',),
        },
        # The number of samples to be captured and store before the trigger
        {
            'path': ':PRESAMPLES',
            'type': 'numeric',
            'value': 1000,
            'options': ('no_write_shot',),
        },
        # The number of samples to be captured and store after the trigger
        {
            'path': ':POSTSAMPLES',
            'type': 'numeric',
            'value': 5000,
            'options': ('no_write_shot',),
        },
        # The time to label the trigger time, usually 0.0
        {
            'path': ':TIME_AT_0',
            'type': 'numeric',
            'value': 0.0,
            'options': ('no_write_shot',),
        },
        # The frequency in Hz, which is how many samples per second to capture
        {
            'path': ':FREQUENCY',
            'type': 'numeric',
            'valueExpr': 'WithUnits(1000, "Hz")',
            'options': ('no_write_shot',),
        },
        # This is just for structural use, think of it as a folder, must be listed before any subnodes
        {
            'path': ':ACTIONS',
            'type': 'structure',
        },
        # This action can be used to call Arm() during the INIT phase. The method will be called on a given mdsip server, specified by the first parameter to Dispatch(). This parameter can either be an IP Address/DNS Name of the server, or the name of an environment variable that contains that information.
        {
            'path': ':ACTIONS:INIT',
            'type': 'action',
            'valueExpr': "Action(Dispatch('MDSIP_SERVER','INIT',50,None),Method(None,'arm',head))"
        },
        # This action can be used to call store() during the STORE phase. The method will be called on a given mdsip server, specified by the first parameter to Dispatch(). This parameter can either be an IP Address/DNS Name of the server, or the name of an environment variable that contains that information.
        {
            'path': ':ACTIONS:STORE',
            'type': 'action',
            'valueExpr': "Action(Dispatch('MDSIP_SERVER','STORE',50,None),Method(None,'store',head))"
        },
        # This is for structural use; think of it as a folder. Must be listed before any subnodes
        {
            'path': ':INPUTS',
            'type': 'structure',
        },
    ]

    # The data captured for each channel, stored in individual nodes
    for i in range(32):
        parts.append({
            'path': f':INPUTS:INPUT_{i + 1:02d}', # INPUT_01, INPUT_02, ...
            'type': 'signal',
            'options': ('no_write_model', 'write_once'),
        })
    ```

2. Write setup function.
    
   This assumes the manufacturer has a python library for users. 

    ```py
    def arm(self):
        import diglib # or whatever the manufacturer has for you

        # Connect to device
        dig = diglib.Digitizer(str(self.ADDRESS.data()))

        # Configure settings
        dig.setFrequency(int(self.FREQUENCY.data()))
        dig.setPrePost(int(self.PRESAMPLES.data()), int(self.POSTSAMPLES.data()))

        # Tell the device to capture data and wait for a trigger
        dig.arm()

    ARM = arm # TODO: Explain, test, possibly remove
    ```

3. Write the data storing function, which will download all data from the digitizer and store it in the input nodes. This should be run at the end of the shot, usually during the `STORE` phase.

    ```py
    def store(self):
        import diglib
        dig = diglib.Digitizer(str(self.ADDRESS.data()))

        presamples = int(self.getNode("PRESAMPLES").data())
        postsamples = int(self.getNode("POSTSAMPLES").data())
        time_at_0 = float(self.getNode("TIME_AT_0").data())
        frequency = int(self.getNode("FREQUENCY").data())

        start_index = -presamples + 1
        end_index = postsamples
        delta_time = 1.0 / float(frequency) # Time in seconds between samples

        # Calculate the time range for this segment of data
        begin = segment_index * seglen * delta_time
        end = begin + ((seglen - 1) * delta_time)
        dim = MDSplus.Range(begin, end, delta_time)
        
        dim = MDSplus.Dimension(
            MDSplus.Window(start_index, end_index, time_at_0),
            MDSplus.Range(None, None, delta_time)
        )

        # Retrieve all of the data from all of the channels
        samples = dig.readSamples(seglen)

        # Store the data for each channel in each INPUT_XX node
        for n in range(32):
            node = self.getNode(f"INPUTS:INPUT_{n+1:02d}")
            channel_data = samples[n]
            node.putData(MDSplus.Signal(channel_data, None, dim))
    STORE = store
    ```

4. Tuning

    Ensure that (`PRESAMPLES` + `POSTSAMPLES`) does not exceed the size of the digitizer's internal ring buffer.

5. Usage

    **Manual**
    ```
    do /method DEV arm
    ...
    do /method DEV store
    ```

    **Dispatching**
    ```
    dispatch /build
    dispatch /phase init
    dispatch /phase store
    ```

### 32-Channel Streaming Digitizer
Here is an example analog-to-digital converter that continuously captures data and sends it back to this code until stopped or until the `LENGTH` is reached. This will be using segmented data ([link](#)).

```py
import MDSplus

# TODO: Rename
class DIG_32_ST(MDSplus.Device):
```

1. Design your node list. (node names need to be 11 characters or less)
    ```py
    parts = [
        # For any notes about this specific device, e.g. location, usage, problems
        {
            'path': ':COMMENT',
            'type': 'text',
            'options': ('no_write_shot',),
        },
        # The IP Address or DNS Name to be able to connect to the device
        {
            'path': ':ADDRESS',
            'type': 'text',
            'options': ('no_write_shot',),
        },
        # The Segment Length, which is how many samples to store in each segment
        {
            'path': ':SEGLEN',
            'type': 'numeric',
            'value': 30000,
            'options': ('no_write_shot',),
        },
        # The Segment Count, which is how many filled segments to store before stopping
        {
            'path': ':SEGCOUNT',
            'type': 'numeric',
            'value': 10,
            'options': ('no_write_shot',),
        },
        # The Frequency in Hz, which is how many samples per second to capture
        {
            'path': ':FREQUENCY',
            'type': 'numeric',
            'valueExpr': 'WithUnits(1000, "Hz")',
            'options': ('no_write_shot',),
        },
        # This node will be on if we are running, or off if we are stopped
        {
            'path': ':RUNNING',
            'type': 'any',
            'options': ('no_write_shot', 'no_write_model'),
        },
        # This is just for structural use, think of it as a folder
        {
            'path': ':ACTIONS',
            'type': 'structure',
        },
        # This action can be used to call start() during the INIT phase. The method will be called on a given mdsip server, specified by the first parameter to Dispatch(). This parameter can either be an IP Address/DNS Name of the server, or the name of an environment variable that contains that information.
        {
            'path': ':ACTIONS:INIT',
            'type': 'action',
            'valueExpr': "Action(Dispatch('<MDSIP_SERVER>','INIT',50,None),Method(None,'start',head))"
        },
        # This is for structural use; think of it as a folder. Must be listed before any subnodes
        {
            'path': ':INPUTS',
            'type': 'structure',
        },
    ]

    # The data captured for each channel, stored in individual nodes
    for i in range(32):
        parts.append({
            'path': f':INPUTS:INPUT_{i + 1:02d}',
            'type': 'signal',
            'options': ('no_write_model'),
        })
    ```

2. Write setup function, assuming the manufacturer has a python library for you:

    The setup for a streaming device often happens right before data acquisition.

    For a streaming device, this is built into the next section
    (TODO confirm with Stephen/Fernando)

3. Write Main Loop Function (Continuous/streaming data capture, all while experiment is running)

    ```py

    class Worker(threading.Thread):
        def __init__(self, device):
            super(DIG_32_ST.Worker, self).__init__(name="Worker")
            self.tree_name = device.tree.name
            self.tree_shot = device.tree.shot
            self.node_path = device.path

        def run(self):
            import diglib # or whatever the manufacturer has for you

            try:
                # TODO: Talk about issues passing the actual device
                tree = MDSplus.Tree(self.tree_name, self.tree_shot)
                dev = tree.getNode(self.node_path)
                
                # Connect to device
                dig = diglib.Digitizer(str(dev.ADDRESS.data()))

                # Don't search for/access nodes during the loop
                frequency = int(dev.getNode("FREQUENCY").data())
                seglen = int(dev.getNode("SEGLEN").data())
                segcount = int(dev.getNode("SEGCOUNT").data())
                input_nodes = []
                for n in range(32):
                    input_nodes.append(dev.getNode(f"INPUTS:INPUT_{n+1:02d}"))

                delta_time = 1.0 / float(frequency) # Time in seconds between samples
                
                # Configure settings
                dig.setFrequency(int(dev.FREQUENCY.data()))

                segment_index = 0
                dev.RUNNING.on = True
                while segment_index < segcount and dev.RUNNING.on:
                    # Retrieve the data for this segment from all channels
                    samples = dig.readSamples(seglen)

                    # Calculate the time range for this segment of data
                    begin = segment_index * seglen * delta_time
                    end = begin + ((seglen - 1) * delta_time)
                    dim = MDSplus.Range(begin, end, delta_time)

                    # Store the data for each channel in each INPUT_XX node
                    for n, node in enumerate(input_nodes):
                        channel_data = samples[n]
                        node.makeSegment(begin, end, dim, channel_data)

                    segment_index = segment_index + 1

            except Exception as e:
                self.exception = e
                traceback.print_exc()

    # TODO: Talk about needing to return
    def start(self):
        thread = self.Worker(self)
        thread.start()
    START = start

    def stop(self):
        self.RUNNING.on = False
    STOP = stop
    ```

4. Tuning

    Adjust `SEGLEN` and `SEGCOUNT` to account for the time it takes to store the data for all channels. This will depend on the speed of your computer and the speed of your hard drive. We have found that storing data every ~30s works well on modern SSD hard drives. To accomplish this, you would set your `SEGLEN` to `(FREQUENCY * 30)`.

5. Usage

    ```py
    do /method DEV arm
    do /method DEV start
    ...
    # either wait for all of the segments to be captured, or call this to end early
    do /method DEV stop
    ```



### Camera


--

### Other Stuff

* devices have a parts array which list out all the possible data you could want from a specific device (? will need clarification on this)
* it will be up to each admin to set up and maintain their own devices
* devices are hardware agnostic