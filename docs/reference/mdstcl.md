# TCL Commands

For use with `mdstcl` TCL (MDSplus Tree Command Language) 
This information also resides the help text for the program (simply type in `help`). Reproduced here for convenience and edited for clarity.
https://github.com/MDSplus/mdsplus/blob/alpha/xml/tcl_commands.xml

Notes:
* Commands are not case sensitive.
* Sometimes you will need to encase things in triple double quotation marks (`"""like this"""`). This is how you wrap TDI expressions. 
* Commands and flags can be abbreviated to a point of disambiguation. (So `show version` can be simply typed as `sho ver` to save time)

Tree Command Language (TCL) is used for MDSplus tree examination and manipulation.  TCL can be used to examine the tree structure, store data to or get data from nodes, examine or change node properties, or clean or compress the datafile associated with a tree. These commands are listed when you type:

    help tree commands

TCL can also be used for dispatching commands or actions to action servers
or to directly execute actions or methods provided by devices described in
the tree. For help on dispatching related commands, type:

    help dispatch commands

With TCL using edit commands you can create a new tree structure or modify
an existing one by adding, deleting or renaming nodes and adding tagnames
to give direct addressing of nodes in the tree. For edit commands, type:

    help edit commands

TCL can also issue and wait for MDSplus events. See:

    help wfevent
    help setevent

TCL can display device information. See:

    help devices


## Edit Commands

The following commands are available for editing the structure of an MDSplus tree:

