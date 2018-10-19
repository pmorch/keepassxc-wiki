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
sudo apt install qtbase5-dev qttools5-dev qttools5-dev-tools \
    libgcrypt20-dev libargon2-0-dev libqrencode-dev zlib1g-dev
```

**Ubuntu 14.04** and **16.04** require newer versions of `libgcrypt20-dev`, which can be installed from [our Ubuntu PPA](https://launchpad.net/~phoerious/+archive/ubuntu/keepassxc). To avoid clashes with the upstream `libgcrypt20-dev` package, our package is named `libgcrypt20-18-dev` and installs to `/opt/keepassxc-libs/`. You therefore need to set the following environment variables for CMake to find the required libraries:

```bash
export CMAKE_INCLUDE_PATH="/opt/keepassxc-libs/include"
export CMAKE_LIBRARY_PATH="/opt/keepassxc-libs/lib/x86_64-linux-gnu"
```

Alternatively, these can be passed as direct parameters to `cmake` later on (`-DCMAKE_INCLUDE_PATH=... -DCMAKE_LIBRARY_PATH=...`).

**Ubuntu 14.04** is also missing the required `libargon2-0-dev` package, which can be installed from the same PPA.

On **Fedora/RHEL/CentOS**:

```bash
sudo dnf install qt5-qtbase-devel qt5-linguist qt5-qttools \
    libgcrypt-devel libargon2-devel qrencode-devel zlib-devel
```

**CentOS** requires more up-to-date packages, provided here: https://copr.fedorainfracloud.org/coprs/bugzy/keepassxc/

On **Arch Linux**:
```bash
sudo pacman -S qt5-base qt5-tools libgcrypt argon2 qrencode zlib
```

### Install the optional dependencies

These are required to build Auto-Type, Yubikey and browser integration support.

On **Debian/Ubuntu**:

```bash
sudo apt install libxi-dev libxtst-dev libqt5x11extras5-dev \
    libyubikey-dev libykpers-1-dev libsodium-dev libcurl4-openssl-dev
```

For **Ubuntu 14.04**, the `libsodium-dev` package is provided through our PPA, see above.

On **Fedora/RHEL/CentOS**:

```bash
sudo dnf install libXi-devel libXtst-devel qt5-qtx11extras \
    qt5-qtx11extras-devel libyubikey-devel ykpers-devel \
    libsodium-devel libcurl-devel
```

**CentOS** requires more up-to-date packages, provided here: https://copr.fedorainfracloud.org/coprs/bugzy/keepassxc/

On **Arch Linux**:
```bash
sudo pacman -S libxi libxtst qt5-x11extras qt5-tools \
    yubico-c yubikey-personalization libsodium curl
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