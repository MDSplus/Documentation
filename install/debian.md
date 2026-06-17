# Debian / Ubuntu

MDSplus now provides an `apt` repository for Ubuntu and Debian Linux distributions, which will allow you to subscribe to automatic updates as they are released. You may also choose which features of MDSplus you want to install on your Linux system. There are currently two different release levels of MDSplus:

| Release Level | Description                                                                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| alpha         | Updates occur whenever a change to an MDSplus source module.<br>Reflects the HEAD of the Git Repository.                                               |
| stable        | Updates occur less frequently.<br>New features added only after significant testing by sites using the alpha packages.<br>Bug fixes applied as needed. |

Instructions are provided below for each release level.

## 1. Import the Signing Key

First, use the terminal command for `curl` or `wget` (below) to install the signing key in `/usr/share/keyrings/` and then tell `apt` to use that key when updating from the MDSplus repository.

```sh
curl -fsSL http://www.mdsplus.org/dist/mdsplus.gpg.key | sudo tee /usr/share/keyrings/mdsplus.asc > /dev/null
```

OR

```sh
wget -O- http://www.mdsplus.org/dist/mdsplus.gpg.key | sudo tee /usr/share/keyrings/mdsplus.asc > /dev/null
```


## 2. Enable MDSplus Debian Repository

To add an MDSplus repository to your system, run the appropriate in Terminal, depending on your version of Ubuntu or Debian (see below for full list; you may use the links in the table below to jump to the sub-section):

