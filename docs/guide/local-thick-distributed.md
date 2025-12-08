# Local/Thick/Distributed

Local/Thick/Distributed are variations of a computing concept where all the work is done locally by your computer (in contrast to the thin implementation, where the server does all of the work and sends you answers to your queries).

TODO: More to come (this came from the access notes)

* you tell it where to go with Tree Path Environment variable
* all the work is done locally on your computer
* admin should configure the server or you can specify the environment yourself. i.e., this can have a default location. 
* uses 2 environment variables: either `$TREE_path` (you enter a specific tree) or `$default_tree_path` (if not specified, whatever the default for tree paths, which will be set up by the admin who sets up the daq server)

These are all values for each of those environment variables:
* Local: `$___ = /path/to/trees` (File I/O)
* Distributed:  `$___ = server::path/to/trees` (File I/O)
* Thick: `$___ = server::` (it uses the server's tree path definitions) (Tree I/O)

So the TDI code would look like:

```py
TreeOpen("TREE", SHOT_NUMBER)
NODE/EXPRESSION (eg `\IP+1`)
```

All of these have varying amounts of network back-and-forth, which affects the speed:
* mdsconnect(server) has the least
* trees i/o has very little
* files i/o has the most

## NFS Bad
TODO: more to come from Stephen 
