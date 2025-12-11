
# Trees

> TODO: Standardize example tree to main? Or provide an example tree described at the top/bottom?

## Node ID (NID)

A unique ID representing a node.

> TODO: Expand

## Shot Stack

A stack of the open shots.

[show db](../mdstcl.md#show-db)

> TODO:

## Default Node

The default node will be used as the reference point for all relative tree paths.
This is analogous to changing directory in a filesystem. When opening a tree, the initial default node will be [`TOP`](#).

See [set default](../mdstcl.md#set-default-node_path) for more information.

The path of the default node can be retrieved with [`$DEFAULT`](#default-default-node-path).

The default [NID](#node-id-nid) can be retrieved with [`GetDefaultNid`](#getdefaultnid-get-nid-of-the-default-node).

The default node can be set with [`TreeSetDefault`](#treesetdefault-set-default-node-by-path) or [`SetDefaultNid`](#setdefaultnid-set-default-node-by-nid).

## Reading the Data from a Node
> TODO: Rename

While a tree is open, simply use the name or path to a node to access the data

TODO> Expand, explain how to use nodes as parameters, explain issues with using nodes without data without quotes e.g. `TreeSetDefault(admin)` vs `TreeSetDefault("admin")`

```tdi
TDI> TreeOpen("mytree", 12345)
265388067

TDI> first
1234

TDI> first:second

```

## `$DEFAULT` (Default Node Path)

|||
|-|-|
|TDI Syntax   | `$DEFAULT` |
|Python Syntax| `MDSplus.dDEFAULT()` |
|Java mdsplus-api Syntax| `CONST.dDefault()`|
|Opcode|386|

The path to the current default tree node.

Same as `getdbi('DEFAULT')`.

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

Same as `getdbi('NAME')`.

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

Same as `getdbi('shot')` or `getdbi('shotid')`.

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

TDI> TreeSetDefault("MYNODE")

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


## `GETDBI` (Get Tree/DataBase Information)

|||
|-|-|
|TDI Syntax   | `GETDBI(_NODE, _NAME)` |
|Python Syntax| `MDSplus.GETDBI(node, name)` |
|Opcode|389|

> TODO: Come back to this after we do tree stuff and write proper examples

Get database information.
Arguments 
 STRING character scalar. The string may be abbreviated in upper or lower case to any unique form.
Logical OPEN_FOR_EDIT modifiable MODIFIED changes made
Long SHOTID shot number NUMBER_OPENED database pointers active MAX_OPEN database pointers allowed
Character NAME experiment name DEFAULT default/current node
INDEX integer scalar less than MAX_OPEN value. Determines which tree location is reported. The default value of 0 is the current tree.
|Result       |Depends on the experiment, shot number, and history.
|See also     |$DEFAULT, $EXPT, $SHOT, and $SHOTNAME constants.

## `GETNCI` (Get Node Characteristic Information)

|||
|-|-|
|TDI Syntax   | `GETNCI(_NODE, _NAME)` |
|Python Syntax| `MDSplus.GETNCI(node, name)` |
|Opcode|175|

> TODO: Come back to this after we do tree stuff and write proper examples

|Return Type  |MDS Operation |
Get node characteristic information about tree elements. Arguments Optional: NODE and USAGE.
NODE a NID or long node identifier or a PATH or character form of the path of a tree element--child or member, or a wildcarded path. May be an array. Default is current position in tree.
* WARNING, path names are case-sensitive. STRING character scalar. The string may be abbreviate in upper or lower case to any unique form. Case-insensitive.
USAGE character scalar or vector. This limits the search of NODE names. It must be a valid usage name like "ALL", "ANY", or "TEXT".
The STRING names by returned type follow. Byte unsigned CLASS storage classification DTYPE storage data type USAGE allowed data type Character FULLPATH path from top of tree MINPATH shortest relative path NODE_NAME last part of pathname ORIGINAL_PART_NAME Original node name in device PATH path from top or tagLogicals COMPRESSIBLE has arrays COMPRESS_ON_PUT use comprssion on put DO_NOT_COMPRESS no compression allowed ESSENTIAL node is essential IS_CHILD parent relationshipIS_MEMBER parent relationshipNID_REFERENCE contains nid references NO_WRITE_MODEL write to model disabled NO_WRITE_SHOT write to shot disabled PARENT_STATE parent on or off PATH_REFERENCE contains path references SETUP_INFORMATION has setup operations STATE on or off USAGE_ACTION allows only action USAGE_ANY allows any data USAGE_AXIS allows only axis USAGE_COMPOUND_DATA allows only compound_data USAGE_DEVICE allows only conglomerate USAGE_DISPATCH allows only dispatch USAGE_NUMERIC allows VMS data USAGE_SIGNAL allows only signal USAGE_STRUCTURE allows no data, was NONE USAGE_SUBTREE allows only subtree USAGE_TASK allows only task USAGE_TEXT allows only text USAGE_WINDOW allows only window WRITE_ONCE change only once Long DEPTH tree parents above LENGTH data size NID_NUMBER tree logical offset NUMBER_OF_CHILDREN number of child nodes NUMBER_OF_MEMBERS number of member nodes PARENT_RELATIONSHIP child or member Long unsigned GET_FLAGS bit flags OWNER ID rights identifier
_
STATUS
status
NID
BROTHER
next child or member
CHILD
first child
MEMBER
first member
PARENT the one above in tree NID arrays CHILDREN_NIDS list of children CONGLOMERATE_NIDS MEMBER_NIDS list of members Quadword unsigned TIME_INSERTED VMS date and time Word unsigned CONGLOMERATE_ELT number of elements Node data RECORD actual data
|Signals      |None, except for RECORD. |Units        |None, except for RECORD. |Form         |VECTOR concatenation of all elements found for the list
of NIDs and PATHs. Scalar for non-array results of single input. All data types are the same for one request except possibly for RECORD. Character names varyin length except for NODE_NAME, which has length 12.
|Result       |A scalar or simple vector list of results. RECORD may not be able to VECTOR the results of a list of NIDs/PATHs. Logicals allow easy testing of bit or value.
>>>>>>>>>WARNING, only GETNCI can handle arrays of NIDs/PATHs.
>>>>>>>>>WARNING, a NID/PATH result used in an expression will have its data taken--just as if the node name had been used. Thus GETNCI(\TOP.XRAY,"MEMBER")//" Z" might be "Xray diagnostic Z" if the first member were the description.
|Examples     |GETNCI(\TOP.XRAY,"PARENT") is \TOP as is GETNCI("\TOP.XRAY","par").



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
