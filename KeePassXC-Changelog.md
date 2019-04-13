**This changelog only lists changes made in KeePassXC against the original KeePassX.**

**Security improvements are tagged with 🔒.**

**Major improvements are tagged with ⭐️.**

2.4.1 (2019-04-13)
=========================
- Fix database deletion when using unsafe saves to a different file system [#2889] ⭐️
- Fix opening databases with legacy key files that contain '/' [#2872] ⭐️
- Fix opening database files from the command line [#2919]
- Fix crash when editing master key [#2836] ⭐️
- Fix multiple issues with apply button behavior [#2947]
- Fix issues on application startup (tab order, --pw-stdin, etc.) [#2830]
- Fix building without WITH_XC_KEESHARE
- Fix reference entry coloring on macOS dark mode [#2984]
- Hide window when performing entry auto-type on macOS [#2969]
- Improve UX of update checker; reduce checks to every 7 days [#2968] ⭐️
- KeeShare improvements [#2946, #2978, #2824]
- Re-enable Ctrl+C to copy password from search box [#2947]
- Add KeePassXC-Browser integration for Brave browser [#2933]
- SSH Agent: Re-Add keys on database unlock [#2982]
- SSH Agent: Only remove keys on app exit if they are removed on lock [#2985]
- CLI: Add --no-password option [#2708]
- CLI: Improve database extraction to XML [#2698]
- CLI: Don't call mandb on build [#2774]
- CLI: Add debug info [#2714]
- Improve support for Snap theming [#2832]
- Add support for building on Haiku OS [#2859]
- Ctrl+PgDn now goes to the next tab and Ctrl+PgUp to the previous
- Fix compiling on GCC 5 / Xenial [#2990]
- Add .gitrev output to tarball for third-party builds [#2970]
- Add WITH_XC_UPDATECHECK compile flag to toggle the update checker [#2968]

2.4.0 (2019-03-20)
=========================
- New Database Wizard [#1952] ⭐️
- Advanced Search [#1797] ⭐️
- Automatic update checker [#2648] ⭐️
- KeeShare database synchronization [#2109, #1992, #2738, #2742, #2746, #2739] ⭐️
- Improve favicon fetching; transition to Duck-Duck-Go [#2795, #2011, #2439] ⭐️
- Remove KeePassHttp support [#1752]
- CLI: output info to stderr for easier scripting [#2558] ⭐️
- CLI: Add --quiet option [#2507]
- CLI: Add create command [#2540]
- CLI: Add recursive listing of entries [#2345]
- CLI: Fix stdin/stdout encoding on Windows [#2425]
- SSH Agent: Support OpenSSH for Windows [#1994] ⭐️
- macOS: TouchID Quick Unlock [#1851] ⭐️
- macOS: Multiple improvements; include CLI in DMG [#2165, #2331, #2583] ⭐️
- Linux: Prevent Klipper from storing secrets in clipboard [#1969] 🔒
- Linux: Use polling based file watching for NFS [#2171]
- Linux: Enable use of browser plugin in Snap build [#2802] ⭐️
- TOTP QR Code Generator [#1167]
- High-DPI Scaling for 4k screens [#2404] ⭐️
- Make keyboard shortcuts more consistent [#2431]
- Warn user if deleting referenced entries [#1744]
- Allow toolbar to be hidden and repositioned [#1819, #2357]
- Increase max allowed database timeout to 12 hours [#2173]
- Password generator uses existing password length by default [#2318]
- Improve alert message box button labels [#2376]
- Show message when a database merge makes no changes [#2551]
- Browser Integration Enhancements [#1497, #2253, #1904, #2232, #1850, #2218, #2391, #2396, #2542, #2622, #2637, #2790]
- Overall Code Improvements [#2316, #2284, #2351, #2402, #2410, #2419, #2422, #2443, #2491, #2506, #2610, #2667, #2709, #2731]

2.3.4 (2018-08-23)
=========================

- Show all URL schemes in entry view [#1768]
- Disable merge when database is locked [#1975]
- Fix intermittent crashes with favorite icon downloads [#1980]
- Provide potential crash warning to Qt 5.5.x users [#2211]
- Disable apply button when creating new entry/group to prevent data loss [#2204]
- Multiple SSH Agent fixes [#1981, #2117]
- Multiple Browser Integration enhancements [#1993, #2003, #2055, #2116, #2159, #2174, #2185]
- Fix browser proxy application not closing properly [#2142]
- Add real names and Patreon supporters to about dialog [#2214]
- Add settings button to toolbar, Donate button, and Report a Bug button to help menu [#2214]

2.3.3 (2018-05-08)
=========================

- Fix crash when browser integration is enabled [#1923]

2.3.2 (2018-05-07)
=========================

- Enable high entropy ASLR on Windows [#1747]
- Enhance favicon fetching [#1786] ⭐️
- Fix crash on Windows due to Auto-Type [#1691]
- Fix dark tray icon changing all icons [#1680]
- Fix --pw-stdin not using getPassword function [#1686]
- Fix placeholders being resolved in notes [#1907]
- Enable auto-type start delay to be configurable [#1908]
- Browser: Fix native messaging reply size [#1719]
- Browser: Increase maximum buffer size [#1720]
- Browser: Enhance usability and functionality [#1810, #1822, #1830, #1884, #1906]
- SSH Agent: Parse aes-256-cbc/ctr keys [#1682] ⭐️
- SSH Agent: Enhance usability and functionality [#1677, #1679, #1681, #1787]

2.3.1 (2018-03-06)
=========================

- Fix unnecessary automatic upgrade to KDBX 4.0 and prevent challenge-response key being stripped [#1568] 🔒
- Abort saving and show an error message when challenge-response fails [#1659] 🔒
- Support inner stream protection on all string attributes [#1646]
- Fix favicon downloads not finishing on some websites [#1657] ⭐️
- Fix freeze due to invalid STDIN data [#1628]
- Correct issue with encrypted RSA SSH keys [#1587]
- Fix crash on macOS due to QTBUG-54832 [#1607]
- Show error message if ssh-agent communication fails [#1614]
- Fix --pw-stdin and filename parameters being ignored [#1608]
- Fix Auto-Type syntax check not allowing spaces and special characters [#1626]
- Fix reference placeholders in combination with Auto-Type [#1649]
- Fix qtbase translations not being loaded [#1611]
- Fix startup crash on Windows due to missing SVG libraries [#1662]
- Correct database tab order regression [#1610]
- Fix GCC 8 compilation error [#1612]
- Fix copying of advanced attributes on KDE [#1640]
- Fix member initialization of CategoryListWidgetDelegate [#1613]
- Fix inconsistent toolbar icon sizes and provide higher-quality icons [#1616] ⭐️
- Improve preview panel geometry [#1609]

2.3.0 (2018-02-27)
=========================

- Add support for KDBX 4.0, Argon2 and ChaCha20 [#148, #1179, #1230, #1494] ⭐️ 🔒
- Add SSH Agent feature [#1098, #1450, #1463] ⭐️
- Add preview panel with details of the selected entry [#879, #1338] ⭐️
- Add more and configurable columns to entry table and allow copying of values by double click [#1305] ⭐️
- Add KeePassXC-Browser API as a replacement for KeePassHTTP [#608] ⭐️ 🔒
- Deprecate KeePassHTTP [#1392]
- Add support for Steam one-time passwords [#1206] ⭐️
- Add support for multiple Auto-Type sequences for a single entry [#1390] ⭐️
- Adjust YubiKey HMAC-SHA1 challenge-response key generation for KDBX 4.0 [#1060] ⭐️
- Replace qHttp with cURL for website icon downloads [#1460] ⭐️ 🔒
- Remove lock file [#1231] ⭐️
- Add option to create backup file before saving [#1385] ⭐️
- Ask to save a generated password before closing the entry password generator [#1499]
- Resolve placeholders recursively [#1078]
- Add Auto-Type button to the toolbar [#1056]
- Improve window focus handling for Auto-Type dialogs [#1204, #1490]
- Auto-Type dialog and password generator can now be exited with ESC [#1252, #1412]
- Add optional dark tray icon [#1154]
- Add new "Unsafe saving" option to work around saving problems with file sync services [#1385] ⭐️
- Add IBus support to AppImage and additional image formats to Windows builds [#1534, #1537] ⭐️
- Add diceware password generator to CLI [#1406]
- Add --key-file option to CLI [#816, #824]
- Add DBus interface for opening and closing KeePassXC databases [#283]
- Add KDBX compression options to database settings [#1419]
- Discourage use of old fixed-length key files in favor of arbitrary files [#1326, #1327]
- Correct reference resolution in entry fields [#1486]
- Fix window state and recent databases not being remembered on exit [#1453]
- Correct history item generation when configuring TOTP for an entry [#1446]
- Correct multiple TOTP bugs [#1414]
- Automatic saving after every change is now a default [#279] ⭐️
- Allow creation of new entries during search [#1398]
- Correct menu issues on macOS [#1335]
- Allow compilation on OpenBSD [#1328]
- Improve entry attachments view [#1139, #1298]
- Fix auto lock for Gnome and Xfce [#910, #1249] 🔒
- Don't remember key files in file dialogs when the setting is disabled [#1188] 🔒
- Improve database merging and conflict resolution [#807, #1165]
- Fix macOS pasteboard issues [#1202]
- Improve startup times on some platforms [#1205]
- Hide the notes field by default [#1124]
- Toggle main window by clicking tray icon with the middle mouse button [#992]
- Fix custom icons not copied over when databases are merged [#1008] ⭐️
- Allow use of DEL key to delete entries [#914]
- Correct intermittent crash due to stale history items [#1527]
- Sanitize newline characters in title, username and URL fields [#1502]
- Reopen previously opened databases in correct order [#774]
- Use system's zxcvbn library if available [#701]
- Implement various i18n improvements [#690, #875, #1436]

2.2.4 (2017-12-14)
=========================

- Prevent database corruption when locked [#1219] ⭐️
- Fixes apply button not saving new entries [#1141] ⭐️
- Switch to Consolas font on Windows for password edit [#1229]
- Multiple fixes to AppImage deployment [#1115, #1228]
- Fixes multiple memory leaks [#1213]
- Resize message close to 16x16 pixels [#1253]

2.2.2 (2017-10-22)
=========================

- Fixed entries with empty URLs being reported to KeePassHTTP clients [#1031] ⭐️
- Fixed YubiKey detection and enabled CLI tool for AppImage binary [#1100]
- Added AppStream description [#1082]
- Improved TOTP compatibility and added new Base32 implementation [#1069]
- Fixed error handling when processing invalid cipher stream [#1099]
- Fixed double warning display when opening a database [#1037]
- Fixed unlocking databases with –pw-stdin [#1087]
- Added ability to override QT_PLUGIN_PATH environment variable for AppImages [#1079]
- Fixed transform seed not being regenerated when saving the database [#1068] 🔒
- Fixed only one YubiKey slot being polled [#1048]
- Corrected an issue with entry icons while merging [#1008]
- Corrected desktop and tray icons in Snap package [#1030]
- Fixed screen lock and Google fallback settings [#1029]

2.2.1 (2017-10-02)
=========================

- Corrected multiple snap issues [#934, #1011]
- Corrected multiple custom icon issues [#708, #719, #994]
- Corrected multiple Yubikey issues [#880]
- Fixed single instance preventing load on occasion [#997]
- Keep entry history when merging databases [#970] ⭐️
- Prevent data loss if passwords were mismatched [#1007] ⭐️
- Fixed crash after merge [#941]
- Added configurable auto-type default delay [#703]
- Unlock database dialog window comes to front [#663]
- Translation and compiling fixes

2.2.0 (2017-06-26)
=========================

- Added YubiKey 2FA integration for unlocking databases [#127] ⭐️ 🔒
- Added TOTP support [#519] ⭐️
- Added CSV import tool [#146, #490] ⭐️
- Added KeePassXC CLI tool [#254] ⭐️
- Added diceware password generator [#373] ⭐️
- Added support for entry references [#370, #378] ⭐️
- Added support for Twofish encryption [#167] ⭐️ 🔒
- Enabled DEP and ASLR for in-memory protection [#371] 🔒
- Enabled single instance mode [#510]
- Enabled portable mode [#645] ⭐️
- Enabled database lock on screensaver and session lock [#545] ⭐️ 🔒
- Redesigned welcome screen with common features and recent databases [#292] ⭐️
- Multiple updates to search behavior [#168, #213, #374, #471, #603, #654]
- Added auto-type fields {CLEARFIELD}, {SPACE}, {{}, {}} [#267, #427, #480]
- Fixed auto-type errors on Linux [#550]
- Prompt user prior to executing a cmd:// URL [#235] 🔒
- Entry attributes can be protected (hidden) [#220] 🔒
- Added extended ascii to password generator [#538]
- Added new database icon to toolbar [#289]
- Added context menu entry to empty recycle bin in databases [#520]
- Added “apply” button to entry and group edit windows [#624]
- Added macOS tray icon and enabled minimize on close [#583]
- Fixed issues with unclean shutdowns [#170, #580]
- Changed keyboard shortcut to create new database to CTRL+SHIFT+N [#515]
- Compare window title to entry URLs [#556]
- Implemented inline error messages [#162]
- Ignore group expansion and other minor changes when making database “dirty” [#464]
- Updated license and copyright information on souce files [#632]
- Added contributors list to about dialog [#629]

2.1.4 (2017-04-09)
=========================

- Bumped KeePassHTTP version to 1.8.4.2
- KeePassHTTP confirmation window comes to foreground [#466]

2.1.3 (2017-03-03)
=========================

- Fix possible overflow in zxcvbn library [#363] 🔒 
- Revert HiDPI setting to avoid problems on laptop screens [#332]
- Set file meta properties in Windows executable [#330]
- Suppress error message when auto-reloading a locked database [#345]
- Improve usability of question dialog when database is already locked by a different instance [#346] ⭐️ 
- Fix compiler warnings in QHttp library [#351]
- Use unified toolbar on Mac OS X [#361] ⭐️ 
- Fix an issue on X11 where the main window would be raised instead of closed on Alt+F4 [#362]

2.1.2 (2017-02-17)
=========================

- Ask for save location when creating a new database [#302]
- Remove Libmicrohttpd dependency to clean up the code and ensure better OS X compatibility [#317, #265] ⭐️ 
- Prevent Qt from degrading Wifi network performance on certain platforms [#318] ⭐️ 
- Visually refine user interface on OS X and other platforms [#299] ⭐️ 
- Remove unusable tray icon setting on OS X [#293]
- Fix compositing glitches on Ubuntu and prevent flashing when minimizing to the tray at startup [#307]
- Fix AppImage tray icon on Ubuntu [#277, #273]
- Fix global menu disappearing after restoring KeePassXC from the tray on Ubuntu [#276]
- Fix result order in entry search [#320]
- Enable HiDPI scaling on supported platforms [#315]
- Remove empty directories from installation target [#282] 

2.1.1 (2017-02-06)
=========================

- Enabled HTTP plugin build; plugin is disabled by default and limited to localhost [#147] 🔒 
- Escape HTML in dialog boxes [#247] 🔒 
- Corrected crashes in favicon download and password generator [#233, #226]
- Increase font size of password meter [#228]
- Fixed compatibility with Qt 5.8 [#211]
- Use consistent button heights in password generator [#229]

2.1.0 (2017-01-22)
=========================

- Show unlock dialog when using autotype on a closed database [#10, #89] ⭐️ 
- Show different tray icon when database is locked [#37, #46] ⭐️ 
- Support autotype on Windows and OS X [#42, #60, #63] ⭐️ 
- Add delay feature to autotype [#76, #77] ⭐️ 
- Add password strength meter [#84, #92] ⭐️ 
- Add option for automatically locking the database when minimizing the window [#57]
- Add feature to download favicons and use them as entry icons [#30] ⭐️ 
- Automatically reload and merge database when the file changed on disk [#22, #33, #93] ⭐️ 
- Add tool for merging two databases [#22, #47, #143] ⭐️ 
- Add --pw-stdin commandline option to unlock the database by providing a password on STDIN [#54]
- Add utility script for reading the database password from KWallet [#55]
- Fix some KeePassHTTP settings not being remembered [#34, #65]
- Make search box persistent [#15, #67, #157] ⭐️ 
- Enhance search feature by scoping the search to selected group [#16, #118] ⭐️ 
- Improve interaction between search field and entry list [#131, #141] ⭐️ 
- Add stand-alone password-generator [#18, #92] ⭐️ 
- Don't require password repetition when password is visible [#27, #92]
- Add support for entry attributes in autotype sequences [#107]
- Always focus password field when opening the database unlock widget [#116, #117]
- Fix compilation errors on various platforms [#53, #126, #130]
- Restructure and improve kdbx-extract utility [#160]

[View the KeePassX v2.0.3 Changelog](https://github.com/keepassx/keepassx/blob/2.0.3/CHANGELOG)