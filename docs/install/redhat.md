# Red Hat / CentOS / Rocky Linux

MDSplus now provides an `apt` repository for Red Hat Linux distributions, which will allow you to subscribe to automatic updates as they are released. You may also choose which features of MDSplus you want to install on your Linux system. There are currently two different release levels of MDSplus:

| Release Level | Description |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| alpha         | Updates occur whenever a change is made to an MDSplus source module.<br>Reflects the HEAD of the Git repository.                                               |
| stable        | Updates occur less frequently.<br>New features added only after significant testing by sites using the alpha packages.<br>Bug fixes applied as needed. |

Instructions are provided below for each release level.


## 0. EPEL Repository

MDSplus depends on a variety of software packages, some of which are included with standard Red Hat Enterprise Linux distributions, but others which must be acquired from Extra Packages for Enterprise Linux (EPEL). Please configure your system to include the EPEL repository **before** trying to install MDSplus. You can find more information about EPEL and the RPMs for configuring your system to use it on the [EPEL Home Page](http://fedoraproject.org/wiki/EPEL).

```sh
# Modern RHEL
sudo dnf install epel-release

# Legacy RHEL
sudo yum install epel-release
```

## 1. Import the Signing Key

First, open a terminal (aka shell) window and run a `curl` or `wget` command  (below) to install the signing key in `/usr/share/keyrings/` and then tell `apt` to use that key when updating from the MDSplus repository.

```sh
curl -fsSL http://www.mdsplus.org/dist/RPM-GPG-KEY-MDSplus | sudo tee /etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus > /dev/null
```

or

```sh
wget -O http://www.mdsplus.org/dist/RPM-GPG-KEY-MDSplus | sudo tee /etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus > /dev/null
```


## 2. Enable MDSplus Repository

To add an MDSplus repository to your system, run one of the following commands in Terminal, depending on your version of Linux:
### Alpha releases

#### RHEL 9 / Rocky Linux 9


```sh
cat - | sudo tee /etc/yum.repos.d/mdsplus.repo << EOF
[MDSplus]
name=MDSplus
baseurl=http://www.mdsplus.org/dist/el9/alpha/RPMS
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus
metadata_expire=300
EOF
```

#### RHEL 8 / CentOS 8 / Rocky Linux 8 

```sh
cat - | sudo tee /etc/yum.repos.d/mdsplus.repo << EOF
[MDSplus]
name=MDSplus
baseurl=http://www.mdsplus.org/dist/el8/alpha/RPMS
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus
metadata_expire=300
EOF
```

### Stable releases

#### RHEL 9 / Rocky Linux 9

```sh
cat -  | sudo tee /etc/yum.repos.d/mdsplus.repo << EOF
[MDSplus]
name=MDSplus
baseurl=http://www.mdsplus.org/dist/el9/stable/RPMS
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus
metadata_expire=300
EOF
```

#### RHEL 8 / CentOS 8 / Rocky Linux 8
```sh
cat - | sudo tee /etc/yum.repos.d/mdsplus.repo << EOF
[MDSplus]
name=MDSplus
baseurl=http://www.mdsplus.org/dist/el8/stable/RPMS
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus
metadata_expire=300
EOF
```

## 3. Update Local Cache

Before you can use the new repository, you will need to update the local repository cache with the following terminal command:

```sh
# Modern RHEL
sudo dnf check-update

# Legacy RHEL
sudo yum check-update
```

## 4. Install Packages

MDSplus is split into several packages so that you can install just the parts you need. The full table is listed below. Select the packages you want to install and run:

```sh
# Modern RHEL
sudo dnf install <packages>

# Legacy RHEL
sudo yum install <packages>
```

| Stable Package         | Alpha Package                | Description                                                                                                                                               |
|------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Core**               |                              |                                                                                                                                                           |
| mdsplus-kernel         | mdsplus-alpha-kernel         | All the core scripts and configuration files needed for most if not all MDSplus functions. Most other packages will include dependencies on this package. |
| mdsplus-kernel_bin     | mdsplus-alpha-kernel_bin     | All the core libraries and executables needed for most if not all MDSplus functions. Most other packages will include dependencies on this package.       |
| mdsplus-devel          | mdsplus-alpha-devel          | Header files for software development.                                                                                                                    |
| mdsplus-devel_bin      | mdsplus-alpha-devel_bin      | Static libraries for software development.                                                                                                                |
| mdsplus-motif          | mdsplus-alpha-motif          | Application menu entries for Open Motif based utilities including dwscope, traverser, actmon, and actions.                                                |
| mdsplus-motif_bin      | mdsplus-alpha-motif_bin      | Executables, libraries, and user interface descriptions for Open Motif based utilities including dwscope, traverser, actmon, and actions.                 |
|**Language/API Bindings**|                     |                                                                                                                                                           |
| mdsplus-idl            | mdsplus-alpha-idl            | Procedures (.pro files) used to access MDSplus from within IDL (Interactive Data Language).                                                               |
| mdsplus-idl_bin        | mdsplus-alpha-idl_bin        | Libraries used to access MDSplus from within IDL (Interactive Data Language).                                                                             |
| mdsplus-java           | mdsplus-alpha-java           | Java classes for accessing MDSplus from within Java and utilities such as jScope, jTraverser, and jDispatcher.                                            |
| mdsplus-java_bin       | mdsplus-alpha-java_bin       | Scripts used to launch jScope, jTraverser, and jDispatcher and the Java JNI interface library.                                                            |
| mdsplus-labview        | mdsplus-alpha-labview        | LabVIEW source code (.vi files) for interfacing with MDSplus.                                                                                             |
| mdsplus-labview_bin    | mdsplus-alpha-labview_bin    | Libraries needed by the LabVIEW source to interface with MDSplus.                                                                                         |
| mdsplus-matlab         | mdsplus-alpha-matlab         | MATLAB API package to interface with MDSplus                                                                                                              |
| mdsplus-mssql          | mdsplus-alpha-mssql          | The MdsSql library, used to access Microsoft SQL relational databases.                                                                                    |
| mdsplus-python         | mdsplus-alpha-python         | Python API package to interface with MDSplus.                                                                                                             |
| mdsplus-epics          | mdsplus-alpha-epics          | Configuration files and examples for integrating MDSplus into the EPICS control system software package.                                                  |
| mdsplus-hdf5           | mdsplus-alpha-hdf5           | TDI functions to convert between HDF5 and MDSplus data files.                                                                                             |
| mdsplus-hdf5_bin       | mdsplus-alpha-hdf5_bin       | Libraries and utilities to convert between HDF5 and MDSplus data files.                                                                                   |
| **Site Specific**      |                              |                                                                                                                                                           |
| mdsplus-d3d            | mdsplus-alpha-d3d            | TDI scripts for accessing data at the D3D experiment operated by GA in California.                                                                        |
| mdsplus-kbsidevices    | mdsplus-alpha-kbsidevices    | TDI device codes for devices used by the Korea Basic Science Institute.                                                                                   |
| mdsplus-mitdevices     | mdsplus-alpha-mitdevices     | TDI and Python device codes for devices used at the MIT Plasma Science and Fusion Laboratory.                                                             |
| mdsplus-mitdevices_bin | mdsplus-alpha-mitdevices_bin | Device libraries for devices used at the MIT Plasma Science and Fusion Laboratory.                                                                        |
| mdsplus-rfxdevices     | mdsplus-alpha-rfxdevices     | TDI, Python and Java device codes for devices used at the RFX experiment in Padova.                                                                       |
| mdsplus-w7xdevices     | mdsplus-alpha-w7xdevices     | Python device codes used at the W7X experiment in Germany.                                                                                                |
| **Legacy**             |                              |                                                                                                                                                           |
| mdsplus-camac          | mdsplus-alpha-camac          | Scripts and TDI functions for communicating with CAMAC serial highway data acquisition devices.                                                           |
| mdsplus-camac_bin      | mdsplus-alpha-camac_bin      | Libraries and executables for communicating with CAMAC serial highway data acquisition devices.                                                           |
| mdsplus-gsi            | mdsplus-alpha-gsi            | Globus security infrastructure configuration files to enable secure mdsip communication using X.509 certificate authentication and authorization.         |
| mdsplus-gsi_bin        | mdsplus-alpha-gsi_bin        | Globus security infrastructure interface libaries to enable secure mdsip communication using X.509 certificate authentication and authorization.          |
| mdsplus-php            | mdsplus-alpha-php            | PHP interface to MDSplus used for web cgi development.                                                                                                    |


## 5. Update MDSplus

To perform updates of your MDSplus packages, enter the following terminal command:

````sh
# Modern RHEL
sudo dnf upgrade 'mdsplus*'

# Legacy RHEL
sudo yum upgrade 'mdsplus*'
````


## Or, Manually Install the MDSplus Package

It is possible to manually install MDSplus RHEL packages instead of using a RHEL repository, but you must account for all the dependencies yourself. It is recommended to use one of the repositories. To download packages, use the correct link below, depending on your operating system version.

The following table shows the most recent MDSplus RHEL packages.

| Branch | Version | MDSplus Package URL |
|--------|--------|-------------|
| Alpha  | 8      | [mdsplus.org/dist/el8/alpha/](https://www.mdsplus.org/dist/el8/alpha/) |
|        | 9      | [mdsplus.org/dist/el9/alpha/](https://www.mdsplus.org/dist/el9/alpha/) |
| Stable | 8      | [mdsplus.org/dist/el8/stable/](https://www.mdsplus.org/dist/el8/stable/) |
|        | 9      | [mdsplus.org/dist/el9/stable/](https://www.mdsplus.org/dist/el9/stable) |