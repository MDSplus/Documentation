# Installation on Red Hat Linux (Rocky, CentOS, Fedora Core)

MDSplus now provides an `apt` repository for Red Hat Linux distributions, which will allow you to subscribe to automatic updates as they are released. You may also choose which features of MDSplus you want to install on your Linux system. There are currently two different release levels of MDSplus:

| Release Level | Description |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| alpha         | Updates occur whenever a change is made to an MDSplus source module.<br>Reflects the HEAD of the Git repository.                                               |
| stable        | Updates occur less frequently.<br>New features added only after significant testing by sites using the alpha packages.<br>Bug fixes applied as needed. |

Instructions are provided below for each release level.


## 0. EPEL Repository

MDSplus depends on a variety of software packages, some of which are included with standard Red Hat Enterprise Linux distributions, but others which must be acquired from Extra Packages for Enterprise Linux (EPEL). Please configure your system to include the EPEL repository **before** trying to install MDSplus. You can find more information about EPEL and the RPMs for configuring your system to use it on the [EPEL Home Page](http://fedoraproject.org/wiki/EPEL).

> NEW INSTRUCTIONS TK STEPHEN AND OR TIM

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

> MORE ALTERNATE LINUX NAMES TK STEPHEN OR TIM

```sh
cat - | sudo tee /etc/yum.repos.d/mdsplus.repo << EOF
[MDSplus]
name=MDSplus
baseurl=http://www.mdsplus.org/dist/el9/alpha/RPMS
enabled=1
gpgcheck=1
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
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MDSplus
metadata_expire=300
EOF
```

## 3. Packages

MDSplus is split into several packages so that you can install just the parts you need. [View the full list here](/install/packages.md). You may add or remove packages as needed.

## 5. Install MDSplus

> MORE INFO TK STEPHEN AND OR TIM

## 6. Update Your Installation

> MORE INFO TK STEPHEN AND OR TIM

## 7. Manually Installing MDSplus package

It is possible to manually install MDSplus RHEL packages instead of using a RHEL repository, but you must account for all the dependencies yourself. It is recommended to use one of the repositories. To download packages, use the correct link below, depending on your operating system version.

The following table shows the most recent MDSplus RHEL packages.

| Branch | Version | MDSplus Package URL |
|--------|--------|-------------|
| Alpha  | 8      | [mdsplus.org/dist/el8/alpha/](https://www.mdsplus.org/dist/el8/alpha/) |
|        | 9      | [mdsplus.org/dist/el9/alpha/](https://www.mdsplus.org/dist/el9/alpha/) |
| Stable | 8      | [mdsplus.org/dist/el8/stable/](https://www.mdsplus.org/dist/el8/stable/) |
|        | 9      | [mdsplus.org/dist/el9/stable/](https://www.mdsplus.org/dist/el9/stable) |