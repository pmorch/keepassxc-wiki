## General preparation and merging the release branch
Make sure all [closed pull requests](https://github.com/keepassxreboot/keepassxc/pulls?q=is%3Apr+is%3Aclosed) have a target version.

Postpone all remaining open issues and pull requests targeted at this version and create a new version milestone for the next release.

If not already done, create a new release branch `release/x.y.z` on which you
  - Bump the version number in `CMakeLists.txt`
  - Update the `CHANGELOG`

Merge the release branch into `master` using [`release-tool merge`](Building-KeePassXC#building-using-the-release-tool). Make sure you sign the release tag using either our GPG release key (`CFB4C2166397D0D2`) or your own trusted GPG key.

When done, merge `master` back into `develop` and push all changes as well as the new release tag.

## Building the binaries:
### Linux
If not already done, [build a Docker image](Building-KeePassXC#building-inside-a-docker-container) from the provided `Dockerfile`. Then build and package KeePassXC with `release-tool build` using the created Docker image.

When finished, build and submit the Snap Package using the provided `snapcraft.yaml` file.

### Windows
Build and package KeePassXC using `release-tool build`.

### OS X
Export the following environment variable:
```
export MACOSX_DEPLOYMENT_TARGET=10.7
```
and then build and package KeePassXC manually:
```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_ARCHITECTURES=x86_64 -DWITH_GUI_TESTS=OFF -DWITH_CXX11=OFF -DWITH_XC_AUTOTYPE=ON -DCMAKE_CXX_FLAGS="-mmacosx-version-min=10.7" ..
make package
```

## Signing release packages
Sign all generated release packages with `release-tool sign` and our KeePassXC GPG release key `CFB4C2166397D0D2` (DO NOT use your own GPG key!).

## Distribution
Before distributing any binaries, check them against virus scanners with [VirusTotal](https://www.virustotal.com/).

Then draft a new release on GitHub and copy the new `CHANGELOG` entry into the release description. Upload all binary packages together with their `*.sig` and `*.DIGEST` files as attachments to this release.

Once the release is published, update download paths and version numbers on the [downloads](https://keepassxc.org/download) page on keepassxc.org.