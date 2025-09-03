# MATLAB API Reference

Below are the main commands you can use in your MATLAB scripts to get and put information into MDSplus. See the the main MATLAB guide (TODO: link here) for more information on how to set up MATLAB to work with MDSplus.

## `mdsconnect(SERVER_NAME)`

Connects to a remote MDSplus data server. This will make a thin client connection to the specified MDSplus data server.  It will cause subsequent invocations of `mdsopen`, `mdsvalue`, `mdsput`, and `mdsclose` to be executed remotely on the specified host. `mdsdisconnect` will destroy this connection, reverting the above described routines to their local behaviors.

|Parameters| |
|----------|-|
|SERVER_NAME | your host/server name goes here |
|Type | Matlab string |
|Usage |  `mdsconnect('name_of_mdsplus_server')`|


```m
%%% TODO: discuss with group a sanitized example server name "my_archive_server1" or an ip address like "123.456.78.9" or something
>> mdsconnect('alcdata-archives')  
ans =
     1
```


## `mdsclose()`
Closes currently active tree.

| Parameters ||
|------------|-|
|Name | - |
|Type | - |
|Usage | `mdsclose()` |


## `mdsdisconnect()`
Disconnect from  a remote mdsplus data server.
%      mdsdisconnect will destroy this connection, reverting the above
%      described routines to their local behaviors
| Parameters ||
|-|-|
| Name | - |
| Type | - |
| Usage | `mdsdisconnect()` |


## `mdsInfo(varargin)`
Used internally by other functions to retrieve configuration information.

|Parameters| |
|-|-|
|Name | varargin "variable argument in" (it's a matlab thing...you can pass multiple3 arguments in... |
|     | TODO: Fernando will do more research on this) |
|Type | - |
|Usage| see below |

> TODO: more to come from Fernando

```m
>> i=mdsInfo(0)
i =
  struct with fields:
           isConnected: 1
            connection: [1x1 MDSplus.Connection]
         connectedHost: 'alcdata-archives'
             usePython: 0
    isPythonConnection: 0
```

```m
>> info = mdsInfo();
>> info.
connectedHost       connection          isConnected         ispy2               isPythonConnection  usePython
```

## `mdsopen(EXPRESSION, SHOT)`
Opens a connection to a remote mdsplus data server. 

TODO: figure out if this is too much info:
This routine will invoke a treeopen(expt, shot). 
`expt` may contain information about a remote server 'server::expt'

TODO: ask Fernando to explain this to me again.

|Parameters | |
|-|-|
|EXPRESSION | can be a treename (MATLAB string) |
|           | can also be a server if separated by double colons (for example: `server::expt`) |
|SHOT       | shot number (Int)                 |
|Usage      | `mdsopen('cmod', 1090909009)` |
|           | also see below for other usage cases  |


```m
>> mdsopen('cmod', 1090909009)
>> a=mdsvalue(':ELECTRONS:TSTART')
a =
  single
    -4
>> [a, status]=mdsvalue(':ELECTRONS:TSTART')
a =
  single
    -4
status =
     1
```
## `mdsput(NODE, EXPRESSION, VARARGIN)`
Puts data into an MDSplus tree node. This routine uses the java or python interface, which you must choose with `mdsUsePython` (see also: `mdsUsePython` [TODO: link]).

| Parameters ||
|-|-|
| Node       |Matlab string|
| expression |Matlab string|
| varargin   |Matlab string|
||TODO: Fernando to do more testing. (does it work? only if the Python bridge is used...maybe)|
|Usage|see below|


```m
>> sample = '"something"'
sample =
    '"acq_address"'
>> mdsput(':ACQ2106_122:ADDRESS', sample)
ans =
     1
>> a=mdsvalue(':ACQ2106_122:ADDRESS')
a =
    "acq_address"
>>
>> mdsput(':TEST', '[1.1, 2.2]')
ans =
     1
>> a=mdsvalue(':TEST')
a =
  2x1 single column vector
    1.1000
    2.2000
```

```m
>> mdsUsePython(false)
>> x = (0:1000)/50;
>> y = sin(x);
>> mdsput(':signal','BUILD_SIGNAL($1,,$2)', y, x)
ans =
     1
>>
```


## `mdstcl(COMMAND)`
Run TCL command or open a TCL prompt. This function provides Matlab with the same MDSTCL interface as IDL. (See also: [MDSTCL](mdstcl.md))
* If a TCL command is passed to this routine, it will execute, output the response, if any, to the terminal, and return to the MATLAB prompt. 
* If this routine is called without a TCL command, then it will go into a loop of prompting for, executing TCL commands, and outputting the responses, until `exit` is entered.

|Parameters| Type |
|-|-|
|COMMAND   | String |
|Usage     | see below|

```m
>> mdstcl('set tree cmod')
>> mdstcl('dir electrons:*')
\ELECTRONS::TOP
 :ENG_ENCODER  :TSTART
Total of 2 nodes.
>> mdstcl('set tree daqtest')
>> mdstcl('put test """e-tacq"""')
>> mdstcl('deco test')
"e-tacq"
>>
>>
```

## `mdsvalue(expression, varargin)`
Call to evaluate MDSplus expressions, i.e. TDI commands.

| Parameters| Type |
|-|-|
| expression | MATLAB string |
| varargin | MATLAB string |
|Usage | `mdsvalue('TDI_EXPRESSION')` |

```m
>> [a, status]=mdsvalue(':ELECTRONS:TSTART')
a =
  single
    -4
status =
     1
```

```m
>> sample='"something"'
sample =
    '"something"'
>> mdsput(':ACQ2106_122:ADDRESS', sample)
```

## `mdsUsePython (true/false)`
This function allows switching between using the Java bridge and the Python bridge. The default (`false`) is Java. 

| Parameters ||
|-|-|
| Arguments | true (1), false (0) |
| Type      | Matlab boolean|
| Usage     | `mdsUsePython(true)` or `mdsUsePython(1)` for Python|
|           | `mdsUsePython(false)` or `mdsUsePython(0)` for Java |

```m
>> mdsUsePython(1)
>> i=mdsInfo()
i =
  struct with fields:
           isConnected: 1
            connection: [1x1 MDSplus.Connection]
         connectedHost: 'alcdata-archives'
             usePython: 1
    isPythonConnection: 0
                 ispy2: 0
>>
```



