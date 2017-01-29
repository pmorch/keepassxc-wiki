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
pacman -S git make mingw-w64-$(uname -m)-gcc mingw-w64-$(uname -m)-binutils mingw-w64-$(uname -m)-cmake
```

### Install the required dependencies

This command will install `qt5` `libgcrypt` `zlib` and `libmicrohttpd`

Open an MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib mingw-w64-$(uname -m)-libmicrohttpd
```

Then add this line to your `/etc/profile` and restart your terminal:

```
export PATH="/mingw64/bin/:$PATH"
```

### Update you environment regularly

Open a MSYS2 shell:

```
pacman -Syyuu
```
