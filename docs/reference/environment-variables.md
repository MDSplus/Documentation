# Environment Variables: Glossary

Following is a list of environment variables that are used or referenced by MDSplus. These are in no particular order, but mostly grouped by relation to each other.

#### MDS_PATH
TDI Search Path. One or more paths separated by semicolons. TDI will search each directory for `.fun` and then `.py` files matching the name of the function being searched for.

#### MDSPLUS_DIR
Path to MDSplus installation. This is used for setting a lot of other variables through `envsyms`.

#### \<tree\>_path
The path to search for the tree files for a given tree name (where `${tree}` is the name of your tree). If present, this will be used instead of `default_tree_path`. This variable can contain one or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.

These two separate variables (`$${tree}_path` and `default_tree_path`) may be useful if you are creating your own tree outside of a tree owned by your organization; the this allows you to quickly access both.

#### default_tree_path
The path to search for the tree files for a tree that does not have `${tree}_path` defined. One or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.

#### TreeHooks
Used to enable a comma-separated list of [tree hooks](tree-hooks.md).
> TODO: Write page on tree-hooks.md

#### mds_event_target
If set, TCP events will be used instead of UDP events. This contains the event server to send the TCP events to.

#### MDS_HOST
This defines the default server/host to connect to when a host is not specified to the `mdsconnect()` function.

#### TCP_WINDOW_SIZE
If set, this will be used by `setsockopt()` to set both `SO_RCVBUF` and `SO_SNDBUF` in bytes, which are two Linux OS settings.

#### MDSIP_MAX_VERSION
If set when running `mdsip`, this will be used when accepting connections to limit the MDSip protocol version. Note: this is separate from the MDSplus version. It is not recommended to set this to any value and this variable may be removed at a later date. 

#### MDSIP_SERVICE_LOGDIR
When using `mdsip_service.exe` to set up an MDSip server on Windows, this controls where the log files will be written to.

#### MDSIP_SERVER_LOGDIR 
This does not control where log files are written, but rather indicates where they already are. This is used to find available servers with wildcards in certain circumstances.

#### MDSIP_CONNECT_TIMEOUT
When set, this will be used as the timeout in seconds for all connections. If not specified, the default value is 10 seconds. 

#### UDP_EVENTS
This is deprecated and unused.

#### DEBUG_DEVICES
Setting this to a non-zero value will enable debug output from most MDSplus devices. 

#### PYDEVICE_ADD_SOURCE 
If set to `yes`, when adding a device to the tree, the python source code will be included in the tree as well. Method calls on this device node in the tree will not require the device source code to be installed.

#### MDS_PYDEVICE_PATH
This is a semicolon-separated list of paths to search for python MDSplus device source code when adding a device. Each path will be searched recursively for device classes by importing all files that end with `.py` and do not begin with `_`. Only subclasses of `MDSplus.Device` will be considered when searching.

#### MDSPLUS_VERSION_CHECK
If set to `0`, `off`, or `no` this will disable the version check when importing the MDSplus package in python. If enabled, the version check will warn if the version of MDSplus the python package was intended for is not being used.

#### PyLib
Path to the python development library, used to run python code from within MDSplus. If not specified, the default is `python2.7`.

Can accept any of the following:
* name (e.g., `python3.10`)
* filename (e.g., `libpython3.10.so`)
* full path (e.g., `/usr/lib64/libpython3.10.so`)

#### MDSPLUS_DEFAULT_RESAMPLE_MODE
Selects the resample mode to be used by default when calling (`Make`?)`PutSegmentResampled` or `SetTimeContext`. The default is `Average`.

The options are:
* `Average`
* `MinMax`
* `Interpolation`
* `Closest`
* `Previous`

>TODO: Stephen will figure out what functions use this

#### PRINTER
The default printer to use when printing a scope with `dwscope`. Defaults to `To file`.

#### MDS_LIB_PS
The path to a setup postscript file to be prepended to your document when printing. Defaults to `$MDSPLUS_DIR/lib/dwscope_setup.ps`.

#### A4PAPER
If set to any value, A4 paper dimensions (210x297mm or 8.27x11.69") will be used when printing (as opposed to 8.5x11").

#### SHELL
Used when spawning shell commands in the form of `$SHELL -c "command"`. Defaults to `/bin/sh`.

#### HISTFILESIZE
Used by `tdic` to limit the number of lines stored in the `$HOME/.tdic` history file. Refer to
[www.gnu.org/software/bash/manual/bash.html#index-HISTFILESIZE](https://www.gnu.org/software/bash/manual/bash.html#index-HISTFILESIZE). On Windows, the history file is called `%LocalAppData%\tdic`.

#### MACHINE
This will be returned by the TDI `machine()` function. Potentially indicates the fusion device the current environment is configured for.

#### MDSMSG_PATH
A single path to search for libraries which contain additional error messages.
Library files matching `$MDSMSG_PATH/*Msg.*` and containing a symbol named `getmsg` will be used.
The default is `$MDSPLUS_DIR/lib`.

>TODO: Stephen to improve this example

Example:
`libMyStatusMsg.so`
```
int getmsg(int sts, char **facnam, char **msgnam, char **msgtext)
{
    if (sts == MY_STATUS_CODE) {
        *facnam = "MY";
        *msgnam = "STATUS_CODE";
        *msgtext = "My Status Code.";
        return SUCCESS;
    }

    return FAILURE;
}
```
#### IDL_PATH
The default is `+$MDSPLUS_DIR/idl:<IDL_DEFAULT>:$IDL_PATH`.

#### MATLABPATH
The default is `$MDSPLUS_DIR/matlab:$MATLABPATH`.

#### PYTHONPATH
The default is `$PYTHONPATH:$MDSPLUS_DIR/pydevices`.

#### JavaMdsLib
Used by the `mdsobjects` java library to find `libJavaMds.*` to be passed to `System.load()`. This library contains the JNI (Java Native Interface) bindings for MDSplus.

#### UIDPATH
The default is `/usr/local/mdsplus/uid`.