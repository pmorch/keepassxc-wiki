**Note:** This is only a one-time setup guide. For actually building KeePassXC, please refer to our [build guide](Building-KeePassXC).

### Install the build environment

Install Homebrew (it is the easiest way to install the required packages on macOS):
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install the C++ toolchain

This command will install Cmake

Open a Terminal

```
brew install cmake
```

### Install the required dependencies

Then install the required libraries (zlib already exists on macOS Sierra so it is not needed to install it):

Open a Terminal:

```
brew install qt5 libgcrypt argon2 qrencode libsodium
```

### Install optional dependencies

These dependencies are only needed if you build with -DWITH_XC_ALL=ON or the specific option you are building:

```
brew install libyubikey ykpers
```

### Update your environment regularly

Open a Terminal:

```
brew update && brew upgrade
```
