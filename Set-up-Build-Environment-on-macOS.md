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

Open a Terminal:

```
brew install qt5 argon2 botan qrencode asciidoctor readline
```

### Update your environment regularly

Open a Terminal:

```
brew update && brew upgrade
```
