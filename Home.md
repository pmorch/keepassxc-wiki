Welcome to the KeePassXC Wiki!

KeePassXC (*KeePass Cross-platform Community Edition*) is a cross platform community-driven port of the Windows application “KeePass Password Safe”.

## About
KeePassXC is a fork of [KeePassX](https://www.keepassx.org/) that [aims to incorporate stalled pull requests, features, and bug fixes that have never made it into the main KeePassX repository](https://github.com/keepassxreboot/keepassx/issues/43).


## Additional features compared to KeePassX
- Autotype on all three major platforms (Linux, Windows, OS X)
- Stand-alone password generator
- Password strength meter
- Use website's favicons as entry icons
- Merging of databases
- Automatic reload when the database changed on disk
- KeePassHTTP support for use with [PassIFox](https://addons.mozilla.org/en-us/firefox/addon/passifox/) in Mozilla Firefox and [chromeIPass](https://chrome.google.com/webstore/detail/chromeipass/ompiailgknfdndiefoaoiligalphfdae) in Google Chrome or Chromium.

For a full list of features and changes, read the [CHANGELOG](https://github.com/keepassxreboot/keepassxc/blob/master/CHANGELOG) document.

### Note about KeePassHTTP
KeePassHTTP is not a highly secure protocol and has certain flaws, which allow an attacker to decrypt your passwords when they manage to intercept communication between a KeePassHTTP server and PassIFox/chromeIPass over a network connection (see [here](https://github.com/pfn/keepasshttp/issues/258) and [here](https://github.com/keepassxreboot/keepassxc/issues/147)). KeePassXC therefore strictly limits communication between itself and the browser plugin to your local computer. As long as your computer is not compromised, your passwords are fairly safe that way, but still use it at your own risk!