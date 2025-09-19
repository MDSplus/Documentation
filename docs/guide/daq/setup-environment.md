# Setting Up Environment Variables

In order to use MDSplus, you must have the correct environment. Due to the amount and complexity of environment variables that MDSplus relies on, it contains a custom structure for managing those variables. There are setup scripts that must be correctly sourced; those setup scripts in turn call an `envsym` file to set those variables; this `envsyms` file and the configuration files that it calls are written in a custom configuration file language similar to shell script. All of these are described in further detail below.


## Setup Scripts

There are two setup scripts in the MDSplus installation directory: `setup.sh` for **bash** and **zsh**, `setup.csh` for **tcsh**. One of these scripts needs to be [`source`](https://www.linuxcommand.org/lc3_man_pages/sourceh.html)ed in order to use MDSplus. Regardless of which one you choose, the setup script will configure system environment variables such as `$PATH` and MDSplus-specific ones such as `$MDS_PATH`, both in the current process and for all subprocesses. Below are some ways to configure this so that it happens automatically. 

* To configure setup for an entire system, you may symlink the MDSplus setup script so that it is run for all login shells with this command `ln -s /usr/local/mdsplus/setup.sh /etc/profile.d/mdsplus.sh`. This is done automatically by the MDSplus installer.

* Alternatively, to configure it only for yourself or for your user, the command `source /usr/local/mdsplus/setup.sh` can be placed into your `~/.bashrc` or `~/.zshrc`, or the command `source /usr/local/mdsplus/setup.csh` can be placed into your `~/.cshrc`.

* You can also simply run one of the `source` commands whenever you want to use MDSplus.

> TODO: add info for Windows


## Configuration File Language

The setup scripts work by parsing `envsyms` (see below) and other configuration files. Those files are written in a custom custom configuration file language similar to shell script&mdash;salient details are provided here. When configuring an experiment, you may also want to add your own environment variables, which can be done once you understand how to use the configuration file language. To learn more about the default variable set, see the [next section](#envsyms) on the `envsyms` file; for a full list of environment variables that affect MDSplus, see the [environment variables reference page](environment-variables.md).

* Comment lines begin with `#`
* Empty lines are ignored
* Any white space (spaces, tabs, etc.) is fine.
    * For example: `name value` will set `$name=value`.
* Values can be wrapped in double quotation marks.
    * To clear a variable, set it to `""`
* `name`/`value` can contain environment variables.
    
    example: `MDS_PATH	$MDSPLUS_DIR/tdi` will set the variable `MDS_PATH` to `$MDSPLUS_DIR/tdi`
* The order of the files to be included is important. In the `envsyms` file below, for example, the last two `include` files can be used to store any overrides to the default envsyms that ships with MDSplus. The `include` statements at the end of the file show the order of the files as they are processed for the purpose of setting up the envsyms. 


## `envsyms`

The setup files mentioned above are in the install directory of MDSplus (usually `usr/local/local/mdsplus`). Regardless of where they live, they will use `$MDSPLUS_DIR` to configure all of the environment variables to use MDSplus. MDSplus also ships with an `envsym` file (`$inst/etc/envsyms`) that is part of the installation and future updates will overwrite this file (TODO Stephen to verify). As an example of the configuration file language and to show the default environment variable set, here is the content of the default `envsym` file:

```
#
# DO NOT MODIFY THIS FILE
#
# To add site customization use a separate configuration
# file which is included below such as:
#
# $MDSPLUS_DIR/local/envsyms
# /etc/mdsplus.conf
# $HOME/.mdsplus
#
MDS_PATH	$MDSPLUS_DIR/tdi
MDS_PYDEVICE_PATH $MDSPLUS_DIR/pydevices
PYTHONPATH      $MDSPLUS_DIR/pydevices >:
MATLABPATH      $MDSPLUS_DIR/matlab <:
UIDPATH		$MDSPLUS_DIR/uid/%U <:
IDL_PATH        \<IDL_DEFAULT\>    <:
IDL_PATH	\+$MDSPLUS_DIR/idl <:
PATH		$MDSPLUS_DIR/bin >:
MANPATH		$MDSPLUS_DIR/man: >:
MDS_LIB_PS	$MDSPLUS_DIR/lib/dwscope_setup.ps
@LIBPATH@       $MDSPLUS_DIR/lib >:
MDSMSG_PATH     $MDSPLUS_DIR/lib >;
UDP_EVENTS      yes
# Define mdsevent_address as compat when using UDP_EVENTS for compatibility with older releases.
# The old default addresses used reserved address space which are not forwarded by modern switches.
#    mdsevent_address compat
#
# The default address is now 224.0.0.175
#
# To use a different address use:
#    mdsevent_address n.n.n.n
# or mdsevent_address n.n.n.nl-nu to use addresses in the range n.n.n.nl through n.n.n.nu
# 
include         $MDSPLUS_DIR/local/envsyms
include         /etc/mdsplus.conf
include         $HOME/.mdsplus
```

It is highly recommended not to modify this file. Instead, you may save any customizations to the environment variables as separate files in one of the following:
* `$MDSPLUS_DIR/local/envsyms`
* `/etc/mdsplus.conf`
* `$HOME/.mdsplus`


## Recommendations
* It is recommended to set variables before modifying (append/prepend) them if possible. This is not always possible, e.g., `$PATH`, which is set by your system. It is possible and common for `setup.sh` to be run multiple times for various reasons. This will prevent environment variables from getting duplicates appended to it. 

    * `name value dir|sep` When you have a list of things in an environment variable, they are often separated by colons or semicolons, and when you are modifying a list, you will want to prepend or append.

    * `dir` can be `<` to prepend or `>` to append. `sep` is usually either a colon or semicolon, but can be any string as long as it does not contain spaces. The documentation at the top of `setup.sh` is up to date and should be helpful.

    * Example: `IDL_PATH \<IDL_DEFAULT\> <:` will prepend `\<IDL_DEFAULT\>` to the beginning of `IDL_PATH` separated by a colon, so it will look like this:

        `\<IDL_DEFAULT\>:IDL_PATH`
    
        Then, running the command `IDL_PATH \+$MDSPLUS_DIR/idl <:` immediately afterwards will repeat the process, and the final result will be:
        
        `\+$MDSPLUS_DIR/idl:\<IDL_DEFAULT\>:IDL_PATH`

* `include` followed by a filename will do this process recursively (see bottom of file `setup.sh`, above). If the file you are including doesn't exist, it won't return an error, it will just keep going. This is a feature is useful when setting up multiple servers, for example (see examples below).

* It is recommended that you create a directory called `$MDSPLUS_DIR/local` and inside of it, a file called `envsyms`. We recommend you put your experiment's configuration in `$MDSPLUS_DIR/local/envsyms`. You can have multiple files here and include them with `include` if you like.

* If you have networked computers that are meant to work on these trees, we recommend making the local directory an NFS mount so that the configuration can be shared among all computers. This can also be accomplished with various system management tools.


## Examples

### Scenario 1: Set up a server for local tree access
The config file will simply look like this:

`$MDSPLUS_DIR/local/envsyms`
```
default_tree_path   /path/to/trees/~t
```

### Scenario 2: Shared configuration used on both servers and clients
The problem to solve with your config files is that the `default_tree_path` cannot point to itself or else the server will recursively connect to itself.


`$MDSPLUS_DIR/local/envsyms` mounted everywhere
```
MDSIP_SERVER myserver::

# This will only exist on myserver
include /etc/trees.conf

default_tree_path   $MDSIP_SERVER/path/to/trees/~t
```

`/etc/trees.conf` on myserver
```
MDSIP_SERVER ""
```

On myserver you will get
`default_tree_path=/path/to/trees/~t`
and on a client you will get
`default_tree_path=myserver::/path/to/trees/~t`

### Scenario 3: Multiple Servers

Lets say you have servers for new, models, and archive; this is useful to separate the functions to different servers. Note that myserver1 is used for two of these functions. When a shot is created, it will be put in the first writeable location in the tree path, so we put "new" at the beginning of the tree path. We do not want new shots to go into models so it should not go at the front of the path. Searching the archive might take a lot of time, so we want to put that at the end.


`$MDSPLUS_DIR/local/envsyms` mounted everywhere
```
MDSIP_SERVER_NEW     myserver1::
MDSIP_SERVER_MODELS  myserver1::
MDSIP_SERVER_ARCHIVE myserver2::

include /etc/trees.conf

default_tree_path   $MDSIP_SERVER_NEW/path/to/new/~t
default_tree_path   $MDSIP_SERVER_MODELS/path/to/models/~t >;
default_tree_path   $MDSIP_SERVER_ARCHIVE/path/to/archive/~t >;
```

`/etc/trees.conf` on myserver1
```
MDSIP_SERVER_NEW    ""
MDSIP_SERVER_MODELS ""
```

`/etc/trees.conf` on myserver2
```
MDSIP_SERVER_ARCHIVE ""
```

So, on **myserver1** you will have:
`default_tree_path=/path/to/new/~t;/path/to/models/~t;$MDSIP_SERVER_ARCHIVE/path/to/archive/~t`

On **myserver2** you will have:
`default_tree_path=$MDSIP_SERVER_NEW/path/to/new/~t;$MDSIP_SERVER_MODELS/path/to/models/~t;/path/to/archive/~t`

And on a **client** you will have:
`default_tree_path=$MDSIP_SERVER_NEW/path/to/new/~t;$MDSIP_SERVER_MODELS/path/to/models/~t;$MDSIP_SERVER_ARCHIVE/path/to/archive/~t`