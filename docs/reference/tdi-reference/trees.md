
### `GETDBI` (Get Tree/DataBase Information)

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

### `GETNCI` (Get Node Characteristic Information)

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




### `TreeOpen` (Open Tree)

|||
|-|-|
|TDI Syntax| `TreeOpen(_TEXT)`  |
|Filepath  | [`tdi/treeshr/TreeOpen.fun`](https://github.com/MDSplus/mdsplus/blob/alpha/tdi/treeshr/TreeOpen.fun) |

Lowercase.