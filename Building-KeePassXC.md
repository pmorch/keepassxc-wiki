# Building KeePassXC manually

First, make sure you have your build environment set up correctly (see guide for [Linux](Set-up-Build-Environment-on-Linux), [OS X](Set-up-Build-Environment-on-OS-X) and [Windows](Set-up-Build-Environment-on-Windows)).

## On Linux
Download the sources from [keepassxc.org](https://keepassxc.org/download) and unpack them:
```
tar xf keepassxc-*-src.tar.xz
```
or pull them directly from Git:
```
git clone git@github.com:keepassxreboot/keepassxc.git
```
Now change into the source directory and run the following commands:
```
mkdir build
cd build
cmake -DWITH_XC_AUTOTYPE=ON -DWITH_XC_HTTP=ON -DCMAKE_BUILD_TYPE=Release ..
make -j8
sudo make install
```

## On OS X
Download and unpack the source code as described in the section [On Linux](#on-linux), change into the source code directory and run:
```
mkdir build
cd build
cmake -DCMAKE_OSX_ARCHITECTURES=x86_64 -DWITH_CXX11=OFF -DWITH_XC_AUTOTYPE=ON -DWITH_XC_HTTP=ON -DCMAKE_BUILD_TYPE=Release ..
make -j8 package
```

## On Windows
In an Msys terminal, download and unpack the source code as described in the section [On Linux](#on-linux), change into the source code directory and run:

```
mkdir build
cd build
cmake -G"MSYS Makefiles" -DWITH_XC_AUTOTYPE=ON -DWITH_XC_HTTP=ON -DCMAKE_BUILD_TYPE=Release ..
make -j8 package
```