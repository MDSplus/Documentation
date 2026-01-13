# Build System

> TODO: Revise/finish

## How to Build and Test
Use the command below to run the test. If your version is not built, it will build it and then it will test it.

```sh
$ python3 deploy/build.py -j --test
```

### Additional Parameters
Type `--help` to see additional parameters you can add to the `build.py`. Reproduced here for convenience.

| parameter                                   | description                                                                                                                                                                                                                                                              |
|---------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-h`, `--help`                              | show this help message and exit                                                                                                                                                                                                                                          |
| `--os OS`                                   | The OS definition to use (see below), which will reference `deploy/os/{--os}.opts` for additional parameters to this script and `deploy/os/{--os}.env` for additional environment variables. This will also change the default for --workspace to be `workspace-{--os}/` |
| `--toolchain TOOLCHAIN`                     | Path to the CMake toolchain file used for cross-compilation. This will be relative to the deploy/toolchains/ directory unless an absolute path is given.                                                                                                                 |
| `--workspace WORKSPACE`                     | The directory that will contain the default build/install directories and helper scripts, defaults to `workspace/` or `workspace-{--os}/` if --os is specified. This will be relative to the source directory unless an absolute path is given.                          |
| `-i`, `--interactive`                       | Drop into an interactive shell, allowing you to configure/build/install/test. This will attempt to clean your environment of references to $MDSPLUS_DIR if any are found.                                                                                                |
| `-j []`, `--parallel []`                    | The number of parallel files to build or tests to run, defaults to `os.cpu_count()` if no value is specified.                                                                                                                                                            |
| `--setup-vscode`                            | Configure `.vscode/settings.json` for use with the CMake and clangd extensions, and generate `.vscode/launch.json` entries for each test.                                                                                                                                |
| `--configure`, `--no-configure`             | Configures CMake in `{--workspace}/build`, enabled automatically if CMakeCache.txt is not found.                                                                                                                                                                         |
| `--build`, `--no-build`                     | Builds the project in `{--workspace}/build`.                                                                                                                                                                                                                             |
| `--clean`                                   | Cleans the project in `{--workspace}/build` before building.                                                                                                                                                                                                             |
| `--install`, `--no-install`                 | Install into `{--workspace}/install/usr/local/mdsplus`. Implied by `--package`. Sets `CMAKE_INSTALL_PREFIX`.                                                                                                                                                             |
| `--package`, `--no-package`                 | Generates packages in `{--workspace}/package`.                                                                                                                                                                                                                           |
| `--verify-packages`, `--no-verify-packages` | When used with `--package`, it validates the contents of the generated packages against `deploy/packaging/{--platform}/*`.                                                                                                                                               |
| `--test`, `--no-test`                       | Run all tests and report the results. Use `-j/--parallel` to run tests in parallel. Use -`R/--test-regex` or `--rerun-failed` to control which tests are run.                                                                                                            |
| `--valgrind [VALGRIND]`                     | Specify valgrind tools to run for supported tests. An additional iteration of each test will be added for each tool. Leave blank to use all default tools. Cannot be used with `--sanitize`. Sets `ENABLE_VALGRIND` and `VALGRIND_TOOLS.`                                |
| `--sanitize SANITIZE`                       | Configures the build to use the specified sanitizer flavor. Cannot be used with --valgrind. Sets ENABLE_SANITIZE.                                                                                                                                                        |
| `--rerun-failed`                            | Use with `--test` to run only the tests that previously failed.                                                                                                                                                                                                          |
| `-R TEST_REGEX`, `--test-regex TEST_REGEX`  | Use with `--test` to run only the tests that match this regex.                                                                                                                                                                                                           |
| `--output-junit`                            | Use with `--test` to store jUnit-style test results in `{--workspace}/mdsplus-junit.xml`.                                                                                                                                                                                |
| `--junit-suite-name JUNIT_SUITE_NAME`       | Use with `--output-junit` to set the name of the jUnit test suite. Defaults to "mdsplus" (or --os if specified).                                                                                                                                                         |
| `--distname DISTNAME`                       | Used by `--package` to determine the directory to generate repository information into, `{--workspace}/dist/{--distname}`.                                                                                                                                               |
| `--platform PLATFORM`                       | The platform type to build for. This controls how directories are named in the build folder, in preparation for packaging for a given platform type. Sets PLATFORM.                                                                                                      |
| `--arch ARCH`                               | The architecture to label packages as. This should be used in conjunction with --toolchain when cross-compiling. Will attempt to autodetect from the current architecture.                                                                                               |
| `--dockerpull`                              | Pull the latest docker image before creating the container.                                                                                                                                                                                                              |
| `--dockerimage`                             | Create a docker container with this image, and run the build inside there. Can be combined with -i/--interactive to get a shell inside the docker container.                                                                                                             |
| `--dockernetwork`                           | Create and use this docker network when creating the docker container.                                                                                                                                                                                                   |




### Additional parameters for `--os`

The following values (and aliases) for `--os` are available. The aliases after the colon on each line are simlinks (you can write one of them and it will symbolically call the value on the left). For example, if you write `ubuntu`, the workspace will be called `workspace-ubuntu-24-amd64`

```
  alpine-3.14-x86_64 : alpine
  amazonlinux-2-x86_64
  bootstrap
  debian-10-amd64 : debian-buster, debian-10
  debian-11-amd64 : debian-bulseye, debian-11
  debian-12-amd64 : debian-bookwork, debian-12, debian
  debian-12-arm64
  fc30
  fc32
  macosx
  maven
  raspberrypi
  rhel-7-x86_64 : rhel-7
  rhel-8-x86_64 : rhel-8
  rhel-9-x86_64 : rhel-9, rhel
  test-asan
  test-helgrind
  test-memcheck
  test-tsan
  test-ubsan
  ubuntu-18-amd64 : ubuntu-bionic, ubuntu-18
  ubuntu-20-amd64 : ubuntu-focal, ubuntu-20
  ubuntu-22-amd64 : ubuntu-jammy, ubuntu-22
  ubuntu-24-amd64 : ubuntu-noble, ubuntu-24, ubuntu
  ubuntu-24-arm64
  windows-x64 : windows
  windows-x86
```

The command below will drop you into an interactive terminal. This is useful for validating changes you have made and testing functionality that might not otherwise be caught in unit tests. 

```sh
$ ./deploy/build.py -i

Spawning a new shell, type `exit` to leave.

You can run `./do-<stage>.sh` to run configure, build, install, or test.
You can run `source setup.sh` to use the installation in `install/usr/local/mdsplus`.

[interactive] ~/mdsplus/workspace (alpha_release-1-2-3)
$ 
```

The command below will let you confirm that the version of mdsplus in the interactive prompt is the version you are expecting it to be. You can also run MDSplus commands to test the functionality of your build. 
```
$ mdstcl
TCL> show ver

MDSplus version: 1.2.3
----------------------
  Release:  your_release-1-2-3
  Date:     Wed Jul 17 12:00:16 AM EDT 2025
  Browse:   https://github.com/MDSplus/mdsplus/tree/your_release-1-2-3
  Download: https://github.com/MDSplus/mdsplus/releases/tag/your_release-1-2-3
```

This is another way to confirm that your interactive environment is running the version you are expecting.
```
source setup.sh
ldd $(which mdsdcl)
```


### do-build.sh
This will build your environment for you with any changes you've saved.

### do-install.sh 

This will install into this shell any changes that you've built.

### do-test.sh 
This will run all of the tests. Parallelization is not available for this command, so they will run in series. 

### do-configure.sh
This runs the configure on cmake.

By default, running `build.py`  will by default use `--configure` and `--build` (which you can skip with `--no-build` and `--no-configure`, respectively). 




## Configure VSCode

1. Install the Clangd extension (https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd) or copy+paste this `llvm-vs-code-extensions.vscode-clangd` into the VSCode search box.
2. Run this this command: 
   ```
   python3 deploy/build.py --setup-vscode
   ```

This will enable syntax hightlighting and many testing features.

This configures the clangd extension. It also configures the vscode launch targets.


### How to use VSCode Debug Targets

1. Click on the `Run and Debug` tab in VSCode (usually in the left icon bar).
2. Select the test you wish to run.
3. Run the test.