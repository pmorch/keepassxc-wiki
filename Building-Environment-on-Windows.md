### Install the building environment

* Download MSYS2 64bit: http://msys2.github.io/
* Start MSYS2 shell
* Update the system packages: `pacman --needed -Sy bash pacman pacman-mirrors msys2-runtime`
* Restart MSYS2 shell
* Update all packages: `pacman -Syu` <br/>If tells you to close the shell, close and reupdate the package (until you are done)

### Install the building toolchain

Open a MSYS2 shell:

```
pacman -S git make mingw-w64-$(uname -m)-gcc mingw-w64-$(uname -m)-binutils mingw-w64-$(uname -m)-cmake
```

### Install the required dependencies

Open a MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib mingw-w64-$(uname -m)-libmicrohttpd
```