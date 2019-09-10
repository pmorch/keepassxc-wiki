### Setup build environment
Please follow either the [Linux](Set-up-Build-Environment-on-Linux), [OS X](Set-up-Build-Environment-on-OS-X), or [Windows](Set-up-Build-Environment-on-Windows) guides to setup your environment.

### Prerequisites
Obtain the following packages prior to beginning the coverage process: **gcov** and **lcov**

**Ubuntu Linux:** ```sudo apt install gcovr lcov```

**MSYS2:** ```pacman -Su mingw-w64-x86_64-lcov python3-pip && pip3 install gcovr```

**macOS:** ```brew install gcovr lcov```

### Build Process

1. Make a build directory for cmake and enter it
2. ```cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_COVERAGE=ON -DWITH_TESTS=ON -DWITH_GUI_TESTS=ON -DWITH_XC_ALL=ON ..```
3. `make coverage -j4`
4. Open up **./coverage/index.html** to view the coverage report
