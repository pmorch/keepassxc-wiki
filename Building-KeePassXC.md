# Required Dependencies

The following tools must exist within your PATH:

* make or ninja
* cmake (>= 3.3)
* g++ (>= 9.3) or clang++ (>= 10.0)

The following libraries are required:

* Qt 5 (>= 5.9.5): qtbase and qttools5
* botan (>= 2.11)
* zlib
* libxi, libxtst, qtx11extras (optional for auto-type on X11)
* libargon2
* readline (for cli history)
* pcsc-lite (Linux only)
* qrencode
* asciidoctor (>= 2.0)

# Build Options

KeePassXC comes with a variety of build options that can turn on/off features. Most notably, we allow you to build the application with all TCP/IP networking code disabled. Please note that we still require and link against Qt5's network library in order to use local named pipes on all operating systems. Each of these build options are supplied at the time of calling cmake. For example: ```cmake -DWITH_XC_AUTOTYPE=ON -DWITH_XC_NETWORKING=OFF -DWITH_XC_KEESHARE=ON ..```

```
-DWITH_XC_AUTOTYPE=[ON|OFF] Enable/Disable Auto-Type (default: ON)
-DWITH_XC_YUBIKEY=[ON|OFF] Enable/Disable YubiKey HMAC-SHA1 authentication support (default: OFF)
-DWITH_XC_BROWSER=[ON|OFF] Enable/Disable KeePassXC-Browser extension support (default: OFF)
-DWITH_XC_NETWORKING=[ON|OFF] Enable/Disable Networking support (e.g., favicon downloading) (default: OFF)
-DWITH_XC_SSHAGENT=[ON|OFF] Enable/Disable SSHAgent support (default: OFF)
-DWITH_XC_KEESHARE=[ON|OFF] Enable/Disable KeeShare group synchronization extension (default: OFF)
-DWITH_XC_ALL=[ON|OFF] Enable/Disable compiling all plugins above (default: OFF)

-DWITH_XC_UPDATECHECK=[ON|OFF] Enable/Disable automatic updating checking (requires WITH_XC_NETWORKING) (default: ON)

-DWITH_TESTS=[ON|OFF] Enable/Disable building of unit tests (default: ON)
-DWITH_GUI_TESTS=[ON|OFF] Enable/Disable building of GUI tests (default: OFF)
-DWITH_DEV_BUILD=[ON|OFF] Enable/Disable deprecated method warnings (default: OFF)
-DWITH_ASAN=[ON|OFF] Enable/Disable address sanitizer checks (Linux / macOS only) (default: OFF)
-DWITH_COVERAGE=[ON|OFF] Enable/Disable coverage tests (GCC only) (default: OFF)
-DWITH_APP_BUNDLE=[ON|OFF] Enable Application Bundle for macOS (default: ON)

-DKEEPASSXC_BUILD_TYPE=[Snapshot|PreRelease|Release] Set the build type to show/hide stability warnings (default: "Snapshot")
-DKEEPASSXC_DIST_TYPE=[Snap|AppImage|Other] Specify the distribution method (default: "Other")
-DOVERRIDE_VERSION=[X.X.X] Specify a version number when building. Used with snapshot builds (default: "")
-DGIT_HEAD_OVERRIDE=[XXXXXXX] Specify the 7 digit git commit ref for this build. Used with distribution builds (default: "")
```

# Building Manually

## 1. Setup your build environment

Use the following guides to setup your build environment:
* [Linux (Ubuntu/Fedora/RHEL/CentOS/Arch)](Set-up-Build-Environment-on-Linux)
* [MacOS 10.15+](Set-up-Build-Environment-on-OS-X)
* [Windows 10/11](Set-up-Build-Environment-on-Windows).

