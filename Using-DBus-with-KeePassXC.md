## Using D-Bus feature

* Open keepassxc database: without password and key file

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.openDatabase /path/to/database.kdbx
```

* Open keepassxc database: with password but without key file

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.openDatabase /path/to/database.kdbx passwd
```

* Open keepassxc database: with password and key file

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.openDatabase /path/to/database.kdbx passwd /path/to/key
```

*  Lock all keepassxc databases

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.lockAllDatabases
```

*  Close all keepassxc databases

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.closeAllDatabases
```
    
*  Exit keepassxc

```
qdbus org.keepassxc.KeePassXC.MainWindow /keepassxc org.keepassxc.KeePassXC.MainWindow.exit
```

## Develop

Regenerate XML file for DBus ( If MainWindow class public methods were modified )

```
cd src/gui    
qdbusxml2cpp -c MainWindowAdaptor -a MainWindowAdaptor.h:MainWindowAdaptor.cpp org.keepassxc.KeePassXC.MainWindow.xml
```

It can be useful to know how to generate the XML adapter

Generate template from sources

```
qdbuscpp2xml -M -s MainWindow.h -o org.keepassxc.KeePassXC.MainWindow.xml
```
    
Make sure interface name is org.keepassxc.KeePassXC.MainWindow

```
<interface name="org.keepassxc.KeePassXC.MainWindow">
```
