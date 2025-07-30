
# Configure access

Examples:
* `/path/to/trees` (local)
* `server::` (thick)
* `server::/path/to/trees` (distributed) 
> more to come from Stephen

![](DAQconnections2a_v2.svg)
*Diagram of clients accessing data*

* client envsyms + tree paths
* port 8000 (systemd / xinetd)
  * logging
* mdsip.hosts is a whitelist/user-mapping file...lets only users from 
  * JAVA_USER :'-(
* ssh?

![](DAQconnections2.svg)

The administrator will need to determine what access methods are allowed (thin, local, thick/dist, ssh) and what access methods are automatically configured ($TREE_path / $default_tree_path)

## Thin client:

* you tell it where to go by connecting to Address of mdsip server

example in TDI:
```py
mdsconnect("SERVER_ADDRESS")
mdsopen("TREE", SHOT_NUMBER)
ans = mdsvalue("NODE/EXPRESSION")
```

So in thin client, all the work is done by the server, and it just sends you the answer.
So the server needs to know how to open the trees. 

## Local/Thick/Distributed client:
* you tell it where to go with Tree Path Environment variable

uses 2 environment variables
($ dollarsign means variable name)

either `$TREE_path` (you enter a specific tree) or `$default_tree_path` (if not specified, whatever the default for tree paths, which will be set up by the admin who sets up the daq server)

THese are all values for each of those environment variables:
* Local: `$___ = /path/to/trees` (File I/O)
* Distributed:  `$___ = server::path/to/trees` (File I/O)
* Thick: `$___ = server::` (it uses the server's tree path definitions) (Tree I/O)

So the TDI code would look like:

```py
TreeOpen("TREE", SHOT_NUMBER)
NODE/EXPRESSION (eg `\IP+1`)
```
So, all of these have varying amounts of network back and forth:
mdsconnect(server) has the least
trees i/o has very little
files i/o has the most
