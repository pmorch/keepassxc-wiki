### Install the build environment

* Download MSYS2 64bit: http://msys2.github.io/
* Start MSYS2 shell
* Update the system packages: `pacman --needed -Sy bash pacman pacman-mirrors msys2-runtime`
* Restart MSYS2 shell
* Update all packages: `pacman -Syu` <br/>If tells you to close the shell, close and reupdate the package (until you are done)

### Install the C++ toolchain

This command will install the MinGW-W GCC compiler, CMake and Binutils

Open an MSYS2 shell:

```
pacman -S git make mingw-w64-$(uname -m)-gcc \
    mingw-w64-$(uname -m)-binutils mingw-w64-$(uname -m)-cmake
```

### Install the required dependencies

This command will install `qt5` `libgcrypt` and `zlib`

Open an MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 \
    mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib
```

If CMake is having trouble finding your compiler, add this line to your `/etc/profile` and restart your terminal:

```
export PATH="/mingw64/bin/:$PATH"
```

### Compile and install needed YubiKey libraries
For compiling KeePassXC with YubiKey support, two libraries are needed which don't come with Msys2: libyubikey and libykpers-1.

#### Download and compile libyubikey
Run these commands in order to build libyubikey:
```
wget https://developers.yubico.com/yubico-c/Releases/libyubikey-1.13.tar.gz
tar xf libyubikey-*.tar.gz
cd libyubikey-*
./configure
make -j8
make install
```

#### Download and install libykpers-1
Go back to the previous directory (`cd ..`) and run the following commands in order to build libykpers-1:
```
pacman -S libutil-linux-devel
export LIBRARY_PATH=/usr/lib

wget https://developers.yubico.com/yubikey-personalization/Releases/ykpers-1.18.0.tar.gz
tar xf ykpers-*.tar.gz
cd ykpers-*
./configure
make -j8
make install
```
`libutil-linux-devel` is a needed dependency for building a shared library (DLL). However, `libuuid` is not installed under the `/mingw64` prefix, so we need to give the compiler some hints where to find it by setting the `LIBRARY_PATH` environment variable. Note that this needs to be done before (!) executing `./configure`.

### Update your environment regularly

Open a MSYS2 shell:

```
pacman -Syyuu
```
