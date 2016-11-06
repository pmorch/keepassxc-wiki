### Setup build environment
Please follow either the [Linux](Building-Environment-on-Linux), [MacOS](Building-Environment-on-MacOS), or [Windows](Building-Environment-on-Windows) guides to setup your environment.

### Prerequisites
Obtain the following packages prior to beginning the coverage process: **gcov, lcov**

### Build Process

1. Make a build directory for cmake and enter it
2. cmake -DCMAKE_BUILD_TYPE=Coverage -DWITH_COVERAGE=ON -DWITH_TESTS=ON -DWITH_GUI_TESTS=ON ..
3. make -j4
4. make kp_coverage
5. Open up ./coverage/index.html to view the coverage report
