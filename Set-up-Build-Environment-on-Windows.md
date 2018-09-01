**Note:** This is only a one-time setup guide. For actually building KeePassXC, please refer to our [build guide](Building-KeePassXC).

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
    mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib \
    mingw-w64-$(uname -m)-argon2 mingw-w64-$(uname -m)-libsodium
```

If CMake is having trouble finding your compiler, make sure you have started the `MINGW64` environment and not the `MINGW32` or the generic `MSYS` environment. You need to have `/mingw64/bin` in your path.

### Install YubiKey libraries
If you do not want/need the Yubikey plugin (-DWITH_XC_YUBIKEY=OFF), you can skip this step.

For compiling KeePassXC with YubiKey support, two libraries are needed: libyubikey and libykpers.

#### Compile libyubikey
Run these commands in order to build libyubikey:
```
wget https://developers.yubico.com/yubico-c/Releases/libyubikey-1.13.tar.gz
tar xf libyubikey-*.tar.gz
cd libyubikey-*
./configure
make -j8
make install
```

#### Download libykpers
Go back to the previous directory (`cd ..`) and run the following commands in order to install libykpers-1:

##### Windows 64-bit
```
pacman -Sy unzip
wget https://developers.yubico.com/yubikey-personalization/Releases/ykpers-1.19.0-win64.zip
unzip ykpers-1.*-win64.zip -d /mingw64/
```

##### Windows 32-bit
```
pacman -Sy unzip
wget https://developers.yubico.com/yubikey-personalization/Releases/ykpers-1.19.0-win32.zip
unzip ykpers-1.*-win32.zip -d /mingw32/
```

### Update your environment regularly

Open a MSYS2 shell:

```
pacman -Syu
```
