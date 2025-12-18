
# Creating/Editing Tree Structures

If your goal is simply to write data, go to the page on [Trees: Reading and Writing Data](../guide/trees-read-write.md). In this context, 'edit' means editing **structure**, which involves creating/deleting nodes, turning nodes on/off, moving nodes under other nodes, etc.

## Beware: Take Extra Precautions

TODO: Checklist?

Please take extra care while creating/editing trees as mistakes made during these operations can cause permanent data loss.

Double check the tree you have open and the shot number

Verify with colleagues that nobody else is making structure modifications before committing your own.

Do not call `openNew()` on shots that already exist:  they will be **overwritten**.

The last person to write will "win", so stay in edit mode for as little time as possible.

Permissions: Inherited from the filesystem, specifically the .tree file

## Open a Tree for Editing

```tcl
edit TREE_NAME [/shot=SHOT_NUMBER] [/new]
```
Edit or create an MDSplus tree file. Before you can edit or create a tree file, you must have either the `treename_path` or `default_tree_path` environment variable set to define the location of the tree files (e.g., `mytree_path=/home/me/mytreedir`).

* The `/shot` qualifier is used to specify a shot number to edit or create. If the `/shot` qualifier is not specified, the `edit` command will default to shot number -1, the "model" tree.

* If the `/new` qualifier is specified, then a new empty tree will be created, overwriting any existing tree if one exists.

* **Note**: Once you are done editing a tree you must use the `write` command to save any
structural changes you might have made to the tree.

## Structure 'EDIT' mode limitations

`openEdit()` or `openNew()` will both land you in structure 'edit' mode.

Subtrees will not be opened; you can only edit one tree at a time.

The last person to write "win", stay in edit mode for as little time as possible

You must `write()` to save changes, `close()` will fail (TODO: verify) otherwise, use `quit()` to disregard changes

Structure 'edit' mode also allows read/write data access, but try to limit using this. Instead, finish your structure changes, then reopen the tree in 'normal' mode.

## Adding Nodes

When adding nodes, be sure to use the intended prefix to control whether node is a `child` (`.`) or a `member` (`:`).

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