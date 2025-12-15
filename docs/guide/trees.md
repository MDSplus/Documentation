
# Reading/Writing Data

## Reading Data

DATA(node) or TreeGetRecord(node)

## Writing TDI Expressions into Nodes

## Writing Data

TreePut(node)

## Segments

## GetMany / PutMany


# Creating/Editing Tree Structures

If you are looking to write data, this is not the right section

'edit' means edit *structure*, use 'normal' to open for data read/write

## Beware: Take Extra Precautions

Please take extra care while creating/editing trees as mistakes made during these operations can cause permanent data loss.

Double check the tree you have open and the shot number

Verify with coworkers that nobody else is making structure modifications

Do not call `openNew()` on shots that already exist, they will be **overwritten**.

The last person to write wins, stay in edit mode for as little time as possible

TODO: Checklist?

Permissions: Inherited from the filesystem, specifically the .tree file

## Structure 'EDIT' mode limitations

`openEdit()` or `openNew()` will both land you in structure 'edit' mode.

Subtrees will not be opened, you can only edit one tree at a time

The last person to write wins, stay in edit mode for as little time as possible

You must `write()` to save changes, `close()` will fail (TODO: verify) otherwise, use `quit()` to disregard changes

Structure 'edit' mode also allows read/write data access, but try to limit using this. Instead, finish your structure changes, then reopen the tree in 'normal' mode.

## Adding Nodes

When adding nodes, be sure to use the intended prefix to control whether node is a `child` (`.`) or a `member` (`:`)

You actually pass a [path](), not just a name, so you can add a node like `.path.to.parent:newnode`

You cannot add a child and a member of the same name under the same parent

Node names should be treated as immutable, even though they can be renamed

Be sure to pick the right usage, this cannot be changed. Don't just use `any` for everything

```tdi
TreeOpenEdit('mytree', -1);
TreeAddNode('mynode', 'numeric');
TreeWrite();
TreeClose();

mdsconnect('myserver');
mdsvalue("TreeOpenEdit('mytree', -1)");
mdsvalue("TreeAddNode('mynode', 'numeric')");
mdsvalue("TreeWrite(); TreeClose();");
```

```tcl
edit mytree /shot=-1
add node mynode /usage=numeric
```

```py
tree = MDSplus.Tree('mytree', -1, 'edit')
tree.addNode('mynode', 'numeric')
tree.write()
tree.close()

conn = MDSplus.Connection('myserver')
conn.get("TreeOpenEdit($, $)", 'mytree', -1)
conn.get("TreeAddNode($, $)", 'mynode', 'numeric')
conn.get("TreeWrite(); TreeClose();")
```

## Adding Devices

Like adding a node, but you specify a device name (model)

Will add the head node and all intended subnodes

## Removing Nodes

Two part operation, use caution

Cannot delete a parent without also deleting the children/members

Cannot delete part of a device

## Renaming Nodes

TODO: Can this be used to move nodes?

You can rename nodes in a device but don't

## Adding Tags

Tags are long (23/24-character?) names that can be used to refer to nodes.

You have to be in edit mode to add/remove tags

Be careful: Tags have to be unique among a tree and all related parent/subtrees.

## Removing Tags

Fairly safe, no extra warnings