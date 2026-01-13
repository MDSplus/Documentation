# MATLAB

MDSplus has a MATLAB API, allowing you to read, analyze, and write data to and from MDSplus trees using MATLAB.

There are three ways to set up communication between MATLAB and MDSplus:
* [Java bridge](#java-bridge)
* [Python bridge](#python-bridge)
* [mdsthin bridge](#mdsthin-bridge)

For Java and Python, the full MDSplus suite must be installed on your computer, plus compatible versions of Java or Python (check MATLAB documentation for compatible [Python](https://www.mathworks.com/support/requirements/python-compatibility.html) and [OpenJDK](https://www.mathworks.com/support/requirements/openjdk.html)). For the mdsthin bridge, only [mdsthin](https://github.com/MDSplus/mdsthin) needs to be installed. See the section on [troubleshooting](#troubleshooting) for more information.


## Setup

As long as `setup.sh` is sourced, the following should work. You can also set `MATLABPATH` or configure the MatLab search path manually. See the section on [troubleshooting](#troubleshooting) for more information).

> TODO: explain `MATLABPATH`? Mark W. found these documentation pieces on the MATLAB site, which we can list to

For more about `MATLABPATH`, please see the documentation on the MATLAB site: 
https://www.mathworks.com/help/matlab/matlab_env/what-is-the-matlab-search-path.html
https://www.mathworks.com/help/matlab/ref/path.html

### Testing

You can access MDSplus from Matlab via Java or Python. Once MATLAB can find the `.m` files in `$MDSPLUS_DIR/matlab` you can run these commands to test the Java or Python bridges:

```m
% to test the Java bridge
mdstest(false)

% to test the Python bridge
mdstest(true)

% to test the mdsthin bridge (TODO STEPHEN TEST)
mdstest(true, true)
```

## Usage

### Initializing MDSplus

#### Java bridge
```m
% Java is the default, but you can force it with:
mdsUsePython(false)
```

#### Python bridge
```m
mdsUsePython(true)
```

#### mdsthin bridge
```m
mdsUsePython(true, true)
```

### Connecting and Opening Trees
```m
% Connect to a server, in this case 123.456.7.89
mdsconnect('123.456.7.89')

ans = 
    1

% Open "mytree" to shot 42
mdsopen('mytree', 42)
```

### Reading Data
```m
% Assign the value from node with tag name "data_node" into a MATLAB workspace variable named "data_read"
data_read = mdsvalue('\data_node')

% If applicable, issue Tree Command Language (TCL) commands to the MDSplus server through MATLAB
mdsvalue('tcl($)', 'set current mytree 42')

% Close the current tree
mdsclose

% Disconnect from the server
mdsdisconnect
```

### Writing Data

```m
% Write the value of the Matlab workspace variable named "data_read" to the node with the tag name "data_node"
mdsput('\data_node', data_read)
 ```


## Troubleshooting

Many issues can be explained by compatibility between different versions of software. ~~In all cases, be sure to check both version of the server and the client.~~ (TODO: Tim thinks we need to say something about this, but not necessarily this.) See below for other specific issues.


### Manually Configuring the MATLAB Search Path

The commands used to read/write data from MDSplus trees are provided as MATLAB script files (`.m`), which are located in `$MDSPLUS_DIR/matlab`. You must add this folder to your MATLAB search path using the `Set Path` option from the File menu or using these commands:

```m
% add $MDSPLUS_DIR/matlab to path
addpath(fullfile(getenv('MDSPLUS_DIR'), 'matlab'))
savepath()
```
Relevant reference articles from the MATLAB Help Center:
* [What is the MATLAB Search Path?](https://www.mathworks.com/help/matlab/matlab_env/what-is-the-matlab-search-path.html)
* More on the [`addpath` command](https://www.mathworks.com/help/matlab/ref/addpath.html)
* Use the [`path` command](https://www.mathworks.com/help/matlab/ref/path.html) for additional troubleshooting
 

###  Java Bridge Troubleshooting

For reference, please also see to the [MathWorks documentation](https://www.mathworks.com/help/matlab/matlab_external/configure-your-system-to-use-java.html) for using Java with MATLAB as needed.

#### Java Compatability

Ensure that your version of Java is compatible with MDSplus. Search for "compatible OpenJDK" on the MATLAB website (or try [this link](https://www.mathworks.com/support/requirements/openjdk.html)).

#### Java `ClassPath`

##### For Personal Computers

Setting the Java class path can be done many ways; see all options in [this table](https://www.mathworks.com/help/matlab/matlab_external/java-class-path.html).
* For permanent configuration, we recommend the [Static Path](https://www.mathworks.com/help/matlab/matlab_external/static-path-of-java-class-path.html).
* For temporary configuration, using the [javaddpath](https://www.mathworks.com/help/matlab/ref/javaaddpath.html) will also work.
* For either method, you will need the following information:
    * The MDSplus Java classes are located in this folder: `$MDSPLUS_DIR/java/classes`
    * Java also needs access to the "libJavaMds" library that is in `$MDSPLUS_DIR/lib`. Use the `javalibrarypath.txt` file to specify that location. Read more about [libraries](https://www.mathworks.com/help/matlab/matlab_external/locate-native-method-libraries.html).
    * To troubleshoot, use the [`javaclasspath` command](https://www.mathworks.com/help/matlab/ref/javaclasspath.html) to make sure that it has `$MDSPLUS_DIR/java/classes`.

##### For Computing Clusters

If your organization runs MATLAB from a computing cluster, it will likely have multiple versions of MATLAB, Python, Java, and MDSplus installed. If so, please follow these instructions instead.

* Place configuration files in your user home directory. For example, on Linux `javaclasspath.txt` and `javalibrarypath.txt` can be placed in `~/.matlab/R2024b` (where "R2024b" is a version of MATLAB).
* To override configuration created by your the system administrator, you may need to use the `<before>` attribute as the first line of the `javaclasspath.txt` file; this ensures that the directories you specify will be searched first (and likely skipping the directories that the system administrator specified).
* To test the configuration of MATLAB / MDSplus, run `mdstest(0)`. 

### Python Bridge Troubleshooting

* Ensure that MATLAB is using the expected version of Python with:
    ```m
    pyversion()
    % TODO: Stephen to add output and example here
    ```

* Ensure you can `import MDSplus` from a Python prompt in the same terminal where you are launching MATLAB.

* Sourcing `setup.sh` doesn't always work when using the Python bridge. Depending on how MDSplus was installed, the `.pth` file might not be present. If it is missing, then one must make sure that the $PYTHONPATH environment variable includes `$MDSPLUS_DIR/python`.

* If on a cluster and MATLAB is using the wrong Python version, the user will likely have to use the `module` command to select a compatible Python before starting MATLAB.   


### mdsthin Bridge Troubleshooting

* Ensure you can `import mdsthin` from a python prompt in the same terminal where you're launching MATLAB.

* Follow steps for troubleshooting Python bridge in the previous section.

* If using mdsthin, the `matlab.tgz` file must also be installed (it is available on [GitHub in the Releases](https://github.com/MDSplus/mdsplus/releases) section).

### Reading Data: Troubleshooting

Occasionally, the API will return MDSplus status codes. These are usually large numbers indicating that a specific status message applies. Even numbers indicate a failure of some sort (basically the lowest bit is set to false, and that indicates a failure...but this may be too much info)

Example: the large number shown in the following output indicates that a `TreeFAILURE` condition occurred because the user does not have write permissions on the specified archive.

    ```
    >> mdsvalue('tcl($)', 'set current cmod 1090909009') 
    ans =

    int32

    265392034
    ```

TODO: link to a table or method of getting the status codes that can appear.
