# IDL

MDSplus has an IDL API, allowing you to read, analyze, and write data to and from MDSplus trees using IDL.


## Setup

Setup consists of simply pointing IDL to the MDSplus installation folder.

The `$MDSPLUS_DIR/setup.sh` script will set the `$IDL_PATH` environment variable.
Alternatively, please also see the [instructions provided on the IDL website](https://www.nv5geospatialsoftware.com/docs/Managing_IDL_Paths.html).


When running IDL, the `print, !PATH` statement can be used to list all paths that should be searched. Please ensures that it includes the `$MDSPLUS_DIR/idl` directory.

If you are using macOS, make sure your directory is changed to where mdsplus installation folder is. The first line of your IDL script will need a reference to your MDSplus installation folder. For example: 

```
CD '/usr/local/mdsplus/lib'  (or wherever you have IDL installed)
```

> TODO: Mark W. will investigate eliminating the CD


## Commands

Once connected, the following six commands will be most essential for communicating with MDSplus through IDL.

[`mdsconnect`](#mdsconnect)
[`mdsopen`](#mdsopen)
[`mdsvalue`](#mdsvalue)
[`mdsput`](#mdsput)
[`mdsclose`](#mdsclose)
[`mdsdisconnect`](#mdsdisconnect)


### `mdsconnect`
Makes a thin client connection to the specified MDSplus data server.  Will cause subsequent invocations of `mdsopen`, `mdsvalue`, `mdsput`, and `mdsclose` to be executed remotely on the specified host. `mdsdisconnect` will destroy this connection~~~, reverting the above described routines to their local behaviors.~~~ (TODO: Mark W. to revisit after github issue#3001)

TODO: Mark W. will investigate local behavior.

Syntax: `mdsconnect, SERVERNAME [, port=PORTNAME] [, socket=ID] [, status=ISTAT] [, /quiet]`

|Parameters||
|-|-|
|`SERVERNAME`| the name (or IP address) of the computer that has an archive of MDSplus trees
|`PORTNAME`  | network port used to connect to the `mdsip` process on the `SERVER`, defaults to `8000` |
|`ID`        |output  <BR> If omitted, then disconnects from current connection, opens a new connection, and returns it in the global variable `!MDS_SOCKET` <BR> If specified, then when successfully connected to the `SERVER`, the associated `connection ID` is returned in the `ID` variable  <BR> Note: `ID`s start at zero (regardless of the API — Python, IDL, MATLAB, C, etc.) and increase by one with each new connection|
|`/quiet`| keyword: if present, suppresses IDL error message if MDSplus TCL command fails |
|`status` | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |

Example:  `mdsconnect, 'archive_server', port=8100, socket=connid, status=conn_status, /quiet`


### `mdsopen`

Open an MDSplus experiment model or pulse file

Syntax: `MDSOPEN,TREE,SHOT[,/quiet][,status=ISTAT]`
|Parameters||
|-|-|
| `TREE` | input: name of the experiment whose model or pulse file you want to open. |
| `SHOT` | input: shot number of the file. |
|`/quiet`| keyword: if present, suppresses IDL error message if MDSplus TCL command fails |
|`status` | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |
|`socket` | keyword: if present, connects to a specific socket. |

> TODO: from Mark W. Issue#2996 needs to be fixed so that Mdsopen, MdsClose and mdsput will accept the socket keyword.

### `mdsvalue`

Return the value of an MDSplus expression.

Syntax: `answer = mdsvalue(EXPRESSION[,ARG1,...,ARG16][, /quiet] [status=STAT] [socket=SOCKET])`

|Parameters||
|-|-|
| `EXPRESSION`    | input: character string containing a valid MDSplus expression
| `arg1,...,argn` | Optional input parameters. Can take up to : values to substitute into the expression where `"$"` or `"$n"` placeholders indicate. |
|`/quiet`| keyword: if present, suppresses IDL error message if MDSplus TCL command fails |
|`status` | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |
|`socket` | keyword: if present, connects to a specific socket. |

> TODO: from Mark W. Issue#2996 needs to be fixed so that Mdsopen, MdsClose and mdsput will accept the socket keyword.


Example
```
plasma_current = mdsvalue('\IP')
result = mdsvalue( '5 * 11 + $’, 15)   ; the result is 70
```

### `mdsput`
Puts data into an MDSplus tree node.

syntax: `mdsput, NODE, EXPRESSION [, ARG1 to ARG16] [, status=ISTAT] [, /quiet]`

|Parameters||
|-|-|
| `NODE`          | input: path to a node in an MDSplus tree|
| `EXPRESSION`    | input: the TDI expression is evaluated and written into `NODE`
| `ARG1 .. ARG16` | input: the expression can accept up to 16 optional arguments
| `status` | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |
| `/quiet` | keyword: if present, suppresses IDL error message if MDSplus TCL command fails |
|`socket` | keyword: if present, connects to a specific socket. |

> TODO: from Mark W. Issue#2996 needs to be fixed so that Mdsopen, MdsClose and mdsput will accept the socket keyword.

Example: `mdsput, 'top.fruit.grape.quantity', '5 * 11 + $', offset, status=ISTAT`


### `mdsclose`

Closes an open MDSplus experiment model or pulse file.

syntax: `mdsclose[,TREE,SHOT][,/quiet,status=ISTAT]`

|PARAMETERS||
|-|-|
|`TREE`       | name of the experiment used in an invocation of MDSOPEN.|
|`SHOT`       | shot number of the file. <BR>If both experiment and shot are omitted, all files will be closed. |
|`/quiet`     | keyword: if present, suppresses IDL error message if MDSplus TCL command fails |
|`status`     | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |


### `mdsdisconnect`
Disconnects from  a remote mdsplus data server.

syntax: `mdsdisconnect [, socket=ID] [, status=ISTAT] [, /quiet]`

|Parameters||
|-|-|
|`ID` | input: <BR> If omitted, disconnects the current connection. <BR> If present, disconnects the specified connection |
|`status` | output:<BR> If omitted, no status is returned. If present, then `=1` for success, `=0` for failure |
|`/quiet` | keyword: if present, suppresses IDL error message if MDSplus TCL command fails |

Example: `mdsdisconnect, socket=connid`

TODO: Mark W. investigation needed (see Issue #2996).


## example script

```idl
; CD, '/usr/local/mdsplus/lib'  ; might have to use this statement so IDL can load the MDSplus libraries
;
function mds_demo
mdsconnect, 'archive-server'
mdsopen, 'fusion', 12345
current = mdsvalue('\IP')  
return, current
end

```

TODO: Mark W. / Stephen to look at these commands:
```
The Maybe List
* Mds_keyword_set.pro
* mdsisclient.pro

The Uncertain List
* mdstcl.pro ??
```


## Troubleshooting
Make sure your IDL_PATH is set correctly; in IDL, use this command to check:

```idl
print, !PATH
```

