#### Build Dependencies

The following tools must exist within your PATH:

* make
* cmake (>= 2.8.12)
* g++ (>= 4.7) or clang++ (>= 3.0)

The following libraries are required:

* Qt 5 (>= 5.2): qtbase and qttools5
* libgcrypt (>= 1.6)
* zlib
* libmicrohttpd
* libxi, libxtst, qtx11extras (optional for auto-type on X11)

#### Prepare the Building Environment

* [Building Environment on Linux](https://github.com/keepassxreboot/keepassx/wiki/Building-Environment-on-Linux)
* [Building Environment on Windows](https://github.com/keepassxreboot/keepassx/wiki/Building-Environment-on-Windows)
* [Building Environment on MacOS](https://github.com/keepassxreboot/keepassx/wiki/Building-Environment-on-MacOS)

#### Build Steps

To compile from source, open a terminal/cmd/MSYS2 in the KeePassXR folder

```bash
mkdir build
cd build
cmake -DWITH_TESTS=OFF ..
make [-jX]
```

You will have the compiled KeePassXR binary inside the `./build/src/` directory.

To install this binary execute the following:

```bash
sudo make install
```

More detailed instructions available in the INSTALL file.