| OS              | Alpha                            | Stable                               | 
|-----------------|----------------------------------|--------------------------------------|
| Ubuntu 24.04    | [amd64](#ubuntu-24-04-alpha-amd64) / [arm64](#ubuntu-24-04-alpha-arm64) | [amd64](#ubuntu-24-04-stable-amd64)     |
| Ubuntu 22.04    | [amd64](#ubuntu-22-04-alpha-amd64) | [amd64](#ubuntu-22.04-stable-amd64)     |
| Ubuntu 20.04    | [amd64](#ubuntu-20-04-alpha-amd64) | [amd64](#ubuntu-20.04-stable-amd64)     |
| Debian Bookworm | [amd64](#debian-bookworm-alpha-amd64) / [arm64](#debian-bookworm-alpha-arm64) | [amd64](#debian-bookworm-stable-amd64) |
| Debian Bullseye | [amd64](#debian-bullseye-alpha-amd64) | [amd64](#debian-bullseye-stable-amd64) |


### Alpha releases

#### Ubuntu 24.04 (alpha, amd64)

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 24.04 (alpha, arm64)

```sh
sudo sh -c "echo 'deb [arch=arm64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 22.04 (alpha, amd64)

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu22/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 20.04 (alpha, amd64)

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu20/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bookworm (alpha, amd64)
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bookworm/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bookworm (alpha, arm64)
```sh
sudo sh -c "echo 'deb [arch=arm64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bookworm/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bullseye (alpha, amd64)
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bullseye/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

### Stable releases

#### Ubuntu 24.04 (stable, amd64)

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 22.04 (stable, amd64)
 
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu22/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 20.04 (stable, amd64)
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu20/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bookworm (stable, amd64)
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bookworm/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bullseye (stable, amd64)
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bullseye/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

## 3. Update Local Cache

Before you can use the new repository, you will need to update the local repository cache with the following terminal command:

```sh
sudo apt-get update
```

## 4. Packages

MDSplus is split into several packages so that you can install just the parts you need. The full table is listed below. Select the packages you want to install and run:

```sh
sudo apt install <packages>
```

| Stable Package         | Alpha Package                | Description                                                                                                                                               |
|------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Core**               |                              |                                                                                                                                                           |
| mdsplus-kernel         | mdsplus-alpha-kernel         | All the core scripts and configuration files needed for most if not all MDSplus functions. Most other packages will include dependencies on this package. |
| mdsplus-kernel-bin     | mdsplus-alpha-kernel-bin     | All the core libraries and executables needed for most if not all MDSplus functions. Most other packages will include dependencies on this package.       |
| mdsplus-devel          | mdsplus-alpha-devel          | Header files for software development.                                                                                                                    |
| mdsplus-devel-bin      | mdsplus-alpha-devel-bin      | Static libraries for software development.                                                                                                                |
| mdsplus-motif          | mdsplus-alpha-motif          | Application menu entries for Open Motif based utilities including dwscope, traverser, actmon, and actions.                                                |
| mdsplus-motif-bin      | mdsplus-alpha-motif-bin      | Executables, libraries, and user interface descriptions for Open Motif based utilities including dwscope, traverser, actmon, and actions.                 |
|**Language/API Bindings**|                     |                                                                                                                                                           |
| mdsplus-idl            | mdsplus-alpha-idl            | Procedures (.pro files) used to access MDSplus from within IDL (Interactive Data Language).                                                               |
| mdsplus-idl-bin        | mdsplus-alpha-idl-bin        | Libraries used to access MDSplus from within IDL (Interactive Data Language).                                                                             |
| mdsplus-java           | mdsplus-alpha-java           | Java classes for accessing MDSplus from within Java and utilities such as jScope, jTraverser, and jDispatcher.                                            |
| mdsplus-java-bin       | mdsplus-alpha-java-bin       | Scripts used to launch jScope, jTraverser, and jDispatcher and the Java JNI interface library.                                                            |
| mdsplus-labview        | mdsplus-alpha-labview        | LabVIEW source code (.vi files) for interfacing with MDSplus.                                                                                             |
| mdsplus-labview-bin    | mdsplus-alpha-labview-bin    | Libraries needed by the LabVIEW source to interface with MDSplus.                                                                                         |
| mdsplus-matlab         | mdsplus-alpha-matlab         | MATLAB API package to interface with MDSplus                                                                                                              |
| mdsplus-mssql          | mdsplus-alpha-mssql          | The MdsSql library, used to access Microsoft SQL relational databases.                                                                                    |
| mdsplus-python         | mdsplus-alpha-python         | Python API package to interface with MDSplus.                                                                                                             |
| mdsplus-epics          | mdsplus-alpha-epics          | Configuration files and examples for integrating MDSplus into the EPICS control system software package.                                                  |
| mdsplus-hdf5           | mdsplus-alpha-hdf5           | TDI functions to convert between HDF5 and MDSplus data files.                                                                                             |
| mdsplus-hdf5-bin       | mdsplus-alpha-hdf5-bin       | Libraries and utilities to convert between HDF5 and MDSplus data files.                                                                                   |
| **Site Specific**      |                              |                                                                                                                                                           |
| mdsplus-d3d            | mdsplus-alpha-d3d            | TDI scripts for accessing data at the D3D experiment operated by GA in California.                                                                        |
| mdsplus-kbsidevices    | mdsplus-alpha-kbsidevices    | TDI device codes for devices used by the Korea Basic Science Institute.                                                                                   |
| mdsplus-mitdevices     | mdsplus-alpha-mitdevices     | TDI and Python device codes for devices used at the MIT Plasma Science and Fusion Laboratory.                                                             |
| mdsplus-mitdevices-bin | mdsplus-alpha-mitdevices-bin | Device libraries for devices used at the MIT Plasma Science and Fusion Laboratory.                                                                        |
| mdsplus-rfxdevices     | mdsplus-alpha-rfxdevices     | TDI, Python and Java device codes for devices used at the RFX experiment in Padova.                                                                       |
| mdsplus-w7xdevices     | mdsplus-alpha-w7xdevices     | Python device codes used at the W7X experiment in Germany.                                                                                                |
| **Legacy**             |                              |                                                                                                                                                           |
| mdsplus-camac          | mdsplus-alpha-camac          | Scripts and TDI functions for communicating with CAMAC serial highway data acquisition devices.                                                           |
| mdsplus-camac-bin      | mdsplus-alpha-camac-bin      | Libraries and executables for communicating with CAMAC serial highway data acquisition devices.                                                           |
| mdsplus-gsi            | mdsplus-alpha-gsi            | Globus security infrastructure configuration files to enable secure mdsip communication using X.509 certificate authentication and authorization.         |
| mdsplus-gsi-bin        | mdsplus-alpha-gsi-bin        | Globus security infrastructure interface libaries to enable secure mdsip communication using X.509 certificate authentication and authorization.          |
| mdsplus-php            | mdsplus-alpha-php            | PHP interface to MDSplus used for web cgi development.                                                                                                    |




## 5. Update Your Installation

To perform updates of your MDSplus packages, enter the following terminal command:

````sh
sudo apt upgrade 'mdsplus*'
````

## Or, Manually Install MDSplus Package

It is possible to manually install MDSplus debian packages instead of using a Debian repository, but you must account for all the dependencies yourself. It is recommended to use one of the repositories. To download packages, use the correct link below, depending on your operating system version.

The following table shows the most recent MDSplus debian packages.

| Branch | Distribution | Version | MDSplus Package URL |
|-------|--------|---------|-------------|
| Alpha | Ubuntu | 24.04 | [mdsplus.org/dist/Ubuntu24/alpha/DEBS/](http://www.mdsplus.org/dist/Ubuntu24/alpha/DEBS/) |
|       |        | 22.04 | [mdsplus.org/dist/Ubuntu22/alpha/DEBS/](https://www.mdsplus.org/dist/Ubuntu22/alpha/DEBS/) |
|       |        | 20.04 | [mdsplus.org/dist/Ubuntu20/alpha/DEBS/](https://www.mdsplus.org/dist/Ubuntu20/alpha/DEBS/) |
|       | Debian | Bookworm | [mdsplus.org/dist/DebianBookworm/alpha/DEBS/](https://www.mdsplus.org/dist/DebianBookworm/alpha/DEBS/) |
|       |        | Bullseye | [mdsplus.org/dist/DebianBullseye/alpha/DEBS/](https://www.mdsplus.org/dist/DebianBullseye/alpha/DEBS/) |
| Stable | Ubuntu | 24.04 | [mdsplus.org/dist/Ubuntu24/stable/DEBS/](https://www.mdsplus.org/dist/Ubuntu24/stable/DEBS/) |
|       |        | 22.04 | [mdsplus.org/dist/Ubuntu22/stable/DEBS/](https://www.mdsplus.org/dist/Ubuntu22/stable/DEBS/) |
|       |        | 20.04 | [mdsplus.org/dist/Ubuntu20/stable/DEBS/](https://www.mdsplus.org/dist/Ubuntu20/stable/DEBS/) |
|       | Debian | Bookworm | [mdsplus.org/dist/DebianBookworm/stable/DEBS/](https://www.mdsplus.org/dist/DebianBookworm/stable/DEBS/) |
|       |        | Bullseye | [mdsplus.org/dist/DebianBullseye/stable/DEBS/](https://www.mdsplus.org/dist/DebianBullseye/stable/DEBS/) |