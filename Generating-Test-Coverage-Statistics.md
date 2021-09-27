### Setup build environment
Please follow either the [Linux](Set-up-Build-Environment-on-Linux), [OS X](Set-up-Build-Environment-on-OS-X), or [Windows](Set-up-Build-Environment-on-Windows) guides to setup your environment.

### Prerequisites
With `gcc` as your compiler, install `gcovr` to generate coverage profiles:

- **Ubuntu Linux:** ```sudo apt install gcovr```
- **MSYS2:** ```pacman -Su python3-pip && pip3 install gcovr```
- **macOS:** ```brew install gcovr```

With `clang`, you need `llvm` installed:

- **Ubuntu Linux:** ```sudo apt install llvm```
- **MSYS2:** ```pacman -Su mingw-w64-x86_64-llvm```
- **macOS:** ```xcode-select —install``` (should already be done if you have `clang` installed)

### Build Process

1. Make a build directory for cmake and enter it
2. ```cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_COVERAGE=ON -DWITH_TESTS=ON -DWITH_GUI_TESTS=ON -DWITH_XC_ALL=ON ..```
3. `make -j4 && make coverage`
4. Open up **./coverage/index.html** to view the coverage report
