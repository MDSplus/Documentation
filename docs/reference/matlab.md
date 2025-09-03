# MATLAB Reference


TODO: Stephen/ will give me a skeleton
there's only like 4 functions that need to be in here:
connect, disconnect, value, mdsinfo
what arguments they accept, what they return

Mark's notes probably already have this
mdsinfo controls what bridge matlab sits on top of

why you would use them should live in the guide portion

---
Stuff from Fernando below

Worklog for 2025-08-25

Notes from Stephen to Fernando:
MATLAB Reference Guide instructions: Please provide to Mark the following:
* A list of the functions in the MATLAB MDSplus API
* These can be found by looking through the .m files in the repo
* My rough memory is that there is mdsconnect, mdsdisconnect, mdsvalue, and mdsInfo, plus Bob’s fake mdstcl wrapper
* For each of these, please provide the arguments, their types, and rough instructions on what to pass to the function, and examples for each
* This should not be exhaustive, this is just meant for people looking up a specific function, the MATLAB Guide page will crosslink to here and will provide a more user-friendly walkthrough of the API

MATLAB API:

## `mdsconnect(SERVER_NAME)`

Connects to a remote MDSplus data server. This will make a thin client connection to the specified MDSplus data server.  It will cause subsequent invocations of `mdsopen`, `mdsvalue`, `mdsput`, and `mdsclose` to be executed remotely on the specified host. `mdsdisconnect` will destroy this connection, reverting the above described routines to their local behaviors.

|Parameters| |
|--|--|
|**SERVER_NAME** | your host/server name goes here |
|**Type** | Matlab string |
|**Usage** |  mdsconnect(‘name_of_mdsplus_server’)|


```m
>> mdsconnect(‘alcdaq6’)
ans =
     1
```
# mdsclose()
% MDSCLOSE - closes currently active tree
%
%     This routine will close the tree at the top of the open tree stack.
%
%      Previous incarnations also disconnected thin-client (mdsconnect) connections.
%      THAT IS NO LONGER DONE
### Parameters
Name: -
Type: -
Usage: mdsclose()
# mdsdisconnect()
% MDSDISCONNECT  disconnect from  a remote mdsplus data server.
%      mdsdisconnect will destroy this connection, reverting the above
%      described routines to their local behaviors
### Parameters
Name: -
Type: -
Usage: mdsdisconnect()
# mdsInfo(varargin)
% MDSINFO  used internally by other functions to retrieve configuration info
### Parameters
Name: varargin
Type:
Usage:
```m
>> i=mdsInfo(0)
i =
  struct with fields:
           isConnected: 1
            connection: [1x1 MDSplus.Connection]
         connectedHost: ‘alcdata-archives’
             usePython: 0
    isPythonConnection: 0
```
```m
>> info = mdsInfo();
>> info.
connectedHost       connection          isConnected         ispy2               isPythonConnection  usePython
```
# mdsopen( EXPRESSION, SHOT )
```m
% MDSOPEN  opens a connection to a remote mdsplus data server.
%   This routine will invoke a treeopen(expt, shot)
%   expt may contain information about a remote server ‘server::expt’
```
### Parameters
```m
Names:
(1) treename
(2) shot number
Types:
(1) Matlab string
(2) Int
Usage: mdsopen(‘cmod’, 1090909009)
```
```m
>> mdsopen(‘cmod’, 1090909009)
>> a=mdsvalue(‘:ELECTRONS:TSTART’)
a =
  single
    -4
>> [a, status]=mdsvalue(‘:ELECTRONS:TSTART’)
a =
  single
    -4
status =
     1
```
# mdsput( node, expression, varargin )
% MDSPUT  put data into MDSplus tree node
%   This routine uses the java or python interface
### Parameters
Names:
(1) Node name
(2) expression
(3) varargin (does it work?) (only if the Python bridge is used, I think)
Types:
(1) Matlab string
(2) Matlab string
(3) Matlab string
Usage:
```m
>> sample = ‘“something”’
sample =
    ‘“acq_address”’
>> mdsput(‘:ACQ2106_122:ADDRESS’, sample)
ans =
     1
>> a=mdsvalue(‘:ACQ2106_122:ADDRESS’)
a =
    “acq_address”
>>
>> mdsput(‘:TEST’, ‘[1.1, 2.2]‘)
ans =
     1
>> a=mdsvalue(‘:TEST’)
a =
  2x1 single column vector
    1.1000
    2.2000
```
```m
>> mdsUsePython(false)
>> x = (0:1000)/50;
>> y = sin(x);
>> mdsput(‘:signal’,‘BUILD_SIGNAL($1,,$2)’, y, x)
ans =
     1
>>
```
# mdstcl(command)
% MDSTCL  used to run tcl command or open a tcl prompt
% This function provides Matlab with the same MDSTCL interface as IDL.
%   Written by R. Granetz on 2014/12/23
%
%   If a TCL command is passed to this routine, then execute it, output the
%   response, if any, to the terminal, and return to the Matlab prompt.  If
%   this routine is called without a TCL command, then go into a loop,
%   prompting for, and executing TCL commands, and outputting the responses,
%   until ‘exit’ is entered.
### Parameters
Name: TCL command
Type: String
Usage:
```m
>> mdstcl(‘set tree cmod’)
>> mdstcl(‘dir electrons:*’)
\ELECTRONS::TOP
 :ENG_ENCODER  :TSTART
Total of 2 nodes.
>> mdstcl(‘set tree daqtest’)
>> mdstcl(‘put test “”"e-tacq”“”’)
>> mdstcl(‘deco test’)
“e-tacq”
>>
>>
```
# mdsvalue( expression, varargin )
% Call to evaluate MDSplus expressions, i.e. TDI commands
### Parameters
Name:
(1) expression
(2) varargin
Type:
(1) Matlab string
(2) Matlab string
Usage: mdsvalue(‘TDI_expression’)
```m
>> [a, status]=mdsvalue(‘:ELECTRONS:TSTART’)
a =
  single
    -4
status =
     1
```
```m
>> sample=‘“something”’
sample =
    ‘“something”’
>> mdsput(‘:ACQ2106_122:ADDRESS’, sample)
```
# mdsUsePython
% This function allows switching between using the Java bridge and the Python bridge.
## Parameters
Name: true (1), false (0)
Type: Matlab boolean
Usage: mdsUsePython(true)
```m
>> mdsUsePython(1)
>> i=mdsInfo()
i =
  struct with fields:
           isConnected: 1
            connection: [1x1 MDSplus.Connection]
         connectedHost: ‘alcdata-archives’
             usePython: 1
    isPythonConnection: 0
                 ispy2: 0
>>
```
Helper functions:
* mdsFromMatlab
* mdsgetmsg
* mdstest
* mdsToMatlab
```m
>> mdsUsePython(true)
Unable to connect to MDSplus using python bridge, using python bridge instead
 Python error:Unable to resolve the name ‘py.MDSplus.version.ispy2’.
 ```
 $ export PYTHONPATH=$MDSPLUS_DIR/python:$PYTHONPATH
