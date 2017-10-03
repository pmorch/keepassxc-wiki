Are you using KeePassXC from the Ubuntu store? Here are some tips to enhance your experience:

### 1. Why doesn't my theme work?

Since snaps are isolated from your system, they cannot know what theme you are currently running. This is a known issue with snaps.

### 2. How do I get my YubiKey to work?

Due to a snap's isolation and security settings you must manually enable the "raw-usb" interface in order to use your YubiKey. Issue the following command from a terminal to enable this interface: ```sudo snap connect keepassxc:raw-usb core:raw-usb```

### 3. Why can't I see anything outside my home directory?

Due to snap's isolation and security settings you cannot access any files outside your home directory. Furthermore, you cannot access any hidden files within your home directory. The only exception is mounted USB drives, but you must type in ```/media/``` into the file open dialog to see them.

### 4. Opening a URL (CTRL+U) doesn't work!

In order for the snap to communicate with the system's dbus you have to install an extra package. If you want to open URL's from within keepassxc install the snapd-xdg-open package using the following command:
```sudo apt-get install snapd-xdg-open```