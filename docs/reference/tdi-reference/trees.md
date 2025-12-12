
# Trees

## Referencing Nodes in TDI

While a shot is open, an expression may simply use a Node's name or [path](#node-paths) to reference it. However, these paths may not contain wildcards as they are meant to reference a single node.

Only nodes in the top-most shot of the [stack](#shot-stack) can be referenced in this way.

When possible, a node referenced in this way will compile to a [`NID`](#node-id-nid), which allows for storing references to other nodes in the tree.

Warning: Storing a reference to a tag will compile to a NID, and won't update if you update the tag
> TODO: Reword/improve

Warning: Passing nodes as parameters to functions will fail if the node does not contain data, even if the function was not intending to use the data of the node. It is recommended to always pass them as [Text](#) instead to avoid this issue. See the example below.

```tdi
TDI> TreeOpen("mytree", 12345)
265388067

TDI> analysis:current
[1,2,3,4,5]

# : and . are interchangable here
TDI> analysis.current
[1,2,3,4,5]

TDI> TreeSetDefault(HARDWARE)
# TODO: fails

TDI> TreeSetDefault('HARDWARE')
# TODO:succeeds
```

See [here](#dummy-tree) for the tree used in the examples.

## Node ID (NID)

A unique ID representing a node. Internally, this is a 32-bit integer representing a specific node in a specific tree.

Most functions that accept a NID will also accept a [Node](#referencing-nodes-in-tdi) or a [Path](#node-paths).

NIDs can be retrieved with [`GETNCI(<node here>, 'NID_NUMBER')`](#getnci-get-node-characteristic-information).

## Children and Members

A parent node can have both children and member nodes. These are functionally equivalent and mostly exist for historical reasons. However, children should nominally be used for structure, and members should nominally be used for nodes with data.

* Children start with `.`
* Members start with `:`

See [node path](#node-paths) for more examples.

The decision of whether a node will be a member or a child is made when [adding](#) the node, determined by the `.` or `:` prefixed on the name.
> TODO: Mark, help

Note: A parent node cannot have both a child and member of the same name.

Note: When referencing [Nodes](#referencing-nodes-in-tdi), `.` and `:` can be used interchangably.

Some commands, like [mdstcl dir](../mdstcl.md#directory-node_path_wild1node_path_wild2-full-usageusage-usageusage1usage2) will separate children and members.

```
TDI> Tcl('dir')

\CMOD::TOP

 :START_TIME

  ANALYSIS      HARDWARE


Total of 3 nodes.
1
```

See [here](#dummy-tree) for the tree used in the examples.

## Shot Stack

When multiple shots are open, they will be stored in a stack. Only the top-most tree will be used by any functions. However, "opening" a tree that is already open in the stack will be instant.

See [show db](../mdstcl.md#show-db) for more information.

> TODO:

## Node Paths
> TODO: Mark, help reword/improve/organize

A node path is similar to a file path, however you can use any of the separators below to refine the search path. Unless prefixed with a `\`, node paths will be relative to the [default node](#default-default-node-path).

For convenience, when searching for nodes, `.`, `:` and `~` are now often interchangable.

`-` or `^` can be used to access a node's parent.

When adding nodes, `.` and `:` will be used as described in [children and members](#children-and-members), and `~` cannot be used at all.

Relative paths can be prefixed with `.` or `:`, however `~` as a prefix will be interpreted as a [bitwise not](./logic.md#inot-bitwise-not).

## Wildcards
> TODO: Mark, help reword/improve/organize

A wildcard is a [node path](#node-paths) with one or more of the following:

|Syntax|Meaning|
|-|-|
|`*`  |Any node at this level|
|`***`|All nodes recursive|
|`:*` |Any member at this level|
|`:::`|All members recursive|
|`.*` |Any child at this level|
|`...`|All children recursive|
|`-`  |The parent node|
|`^`  |Ancestor (equivalent to `-`)|
|`^^^`|All ancestors recursive|
|`~*` |Any child or member at this level|
|`~~~`|All children and members recursive (equivalent to `***`)|

> TODO: `%` in node names?

Note: Not all functions can take wildcards, see the documentation for each function to be sure.

```tdi
TDI> getnci('***', 'path')
TODO: Output

TDI> getnci('...', 'path')
TODO: Output

TDI> getnci(':::', 'path')
TODO: Output

# Get the path to a node as individual nodes
TDI> getnci('\\temp_sensor^^^', 'node_name')
["ADC     ","HARDWARE","TOP     "]
```

## Default Node

The default node will be used as the reference point for all relative tree paths.
This is analogous to changing directory in a filesystem. When opening a tree, the initial default node will be [`TOP`](#).

See [set default](../mdstcl.md#set-default-node_path) for more information.

The path of the default node can be retrieved with [`$DEFAULT`](#default-default-node-path).

The default [NID](#node-id-nid) can be retrieved with [`GetDefaultNid`](#getdefaultnid-get-nid-of-the-default-node).

The default node can be set with [`TreeSetDefault`](#treesetdefault-set-default-node-by-path) or [`SetDefaultNid`](#setdefaultnid-set-default-node-by-nid).


## `Tcl` (Run MDSTCL Command)

|||
|-|-|
|TDI Syntax| `Tcl(_COMMAND, [_OUTPUT], [_ERROR])` |
|Filepath  | [`tdi/tcl/Tcl.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/tcl/Tcl.fun) |

Run an [`mdstcl`](../mdstcl.md) command. If `_OUTPUT` is specified, it will contain the output text of the command, otherwise it will print to stdout. If `_ERROR` is specified, it will contain the error text of the command, otherwise it will print to `stderr`. Returns the return code from executing the given command.

If specified, `_OUTPUT` and `_ERROR` can either be variables or strings containing variable names. The variables don't need to be already defined.

This can be used to open/close trees, change the [default node](#default-default-node-path), or query information about the current context. For example:
* `Tcl("show version")` can be used to query the MDSplus version of a server you are connected to.
* `Tcl("set def .-.")` can be used to easily move the [default node](#default-default-node-path) up one level (`cd ..`).
* `Tcl("show db")` can be used to easily see the open [shot stack](#shot-stack).

```tdi
TDI> Tcl("show version")


MDSplus version: 7.157.0
----------------------
  Release:  alpha_release-7-157-0
  Date:     Thu Nov 20 23:04:24 UTC 2025
  Browse:   https://github.com/MDSplus/mdsplus/tree/alpha_release-7-157-0
  Download: https://github.com/MDSplus/mdsplus/releases/tag/alpha_release-7-157-0


1


TDI> TreeOpen("mytree", 12345)
265388067

TDI> Tcl("show db", _out)
265389633

TDI> _out
"000  MYTREE        shot: 12345 [\\MYTREE::TOP]   \n\n"


# The current tree / default node will be used
TDI> TreeSetDefault('HARDWARE')
TODO: Output

TDI> Tcl("dir /full")
TODO: Output


# Query the MDSplus version of a server
TDI> mdsconnect('oldserver')

TDI> write(, mdsvalue('Tcl("show version", _out); _out'))


MDSplus version: 7.112.1
----------------------
  Release:  alpha_release_7.112.1
  Browse:   https://github.com/MDSplus/mdsplus/tree/alpha_release_7.112.1
  Download: https://github.com/MDSplus/mdsplus/archive/alpha_release_7.112.1.tar.gz



245
```

## `$DEFAULT` (Default Node Path)

|||
|-|-|
|TDI Syntax   | `$DEFAULT` |
|Python Syntax| `MDSplus.dDEFAULT()` |
|Java mdsplus-api Syntax| `CONST.dDefault()`|
|Opcode|386|

The path to the current default tree node.

Same as `GETDBI('DEFAULT')`.

```tdi
# With a tree open
TDI> $default
"\\MAIN::TOP"

# Without a tree open
TDI> $default
%TDI Error in $DEFAULT()
%TDI Error in EXECUTE("$DEFAULT")
```

See also
* `GETDBI()`

## `$EXPT` (Tree/Experiment Name)

|||
|-|-|
|TDI Syntax   | `$EXPT` |
|Python Syntax| `MDSplus.dEXPT()` |
|Java mdsplus-api Syntax| `CONST.dExpt()`|
|Opcode|387|

The name of the current tree.

Same as `GETDBI('NAME')`.

```tdi
# With a tree open
TDI> $expt
"MAIN"

# Without a tree open
TDI> $expt
%TDI Error in $EXPT()
%TDI Error in EXECUTE("$EXPT")
```

See also:
* `GETDBI()`

## `$SHOT` (Current Shot Number)
|Opcode|388|
|||
|-|-|
|TDI Syntax   | `$SHOT` |
|Python Syntax| `MDSplus.dSHOT()` |
|Java mdsplus-api Syntax| `CONST.dShot()`|

The shot number of the current tree.

Same as `GETDBI('shot')` or `GETDBI('shotid')`.

```tdi
# With a tree open
TDI> $shot
12345

# With a model tree open
TDI> $shot
-1

# Without a tree open
TDI> $shot
%TDI Error in $SHOT()
%TDI Error in EXECUTE("$shot")
```

See also:
* `$SHOTNAME`
* `GETDBI()`

## `$SHOTNAME` (Current Shot Number String)

|||
|-|-|
|TDI Syntax   | `$SHOTNAME` |
|Python Syntax| `MDSplus.dshotname` |
|Java mdsplus-api Syntax| `CONST.dShotname()`|
|Opcode|444|

The shot number of the current tree as a string, or "MODEL" for shot -1.

```tdi
# With a tree open
TDI> $shotname
"12345"

# With a model tree open
TDI> $shotname
"MODEL"

# Without a tree open
TDI> $shotname
%TDI Error in $SHOTNAME()
%TDI Error in EXECUTE("$shotname")
```

See also:
* `$SHOT`


## `TreeOpen` (Open Tree)

|||
|-|-|
|TDI Syntax| `TreeOpen(_TREE, [_SHOT], [_READONLY])`  |
|Filepath  | [`tdi/treeshr/TreeOpen.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeOpen.fun) |

Open the shot file identified by (`_TREE`, `_SHOT`) for use with other `Tree*` functions or to access nodes by path. If `_SHOT` is not specified, the model shot (-1) will be used. If `_READONLY` is specified and nonzero, the tree will be open read-only, otherwise it will be open for read/write.

If the shot was already open, it will be moved to the top of the [stack](#shot-stack).

This will search [$<tree>_path](../environment-variables.md#tree_path) or [$default_tree_path](../environment-variables.md#default_tree_path) as described there.

This will trigger the [OpenTree hook](../tree-hooks.md#opentree).

```tdi
```

## `TreeOpenNew` (Create/Overwrite a Tree and Open for Structure Editing)

|||
|-|-|
|TDI Syntax| `TreeOpenNew(_TREE, _SHOT)`  |
|Filepath  | [`tdi/treeshr/TreeOpenNew.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeOpenNew.fun) |

For use with [structure editing](#).

TODO:

## `TreeOpenEdit` (Open Tree for Structure Editing)

|||
|-|-|
|TDI Syntax| `TreeOpenEdit(_TREE, _SHOT)`  |
|Filepath  | [`tdi/treeshr/TreeOpenEdit.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeOpenEdit.fun) |

For use with [structure editing](#).

TODO:

## `TreeClose` (Close Tree)

|||
|-|-|
|TDI Syntax| `TreeClose([_TREE], [_SHOT])`  |
|Filepath  | [`tdi/treeshr/TreeClose.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeClose.fun) |

Close a shot that was opened with [`TreeOpen`](#treeopen-open-tree). If `_TREE` is specified, the shot identified by (`_TREE`, `_SHOT`) will be closed. Otherwise, the shot at the top of the [stack](#shot-stack) will be closed.

A useful expression to close all open trees (as used by `closeAllTrees()` in the various `Connection` classes):
```tdi
_i=0; while(iand(TreeClose(), 1)) _i++;
# _i will be the number of trees closed
```

```tdi
```

## `TreeWrite` (Write Structure Changes)

|||
|-|-|
|TDI Syntax| `TreeWrite([_TREE], [_SHOT])`  |
|Filepath  | [`tdi/treeshr/TreeWrite.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeWrite.fun) |

For use with [structure editing](#).

Writes the structure changes to disk of a shot that was opened with [`TreeOpenEdit`](#treeopenedit-open-tree-for-structure-editing) or [`TreeOpenNew`](#treeopennew-createoverwrite-a-tree-and-open-for-structure-editing). If `_TREE` is specified, the shot identified by (`_TREE`, `_SHOT`) will be written. Otherwise, the shot at the top of the [stack](#shot-stack) will be written.

## `TreeQuit` (Discard Structure Changes and Close Tree)

|||
|-|-|
|TDI Syntax| `TreeQuit([_TREE], [_SHOT])`  |
|Filepath  | [`tdi/treeshr/TreeQuit.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeQuit.fun) |

For use with [structure editing](#).

Discard the structure changes and close a shot that was opened with [`TreeOpenEdit`](#treeopenedit-open-tree-for-structure-editing) or [`TreeOpenNew`](#treeopennew-createoverwrite-a-tree-and-open-for-structure-editing). If `_TREE` is specified, the shot identified by (`_TREE`, `_SHOT`) will be quit. Otherwise, the shot at the top of the [stack](#shot-stack) will be quit.

## `TreeFileName` (Get Shot File Path)

|||
|-|-|
|TDI Syntax| `TreeFileName([_TREE], [_SHOT])`  |
|Filepath  | [`tdi/treeshr/TreeFileName.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeFileName.fun) |

Returns the local or remote path to the shot file. If `_SHOT` is specified, the shot identified by (`_TREE`, `_SHOT`) will be used (regardless of whether it is open or not). If `_TREE` is specified, but `_SHOT` is not, the shot identified by (`_TREE`, [`$SHOT`](#shot-current-shot-number)) will be used. Otherwise, the shot at the top of the [stack](#shot-stack) will be used.

To get the directory of a shot file, use [`TreeDirName`](#treedirname-get-shot-directory-path).

The `.characteristics` and `.datafile` files will be stored in the same directory, and the paths can be inferred like so:
```tdi
TDI> _tree_path = TreeFileName()
"/path/to/trees/mytree/mytree_12345.tree"

TDI> _base_path = extract(0, index(_tree_path, '.', $true), _tree_path)
"/path/to/trees/mytree/mytree_12345"

TDI> _characteristics_path = _base_path // '.characteristics'
"/path/to/trees/mytree/mytree_12345.characteristics"

TDI> _datafile_path = _base_path // '.datafile'
"/path/to/trees/mytree/mytree_12345.datafile"
```

```tdi
TDI> TreeFileName()
""

TDI> TreeOpen("mytree", 12345)
265388067

# If the files are local
TDI> TreeFileName()
"/path/to/trees/mytree/mytree_12345.tree"

# If the files are remote
TDI> TreeFileName()
"mydatasrv::/path/to/trees/mytree/mytree_12345.tree"
```

## `TreeDirName` (Get Shot Directory Path)

|||
|-|-|
|TDI Syntax| `TreeDirName(_TREE, _SHOT)`  |
|Filepath  | [`tdi/treeshr/TreeDirName.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeDirName.fun) |

Returns the local or remote path to the directory containing the shot file. If `_SHOT` is specified, the shot identified by (`_TREE`, `_SHOT`) will be used (regardless of whether it is open or not). If `_TREE` is specified, but `_SHOT` is not, the shot identified by (`_TREE`, [`$SHOT`](#shot-current-shot-number)) will be used. Otherwise, the shot at the top of the [stack](#shot-stack) will be used.

To get the path to a shot file, use [`TreeFileName`](#treefilename-get-shot-file-path).

```tdi
TDI> TreeDirName()
""

TDI> TreeOpen("mytree", 12345)
265388067

# If the files are local
TDI> TreeDirName()
"/path/to/trees/mytree"

# If the files are remote
TDI> TreeDirName()
"mydatasrv::/path/to/trees/mytree"
```

## `TreeGetCurrentShot` (Get Current Shot Number or Zero)

|||
|-|-|
|TDI Syntax| `TreeGetCurrentShot(_TREE)`  |
|Filepath  | [`tdi/treeshr/TreeGetCurrentShot.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeGetCurrentShot.fun) |

Return the current shot number for the given `_TREE`. If no current shot number is found, this will return `0`.

To throw an error if the current shot is not found, use [`CURRENT_SHOT`](#current_shot-get-current-shot-number-or-error).

```tdi
TDI> TreeGetCurrentShot("mytree")
12345

TDI> TreeGetCurrentShot("nocurrent")
0
```

## `TreeSetCurrentShot` (Set Current Shot Number)

|||
|-|-|
|TDI Syntax| `TreeSetCurrentShot(_TREE)`  |
|Filepath  | [`tdi/treeshr/TreeSetCurrentShot.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeSetCurrentShot.fun) |

TODO: 

## `CURRENT_SHOT` (Get Current Shot Number or Error)

|||
|-|-|
|TDI Syntax| `CURRENT_SHOT(_TREE)`  |
|Filepath  | [`tdi/treeshr/current_shot.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/current_shot.fun) |

Return the current shot number for the given `_TREE`. If no current shot number is found, `abort()` will be called.

To get the current shot number without potentially throwing an error, use [`TreeGetCurrentShot`](#treegetcurrentshot-get-current-shot-number-or-zero).

```tdi
TDI> current_shot("mytree")
12345

TDI> current_shot("nocurrent")
<stack trace>
%TDI Error in EXECUTE('current_shot("nocurrent")')
```

## `GetDefaultNid` (Get NID of the Default Node)

|||
|-|-|
|TDI Syntax| `GetDefaultNid()`  |
|Filepath  | [`tdi/treeshr/GetDefaultNid.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/GetDefaultNid.fun) |

Return the [NID](#node-id-nid) of the [default node](#default-node), otherwise `"error"`.

To get the path of the [default node](#default-node), use `$DEFAULT`.

```tdi
TDI> GetDefaultNid()
"error"

TDI> TreeOpen("mytree", 12345)
265388067

# TOP, the initial default NID
TDI> GetDefaultNid()
0

TDI> TreeSetDefault("HARDWARE")

TDI> GetDefaultNid()
42
```

## `SetDefaultNid` (Set Default Node by NID)

|||
|-|-|
|TDI Syntax| `SetDefaultNid(_NID)`  |
|Filepath  | [`tdi/treeshr/SetDefaultNid.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/SetDefaultNid.fun) |

Sets the [default node](#default-node) to the node indicated by `_NID`.

To set the [default node](#default-node) using a path, use [`TreeSetDefault`](#treesetdefault-set-default-node-by-path).

```tdi
# With no tree open, 265388200 is TreeNOT_OPEN
TDI> SetDefaultNid(0)
265388200

TDI> TreeOpen("mytree", 12345)
265388067

TDI> $DEFAULT
"\\MYTREE::TOP"

TDI> _nid = getnci('first', 'NID_NUMBER')
1

TDI> SetDefaultNid(_nid)
265389633

TDI> $DEFAULT
"\\MYTREE::TOP:FIRST"
```

## `TreeSetDefault` (Set Default Node by Path)

|||
|-|-|
|TDI Syntax| `TreeSetDefault(_PATH)`  |
|Filepath  | [`tdi/treeshr/TreeSetDefault.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeSetDefault.fun) |

Sets the [default node](#default-node) to the node indicated by `_PATH`.

`_PATH` can either be a string indicating the path or a [node](#), however it is recommended to use a string, if the node doesn't have data it will be an error.
> TODO: Improve

To set the [default node](#default-node) using a path, use [`TreeSetDefault`](#treesetdefault-set-default-node-by-path).

```tdi
# With no tree open, 265388200 is TreeNOT_OPEN
TDI> SetDefaultNid('first')
265388200

TDI> TreeOpen("mytree", 12345)
265388067

TDI> $DEFAULT
"\\MYTREE::TOP"

TDI> SetDefaultNid('first')
265389633

TDI> $DEFAULT
"\\MYTREE::TOP:FIRST"
```

## `TreeTurnOn` (Turn Node On)

|||
|-|-|
|TDI Syntax| `TreeTurnOn(_NID)`  |
|Filepath  | [`tdi/treeshr/TreeTurnOn.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeTurnOn.fun) |

Sets the [NCI](../metadata.md#nci) `state` flag to 0, indicating that the node is [on](#node-on-off). Additionally, this sets the [NCI](../metadata.md#nci) `parent_state` flag of any [children](#) or [members](#) to 0 as well.

```tdi
TDI> TreeTurnOn('A')

# state, 0 means on
TDI> btest(getnci('A', 'get_flags'), 0)
0BU
# parent_state, 0 means on
TDI> btest(getnci('A:B', 'get_flags'), 1)
0BU
```

## `TreeTurnOff` (Turn Node Off)

|||
|-|-|
|TDI Syntax| `TreeTurnOff(_NID)`  |
|Filepath  | [`tdi/treeshr/TreeTurnOff.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeTurnOff.fun) |

Sets the [NCI](../metadata.md#nci) `state` flag to 1, indicating that the node is [off](#node-on-off). Additionally, this sets the [NCI](../metadata.md#nci) `parent_state` flag of any [children](#) or [members](#) to 1 as well.

```tdi
TDI> TreeTurnOff('A')

# state, 1 means on
TDI> btest(getnci('A', 'get_flags'), 0)
1BU
# parent_state, 1 means on
TDI> btest(getnci('A:B', 'get_flags'), 1)
1BU
```

## `GetExtendedAttribute` (Get XNCI/Extended Attribute)

|||
|-|-|
|TDI Syntax| `GetExtendedAttribute(_NODE, [_NAME])`  |
|Filepath  | [`tdi/treeshr/GetExtendedAttribute.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/GetExtendedAttribute.fun) |

TODO:

`_NODE` can be a node, nid, or path.

If `_NAME` is not specified, `"attributenames"` will be used.
> TODO: What is that?

## `SetExtendedAttribute` (Set XNCI/Extended Attribute)

|||
|-|-|
|TDI Syntax| `SetExtendedAttribute(_NODE, _NAME, _VALUE)`  |
|Filepath  | [`tdi/treeshr/SetExtendedAttribute.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/SetExtendedAttribute.fun) |

TODO:

`_NODE` can be a node, nid, or path.

## `TreeSetDbiItm` (Set Tree/DataBase Information)

|||
|-|-|
|TDI Syntax| `TreeSetDbiItm(_CODE, _VALUE)`  |
|Filepath  | [`tdi/treeshr/TreeSetDbiItm.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeSetDbiItm.fun) |

## `GETDBI` (Get Tree/DataBase Information)

|||
|-|-|
|TDI Syntax   | `GETDBI(_NAME)` |
|Python Syntax| `MDSplus.GETDBI(name)` |
|Opcode|389|

Returns the [DBI](../metadata.md#dbi) indicated by `_NAME` from the shot's metadata.

`_NAME` must be [Text](#) and is case-insensitive.

> TODO: Document that substrings are allowed? or not?

```tdi
TDI> getdbi('shot')
12345

TDI> getdbi('name')
"MYTREE"
```

See also:
* [`$DEFAULT`](#default-default-node-path)
* [`$EXPT`](#expt-treeexperiment-name)
* [`$SHOT`](#shot-current-shot-number)
* [`$SHOTNAME`](#shotname-current-shot-number-string)

## `TreeSetNciItm` (Set Node Characteristic Information)

|||
|-|-|
|TDI Syntax| `TreeSetNciItm(_NID, _CODE, _VALUE)`  |
|Filepath  | [`tdi/treeshr/TreeSetNciItm.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeSetNciItm.fun) |

## `GETNCI` (Get Node Characteristic Information)

|||
|-|-|
|TDI Syntax   | `GETNCI(_NODE, _NAME, [_USAGE])` |
|Python Syntax| `MDSplus.GETNCI(node, name, [usage])` |
|Opcode|175|

Returns the [NCI](../metadata.md#dbi) indicated by `_NAME` from the `_NODE`. If `_USAGE` is specified, only nodes with matching [usages](../node-usages.md) will be used.

`_NODE` can be a [Scalar](#) or [Array](#) of [NIDs](#node-id-nid), [Nodes](#reading-the-data-from-a-node), or [Paths](#node-paths). Paths can contain [wildcards](#wildcards).

`_USAGE` can be a [Scalar](#) or [Array](#) of case-insensitive [Text](#) describing the allowed [usages](../node-usages.md).

```tdi
```

## `USING`

|||
|-|-|
|TDI Syntax   | `take_from_Compiler_syntax` |
(Opcode 384
|Min arguments| 2
|Max arguments| 4
******Compiler syntax: USING(arg0,arg1,arg2,arg3) 
|Native python|False|


|Return Type  |MDS Operation |
Evaluate expression from a different tree location.
Arguments Optional: DEFAULT, SHOTID, EXPT. A an expression.
>>>>>>>>>WARNING, pathnames in the expression A will be relative to the temporary tree location and may not be related to the old tree.
DEFAULT character, NID, long, or PATH scalar. The new tree path.
>>>>>>>>>WARNING, relative paths are like the full name in the old tree. SHOTID integer scalar. The shot number. EXPT character scalar. The experiment name.
|Result       |Depends on the expression at the node in the new tree. The old node, shot, and experiment are used to evaluate the expressions for DEFAULT, SHOTID, and EXPT. If SHOTID or EXPT present, a new tree is opened for reading. The temporary path is set from DEFAULT. If omitted, the values used are those of the current tree and path. There will be an error if the old tree is not open or the old path is bad.
|Examples     |Say shot 1234 is a "vacuum" subtraction shot for the current shot and we are positioned at \TOP.XRAY:CHAN_01, which has data, then the subtracted data might be
:DATA -USING(:DATA,,1234)

### `do_task` 

|||
|-|-|
|TDI Syntax   | `DO_TASK(arg0) ` |
|Python Syntax| `MDSplus.DO_TASK(arg0) ` |
|Opcode|448|

TODO: Move?

TODO: Come Back To This and investigate further

Execute Task
Executes the task item found in the argument.
ARGUMENT TASK refers to an ACTION or a TASK

## Tree Hooks

> TODO: Write a little bit more here
> TODO: Add links to relevant hooks

See [Tree Hooks](../tree-hooks.md).

## Dummy Tree

() usage
[] data

`mytree`
```
:START_TIME (NUMERIC)

.ANALYSIS (STRUCTURE)
    :CURRENT [Path("\\CURRENT_SENSOR")]
    :TEMP [Path("\\TEMP_SENSOR")]

.HARDWARE (STRUCTURE)

    .ADC (DEVICE) \ADC # Analog-to-Digital Converter
        .ACTIONS (STRUCTURE)
            :INIT (ACTION)
            :STORE (ACTION)

        :IN_01 (SIGNAL) \CURRENT_SENSOR [Build_Signal($VALUE * :CAL, ..., ...)]
            :CAL (NUMERIC)
        :IN_02 (SIGNAL) \TEMP_SENSOR
            :CAL (NUMERIC)
        :IN_03 (SIGNAL)
            :CAL (NUMERIC)

    .DAC (DEVICE) \DAC # Digital-to-Analog Converter
        .ACTIONS (STRUCTURE)
            :INIT (ACTION)

        :OUT_01 (SIGNAL)
        :OUT_02 (SIGNAL)
        :OUT_03 (SIGNAL)
```

too git first output of dac:
.HARDWARE.DAC:OUT_01 (path, maybe)
\DAC:OUT_1 (minpath)
\MYTREE::TOP.HARDWARE.DAC:OUT_01 (fullpath)
***:OUT_01 (~~~ too)
\ADC^:DAC:OUT_01

find all of the devices with outputs
union(getnci('***OUT*^', 'nid_number'))

get the fullpath of every signal node via usage mask
getnci(***, 'FULLPATH', 'SIGNAL')
