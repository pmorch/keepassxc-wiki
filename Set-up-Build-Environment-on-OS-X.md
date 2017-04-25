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
brew install qt5 libgcrypt libyubikey ykpers
```

### Fix the QT5 Environment

Copy the following line inside a text file and name it `fix_mac.sh` (by @rockihack)
```shell
#!/bin/bash

# Canonical path to qt5 directory
QT="/usr/local/Cellar/qt"
if [ ! -d "$QT" ]; then
    # Alternative (old) path to qt5 directory
    QT+="5"
    if [ ! -d "$QT" ]; then
        echo "Qt/Qt5 not found!"
        exit
    fi
fi
QT5_DIR="$QT/$(ls $QT | sort -r | head -n1)"
echo $QT5_DIR

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


### Update your environment regularly

Open a Terminal:

```
brew update && brew upgrade
```
