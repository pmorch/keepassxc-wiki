## How to prepare a new release

-  Make sure all closed bugs and features have a target version
-  Postpone all open issues and PR targeted at this version
-  Close the version Github Project
-  Create a new version milestone / Github Project
-  Bump version in `CMakeLists.txt`
-  Update `CHANGELOG`
-  Update translations (run `share/translations/update.sh`)
-  Remove translations that don't meet the 80% criteria from Transifex
-  Build Mac OS X bundle
  - Boot Mac OS X 10.7 and follow instructions in INSTALL
    - `cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_ARCHITECTURES=x86_64 -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_GUI_TESTS=ON -DWITH_CXX11=OFF`
    - `make package`
    - `make test`
 - Build Window bundle
  - Boot Windows 7 and follow instructions in INSTALL
    - `cmake -G"MSYS Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_GUI_TESTS=ON -DCMAKE_PREFIX_PATH=/opt/windows_32`
    - `make package`
    - `make test`
- Check binaries against virus scanners with [VirusTotal](https://www.virustotal.com/)
- Create a `tag` for the git repository signed with a Release Key
   - `git tag -s $VERSION`
- Create source tarball
   - `git archive --prefix keepassx-$VERSION/ -o keepassx-$VERSION.tar.gz $VERSION`
- Sign all release files:

    ```
for file in KeePassX-$VERSION.dmg keepassx-$VERSION.tar.gz KeePassX-$VERSION.zip; do gpg --armor --sign --detach-sign -u release@keepassxc.org --output $file.sig $file; done
```

    ```
sha256sum KeePassX-$VERSION.dmg keepassx-$VERSION.tar.gz KeePassX-$VERSION.zip >> KeePassXC-$VERSION.DIGESTS; 
sha512sum KeePassX-$VERSION.dmg keepassx-$VERSION.tar.gz KeePassX-$VERSION.zip >> KeePassXC-$VERSION.DIGESTS; 
gpg --armor --sign --clearsign -u release@keepassxc.org --output KeePassXC-$VERSION.DIGESTS KeePassXC-$VERSION.DIGESTS
```

- Upload files in the Github Release
- `git push origin master $TAG`
- Update the website with Changelog and links to downloads
- Long life KeePassXC
