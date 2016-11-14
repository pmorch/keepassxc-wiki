### Install the building environment

* Download MSYS2 64bit: http://msys2.github.io/
* Start MSYS2 shell
* Update the system packages: `pacman --needed -Sy bash pacman pacman-mirrors msys2-runtime`
* Restart MSYS2 shell
* Update all packages: `pacman -Syu` <br/>If tells you to close the shell, close and reupdate the package (until you are done)

### Install the building toolchain

This command will install the MinGW-W GCC compiler, Cmake and Binutils

Open a MSYS2 shell:

```
pacman -S git make mingw-w64-$(uname -m)-gcc mingw-w64-$(uname -m)-binutils mingw-w64-$(uname -m)-cmake
```

### Install the required dependencies

This command will install `qt5` `libgcrypt` `zlib` and `libmicrohttpd`

Open a MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 mingw-w64-$(uname -m)-libgcrypt mingw-w64-$(uname -m)-zlib mingw-w64-$(uname -m)-libmicrohttpd
```

### Fix the environment
[Revert this patch with the following step](https://github.com/Alexpux/MINGW-packages/blob/2627fe6cdcf43a39d66f7b869655d88e6ef934a9/mingw-w64-cmake/do-not-generate-import-library-for-executables.patch)
- Navigate to `C:\msys64\mingw64\share\cmake-3.6\Modules\Platform`  
- Locate the `Windows-GNU.cmake` file and rename it `Windows-GNU.cmake.fix`  
- Rename `Windows-GNU.cmake.orig` to `Windows-GNU.cmake`.

### Update you Environment regularly

Open a MSYS2 shell:

```
pacman -Syu
```
