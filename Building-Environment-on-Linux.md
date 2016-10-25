### Install the building toolchain
**You can skip this step if you have a working C/C++ toolchain (gcc, g++, cmake and make)**

On Debian/Ubuntu you can install them with:

```bash
sudo apt-get install build-essential cmake
```

On Fedora/RHEL/CentOS you can install them with:

```bash
sudo dnf install make automake gcc gcc-c++ cmake 
```

### Install the required dependencies

On Debian/Ubuntu you can install them with:

```bash
sudo apt-get install libmicrohttpd-dev libxi-dev libxtst-dev qtbase5-dev libqt5x11extras5-dev qttools5-dev qttools5-dev-tools libgcrypt20-dev zlib1g-dev
```

On Fedora/RHEL/CentOS you can install them with:

```bash
sudo dnf install libmicrohttpd-devel libXi-devel libXtst-devel qt5-qtbase-devel qt5-qtx11extras qt5-qttools libgcrypt-devel zlib-devel
```

### Update you Environment regularly

On Debian/Ubuntu you can install them with:

```bash
sudo apt-get update; sudo apt-get upgrade
```

On Fedora/RHEL/CentOS you can install them with:

```bash
sudo dnf update; sudo dnf upgrade
```