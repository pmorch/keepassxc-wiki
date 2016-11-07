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

### Fix the QT5 Environment

Copy the following line inside a text file and name it `fix_mac.sh`
```shell
#!/bin/bash

# Canonical path to qt5 directory
QT5_DIR="/usr/local/Cellar/qt5/5.7.0"

# Change qt5 framework ids
for framework in $(find "$QT5_DIR/lib" -regex ".*/\(Qt[a-zA-Z]*\)\.framework/Versions/5/\1"); do
    echo "$framework"
    install_name_tool -id "$framework" "$framework"
done
```

Open a terminal and execute the following command *(insert your User password when asked)*
```
chmod +x ./fix_mac.sh
sudo ./fix_mac.sh
```


### Update you Environment regularly

Open a Terminal:

```
brew update && brew upgrade
```
