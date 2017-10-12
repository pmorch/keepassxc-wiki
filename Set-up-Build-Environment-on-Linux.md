**Note:** This is only a one-time setup guide. For actually building KeePassXC, please refer to our [build guide](Building-KeePassXC).

### Install the C++ toolchain
**You can skip this step if you have a working C++ toolchain (g++, cmake and make)**

On Debian/Ubuntu:

```bash
sudo apt install build-essential cmake g++
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
sudo apt install libxi-dev libxtst-dev qtbase5-dev \
    qttools5-dev qttools5-dev-tools libgcrypt20-dev zlib1g-dev
```

On Fedora/RHEL/CentOS:

> Note: CentOS may require more up-to-date packages, provided here: https://copr.fedorainfracloud.org/coprs/bugzy/keepassxc/

```bash
sudo dnf install libXi-devel libXtst-devel qt5-qtbase-devel \
    qt5-linguist qt5-qttools libgcrypt-devel zlib-devel
```

On Arch Linux:
```bash
sudo pacman -S libxi libxtst qt5-base qt5-tools libgcrypt zlib
```

### Install the optional dependencies

These are required to build Auto-Type and Yubikey support.

On Debian/Ubuntu:

```bash
sudo apt-get install libxi-dev libxtst-dev libqt5x11extras5-dev \
    libyubikey-dev libykpers-1-dev
```

On Fedora/RHEL/CentOS:

> Note: CentOS may require more up-to-date packages, provided here: https://copr.fedorainfracloud.org/coprs/bugzy/keepassxc/

```bash
sudo dnf install libXi-devel libXtst-devel qt5-qtx11extras \
    qt5-qtx11extras-devel libyubikey-devel ykpers-devel
```

On Arch Linux:
```bash
sudo pacman -S libxi libxtst qt5-x11extras qt5-tools \
    yubico-c yubikey-personalization
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