# GitHub Releases

Each release is published to github with the source code, installers, and zipped up `/usr/local/mdsplus` directories for each distribution we support.

See [https://github.com/MDSplus/mdsplus/releases](https://github.com/MDSplus/mdsplus/releases) and assets for your distribution.

## Source Tarballs

The source tarballs can be used to build a specific version of MDSplus from source. Be warned, the version information is not stored in the source code, but rather in the git tags, which will not be included in the source tarballs. In order to build with the correct version information, specify a version while building:

For a release tagged `alpha_release-1-2-3` you would run:
```sh
# If using build.py
./deploy/build.py --flavor=alpha --version=1.2.3

# If using CMake directly
cmake -DRELEASE_TAG=alpha_release-1-2-3 .
```

## Build Tarballs

The build tarballs are snapshots of the full `/usr/local/mdsplus/` directory that would then be included in the various installation packages (debs, rpms, etc.) below. This can be used to quickly test out a specific version, or to install multiple versions on a single system.

This is recommended for testing new versions before upgrades on production systems, or for clusters with multiple versions of MDSplus managed using modules.

To use a build tarball, extract it and then run:
```sh
export MDSPLUS_DIR=/path/to/extracted/files
source $MDSPLUS_DIR/setup.sh
```

## Package / Installer Tarballs

The package tarballs contain the installation packages for the given system (debs, rpms, etc.). These are the same as what is published to [www.mdsplus.org/dist/](www.mdsplus.org/dist/). These can be used to install a specific version system wide, or to rollback after an upgrade. 

To use a package tarball, extract it and then run:
```sh
# For Debian, Ubuntu, etc
sudo dpkg -i *.deb

# For Red Hat, Rocky, etc
sudo rpm -i *.rpm
```
