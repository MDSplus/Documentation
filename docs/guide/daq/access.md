# Configure Access



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
* mdsip.hosts is a whitelist/user-mapping file...lets only specified users 
  * JAVA_USER :'-(
    * jScope unfortunately does not use your user credentials when connecting to mdsip servers. It instead uses `JAVA_USER`. This can be overwritten by the command line, however, to allow users of jScope to access your data, it can be useful to add a line for `JAVA_USER` to `mdsip.hosts` 
* ssh?

![](DAQconnections2.svg)
*Diagram of clients accessing data through the :8000 port as well as as over SSH*

The administrator will need to determine what access methods are allowed (thin, local, thick/dist, ssh) and what access methods are automatically configured ($TREE_path / $default_tree_path)

## Thin Client

In thin client, all the work is done by the server, and it just sends you the answer, so the server needs to know how to open the trees.
* you tell it where to go by connecting to Address of mdsip server
* user must specify server (i.e., you must know where you're going)

example in TDI:
```py
mdsconnect("SERVER_ADDRESS")
mdsopen("TREE", SHOT_NUMBER)
ans = mdsvalue("NODE/EXPRESSION")
```


## Local/Thick/Distributed client
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


## `mdsip.hosts`

When calling `mdsip` you must specify a `mdsip.hosts` file with `-h`; for example: 
```
mdsip -c 0 -p 8123 -h /etc/mdsip.hosts
```

The `mdsip.hosts` file  defines how to map users for incoming connections. It can also be used to control access for specific user groups. (*but not really...TODO: More to come). NOTE: SSH access--we have this described somewhere else and if you want some authorization, use SSH. The `mdsip.hosts` file follows the language/formatting conventions below:
* `#` indicates a comment and the rest of the line will be ignored; must be placed at the beginning of the line
* `|` separates the two halves (TODO: Come back to this)
  * left is address wildcard
  * right is the mapping information
* `!` at the beginning of a line denies access. Examples:
  * `! slwalsh@*` block the user slwalsh from anywhere
  * `! *@192.168.10.42` block every user from 192.168.10.42
  * `! 192.168.10.42` does **NOT** block users from that IP
  * Note: When using the `!` anything after the `|` divider is ignored.
* The file is checked top to bottom and the first line that succeeds will finish the process
* additional whitespace is ignored

TODO: Investigate -h TDImyaccessfunction 
See also: systemd/xinetd under [On Demand mdsip](on-demand-mdsip).


### Examples
The following examples are solutions to specific problems and can be combined as needed. 

#### Read-only
This maps everyone to a read-only user.

```
* | nobody 
```


#### Normal Configuration
This can be considered the basic normal configuration. 
* the first line accepts connections from anywhere and attempts to map the username specified to a user on the system. if it fails, it will go to the next line. 
* the second line accepts connections from anywhere and maps to them to a read-only user 

```
* | MAP_TO_LOCAL
* | nobody 
```


#### Controlling user mapping based on incoming subnet

In this example, we have 2 networks: 
* `192.168.10.0/24` is for computers accessing data. 
  * Users coming from here will be mapped to their accounts, with their privileges.
* `192.168.20.0/24` is for devices capturing and storing data. 
  * Any incoming connections will be mapped to the `daq_user` service account, which for the purposes of this example, would be an account set up with privileges to write data.

```
*@192.168.10.* | MAP_TO_LOCAL 
*@192.168.20.* | daq_user
```


#### Controlling user mapping based on incoming subnet, not octet-aligned

This example is the same as above, however, the networks do not align to an octet boundary. Currently, MDSplus does not understand CIDR (or even netmask) subnetting, so we must rely solely on wildcards. 

In this example, our two networks are:
* `172.16.4.0/22`
* `172.16.8.0/22`

```
*@172.16.4.*  | MAP_TO_LOCAL 
*@172.16.5.*  | MAP_TO_LOCAL 
*@172.16.6.*  | MAP_TO_LOCAL 
*@172.16.7.*  | MAP_TO_LOCAL 
*@172.16.8.*  | daq_user
*@172.16.9.*  | daq_user
*@172.16.10.* | daq_user
*@172.16.11.* | daq_user
```

#### Allowing a specific user from a specific host

```
# allow John from his workstation
jdoe@192.168.42.123 | MAP_TO_LOCAL
```

#### Using a Domain Name
TODO: intro text
```
*@example.com | MAP_TO_LOCAL
```


#### MULTI
TODO: more to come
```
MULTI | username
```


#### Fusion Grid
TODO

