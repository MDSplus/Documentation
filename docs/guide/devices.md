# MDSplus Devices

 The `MDSplus device` framework is what MDSplus uses to integrate an experiment's hardware into the software. In the simplest terms, a device is a collection of nodes in the data tree containing all of the necessary setup parameters, task descriptions, and raw data associated with each physical data acquisition module in an experiment. This collection of nodes can be used to interface with the hardware, both controlling the hardware and collecting data from it.


## Assumptions

The instructions on this page assume that the following are true:

* MDSplus has been installed on experiment operator's computers

* MDSplus DAQ server has already been set up

* The data for collecting data from the experiment has already been set up

* Environment variables that point to the tree have already set up

* The driver has already been written for your device and has been added during the MDSplus installation process (e.g., in `pydevices/HtsDevices`). You will need the name of the driver and the classes that need to be called during Devices setup.


# Setting up a Device using mdstcl

## 1. Add Device to Tree

* open a terminal window

* type `$ mdstcl`

* type `edit <tree name>`

    **Note**: this will open in "edit" mode, which will allow you to edit the structure of the tree. This should only be done when creating the device.

* type `add node <node name> /model=<MDSplus device name>`

* type `write` to save

* example: 
    ```
    $ mdstcl
    TCL> edit testree
    TCL> add node ACQ161 /model=ACQ2106_435_1ST
    TCL> write
    ```

Use the `dir` command to confirm what was added in the above steps:
      
* type `dir` to see the full list of devices so far. The device you just added should now appear in the list. Example: 
  
    ```
    TCL> dir
    \TESTREE::TOP
    :ACQ161
    Total of 2 nodes.
    ```

    In the above example, the current tree ("Testree") has the device "ACQ161" (in this case a digitizer) and that there are two nodes: one for the data, and one representing the device.

* type `dir <device name>:*` to see the list of nodes (METHODS?) associated with this device. Example:
    ```    
    TCL> dir ACQ161:*

    \TESTREE::TOP:ACQ161

    :COMMENT      :DEF_DCIM     :EXT_CLOCK    :FREQ         :GIVEUP_TIME 
    :HW_FILTER    :INIT_ACTION  :INPUT_001    :INPUT_002    :INPUT_003   
    :INPUT_004    :INPUT_005    :INPUT_006    :INPUT_007    :INPUT_008   
    :INPUT_009    :INPUT_010    :INPUT_011    :INPUT_012    :INPUT_013   
    :INPUT_014    :INPUT_015    :INPUT_016    :INPUT_017    :INPUT_018   
    :INPUT_019    :INPUT_020    :INPUT_021    :INPUT_022    :INPUT_023   
    :INPUT_024    :INPUT_025    :INPUT_026    :INPUT_027    :INPUT_028   
    :INPUT_029    :INPUT_030    :INPUT_031    :INPUT_032    :LOG_OUTPUT  
    :MAX_SEGMENTS :NODE         :RUNNING      :SEG_EVENT    :SEG_LENGTH  
    :SITE         :STATUS_CMDS  :STATUS_OUT   :STOP_ACTION  :TRIGGER     
    :TRIG_MODE    :TRIG_STR     :TRIG_TIME   

    Total of 53 nodes.
    TCL> 
    ```

* When you are finished adding devices, type `close` to exit edit mode.

> Stephen/Fernando will make some example devices. 

## 2. Configuring the Device

Next, add basic configuration information so users can contact the device through the network. Changing the values of the nodes does not need to be done in edit mode, which should be reserved for setup.

* Use the `put` command to add the IP address of the device to the node called `NODE`

* Add a software switch to the node `TRIG_MODE` to allow MDSplus to trigger the device; this will eliminate the need to physically interact with the device

* use the `deco` command to display the contents of the node

* For example: 

    ```
    TCL> put ACQ161:NODE """172.25.202.51"""
    TCL> deco ACQ161:NODE
    "172.25.202.51"
    TCL> put ACQ161:TRIG_MODE """master:soft"""
    TCL> deco ACQ161:TRIG_MODE
    "master:soft"
    TCL> 
    ```


## Calling a method

This is unique to devices

1. manually calling methods

    * also: Utility methods (get state, reboot) 

2. setting up actions to call methods (basically setting up the init() and store() methods to automatically capture data)--link to the page describing the dispatcher

## Listing available devices

how to list the available devices on your computer

* jTraverser2: there's a dropdown!

* there's also a method you can call
