### Install the C++ toolchain
**You can skip this step if you have a working C++ toolchain (g++, cmake and make)**

On Debian/Ubuntu:

```bash
sudo apt-get install build-essential cmake g++
```

On Fedora/RHEL/CentOS:

```bash
sudo dnf install make automake gcc-c++ cmake 
```

On Arch Linux:

```bash
sudo pacman -S cmake make gcc
```
or
```bash
sudo pacman -S cmake make gcc-multilib
```

### Install the required dependencies

On Debian/Ubuntu:

```bash
sudo apt-get install libmicrohttpd-dev libxi-dev libxtst-dev qtbase5-dev libqt5x11extras5-dev qttools5-dev qttools5-dev-tools libgcrypt20-dev zlib1g-dev
```

On Fedora/RHEL/CentOS:

```bash
sudo dnf install libmicrohttpd-devel libXi-devel libXtst-devel qt5-qtbase-devel qt5-linguist qt5-qtx11extras qt5-qtx11extras-devel qt5-qttools libgcrypt-devel zlib-devel
```

On Arch Linux:
```bash
sudo pacman -S libmicrohttpd qt5-x11extras qt5-base qt5-tools
```

### Update your environment regularly

On Debian/Ubuntu:

```bash
sudo apt-get update && sudo apt-get upgrade
```

On Fedora/RHEL/CentOS:

```bash
sudo dnf update && sudo dnf upgrade
```

On Arch Linux

```bash
sudo pacman -Syyuu
```