# Thin Client

With thin client, only the bare minimum of MDSplus runs on your computer; you send instructions to the server, which opens trees and does all of calculations, etc. before returning the answers to you.

Why use thin:
* you might not have admin rights on your computer
* less latency, less back and forth

## How to Use 
### 1. connect ()/disconnect ()
You'll need:
* a server that will be running MDSplus for you. Find your server for your environment (probably from your sys admin or whoever)--aka the server  and use the `connect()` command.
TODO: confirm with Stephen

### 2. value / get
MDSvalue everywhere except Python, which calls it "get"
You'll need:
* Expression
* Arguments

#### What Runs Where

### 3. Base arguments


major  exception: `mdsconnect ('local')` which allows you run thin but on your own computer. useful for testing, for example. this doesn't exist for all languages. we'll need to call this out






## Sample Code Snippets:
TODO: SLW. Mostly like a "frequently used snippets" (like a faq)

and or I want to do X, and here's where you go for those TDI expressions

`getnci` is a major one


### Get the nids of the members or children of a node
Tip: Members and children are basically the same thing but for historical reasons they exist as two separate entities

If you call `getnci(_node, "member_nids")` (where `_node` is either a NID or a path) you will get the member nodes themselves which will then try to evaluate as if you called `data(getnci(_node, "member_nids"))` which doesn't make any sense (TODO: improve this. but it's a true statement. lol. but it makes sense in the context in which it was written--TDI inherently is trying to give you the answer). In order to get a functional list of these nodes, you need to either get their NIDs, paths, or names. You can do that with the following: 

```tdi
getnci(getnci(_node, "member_nids"), "nid_number")
getnci(getnci(_node, "member_nids"), "fullpath")
getnci(getnci(_node, "member_nids"), "node_name")
getnci(getnci(_node, "children_nids"), "nid_number")
getnci(getnci(_node, "children_nids"), "fullpath")
getnci(getnci(_node, "children_nids"), "node_name")
```

```
def __dir__(self):
        name_list = self.conn.get('''
            set_range(size(_list), _list=[
                getnci(getnci($, "CHILDREN_NIDS"), "NODE_NAME"),
                getnci(getnci($, "MEMBER_NIDS"), "NODE_NAME")
            ])
            ''', self.nid, self.nid)
        return [ name.strip() for name in name_list ]
```



---
NOTES: 
TODO: figure out how to fold this in

In thin client, all the work is done by the server, and it just sends you the answer, so the server needs to know how to open the trees.
* you tell it where to go by connecting to Address of mdsip server
* user must specify server (i.e., you must know where you're going)

example in TDI:
```py
mdsconnect("SERVER_ADDRESS")
mdsopen("TREE", SHOT_NUMBER)
ans = mdsvalue("NODE/EXPRESSION")
```
