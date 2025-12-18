# Trees: Reading and Writing Data

This page assumes that you have already committed to the major decisions made during the [foundational tree setup](../guide/daq/tree-setup.md) steps (tree names, schemes for storage and shot numbers, etc.) Now you are ready to start writing data to your trees.


## TCL Commands

Navigating and manipulating trees is done through MDSTCL (MDSplus Tree Command Language). See the [MDSTCL reference page](../reference/mdstcl.md) for a complete list of commands and syntax. This information also resides in the program's built-in help text (simply type `help` into the `TCL>` prompt). The [jTraverser2](../guide/gui/jTraverser2.md) GUI is also available.

Notes:
* Commands are not case sensitive.
* Some commands (e.g., TDI expressions) need to be encased in triple double quotation marks (`"""like this"""`). 
* Commands and flags can be abbreviated to a point of disambiguation. (For example, `show version` can be simply typed as `sho ver`).
* Additional qualifiers or arguments that begin with a slash (e.g., `directory /tag` or `clean cmod /shot...`) can be preceeded by a space. However, when using the built-in help, there must be no space before parameters (e.g., `help directory/tag`).
* Users who prefer a graphical user interface (over TCL's command line) can accomplish many of the same things using the jTraverser2 tool (link to GUI tools here).

## Opening a tree

```tcl
set tree TREE_NAME[,SUBTREE1[,SUBTREE2,..]] [/shot=SHOT_NUMBER] [/readonly]

# example
set tree my_tree, my_subtree1 /shot=0 /readonly
```

There are three modes when opening a tree:
* `readonly`: provides a safe way to see the data and tree structure. No changes can be made to the nodes or their data.
* `normal`: allows for writing data
* `edit`: allows for modifying the structure of trees (creating, modifying, and deleting nodes). This mode should be used sparingly and with great care. See the [Creating/Editing Tree Structures](../guide/trees-edit-structure) for more information.

About shot numbers:
* If omitted, the "model" tree or shot `-1` is opened.
* The parameter `/shot=0` opens the "current" tree.
* The shot number can also be a [TDI](../guide/tdi.md) expression.

See the [TCL reference page](../reference/mdstcl.md) for more information on syntax and parameters.



## Reading Data

Once the tree is open, you can use [TDI](../guide/tdi.md) expressions to perform calculations.

```tdi
# This gets the data of the node and you can assign it to a variable or whatever
DATA(node)

# TODO Example Syntax
TDI> _A = data(my_node)
# And now you can do stuff with _A

TreeGetRecord(node)
```

# Writing Data

TreePut(node)

To save your data, use the `write` command:
```
write [TREENAME] [/SHOT=SHOT_NUMBER]
```

## Segments


## Writing TDI Expressions into Nodes

## GetMany / PutMany

