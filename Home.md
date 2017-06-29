Welcome to the KeePassXC Wiki!

## About
KeePassXC is a community fork of [KeePassX](https://www.keepassx.org/), a native cross-platform port of [KeePass](http://keepass.info/) Password Safe, with the goal to extend and improve it with new features and bugfixes to provide a feature-rich, fully cross-platform and modern open-source password manager.

## Additional features compared to KeePassX
- Auto-Type on all three major platforms (Linux, Windows, macOS)
- Twofish encryption
- YubiKey challenge-response support
- TOTP generation
- CSV import
- Command line interface
- DEP and ASLR hardening
- Stand-alone password and passphrase generator
- Password strength meter
- Using website favicons as entry icons
- Merging of databases
- Automatic reload when the database was changed externally
- KeePassHTTP support for use with [PassIFox](https://addons.mozilla.org/en-us/firefox/addon/passifox/) in Mozilla Firefox, [chromeIPass](https://chrome.google.com/webstore/detail/chromeipass/ompiailgknfdndiefoaoiligalphfdae) in Google Chrome or Chromium and [passafari in Safari](https://github.com/mmichaa/passafari.safariextension/).
- Many bug fixes

For a full list of features and changes, read the [CHANGELOG](https://github.com/keepassxreboot/keepassxc/blob/master/CHANGELOG) document.

### Note about KeePassHTTP
KeePassHTTP is not a highly secure protocol and has certain flaws, which allow an attacker to decrypt your passwords when they manage to intercept communication between a KeePassHTTP server and PassIFox/chromeIPass over a network connection (see [here](https://github.com/pfn/keepasshttp/issues/258) and [here](https://github.com/keepassxreboot/keepassxc/issues/147)). KeePassXC therefore strictly limits communication between itself and the browser plugin to your local computer. As long as your computer is not compromised, your passwords are fairly safe that way, but still use it at your own risk!