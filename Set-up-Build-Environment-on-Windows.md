**Note:** This is only a one-time setup guide. For actually building KeePassXC, please refer to our [build guide](Building-KeePassXC).

## Setup Visual Studio Environment
We recommend building KeePassXC using Visual Studio to maximize feature availability. Visual Studio is free to use and dependencies are provided from trusted sources or self-built using Vcpkg.

### Install Visual Studio
1. Download and install Visual Studio Community 2022: https://visualstudio.microsoft.com/downloads/

2. At a minimum, ensure the following options are selected. We require at least Windows SDK version 10.0.22000.0. You can also import this installation configuration to auto-select these options: [vsconfig.zip](https://github.com/keepassxreboot/keepassxc/files/8228563/vsconfig.zip)

![image](https://user-images.githubusercontent.com/2809491/157791055-cf6c3ba1-b4d7-4f37-9284-d792c7e6378c.png)

3. (Optional) Instead of the entire IDE, you may install [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022) and use [VSCode](https://code.visualstudio.com/download) as an IDE.

### Install vcpkg and Dependencies
**Recommended Option:**

KeePassXC provides a pre-built dependency bundle to save time building them yourself. Simply download and unzip the pre-built dependency package to a folder of your choice. Download here: https://kpxcstorage.blob.core.windows.net/vcpkg/vcpkg-export-20220310-221613.zip

**Alternative Option:**
1. Download and install vcpkg: https://vcpkg.io/en/getting-started.html

2. From the KeePassXC source directory, navigate to `utils\vcpkg_ports`. Copy all folders within this directory to your vcpkg ports subfolder.

![image](https://user-images.githubusercontent.com/2809491/157793947-c248b8e1-e1e2-4872-8ffa-45691f1d3123.png)

2. Open a command prompt to the vcpkg directory and run the following command. This will take up to an hour to complete the build process. 

`.\vcpkg.exe install argon2 botan minizip qt5 qt5-svg qt5-tools qt5-imageformats qt5-translations readline zlib libqrencode --triplet=x64-windows`

### Install Asciidoctor
1. Download and install Ruby without devkit: https://rubyinstaller.org/downloads/

    a. Make sure to **uncheck** install MSYS2/MINGW on the final install screen.

2. Open a command prompt and run: `gem install asciidoctor`

3. In the same command prompt, test the install by running: `asciidoctor`

## Setup MSYS Environment
_Building using MSYS is deprecated, we no longer recommend this method._

### Install the build environment

* Download MSYS2 64bit: http://msys2.github.io/
* Start MSYS2 shell
* Update the system packages: `pacman --needed -Sy bash pacman pacman-mirrors msys2-runtime`
* Restart MSYS2 shell
* Update all packages: `pacman -Syu` <br/>If prompted, restart the shell and re-run this command until done

### Install the C++ toolchain

This command will install the MinGW-W GCC compiler, CMake and Binutils

Open an MSYS2 shell:

```
pacman -S git make mingw-w64-$(uname -m)-gcc mingw-w64-$(uname -m)-toolchain \
    mingw-w64-$(uname -m)-binutils mingw-w64-$(uname -m)-cmake
```

### Install the required dependencies

Open an MSYS2 shell:

```
pacman -S mingw-w64-$(uname -m)-qt5 \
    mingw-w64-$(uname -m)-libbotan mingw-w64-$(uname -m)-zlib \
    mingw-w64-$(uname -m)-argon2 mingw-w64-$(uname -m)-qrencode \
    mingw-w64-$(uname -m)-asciidoctor
```

### Packaging Requirements
To build an installation package when running ```make package``` you need to have the WiX toolset installed. You can obtain it from https://github.com/wixtoolset/wix3/releases

Once installed you will need to add the toolset folder to your MSYS PATH environment: ```export PATH="${PATH}:/c/Program Files (x86)/WiX Toolset v3.11/bin"```

### Update your environment regularly

Open a MSYS2 shell:

```
pacman -Syu
```
