# Installation on Debian (Ubuntu)

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
| Ubuntu 24.04    | [amd64](#ubuntu-2404-amd64) / [arm64](#ubuntu-2404-arm64) | [amd64](#ubuntu-2404-1)     |
| Ubuntu 22.04    | [amd64](#ubuntu-2204) | [amd64](#ubuntu-2204-1)     |
| Ubuntu 20.04    | [amd64](#ubuntu-2004) | [amd64](#ubuntu-2004-1)     |
| Debian Bookworm | [amd64](#debian-bookworm) / [arm64](#ubuntu-2404-arm64) | [amd64](#debian-bookworm-1) |
| Debian Bullseye | [amd64](#debian-bullseye) | [amd64](#debian-bullseye-1) |




### Alpha releases

#### Ubuntu 24.04 (amd64)

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 24.04 (arm64)

```sh
sudo sh -c "echo 'deb [arch=arm64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 22.04

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu22/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 20.04

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu20/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bookworm
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bookworm/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bullseye
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bullseye/repo MDSplus alpha' > /etc/apt/sources.list.d/mdsplus.list"
```

### Stable releases

#### Ubuntu 24.04

```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu24/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 22.04
 
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu22/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Ubuntu 20.04
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/Ubuntu20/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bookworm
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bookworm/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

#### Debian Bullseye
```sh
sudo sh -c "echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/mdsplus.asc] http://www.mdsplus.org/dist/debian/bullseye/repo MDSplus stable' > /etc/apt/sources.list.d/mdsplus.list"
```

## 3. Update Local Cache

Before you can use the new repository, you will need to update the local repository cache with the following terminal command:

```sh
sudo apt-get update
```

## 4. Packages

MDSplus is split into several packages so that you can install just the parts you need. [View the full list here](/install/packages.md). You may add or remove packages as needed.

## 5. Install MDSplus

Once the MDSplus repository has been added to the /etc/apt/sources.list file, installing MDSplus packages can be done using the `apt-get` command. There are slight nuances to this command depending on whether you are using the alpha or stable version of Linux&mdash;see below. Please note you can only install packages from one flavor of repositories since packages from different releases may be incompatible. After successfully installing MDSplus you will need to log out and back in to pick up environment variables needed to operate MDSplus.

### Alpha Package Installation

Use this terminal command:

```sh
sudo apt-get install mdsplus-alpha-package
```

If you are using the alpha repository, you will need to include `[alpha]` in the package name. See these examples:

````
sudo apt-get install mdsplus-alpha-idl #### Installs the alpha version of camac package
sudo apt-get install mdsplus-alpha     #### Installs all the alpha packages
````

### Stable Package Installation

Use this terminal command:

```sh
sudo apt-get install mdsplus-package
```

Here some example installation commands for the stable repository:

````
sudo apt-get install mdsplus-python #### Installs the python module and dependencies
sudo apt-get install mdsplus-kernel #### Installs the core part of MDSplus
sudo apt-get install mdsplus        #### Installs all the core MDSplus packages
````
## 6. Update Your Installation

To perform updates of your MDSplus packages, enter the following terminal command:

````sh
sudo apt-get upgrade 'mdsplus*'
````

## 7. Manually Installing MDSplus package

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