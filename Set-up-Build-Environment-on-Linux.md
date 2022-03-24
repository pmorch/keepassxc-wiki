**Note:** This is only a one-time setup guide. For actually building KeePassXC, please refer to our [build guide](Building-KeePassXC).

### Install the C++ toolchain
You can skip this step if you have a working C++ toolchain (g++, cmake and make)

On **Debian/Ubuntu**:

```bash
sudo apt install build-essential cmake g++
```

On **Fedora/RHEL/CentOS**:

```bash
sudo dnf install make automake gcc-c++ cmake 
```

On **Arch Linux**:

```bash
sudo pacman -S cmake make gcc
```
or
```bash
sudo pacman -S cmake make gcc-multilib
```

### Install the required dependencies

On **Debian/Ubuntu**:

```bash
sudo apt install qtbase5-dev qtbase5-private-dev qttools5-dev qttools5-dev-tools \
    libqt5svg5-dev libargon2-dev libminizip-dev libbotan-2-dev libqrencode-dev \
    zlib1g-dev asciidoctor libreadline-dev libpcsclite-dev libusb-1.0-0-dev \
    libxi-dev libxtst-dev  libqt5x11extras5-dev
```
**Ubuntu 18.04 and below** replace ```libargon2-dev``` with ```libargon2-0-dev```

On **Fedora/RHEL/CentOS**:

```bash
sudo dnf install qt5-qtbase-devel qt5-qtbase-private-devel qt5-linguist qt5-qttools \
    qt5-qtsvg-devel libargon2-devel qrencode-devel botan2-devel readline-devel \
    zlib-devel rubygem-asciidoctor pcsc-lite-devel libusb1-devel libXi-devel \
    libXtst-devel qt5-qtx11extras-devel minizip-compat-devel
```

**CentOS** requires more up-to-date packages, provided here: https://copr.fedorainfracloud.org/coprs/bugzy/keepassxc/

On **Arch Linux**:
```bash
sudo pacman -S qt5-base qt5-tools argon2 botan qrencode zlib asciidoctor readline \
    pcsclite libusb libxi libxtst qt5-x11extras minizip
```

### Update your environment regularly

On **Debian/Ubuntu**:

```bash
sudo apt-get update && sudo apt-get upgrade
```

On **Fedora/RHEL/CentOS**:

```bash
sudo dnf update && sudo dnf upgrade
```

On **Arch Linux**:

```bash
sudo pacman -Syyuu
```