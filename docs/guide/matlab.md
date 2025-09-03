# MATLAB with MDSplus

MDSplus has a MATLAB API, allowing you to read, analyze, and write data to and from MDSplus trees using MATLAB.

There are three ways to set up communication between MATLAB and MDSplus:
* Java bridge
* Python bridge
* mdsthin

For Java and Python, the full MDSplus suite must be installed on your computer, plus compatible versions of Java or Python (check MATLAB documentation for compatible [Python](https://www.mathworks.com/support/requirements/python-compatibility.html) and [OpenJDK](https://www.mathworks.com/support/requirements/openjdk.html)). For mdsthin, only [mdsthin](https://github.com/MDSplus/mdsthin) needs to be installed. 

Note: In the documentation below, the environment variable `$MDSPLUS_DIR` will be used as an abbreviation for wherever MDSplus is installed on your computer. However, when entering paths into the MATLAB configuration settings, please use the full path as it pertains to your computer, not the variable. (Typically on Linux and MacOS: `/usr/local/mdsplus`; for Windows: `c:\Program Files\MDSplus`)

## 1.  Set Up Search Path
The commands used to read/write data from MDSplus trees are provided as MATLAB script files (`.m`), which are located in `$MDSPLUS_DIR/matlab`. You must add this folder to your MATLAB search path using the `Set Path` option from the File menu or using these text commands:

```m
% add $MDSPLUS_DIR/matlab to path
addpath(fullfile(getenv('MDSPLUS_DIR'), 'matlab'))
savepath()
```


You can access MDSplus from Matlab via java or python. Once MATLAB can find the `.m` files in `$MDSPLUS_DIR/matlab` you can run these commands to test the Java or Python bridges:

```m
% to test the Java bridge
mdstest(0)
% to test the Python bridge
mdstest(1)
```

Additional configuration may be needed to use MDSplus from MATLAB depending on the preferred bridge (Java or Python). Both bridges should work interchangeably but depending on your configuration one may be more performant than the other. The first use of the MATLAB API might be a bit slow; subsequent uses will be faster.


## 2a. Java Bridge

### Compatibility
Ensure that your version of Java is compatible with MDSplus. Search for "compatible OpenJDK" on the MATLAB website (or try [this link](https://www.mathworks.com/support/requirements/openjdk.html)).
* > TODO: get list of compatible Java versions (or simply link to the page where that lives)

### Set up Java Class Path: Personal Computers
Setting the Java class path can be done many ways: see all options in [this table](https://www.mathworks.com/help/matlab/matlab_external/java-class-path.html).
* For permanent configuration, we recommend the [Static Path](https://www.mathworks.com/help/matlab/matlab_external/static-path-of-java-class-path.html).
* For temporary configuration, using the [javaddpath](https://www.mathworks.com/help/matlab/ref/javaaddpath.html) will also work.
* For either method, you will need the following information:
    * The MDSplus Java classes are located in this folder: `$MDSPLUS_DIR/java/classes`
    * Java also needs access to the "libJavaMds" library that is in `$MDSPLUS_DIR/lib`. Use the `javalibrarypath.txt` file to specify that location. Read more about [libraries](https://www.mathworks.com/help/matlab/matlab_external/locate-native-method-libraries.html).
    * To troubleshoot, use the [`javaclasspath` command](https://www.mathworks.com/help/matlab/ref/javaclasspath.html) to make sure that it has `$MDSPLUS_DIR/java/classes`.



### Set up Java Class Path: Computing Clusters
If your organization runs MATLAB from a computing cluster, which will likely have multiple versions of MATLAB, Python, Java, and MDSplus installed. If so, please follow these instructions instead.
* Place configuration files in your user home directory. For example, on Linux `javaclasspath.txt` and `javalibrarypath.txt` can be placed in `~/.matlab/R2024b` (where "R2024b" is a version of MATLAB).
* To override configuration created by your the system administrator, you may need to use the `<before>` attribute as the first line of the `javaclasspath.txt` file; this ensures that the directories you specify will be searched first (and likely skipping the directories that the system administrator specified).
* To test the configuration of MATLAB / MDSplus, run `mdstest(0)`. 


### Open Tree, Read Data
```m
% Connect to a server, in this case 123.456.7.89
mdsconnect('123.456.7.89')

% Open "mytree" to shot 42
mdsopen('mytree', 42)

% Assign the value from node with tag name "data_node" into a MATLAB workspace variable named "data_read"
data_read = mdsvalue('\data_node')

% If applicable, issue Tree Command Language (TCL) commands to the MDSplus server through MATLAB
mdsvalue('tcl($)', 'set current mytree 42')

% Close the current tree
mdsclose

% Disconnect from the server
mdsdisconnect
```

### Write Data

```m
% Write the value of the Matlab workspace variable named "data_read" to the node with the tag name "data_node"
mdsput('\data_node', data_read)
 ```



### Other things
* [Requirements](https://www.mathworks.com/support/requirements/openjdk.html)
* [General Info](https://www.mathworks.com/help/matlab/matlab_external/configure-your-system-to-use-java.html)





> note to self: To test the configuration of MATLAB / MDSplus, run `mdstest(0)`. See the "Setup" section of this page from the Wiki.   https://www.mdsplus.org/index.php/Documentation:Reference:Matlab. TODO: Delete this note before this page gets published


## 2b. Python Bridge

The Java bridge is the default. To use the Python bridge, the MATLAB script must start with:
```
mdsUsePython(true)
```

To disable the Python bridge and revert to the Java bridge, use:
```
mdsUsePython(false)
```

### Open Tree
```m
%Code Snippet goes here
```

### Read Data

```m
%Code Snippet goes here
```


## mdsthin Bridge

More to come.

It must be called with:
```
mdsUsePython(true, true)
```




---

### FAQs/Reference/Additional Help
Reference articles from the MATLAB Help Center:
* [What is the MATLAB Search Path?](https://www.mathworks.com/help/matlab/matlab_env/what-is-the-matlab-search-path.html)
* More on the [`addpath` command](https://www.mathworks.com/help/matlab/ref/addpath.html)
* Use the `path command` ([reference article here](https://www.mathworks.com/help/matlab/ref/path.html)) for troubleshooting issues


