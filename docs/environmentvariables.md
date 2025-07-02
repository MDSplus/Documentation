# Environment Variables: Glossary

# Core
## MDSPLUS_DIR
Path to MDSplus installation. This is used for setting a lot of other variables through `envsyms`.

## MDS_PATH
TDI Search Path. One or more paths separated by semicolons. TDI will search left-to-right for `.fun` or `.py` files matching the name of the function being searched for.

# Trees
## $${tree}_path
The path to search for the tree files for a given tree name (where `${tree}` is the name of your tree). If present, this will be used instead of `default_tree_path`. This variable can contain one or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.

These two separate variables (`$${tree}_path` and `default_tree_path`) may be useful if you are creating your own tree outside of a tree owned by your organization; the this allows you to quickly access both.


## default_tree_path
The path to search for the tree files for a tree that does not have `${tree}_path` defined. One or more paths separated by semicolons. Each path to search can be anything defined elsewhere in this documentation.

## mds_event_target
If set, TCP events will be used instead of UDP events. This contains the event server to send the TCP events to.

## MDS_HOST
This defines the default server/host to connect to when a host is not specified to the `mdsconnect()` function.

## TCP_WINDOW_SIZE
If set, this will be used by `setsockopt()` to set both `SO_RCVBUF` and `SO_SNDBUF` in bytes, which are two Linux OS settings.

## MDSIP_MAX_VERSION
If set when running `mdsip`, this will be used when accepting connections to limit the MDSip protocol version. Note: this is separate from the MDSplus version.

## MDSIP_SERVICE_LOGDIR
When using `mdsip_service.exe` to set up an MDSip server on Windows, this controls where the log files will be written to.

## MDSIP_SERVER_LOGDIR 
This does not control where log files are written, but rather indicates where they already are. This is used to find available servers with wildcards in certain circumstances.

## MDSIP_CONNECT_TIMEOUT
When set, this will be used as the timeout in seconds for all connections. If not specified, the default value is 10 seconds. 

## UDP_EVENTS
This is deprecated and unused.

## DEBUG_DEVICES
Setting this to a non-zero value will enable debug output from most MDSplus devices. 

## PYDEVICE_ADD_SOURCE 
If set to `yes`, when adding a device to the tree, the python source code will be included in the tree as well. Method calls on this device node in the tree will not require the device source code to be installed.

## MDS_PYDEVICE_PATH
This is a semicolon-separated list of paths to search for python MDSplus device source code when adding a device. 
> To Do: explain how path is searched. (More TK Stephen)

## PRINTER
The default printer to use when printing a scope with `dwscope`. Defaults to `To file`.

# MDS_LIB_PS
The path to a setup postscript file to be prepended to your document when printing. Defaults to `$MDSPLUS_DIR/lib/dwscope_setup.ps`.

## A4PAPER
If set to any value, A4 paper dimensions (210x297mm or 8.27x11.69") will be used when printing (as opposed to 8.5x11").

## SHELL
Used when spawning shell commands in the form of `$SHELL -c "command"`. Defaults to `/bin/sh`.

## MACHINE
This will be returned by the TDI `machine()` function. Potentially indicates the fusion device the current environment is configured for.