## 2. Building
### Linux
Download the sources from [keepassxc.org](https://keepassxc.org/download) and unpack them:
```
tar xf keepassxc-*-src.tar.xz
```
or pull them directly from Git (note: default branch is ```develop```):
```
git clone https://github.com/keepassxreboot/keepassxc.git
```
Now change into the source directory and run the following commands. If you would like to run tests after building, add ```-DWITH_TESTS=ON -DWITH_GUI_TESTS=ON``` before the ..
```
mkdir build
cd build
cmake -DWITH_XC_ALL=ON -DCMAKE_BUILD_TYPE=Release ..
make -j8
make DESTDIR=~/.local install
```
This will build the KeePassXC binaries and install them to `~/.local`. You can of course specify any other installation directory or omit `DESTDIR` completely, in which case it will install to `/usr` (use `sudo` for that).

If you don't want to install KeePassXC at all, you can also run it directly from the build directory:
```
./src/keepassxc
```

#### Notes:
If you are experiencing issues with icons not showing up in the KeePassXC user interface, you may want to set the data directory during compilation manually with the following CMake parameter:

- `-DCMAKE_INSTALL_DATADIR="$HOME/.local/share"`

or

- `-DCMAKE_INSTALL_DATADIR="/usr/share"`

### macOS
Download and unpack the source code as described in the [Linux](#linux) section, change into the source code directory and run:
```
mkdir build
cd build
cmake -DCMAKE_OSX_ARCHITECTURES=x86_64 \
  -DCMAKE_BUILD_TYPE=Release \
  -DWITH_XC_ALL=ON ..
make -j8 package
```
#### Notes:
If you installed via Homebrew, you should be able to compile KeePassXC this way, but if CMake fails to find your Qt installation, you can specify it manually by adding the following parameter:

- `-DCMAKE_PREFIX_PATH=/usr/local/opt/qt/lib/cmake`

(or whatever your Qt installation path is)

### Windows
In a _MSYS2 MinGW_ terminal (*not* _MSYS2 MSYS_ which is the default), download and unpack the source code as described in the [Linux](#linux) section, change into the source code directory and run:

```
mkdir build
cd build
cmake -G"MSYS Makefiles" -DWITH_XC_ALL=ON -DCMAKE_BUILD_TYPE=Release ..
make -j8 package
```

## 3. Running tests
If you compiled KeePassXC with the CMake flags `-DWITH_TESTS=ON` and `-DWITH_GUI_TESTS=ON`, you can run our unit test suite with:
```
make test
```

_Note: the importcsv test requires a UTF-8 environment to run successfully._

# Building using the release-tool
Starting with version 2.1.1, KeePassXC ships with a `release-tool` that automates building release packages from a specified release tag (the `--version parameter`). To see a help listing for the command, download and unpack the source code as described in the [Linux](#linux) section, change into the source directory and run
```
./release-tool help
```
The `release-tool` has three subcommands. You can get help for each by running
```
./release-tool help <COMMAND>
```
Sub commands are:
## build
```
$ ./release-tool help build
KeePassXC Release Preparation Helper
Copyright (C) 2017 KeePassXC Team <https://keepassxc.org/>

Usage: release-tool build [options]

Build and package binary release from sources

Options:
  -v, --version           Release version number or name (required)
  -a, --app-name          Application name (default: 'KeePassXC')
  -s, --source-dir        Source directory (default: '.')
  -o, --output-dir        Output directory where to build the release
                          (default: 'release')
  -t, --tag-name          Release tag to check out (defaults to version number)
  -b, --build             Build sources after exporting release
  -d, --docker-image      Use the specified Docker image to compile the application.
                          The image must have all required build dependencies installed.
                          This option has no effect if --build is not set.
      --container-name    Docker container name (default: 'keepassxc-build-container')
                          The container must not exist already
  -c, --cmake-options     Additional CMake options for compiling the sources
      --compiler          Compiler to use (default: 'g++')
  -m, --make-options      Make options for compiling sources (default: '-j8')
  -i, --install-prefix    Install prefix (default: '/usr/local')
  -p, --plugins           Space-separated list of plugins to build
                          (default: autotype)
  -n, --no-source-tarball Don't build source tarball
  -h, --help              Show this help
```
## merge (only useful for KeePassXC maintainers)
```
$ ./release-tool help merge
KeePassXC Release Preparation Helper
Copyright (C) 2017 KeePassXC Team <https://keepassxc.org/>

Usage: release-tool merge [options]

Merge release branch into main branch and create release tags

Options:
  -v, --version        Release version number or name (required)
  -a, --app-name       Application name (default: 'KeePassXC')
  -s, --source-dir     Source directory (default: '.')
  -g, --gpg-key        GPG key used to sign the merge commit and release tag,
                       leave empty to let Git choose your default key
                       (default: '')
  -r, --release-branch Source release branch to merge from (default: 'release/VERSION')
      --target-branch  Target branch to merge to (default: 'master')
  -t, --tag-name       Override release tag name (defaults to version number)
  -h, --help           Show this help
```
## sign (only useful for KeePassXC maintainers)
```
$ ./release-tool help sign
KeePassXC Release Preparation Helper
Copyright (C) 2017 KeePassXC Team <https://keepassxc.org/>

Usage: release-tool sign [options]

Sign previously compiled release packages

Options:
  -f, --files       Files to sign (required)
  -g, --gpg-key     GPG key used to sign the files (default: 'CFB4C2166397D0D2')
  -h, --help        Show this help
```

If you are not a KeePassXC maintainer, the only interesting command for you is `release-tool build`. This will automate the compilation and packaging steps described [above](#building-keepassxc-manually) and also perform a few more packaging steps such as exporting a source tarball and building an [AppImage](http://appimage.org/) on Linux.

When not specified otherwise, it will create a directory called `release` containing the build directory, a source tarball and the packaged binary bundles. On Linux, there will also be a directory `release-bin` inside the `release` directory, containing stripped versions of all the compiled binaries without additional dependencies.

# Building inside a Docker container
The `release-tool` also allows you to build KeePassXC inside a Docker container on Linux. This is important when building a cross-platform `AppImage`. To pull the needed Docker image, run
```
docker pull keepassxc/keepassxc-ci
```
This will pull the latest Docker image from the Docker hub registry. You can then start the build process with
```
./release-tool build -v VERSION --appimage -d keepassxc/keepassxc-ci
```
**Important:** rebuild the image regularly with `--no-cache` to ensure it has the latest security updates!