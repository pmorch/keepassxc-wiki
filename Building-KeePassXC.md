# Required Dependencies

The following tools must exist within your PATH:

* make
* cmake (>= 3.1)
* g++ (>= 4.7) or clang++ (>= 3.0)

The following libraries are required:

* Qt 5 (>= 5.2): qtbase and qttools5
* libgcrypt (>= 1.7)
* argon2
* libsodium
* libcurl
* zlib

The follow libraries are optional:
* libxi, libxtst, qtx11extras (for auto-type on X11)
* libyubikey, libykpers-1

# Building Manually

## 1. Setup your build environment

Use the following guides to setup your build environment:
* [Linux (Ubuntu/Fedora/RHEL/CentOS/Arch)](Set-up-Build-Environment-on-Linux)
* [OS X 5.10+](Set-up-Build-Environment-on-OS-X)
* [Windows 7/10](Set-up-Build-Environment-on-Windows).

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
Now change into the source directory and run the following commands:
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
In an Msys terminal, download and unpack the source code as described in the [Linux](#linux) section, change into the source code directory and run:

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
The `release-tool` also allows you to build KeePassXC inside a Docker container on Linux. This is important when building a cross-platform `AppImage` to ensure the used library versions are not too new. To build the needed Docker image, run
```
docker build --no-cache -t keepassxc/ubuntu:14.04 .
```
inside the source directory. This will build a Docker image with the name `keepassxc/ubuntu:14.04` from the `Dockerfile` provided inside the directory. You can then start the build process with
```
./release-tool build -v VERSION -d keepassxc/ubuntu:14.04
```
**Important:** rebuild the image regularly with `--no-cache` to ensure it has the latest security updates!