
# Tree Access

When accessing data stored in MDSplus, you will need to choose one of the following access methods. Alternatively, your site may dictate which access methods are permitted. The methods available are described below, along with their pros, cons, and our recommendations.

## Local

Local access is, of course, the fastest method available. It should be used for writing data and for large analysis jobs when possible. When creating an mdsip server to serve data to a site, this server should have local access to the data if possible. "Local" access to shared filesystems such as NFS is not recommended, as the number of locks will tank your performance. Not every language API supports local access, as some require an mdsip server to communicate with.

Configuring local access only requires setting the tree-specific path or default tree path environment variables. See [Environment Variables](./environment-variables.md#tree_path) for more information.

```sh
export mytree_path=/path/to/trees/mytree
# or
export default_tree_path=/path/to/trees/~t
```

> TODO: object APIs and thin-style apis with local://0 thread://0 etc
> See thick/distributed for more information

*Note:* Some language APIs support [Local](#local) access with a [Thin Client](#thin-client) style API using connection strings such as "local://0" or "thread://0".

## Thin Client

Thin client provides the fastest method for reading data over a network, and the most minimal installation. It should be used for reading data from a centralized server and is available from all languages supported by MDSplus. It is not recommended to use thin client for writing data, especially segmented records or structured data. 

This works by sending TDI expressions to the server for evaluation, and then returning the result. This is the most similar method available to working with an SQL server. This works best when the server has [Local](#local) access to the data, and enough resources to handle the evaluations and calculations. The only data that can be transmitted over thin client is scalars and arrays, so any structured data needs to be sent as the TDI expression that would build the data structure.

Regardless of the language, the workflow remains the same:
1. `mdsconnect()`: Connect to the server (or to "local" for supported languages)
2. `mdsvalue()`: Evaluate one or more expressions
3. `mdsdisconnect()`: Disconnect

Additionally, helper functions such as `mdsopen()` and `mdsput()` exist in most language APIs to streamline common operations. These often call other TDI functions, such as `TreeOpen()` and `TreePut()` on the server.

Comprehensive documentation for TDI to use when writing expressions is in progress.
<!--- TODO: See [TDI](./tdi/) for a comprehensive guide on the language features and functions available when writing expressions. --->

**Using TDI**
```tdi
mdsconnect("myserver")

mdsopen("mytree", 12345)

# Absolute value of the data in the node, and the dimension (timebase)
_y = mdsvalue("abs(mynode)")
_x = mdsvalue("dim_of(mynode)")

# Store simple data in a node
mdsput("myfreq", "$", 10000)

# Store data with units in a node
mdsput("myfreq", "Build_With_Units($, 'Hz')", 10000)

# Construct and store a signal
mdsput("mynode", "Build_Signal($, *, $)", [0, 5, 0, 5], [0.1, 0.2, 0.3, 0.4])
```

See [Using MATLAB](./apis/matlab.md#usage) for more examples.

*Note:* If you are using Python, consider using [mdsthin](https://github.com/MDSplus/mdsthin) which can be installed without the rest of MDSplus.

## Thick / Distributed Clients

With Thick or Distributed clients the data is transferred from the server and then the expressions are evaluated locally. The two only differ in the way the data is accessed and transferred. These provide access to the rich object-based APIs, but often have performance limitations and are not recommended for writing data.

Thick exists at the level of tree operations, and Distributed exists at the level of file operations. Functionally, the main difference is that Thick uses the tree paths configured on the server, where Distributed requires you to provide them. They have comparable performance, but you may find one to be better based on your network configuration.

**Thick Client**
```sh
export mytree_path=myserver::
# or
export default_tree_path=myserver::
```

**Distributed Client**
```sh
export mytree_path=myserver::/path/to/trees/mytree
# or
export default_tree_path=myserver::/path/to/trees/~t
```

Use any of the object-based APIs or the C TreeShr functions to utilize Thick, Distributed, and Local access methods.

**Using TDI**
```tdi
TreeOpen("mytree", 12345)

# Absolute value of the data in the node, and the dimension (timebase)
_y = abs(mynode)
_x = dim_of(mynode)
```

<!--- TODO: Crosslink to python documentation and other object-based APIs --->