(olderpy)
fsantoro at mfews-fsantoro2 in ~
$ matlab
MATLAB is selecting SOFTWARE OPENGL rendering.
                                                                 < M A T L A B (R) >
                                                       Copyright 1984-2023 The MathWorks, Inc.
                                                  R2023b Update 6 (23.2.0.2485118) 64-bit (glnxa64)
                                                                  December 28, 2023
To get started, type doc.
For product information, visit www.mathworks.com.
>> mdsconnect(‘alcdata-archives’)
ans =
     1
```m
>> mdsUsePython(true)
Unable to connect to MDSplus using python bridge, using python bridge instead
 Python error:Unable to resolve the name ‘py.MDSplus.version.ispy2’.
>> exit
(olderpy)
fsantoro at mfews-fsantoro2 in ~
$ echo $PYTHONPATH
/usr/local/mdsplus/python:/usr/local/mdsplus/pydevices
# Error:
```m
fsantoro at mfews-fsantoro2 in ~
$ python
Python 3.10.18 (main, Jun  5 2025, 13:14:17) [GCC 11.2.0] on linux
Type “help”, “copyright”, “credits” or “license” for more information.
>>> import numpy
>>> import MDSplus
Issues loading MdsShr, trying find_library
Traceback (most recent call last):
  File “/usr/local/mdsplus/python/MDSplus/version.py”, line 105, in load_library
    return C.CDLL(os.path.basename(libnam))
  File “/home/fsantoro/miniconda3/envs/older310py/lib/python3.10/ctypes/__init__.py”, line 374, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /home/fsantoro/miniconda3/envs/older310py/bin/../lib/libstdc++.so.6: version `GLIBCXX_3.4.30' not found (required by /lib/x86_64-linux-gnu/libicuuc.so.74)
During handling of the above exception, another exception occurred:
Traceback (most recent call last):
  File “<stdin>“, line 1, in <module>
  File “/usr/local/mdsplus/python/MDSplus/__init__.py”, line 64, in <module>
    class libs:
  File “/usr/local/mdsplus/python/MDSplus/__init__.py”, line 65, in libs
    MdsShr = _ver.load_library(‘MdsShr’)
  File “/usr/local/mdsplus/python/MDSplus/version.py”, line 107, in load_library
    raise ImportError(‘Could not load library: %s’ % (name,))
ImportError: Could not load library: MdsShr
>>>
(older310py)
```
# Run for the particular Conda env:
$ conda install -n older310py gcc
$ conda install -n older310py gcc_linux-64
# Check:
$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
# Link:
fsantoro at  in ~
$ ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /home/fsantoro/miniconda3/envs/older310py/lib/libstdc++.so.6
(base)
fsantoro at  in ~
$ ls -l /home/fsantoro/miniconda3/envs/older310py/lib/libstdc++.so.6
lrwxrwxrwx 1 fsantoro unix_users 40 Aug 27 15:12 /home/fsantoro/miniconda3/envs/older310py/lib/libstdc++.so.6 -> /usr/lib/x86_64-linux-gnu/libstdc++.so.6
(base)
fsantoro at  in ~
$ conda activate older310py
(older310py)
fsantoro at x86_64-conda-linux-gnu in ~
$ echo $LD_LIBRARY_PATH
/usr/local/epics/base-7.0.6.1//lib/linux-x86_64:/usr/local/epics/base-7.0.6.1//lib/linux-x86_64::/usr/local/mdsplus/lib:/etc/alternatives/jre/lib/amd64:/usr/local/cmod/lib64:/usr/local/cmod/lib32:/usr/local/cmod/lib64:/usr/local/cmod/lib32
(older310py)
fsantoro at x86_64-conda-linux-gnu in ~
$ mdstcl
TCL> exit
(older310py)
fsantoro at x86_64-conda-linux-gnu in ~
$ python
Python 3.10.18 (main, Jun  5 2025, 13:14:17) [GCC 11.2.0] on linux
Type “help”, “copyright”, “credits” or “license” for more information.
>>> import MDSplus
>>>
```
https://mdsplus.org/index.php/Documentation:Tutorial:APIs:MATLAB