| Command                 | Description                                                 |
|-------------------------|-------------------------------------------------------------|
| [`add node`](#add-node) | Add a node to an MDSplus tree.                              |
| `add tag`               | Assign a tagname to a node in the tree.                     |
| `delete node`           | Delete a node in an MDSplus tree.                           |
| `edit`                  | Open a tree or create a new tree for subsequent editing.    |
| `remove tag`            | Remove a tagname.                                           |
| `rename`                | Rename a node in a tree.                                    |
| `set readonly`          | Mark tree as readonly. No changes to data or nci permitted. |
| `set versions`          | Enable data version support in a tree.                      |
| `write`                 | Write out a modified tree committing edit changes.          |


Type `HELP` command-name for more information on the command or `HELP TREE COMMANDS` or `HELP DISPATCH COMMANDS` for info on additional commands.




## Tree Commands

The following commands are available for viewing or manipulating data and attributes of nodes in a tree:

| Command | Description |
|---------|-------------|
| `clean`          | Clean the datafile of a tree reclaiming unused space. |
| `close`          | Close one or more trees currently open by this process. |
| `compress`       | Compress a datafile by compressing data records. |
| `create pulse`   | Create a new pulse file. |
| `decompile`      | Decompile the data stored in a node. |
| `delete pulse`   | Delete a pulse file. |
| `directory`      | List the nodes in a tree. |
| `directory/tag`  | List the tagnames in a tree. |
| `put`            | Store data in a node. |
| `set attribute`  | Set an extended attribute for a node. |
| `set current`    | Set the current shot number fo a tree. |
| `set default`    | Change the current location in a tree. |
| `set node`       | Modify node characteristics in an MDSplus tree. |
| `set tree`       | Open an MDSplus tree. |
| `set view`       | Specify a point in time for examining the tree. This command only applies to trees with versioning enabled. |
| `show attribute` | Show an extended attribute for a node. |
| `show current`   | Show the current shot for a tree. |
| `show data`      | Show the data structure stored in a node. |
| `show db`        | Show the tree currently opened. |
| `show default`   | Show the current location in a tree. |
| `show versions`  | Show whether or not versioning is enabled in the tree. |
| `verify`         | Verify the tree structure of an MDSplus tree. |
    

## Dispatch Commands

The following commands are available for dispatching or executing actions in an MDSplus tree.

| Command            | Description                                                       |
|--------------------|-------------------------------------------------------------------|
| `abort server`     | Abort the action currently executing in an action server.         |
| `dispatch`         | Dispatch an action node to an action server.                      |
| `dispatch/build`   | Build a dispatch table in preparation for dispatch action phases. |
| `dispatch/check`   | Determine if all essential actions completed successfully.        |
| `dispatch/close`   | Tell all action servers used to close all tree.                   |
| `dispatch/command` | Dispatch a commands to an action server.                          |
| `dispatch/phase`   | Dispatch the actions associated with an experiment phase.         |
| `do`               | Execute an action in a tree.                                      |
| `do/method`        | Execute a method provided by a device in a tree.                  |
| `show server`      | Show the current status of an action server.                      |
| `stop server`      | Stop an action server.                                            |






## In-Depth Descriptions

> STYLE NOTE: all caps, underscore, no angle brackets <>

###  `devices [DEVICE_TYPE] [/full]`
Obtains information about a python device support module. 
* If the `DEVICE_TYPE` parameter is omitted, a list of all the available python devices will be displayed.
* If the `DEVICE_TYPE` contains a wildcard character, such as an asterisk, the devices matching that wildcard will be listed.
* The `/full` qualifier will show the full python help for the device class.

### `abort server SERVER1[,SERVER2[,SERVER3...]]`
Aborts the action currently being executed by an MDSplus action server. Actions are executed in servers when dispatched using the `dispatch` command.

### `add node NODE_PATH [/usage=USAGE]|[/model=DEVICE_TYPE]`
Adds a new node to an MDSplus tree which has been opened using the `edit` command.
* The `NODE_PATH` parameter specifies the name of the new node to be added. It can be an absolute node path or a relative node path. If the path name includes parent nodes, those parent nodes must already exist or the command will fail. Node names must begin with an alphabetic character followed by zero or more alphanumeric or underscore characters. The node name must be 12 characters or less in length.
* The `/usage` qualifier specifies a usage type of the node. This must be one of: `action`, `any`, `axis`, `compound_data`, `device`, `dispatch`, `numeric`, `signal`,   `structure`, `subtree`, `text`, or `window`. If not specified, a member node `(:name)` will default to usage `any`, and a child node `(.name)` will default to usage `structure`.
* If adding a device (e.g., data acquisition device) use the `/model` qualifier to specify the type of supported device you are adding.
* **Note**: The `add node` command can only be used when a tree is opened for edit.

### `add tag NODE_PATH TAG_NAME`
Adds a tagname to a node. A tagname can be thought of as a shortcut for referencing a node in a tree, saving you from entering the full path location of the node. For example, if a node has a tagname of "ip" you could reference that node by using `\ip` or `\treename:ip`.
* The tagname must be unique for a given tree.
* Tagnames can be up to 23 characters in length and must consist of an alphabetic character followed by up to 22 alphanumeric or underscore characters.
* **Note**: The `add tag` command can only be used when you have opened the tree using the `edit` command.

### `clean TREE_NAME [/shot=SHOT_NUMBER]`
Recovers wasted space in the tree's datafile.

* As data is written to a tree, if the record is greater than 16 bytes in length, it is appended to the end of the tree's datafile. When the data in a node is modified, unless the size of the data is exactly the same length as was previously stored, the new data is appended at the end of the datafile. The previous data continues to occupy its original space in the datafile but will not be reused. The `clean` command can be used to recover this wasted space.
* When the `clean` command is issued, the datafile is recreated by reading in the current data for each node and writing it to the new datafile, thus discarding the orphaned data in the file.
* The `clean` command is similar to the `compress` command except the `compress` command will also employ data compression on the data records, often drastically reducing the file size if the nodes were not set to be compressed on put.
* Since both the `clean` and `compress` command create new datafiles, it is recommended that they only be used when there is unlikely to be any other write activity on the tree.
* **Note**: The shot number may be expressed as a TDI expression. For example, `clean cmod/shot="current_shot(""cmod"")-1"`

### `close [TREE_NAME [/shot=SHOT_NUMBER]]|[/all][/confirm]`
Closes the current tree or all open trees. 

* Using the `close` command without any parameters or qualifiers will close the last tree opened with either a `set tree` command or an `edit` command.

* Since TCL will keep a stack of previously opened trees; you can selectively close a particular tree by adding treename and shot number as parameters. To close all the trees, add the `/all` qualifier. To determine which trees you currently have open, use the `show db` command.

* **Note**: You must use the `write` command on a tree opened using the `edit` command if you want to save any edits you might have done to that tree before using the `close` command to close it. If you attempt to close a tree with edit modifications you will get an error unless you force the close using the `/confirm` qualifier. If you close and modified tree with the `/confirm` qualifier, the tree will be closed and any edit modification will be discarded.

* **Note**: The shot number may be expressed as a TDI expression. For example,
`close cmod/shot="current_shot(""cmod"")-1"`

### `compress TREE_NAME [/shot=SHOT_NUMBER]`
Recovers wasted space and compresses the tree's datafile.

* As data is written to a tree, if the record is greater than 16 bytes in length, it is appended to the end of the tree's datafile. When the data in a node is modified, unless the size of the data is exactly the same length as was previously stored, the new data is appended at the end of the datafile. The previous data continues to occupy its original space in the datafile but will not be reused. The `compress` command can be used to recover this wasted space.
* When the `compress` command is issued, the datafile is recreated by reading in the current data for each node and writing it to the new datafile, thus discarding the orphaned data in the file.
* The `compress` command is similar to the `clean` command except the `compress` command will also employ data compression on the data records, often drastically reducing the file size if the nodes were not set to be compressed on put.
* Since both the `clean` and `compress` command create new datafiles, it is recommended that they only be used when there is unlikely to be any other write activity on the tree.
* **Note**: The shot number may be expressed as a TDI expression. For example, `clean cmod/shot="CURRENT_SHOT(""cmod"")-1"`


### `create pulse SHOT_NUMBER [/include=(SUBTREE1,SUBTREE2,...)] [/exclude=(SUBTREE1,SUBTREE2,...)] [/conditional] [/nomain]`
Copies the currently open tree (usually the model, shot -1) into a pulse file.

The `create pulse` command will copy the currently opened tree and all its subtrees (unless the optional qualifiers are specified) to pulses with the specified shot number.

* The `/include`, `/exclude`, `/conditional`, and `/nomain` qualifiers can be used to customize which trees will be included in the new pulse files.
* Specifying the `/conditional` qualifier will cause the command to examine the "include in pulse" characteristic (set by `set node` command and view by the `dir /full` command) of the subtree nodes to decide if that subtree should be included.
* The `/include` and `/exclude` qualifiers can take a list of node paths to specify which subtree nodes to include or exclude.
  * If the `/include` qualifier is specified only the subtrees specified will be included.
  * If the `/exclude` qualifier is specified, all but the subtrees specified will be included.
* If the `/nomain` qualifier is included, the top-most tree will not be included in the new pulse files.
* **Note**: The shot number may be specified as a TDI expression such as `"current_shot(""cmod"")+1"`.

### `decompile NODE_PATH`
Display the contents of a node in the tree. If the data converted to a string exceeds approximately 30,000 characters, the string representation of large arrays will be truncated.

### `define server/tree=(TREE_NAME1[,TREE_NAME2...]) SERVER_NAME`
This command has been removed.
<!-- * **Purpose**:  The `define server` command specifies an MDSplus server to be responsible for creating pulse files for particular tree(s).

* **Description**: The `define server` command specifies actions server which should be used for creating MDSplus pulse files for particular trees. The server definitions are used by the CREATE PULSE command to distribute the pulse creation to distributed servers. For more information on this see HELP CREATE PULSE. -->


### `delete node NODE_PATH[,NODE_PATH...] /log /confirm /dryrun`
* Deletes one or more nodes from an MDSplus tree which has been opened for edit using the `edit` command.
* The `/log` qualifier can be used to display the nodes being deleted.
* The `/confirm` qualifier must be included to delete a node which has descendants or is part of a device (conglomerate) representation in the tree because deletion of that node will result in multiple nodes being deleted.
* If you attempt to delete a node which has descendants or is part of a device (conglomerate) representation in the tree, then the deletion of the node will result in multiple nodes being deleted. If this is your intention, then you must include the `/confirm` qualifier on the command.
* The `/dryrun` qualifier can be used to just display the nodes that would be deleted without actually deleting any nodes.


### `delete pulse SHOT_NUMBER`
Deletes an MDSplus pulse file instance of the currently opened tree. The `delete pulse` command will delete the three files making up an MDSplus tree for the specified shot number.

**Note**: If the currently opened tree includes subtrees, those subtrees will also be deleted for that shot number.

  For example:

  ```
  TCL> SET TREE cmod
  TCL> DELETE PULSE 42
  ```

This would delete the cmod pulse files for shot number 42 as well as any subtrees of the cmod tree with shot number 42.

### `directory [NODE_PATH_WILD1[,NODE_PATH_WILD2,...]] [/full] [/usage=USAGE] [/usage=(USAGE1,USAGE2,...)]`

The `directory` command is used to list one or more nodes in the currently opened tree. You can specify one or more node paths which may include wildcard characters. If no node paths are specified, it defaults to listing the member and child nodes in the current location of the tree (See: `set default` command).

* If the `/full` qualifier is included, then detailed information about each node is shown.

* Use the `/usage` qualifier if you want to list only nodes of a certain usage. Usage names include `action`, `any`, `axis`, `compound_data`, `device`, `dispatch`, `numeric`, `signal`, `structure`, `subtree`, `text`, or `window`.

### `directory/tag [TAG_NAME_WILD] [/PATH]`
List tagname definitions in the tree. A wildcard string parameter can be included to list only the tags matching the wildcard string (e.g.,: `directory/tag MYT*G`).

If the `/path` qualifier is included, the full paths of the nodes pointed to by the tagname will also be displayed.

See `add tag` for more information.


### `dispatch ACTION_NODE_PATH [/wait]`
The `dispatch` command is used to dispatch an action node to an action server. If the `/wait` qualifier is included, the command will wait for the action execution to complete.


### `dispatch/build [/monitor=ACTION_SERVER]`
The `dispatch/build` command finds all the actions in a tree which are currently turned on and builds a sorted table of those actions.
* Actions are grouped by phase and ordered by sequence numbers. Actions which are configured to be dispatched based on dependency expressions are also identified. 
* The `dispatch/phase` command utilizes this table when deciding which actions and in which order they should be dispatched to action servers.
* The `/monitor` qualifier is used to send messages to an action monitor server which are in turn transmitted to `actmon` processes, which display the current status of data acquisition actions being performed.


### `dispatch/check [/reset]`
Returns a failure status if the failed essential flag is set successfully.

When data acquisition phases are dispatched, a failure flag is set if any action marked as essential (see the `set node` command) fails during execution. The `dispatch/check` command checks on the current state of that failure flag. If the flag is set, the `dispatch/check` command will return a failure status, otherwise it will return a success status.

If the `/reset` qualifier is used, the failure flag will be reset after the check is made so that subsequent `dispatch/check` commands will return a success status unless another essential action subsequently fails before the next `dispatch/check` command is issued.


### `dispatch/phase phase-name [/noaction] [/synch=N] [/log] [/monitor=MONITOR_SERVER]`
This command dispatches all actions assigned to a named phase to action servers for execution.
  * This command uses the action table created by a `dispatch/build`, therefore a `dispatch/build` command must be given before using the `dispatch/phase` command for any pulse file.
  * Actions are dispatched in order of the action's sequence number, or if the sequence is an expression containing other nodes, the action will be dispatched if all the actions in the expression have completed and the expression evaluates to a true value.

* The `/synch` qualifier can be used to synchronize all action servers based on the sequence numbers of the actions.
  * Without the `/synch` qualifier, all actions matching the phase specified are dispatched immediately to all the action servers in order of the sequence numbers. Each action server maintains a queue of actions and will execute those actions one after the other until all the actions in its queue have been executed.
  * With the `/synch` qualifier, the actions will be dispatched in groups of the synch value, thus synchronizing the actions across multiple servers. For example, a `/synch=10` specification would cause the DISPATCH/PHASE command to dispatch all the actions with sequence numbers 1 through 10 to be dispatched to their designated action servers in sequence order. No other actions will be dispatched to action servers until this first "batch" have all completed. Then sequence numbers 11-20 would then be dispatched. This ensures that an action with sequence number 15 would on one server would not be executed before one with sequence number 10 on another server. This is often critical during the initialization phase where certain types of modules such as triggering devices must be initialized before data acquisition devices that they trigger are armed.

* The `/log` qualifier will output log messages of actions being dispatched, started, and completed. The `/noaction` qualifier can be used with the `/log` qualifier to log what would be dispatched, but no actions would actually be dispatched.

* The `/monitor` qualifier is used to specify an action monitor action server which is used to relay action activity to actmon processes which display the status of action execution.


### `dispatch/close[/server=(SERVER1,SERVER2...)]`
The `dispatch/close` command can be used to instruct an MDSplus action server to close all MDSplus trees that the server currently has open.

* If the `/server` qualifier is not included to specify any action servers, then the current dispatch table (See: `dispatch/build` and `dispatch/phase` commands) is inspected to construct a list of servers that had actions dispatched to them to send close instructions to.

* The `dispatch/close` command is typically used at the end of a data acquisition cycle to instruct the action server to close any open trees.


### `dispatch/command/server=SERVER_NAME[/wait][/table=COMMAND_TABLE] COMMAND_TO_EXECUTE`
Dispatches an mdsdcl command to a server for execution by the server process.

* The command will be executed asynchronously unless the `/wait` qualifier is included in the command.

* The `/table` qualifier can be used to specify a command table to use. If the `/table` qualifier is omitted then the command will be assumed to be a TCL or MDSDCL command.


### `do ACTION_NODE_PATH`
Executes an action node in a tree in the context of the current process. This can be useful for debugging actions but care must be taken that you are attempting to execute the action on a host which can actually execute the action. The action may need to access data acquisition hardware which might only be accessible by the host specified in the action so attempting to execute the action on another node would likely generate errors.

### `do/method DEVICE_NODE_PATH method [/arg="EXPRESSION"] [/if=EXPRESSION] [/override]`
Executes a method of a device represented in the tree.

The `do/method` command is used to perform a method supported for the device type of the device collection of nodes in a tree. When using the `do/method` command you can specify any node in that device to identify the device. Like to `do` command, you must be careful that the device you are trying to operate is accessible on the host where you are executing the command as the method is executed in your current process context. 

* The `/arg` qualifier lets you supply one or more arguments to the method. The arguments must be in the form of an tdi expression. If you need to pass a string argument you would do a command such as: 

  ```sh
  TCL> do/method MYDEVICE init /arg="""MYSTRING"""
  ```

  Multiple arguments can be passed using the syntax:

  ```sh
  TCL> do/method MYDEVICE init /arg=(1,"""mystring""",42)
  ```

* The `/override` qualifier is use to override the current on/off status
of the device in the tree. If the device nodes are turned off and the
`/override` qualifier is not present, then no action will be performed.

* The `/if` qualifier can be used to provide an expression. The method will
then only be executed if the evaluation of the expression generates


### `edit TREE_NAME [/shot=SHOT_NUMBER] [/new]`
Edit or create an MDSplus tree file. Before you can edit or create a tree file you must have `treename_path` environment variable set to define the location of the tree files (e.g., mytree_path=/home/me/mytreedir).

* The `/shot` qualifier is used to specify a shot number to edit or create. If the `/shot` qualifier is not specified, the `edit` command will default to shot number -1, the "model" tree.

* If the `/new` qualifier is specified then a new empty tree will be created overriding any existing tree if one exists.

* **Note**: Once you are done editing a tree you must use the `write` command to save any
structural changes you might have made to the tree.


### `put NODE_PATH (EXPRESSION | [/extended] [/lf] [/eof=XXX])`
The PUT command is used to store data into a node in an MDSplus tree.

* The EXPRESSION parameter is compiled into a tdi expression and stored into the node. 
* If the `/extended` qualifier is specified, the expression string will be read from subsequent input lines until either an `EOF` string is read or a zero length line is read.
* If the `/lf` qualifier is used with the `/extended` qualifier, the line feeds at the end of each line will be included in the expression.
* The `/lf` qualifier is generally only useful if the expression is a quoted string containing line feeds.
* The `/eof` qualifier can be used to specify an `eof` string which would terminate the expression input. If the expression has zero length, the node will be emptied of its data. 


Examples:
```sh
# Store an integer, 42, in a node:
TCL> put MY_NODE 42

# Empty a node:
TCL> put MY_NODE ""    

# Store a text string:
TCL> put MY_NODE ""this is a string""

# Store an integer:
TCL> put/extend MY_NODE
PUT> 42
PUT>

# Store an integer with units:
TCL> put/extend MY_NODE  
PUT> build_with_units(42,"volts")
PUT>

TCL> put/extend/lf MY_NODE
PUT> "This is a test
PUT> with line feeds in the text"
```

### `remove tag TAGNAME`
Removes a tagname from a node. The tree must be opened by the `edit` command. The changes must be preserved by issuing a `write` command before closing the tree with the `close` command.     


### `rename OLD_NODE_PATH NEW_NODE_PATH [/log]`
Renames a node in an MDSplus tree. Before the `rename` command can be used, the tree must be opened with the `edit` command. If the NEW_NODE_PATH specified contains parent nodes, those parent nodes must already exist or the rename command will fail. The changes must be preserved by issuing a `write` command before closing the tree with the `close` command.

The `/log` qualifier can be used to display log messages indicating the rename operation.

### `set attribute NODE_PATH /name=ATTRIBUTE_NAME (VALUE | /extended)`
The `set attribute` command will add an attribute to a node as named with the `/name` qualifier. These are also called Extended Attributes or XNCI (eXtended Node Characteristic Information).
* The `VALUE` argument is used to specify the value of the named attribute and is compiled as a TDI expression. 
* The `/extended` qualifier can be specified to enable you to supply the expression content in following lines ended by a blank line. This provides an easy way to add quoted strings that would otherwise require special handling in the main command line.
* See also: `show attribute`

Examples:

```sh
# set two attributes, one with an int, one with an expression
TCL> set attribute MYNODE /name=special 42
TCL> set attribute MYNODE /NAME=myattr/EXTENDED
build_with_units(42,"volts")
TCL> 

# show contents of each one
TCL> show attribute MYNODE /name=special
42
TCL> show attribute MYNODE /name=myattr
BUILD_WITH_UNITS(42,"volts")

# show which attributes are defined for the node
TCL> show attribute MYNODE
Defined attributes for this node:
myattr
special
```

### `set current TREENAME (SHOT_NUMBER_EXPRESSION | /increment)`
This command is used to designate a "current" shot for a given tree.

When opening a tree, the user can specify the reserved shot number 0 to designate opening the "current" shot for that tree. Typically during experiment shot cycles the "current" shot for the main tree is incremented so that applications can reference shot 0 and always be looking at the latest/"current" shot. The shot number can either be expression by a shot number expression, the simplest being just an integer value, or you can use the `/increment` qualifier to make the current shot the previous current shot number plus one. 

Examples:

```sh
  TCL> SET CURRENT CMOD 1000
  TCL> SET CURRENT CMOD "current_shot('cmod')+2"
  TCL> SHOW CURRENT CMOD
  Current shot is 1002
```

**Note**: The shot number is a signed 32-bit integer, so the largest value for a shot number is 2147483647. Also except for the model (shot number -1) and the "current" shot (shot number 0) all shot numbers must be between 1 and 2147483647.

See also: `show current`

### `set view DATE_TIME_SPECIFIER`
This command used to set the time  context for examining the contents of a MDSplus tree. If data versioning is enabled on a tree, then a history of data entries for each node is kept each being timestamped. When you specify a "view" date and time the commands such as DIRECTORY, DECOMPILE and SHOW DATA will present a description of the data the same as if you issued those commands at that particular time. 

The DATE_TIME_SPECIFIER must be in the format `dd-mon-yyyy hh:mm:ss`, where:

  * `dd`    - the day of the month, integer such as 29.
  * `mon`   - the first three characters of the month (English), such as JAN.
  * `yyyy`  - the year, integer such as 2015.
  * `hh`    - the hour of the day, integer 0-23.
  * `mm`    - the minute, integer 0-59.
  * `ss`    - the seconds, integer 0-59
  * or special keyword `NOW`, meaning the current time.


### `set default NODE_PATH`
Set your current location in an open tree. The `set default` command is similar to a `cd` command in a file system. The default location in the tree hierarchy affects things like the `directory` command as well as all commands that take a node-path as an argument. Node paths specified as relative path strings are resolved by finding the node relative to the current default location in the tree. 


> TODO: ask Stephen if the word "wild" here is needed

### `set node NODE_PATH_WILD /option[/option...]`
The `set node` command is used to change the characteristics of one or more nodes in an MDSplus tree. The `/option` can be one of the following:

| Option | Explanation |
|--------|-------------|
| `ON`                    | turn node "on" |
| `OFF`                   | turn node "off" |
| `[NO]SUBTREE`           | make node a subtree reference (or not) available only during `edit` |
| `[NO]WRITE_ONCE`        | make node write once (or not) |
| `[NO]COMPRESS_ON_PUT`   | turn on or off automatic compression |
| `[NO]COMPRESS_SEGMENTS` | turn on or off automatice segment compression |
| `[NO]DO_NOT_COMPRESS`   | turn off any data compression on the node |
| `[NO]SHOT_WRITE`        | enable writing to this node in a pulse file |
| `[NO]MODEL_WRITE`       | enable writing to this node in shot -1 |
| `[NO]INCLUDED`          | include this subtree in 'conditional' create pulse |
| `[NO]ESSENTIAL`         | make this node 'essential' for `dispatch/check` |
| `LOG`                   | log node changes |
| `STATUS=n`              | Write a status value to a node (usually action nodes). |
| `COMPRESSION_METHOD={standard \| gzip}` | set the compression method for this node.

**Notes:**
* All nodes in an MDSplus tree have a set of attributes; some are set automatically when data is stored, some are set when the nodes are first added to a tree, and some are modifiable by this command.
* The options indicated with a `[NO]` prefix indicates that the option can be negated. For example, using the command `set node gub/write_once` will set a flag in the nodes characteristics that indicates that data can only be written once after which the data cannot be overwritten. Using the command `set node gub/nowrite_once` clears the "write once" flag, thus enabling the node to be overwritten with new data. 


### `set server/log=(log | statistics | none)`
Change the logging mode for an action server.
* Action servers by default will write log messages to `stdout` when they are dispatched and action, when they begin an action, and when the complete an action. This is the type of logging produced by using `/log=log`.
* The parameter `/log=statistics` produces more detailed logs indicating the CPU and memory resources used during the execution of an action.
* The parameter `/log=none` disables standard logging of action execution.


### `set readonly [/off]`
This command is used to make a tree readonly. No store of data or change of node characteristics is permitted. This is an edit operation and a `write` command must be performed to save the readonly property of a tree. Use the `/off` qualifier to disable the readonly setting to make the tree writable again. 

### `set tree TREE_NAME[,SUBTREE1[,SUBTREE2,]] [/shot=SHOT_NUMBER] [/readonly]`
The `set tree` command is used to open an MDSplus tree. If subtree names are included in the TREE_NAME parameter then only those trees will be opened if they are available.
* The `/shot` qualifier can be used to specify a particular shot number to open. The shot number can be a TDI expression. If omitted, the "model" tree or shot -1 is opened.
* If the `/readonly` qualifier is included then the tree is opened in a readonly mode and no changes can be made to the nodes or their data.



### `set versions [/[no]model] [/[no]shot]`
The `set versions` command is used to enable or disable data versioning in an MDSplus tree. When versioning is enabled, new data records stored to a node do not overwrite the existing data but instead are added to a list of data records for that node. Each new data record is timestamped and you can use the `set view` command to designate a particular reference time so that your view would be equivalent to having examined the tree at that particular date and time. You can enable versioning for either the model or pulse files or both.

**Note**: Data versioning is not supported for segmented data records.

### `set alternate_compression [on|off]`
This command is used to enable or disable support for alternate compression methods (stored in the NCI for a node) across an entire tree. 


### `setevent EVENTNAME`
This command can be used to issue an MDSplus event. MDSplus events are named happenings that other processes can wait for by name. See the WFEVENT command. The TCL command does not currently support sending a data message with the event.



### `show attribute/name=ATTRIBUTE_NAME`
The SHOW ATTRIBUTE command is used to display the contents of a node's named attribute.

See also: `set attribute`


### `show current TREENAME`
This command is useful for displaying the current shot for a particular tree. See `set current` for more information on the meaning of "current" shot.


### `show data NODE_PATH1[,NODE_PATH2,...]`
The `show data` command will display the data stored in a node in a tree. Unlike the `decompile` command, the `show data` shows the data structure stored in the node as well as following node references recursively if an expression store in a node references other nodes in the tree.


### `show db`
Display the current tree and default node opened in the current process.

The SHOW DB can be used to display what the current tree context is: it displays the tree and shot, open mode, and the current default node in the tree.

Example:

```sh
TCL> SHOW DB
000  MAIN                              shot: -1 [\MAIN::TOP]
```



### `show default`
This command displays the current default node location in the opened tree.

Example:

```sh
TCL> SHOW DEFAULT
\MAIN::TOP
```



### `show server SERVER_SPEC[,SERVER_SPEC] [/nooutput]`
Displays the current status of one or more action servers; you may use this command to query action servers to see what, if anything, they are currently working on. The `/nooutput` command can be useful to just detect if there is a problem accessing an action server.

Wildcard characters can be used in the server name but only if the following conditions are met:
1. All the servers are logging their output to a single log directory.
2. The server logs are named the same as the string you would use to communicate with that server (e.g., `myhost-name:8100`).
3. There is an environment variable `MDSIP_SERVER_LOGDIR` defined pointing to that directory.
4. Your process has access to that directory.

When wildcards are used in the server name, the log directory is searched for logfiles matching the wildcard specification and then the log file name is used for the server specification when connecting to that server.
Example:

```sh
TCL> show server localhost:9000
Checking server: localhost:9000
Tue Feb 10 15:51:27 2015, fc21-vm:9000, logging disabled, Inactive
```


### `show git [/tag] [/branch] [/commit] [/remote] [/remote_url] [/srcdir]`

> TODO: Find what these different parameters do

Show the version information of this MDSplus git repository. These parameters are available:

* `/tag`
* `/branch`
* `/remote`
* `/commit`
* `/srcdir`
* `/remote_url`



### `show versions`
This command displays whether or not data versioning is enabled for the current tree.

Example:

```sh
TCL> SET TREE main
TCL> SHOW VERSIONS
  Versions are disabled in the model file and disabled in the shot file.
```

### `show alternate_compression`
Displays whether or not data alternate compression methods are enabled for the current tree.

Example:

```sh
TCL> SET TREE main
TCL> SHOW ALTERNATE_COMPRESSION
  Alternate Compression is disabled.
```


> TODO: there's some html comment for a "Start_server" command, but there's no description> Stephen to verify that this command

  <!--
  <verb name="start">
    <parameter name="p1" prompt="What" required="True" type="start_TYPE"/>
  </verb>

  <syntax name="start_server">
    <routine name="TclDispatch_start_server"/>
    <parameter name="p1" prompt="What" required="True" type="start_type"/>
    <parameter name="p2" label="server" prompt="Server" required="True" list="True"/>
  </syntax>

  <type name="start_TYPE">
    <keyword name="SERVER" syntax="start_server"/>"
    </type>
    -->


### `stop server SERVER_SPEC[,SERVER_SPEC]`

Stops or restarts one or more MDSplus action servers.

Normally MDSplus action servers are configured to restart automatically so this command effectively will restart an action server. It is not uncommon to restart action servers at some interval such as once per day to recover fragmented virtual memory within the action server process. Other reasons for stopping an action server might be to reset I/O channels to data acquisition devices which might become non-responsive or device support code may introduce memory leaks which may require the process to be restarted to release virtual memory.

Unlike the `show server` command, wildcard characters cannot be used in the
`SERVER_SPEC` string.




### `verify`

Checks the integrity of the currently open tree to ensure that the tree structure representation is valid and complete. This command is a useful diagnostic tool if file system or disk corruption problems have been detected on the storage device where the tree files are stored. If damage to the tree (file name such as `mytree_nnn.tree`) is discovered, it is usually safe to copy the tree file from an adjacent shot since the tree file contains only the tree structure and not the data or characteristics of the nodes in the tree.

The VERIFY command will display a count of the nodes in the tree. If there are subtree nodes included in the tree those nodes will be listed as "other" in the node counts.

Example:

```sh
TCL> SET TREE mytree
TCL> VERIFY
Node summary:
  Allocated = 7/14
  Free      = 7/14
  Other     = 0/14
```


### `wfevent EVENT_NAME /timeout=SECONDS`

This can be used to Wait For an MDSplus event to be issued. MDSplus events are named occurrences that can be issued by other processes on the same or different host computers. The `wfevent` command will not complete until the MDSplus event is generated. The `/timeout` qualifier can be specified to cause the wait to time out if no event is generated within the specified number of seconds.


### `write [TREENAME] [/SHOT=SHOT_NUMBER]`

This command must be used when tree is open for edit (using the `edit` command) in order to write the tree structure to the `.tree` file, preserving changes made via editing commands (such as those listed in `HELP EDIT COMMANDS`). Closing a tree that is open for edit, without calling the `write` command will discard any changes made to the tree's structure. 

If the treename parameter or `/shot` qualifier is omitted, the tree and shot specified with the `edit` command is assumed. 

Note: This command has nothing to do with writing data into nodes (which should be done from normal mode).

---
The `write` command is used to write out a new tree to preserve any changes using editing commands such as those listed in: `HELP EDIT COMMANDS`


If the treename parameter or `/shot` qualifier is omitted, the tree and shot specified with the `edit` command is assumed. If a tree is modified by edit commands and a `write` command is not issued, those changes will be discarded.
