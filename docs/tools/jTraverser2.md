# jTraverser2

jTraverser2 allows you to set up, edit, and browse through your data trees with a graphical user interface. These commands are mostly graphical front-ends for the text commands listed in the [MDSTCL reference page](/docs/reference/mdstcl.md); please go there for in-depth descriptions. 

### Opening jTraverser2


You may be able to launch the application via searching for the program `jTraverser2`, depending on your installation method.

To open via Terminal in Linux, type the following. This command is case sensitve in Linux.

```sh
jTraverser2
```

If this fails, you check that the `$MDSPLUS_DIR/setup.sh` is correctly [sourced](/docs/guide/daq/setup-environment).

> TODO: Caveats



## Connect to Server

[screenshot goes here: menu for "file> connect"]
[screenshot goes here: the window that appears when you go to "file> connect"]

`File > Connect` opens a new [thin client](/docs/guide/thin.md) connection to the specified server in a new tab. Whatever you type in this field will be passed to [MDSCONNECT](TODO: link). Once connected, follow the directions above (`file > open` to open a specific tree)

[screenshot goes here: window with new tab]

`File > Disconnect` calls the `disconnect()` function and disconnects from the current server



[screenshot goes here: File...]



## Open Tree

[screenshot goes here: menu for "file> open"]
[screenshot goes here: the window that appears when you go to "file> open"]

`File > Open >`
* `path` Specifying a path here overrides any default paths. This field should be blank.  
    > TODO: Crosslink to where we talk about $MDSPATH, $default tree path.  
    > TODO: rephrase as needed based on recommended user workflow
* `expt` is short for experiment/tree.
* `shot` shot number goes here

[screenshot goes here: window with tree opened]

Open Options
TODO: Crosslink to [MDSTCL reference](/docs/reference/mdstcl.md)
* `readonly` provides a read-only instance of a tree
* `normal` opens an existing tree in read-write mode. You can write data to the tree in this mode (this is the default mode when you open a tree in MDSTCL), but not edit the structure. 
* `edit/new` Think of this option as `edit structure`. See the entry for `write` in the page on [MDSTCL reference](/docs/reference/mdstcl.md)

[screenshot goes here: file menu with "close" highlighted]
`File > Close` calls a `close()` and will close the currently opened tree. 

[screenshot goes here: file menu with "write" highlighted]
`File > Write`
See the entry for `write` in the page on [MDSTCL reference](/docs/reference/mdstcl.md)


## Create New Tree / Modify Tree Structure

[screenshot goes here: the window that appears when you go to file > open, but with the "edit/new" radio button activated]

* Go to `File > Open >`
* make sure the `edit/new` radio button is activated.
* This creates a new tree if an existing tree of the name specified cannot be found
* by default, it will create the tree in your `tree_Path` variable, [TODO: crosslink to wherever we talk about tree_path]

Reminder/tip--structured usage exists: don't just say "usage:any" for everything. This will help create guardrails. E.g., "width" and "height" should contain numerical data. Node names should not just be Numerical data even if that's true for some of them.

Verifying data: look at the last shot 

[screenshot goes here: all of the following--
add node  
add device  
add tag  
rename node  
remove node  
remove device  
remove tag  
]




## Modify Tree Data
[screenshot goes here: the window that appears when you go to file > open, but with the "normal" radio button activated]


TODO: crosslink to `put` in the [MDSTCL reference page](/docs/reference/mdstcl.md)

[screenshot goes here: some permutation of the following--
Edit data/Changing Settings/Parameters (width/height/segment length, hard coding gate arrays)]



## View Tree Data

[screenshot goes here: window with tree opened]

The main window behaves like your file explorer in your OS. Parent nodes are shown first, and you can expand them with the triangle icon (`►`) to see its child nodes.

[screenshot goes here: the window that appears when you go to "display data"]

* To view the data of a node, from the Display menu or right-click, select `Display Data` to see the expressions and other information. From this window you can modify the meta data here if you are in `normal` mode. 

[screenshot goes here: the window that appears when you go to "plot signal"]

* To view a plot of the data in a node, from the Display menu or right-click, select `Display Data... > Plot Signal`.

[screenshot goes here: a nice tooltip with lots of stuff in it]
* Tooltips: hover over any node to see at-a-glance meta-data about the contents of the node.  





