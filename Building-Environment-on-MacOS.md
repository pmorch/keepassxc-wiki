### Install the building environment

Install Homebrew (it is the easiest way to install the required packages on macOS):
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install the building toolchain

This command will install Cmake

Open a Terminal

```
brew install cmake
```

### Install the required dependencies

Then install the required libraries (zlib already exists on macOS Sierra so it is not needed to install it):

Open a Terminal:

```
brew install qt5
brew install libgcrypt
brew install libmicrohttpd
```

### Update you Environment regularly

Open a Terminal:

```
brew update && brew upgrade
```
