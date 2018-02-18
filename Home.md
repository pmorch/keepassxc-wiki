Welcome to the KeePassXC Wiki!

## About
KeePassXC is a community fork of [KeePassX](https://www.keepassx.org/), a native cross-platform port of [KeePass](http://keepass.info/) Password Safe, with the goal to extend and improve it with new features and bugfixes to provide a feature-rich, fully cross-platform and modern open-source password manager.

## Main Features
- Secure storage of passwords and other private data with AES or Twofish encryption
- Cross-platform, runs on Linux, Windows and macOS without modifications
- File format compatibility with KeePass2, KeePassX, MacPass, KeeWeb and others
- Auto-Type on all supported platforms for automagically filling in login forms
- Key file and YubiKey challenge-response support for additional security
- TOTP generation
- CSV import from other password managers (e.g., LastPass)
- Command line interface
- Stand-alone password and passphrase generator
- Password strength meter
- Custom icons for database entries and download of website favicons
- Database merge functionality
- Automatic reload when the database was changed externally
- KeePassHTTP support for use with [PassIFox](https://addons.mozilla.org/en-us/firefox/addon/passifox/) in Mozilla Firefox, [chromeIPass](https://chrome.google.com/webstore/detail/chromeipass/ompiailgknfdndiefoaoiligalphfdae) in Google Chrome or Chromium and [passafari](https://github.com/mmichaa/passafari.safariextension/) in Safari

For a full list of features and changes, read the [CHANGELOG](https://github.com/keepassxreboot/keepassxc/blob/master/CHANGELOG) document.

### Note about KeePassHTTP
KeePassHTTP is not a highly secure protocol and has certain flaws, which allow an attacker to decrypt your passwords when they manage to intercept communication between a KeePassHTTP server and PassIFox/chromeIPass over a network connection (see [here](https://github.com/pfn/keepasshttp/issues/258) and [here](https://github.com/keepassxreboot/keepassxc/issues/147)). KeePassXC therefore strictly limits communication between itself and the browser plugin to your local computer. As long as your computer is not compromised, your passwords are fairly safe that way, but still use it at your own risk!