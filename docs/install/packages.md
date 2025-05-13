 # MDSplus Packaging

MDSplus has been split into several packages so that you can install only the parts which you need. The following is the list of packages available to install. You can alway add or remove packages as needed.

| Package | Description |
| ------- | ----------- |
| &nbsp; | Catch all. If specific package is not specified, a catch all package will be installed which contains dependencies to the core system MDSplus subpackages. |
| camac | scripts and tdi functions for communicating with CAMAC serial highway data acquisition devices. |
| camac_bin | Libraries and executables for communicating with CAMAC serial highway data acquisition devices. |
| devel | Include files for software development. |
| devel_bin  | Static libraries for software development. |
| epics | Configuration files to provide the interface between EPICS and MDSplus |
| d3d | Tdi scripts for accessing data at the D3D experiment operated by GA in California. |
| epics | Configuration files used to integrate MDSplus into the EPICS control system software package. |
| gsi | Globus security infrastructure configuration files to enable secure mdsip communication using X.509 certificate authentication and authorization. |
| gsi_bin | Globus security infrastructure interface libaries to enable secure mdsip communication using X.509 certificate authentication and authorization. |
| hdf5 | tdi functions to convert between HDF5 and MDSplus data files. |
| hdf5_bin | Libraries and utilities to convert between HDF5 and MDSplus data files. |
| idl | Procedures used to access MDSplus from within the IDL (Interactive Data Language) product. |
| idl_bin | Libraries needed to access MDSplus from within the IDL (Interactive Data Language) product. |
| java | Java classes for accessing MDSplus from within java. Includes utilities such as jScope, jTraverser, and jDispatcher. |
| java_bin | Libraries used for accessing MDSplus from within java. Includes utilities such as jScope, jTraverser, and jDispatcher. |
| kbsidevices | Device support of devices used by the Korea Basic Science Institute. |
| kernel | All the core scripts and configuration files needed for most if not all MDSplus functions. Most other packages will include dependencies on this package. |
| kernel_bin | All the core libraries and executables needed for most if not all MDSplus functions. Most other packages will include dependencies on this package. |
| labview | Labview VI's for accessing MDSplus. |
| labview_bin | Libraries needed by Labview VI's for accessing MDSplus. |
| matlab | Matlab interface for MDSplus |
| mitdevices | Device support for many types of data acquisition devices developed at MIT Plasma Science and Fusion Laboratory. |
| mitdevices_bin | Libraries needed to provide device support for many types of data acquisition devices developed at MIT Plasma Science and Fusion Laboratory. |
| motif | Configuration files for Openmotif based utilities including dwscope, traverser, actmon, and actions. |
| motif_bin | Libraries and user interface descriptions used by the MDSplus motif applications. |
| mssql | Interface to Microsoft SQL relational databases. |
| php | PHP interface to MDSplus used for web cgi development. |
| python | Python language support for accessing MDSplus from python or python from MDSplus. |
| rfxdevices | Device support for many types of data acquisition devices developed for the RFX experiment in Padova.