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

In addition, CLion needs

```
pacman -S mingw-w64-$(uname -m)-toolchain
```

to detect your Msys2 toolchain.

### Install the required dependencies

This command will install `qt5` `libgcrypt` and `zlib`

Open an MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 \
    mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib \
    mingw-w64-$(uname -m)-argon2 mingw-w64-$(uname -m)-libsodium \
    mingw-w64-$(uname -m)-qrencode mingw-w64-($uname -m)-quazip
```

If CMake is having trouble finding your compiler, make sure you have started the `MINGW64` environment and not the `MINGW32` or the generic `MSYS` environment. You need to have `/mingw64/bin` in your path.

### Install YubiKey libraries
If you do not want/need the Yubikey plugin (-DWITH_XC_YUBIKEY=OFF), you can skip this step.

#### Download libykpers

For compiling KeePassXC with YubiKey support, we need some extra libraries. To install them, run the following commands:

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

### Packaging Requirements
To build an installation package when running ```make package``` you need to have the WiX toolset installed. You can obtain it from https://github.com/wixtoolset/wix3/releases

Once installed you will need to add the toolset folder to your MSYS PATH environment: ```export PATH="${PATH}:/c/Program Files (x86)/WiX Toolset v3.11/bin"```

### Update your environment regularly

Open a MSYS2 shell:

```
pacman -Syu
```
