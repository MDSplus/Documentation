# Python

Intro text goes here. If you want to use python, this page is for you. There are basically only 2 ways to interact with MDSplus with Python: Connections or Trees. [link to the thin/thick concepts page] If you are unsure, go the Connection() route.

> TODO: Arguments to .get()

For a full list of types and functions, see the [Python API Reference](./reference/python.md).

## Setup

Tell python where our package is.

`mdsplus.pth` or `PYTHONPATH`

```py
import MDSplus
...
```

## Types
> TODO: We'll come back to this. it's all of the mdsplus types: signal, dispatch, conglom. examples of how to use the more useful ones, and then a link to reference of all the others

## Connection

Explanation of thin client [link]. The python interface for thin client is `MDSplus.Connection`.

> SLW TODO: Connection('local')

This is how you initialize a connection:
```py
import MDSplus
c = MDSplus.Connection('SERVER')
```

...and open a tree:
```py
c.openTree('TREE', SHOT)
```

### Reading Data

The way you query an MDSplus connection for data is using the `.get()` method. You can pass a TDI expression and arguments.

* `.get()` returns the MDSplus type
* `.data()` on that returns the native numpy type

```py
# Get data of node
data = c.get('NODE_NAME').data()

# Get data of tag
data = c.get('\\TAG_NAME').data()
data = c.get(r'\TAG_NAME').data()

# Compute data using TDI [link to TDI]
c.get('abs(NODE_NAME)').data() 

# Get data with timebase
values = c.get('NODE_NAME').data()
times = c.get('dim_of(NODE_NAME)').data()

# Increased performance by caching the signal in a variable
values = c.get('_sig = NODE_NAME').data()
times = c.get('dim_of(_sig)').data()

# Get the object, but watch out
# only works if the data structure in NODE_NAME doesn't reference any other nodes
# otherwise we can't evaluate it locally
# in the case of mdsthin, we can't evaluate it at all sooo
sig = c.getObject('NODE_NAME')
```

And that's basically it. You can do stuff with the data however you normally do it in python after that.

### Writing Data

`data` can be any `MDSplus.*` type or `numpy` type

```py
import numpy

data = numpy.array(...)
c.put('NODE_NAME', data)

values = numpy.array(...)
times = numpy.array(...)
data = MDSplus.Signal(values, None, times)
c.putObject('NODE_NAME', data) # SLW TODO Check


values = numpy.array(...)
times = numpy.array(...)
c.put('NODE_NAME', 'Build_Signal($, *, $)', values, times) # SLW TODO Check
```

> Move?
### GetMany

```py
gm = c.getMany()
gm.append('open', 'TreeOpen("TREE", "SHOT")')
gm.append('values', '_sig = NODE_NAME')
gm.append('times', 'dim_of(_sig)')
gm.execute()

values = gm.get('values').data()
times = gm.get('times').data()

# or
result = gm.execute()
values = result['values']
times = result['times']
```

### PutMany

> the same as above



## Tree

local/thick/distributed [link]
uses tree paths.

```py
import MDSplus
t = MDSplus.Tree('TREE', SHOT)
```

### Reading Data
Basically you get nodes, and then you can do stuff with them.
Note: For optimal performance, don't put `getNode()` in loops/during data acquisition/time sensitive, call `getNode()` before and store it in a variable.

```py

# Get the data of a node
data = t.getNode('NODE_NAME').data()
data = t.NODE_NAME.data() # The "magic" that Josh was talking about

# Get the data of a tag
data = t.getNode('\\TAG_NAME').data()
data = t.getNode(r'\TAG_NAME').data()
data = t._TAG_NAME.data() # e.g. t._IP -> t.getNode('\\IP')

# Get the data and timebase
sig = t.getNode('NODE_NAME').record # SLW check if .record or .data() is correct here
values = sig.data()
times = sig.dim_of().data()

# Don't do this. You should grab the whole object first and then get the pieces of it that way
# TODO: SLW check if this is correct. please and thank you.
# values = t.getNode('NODE_NAME').data()
# times = t.getNode('NODE_NAME').dim_of().data()

```

### Writing Data

actual recommendation for writing data during an experiment
especially segmented records
this is what devices use


```py
import numpy

data = numpy.array(...)
t.NODE_NAME.record = data
t.NODE_NAME.putRecord(data) # TODO: SLW check

values = numpy.array(...)
times = numpy.array(...)
data = MDSplus.Signal(values, None, times)
t.NODE_NAME.record = data
t.NODE_NAME.putRecord(data) # TODO: SLW check
```

#### Segmented Data

Mostly used with Devices [link to devices page].

```py
# can't (really) do this in thin client, too complicated for thin client

# segment length = # of samples per segment
# seglen is sort of a function of time, (sample rate / segment length) = # of seconds between calls to makeSegment(). so like a sample rate of 1kHz / seglen of 1000 = 1 write per sec. tuned as parameters to your device. Many little writes are more expensive than fewer larger writes.
# TODO: more from Stephen (eg, difference between makeSegment() and putSegment()). Each one of these has like 4 arguments that need to get passed. Please and thank you.

t.NODE_NAME.putRow()

t.NODE_NAME.makeSegment()
t.NODE_NAME.makeSegmentResampled()
t.NODE_NAME.makeTimestampedResampled()

t.NODE_NAME.putSegment()
t.NODE_NAME.putSegmentResampled()
t.NODE_NAME.putTimestampedResampled()
```

## mdsthin

This is basically the same as "Connection" above, just doing it in a different way. i.e., without installing MDSplus.

```sh
python3 -m pip install mdsthin
```

```py
import mdsthin
c = mdsthin.Connection('SERVER')
```

### Compatibility

```py
# import MDSplus
from mdsthin import MDSplus
# business as usual
```


```py
try:
    import MDSplus
except:
    from mdsthin import MDSplus
```

### Additional Functionality

> improved sshp://

> c.mdstcl()

> c.tdic()

> python3 -m mdsthin.mdstcl SERVER
> python3 -m mdsthin.tdic SERVER

```py
c.tcl("show version")
```