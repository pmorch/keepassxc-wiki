**This changelog only lists changes made in KeePassXC against the original KeePassX.**

**Security improvements are tagged with 🔒.**

**Major improvements are tagged with ⭐️.**

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