
![Homepage:](https://github.com/zhuyaliang/images/blob/master/000.png)
![Choose Images:](https://github.com/zhuyaliang/images/blob/master/001.png)
![Add User:](https://github.com/zhuyaliang/images/blob/master/002.png)
![choose lang:](https://github.com/zhuyaliang/images/blob/master/008.png)
![view login:](https://github.com/zhuyaliang/images/blob/master/009.png)
![Group set:](https://github.com/zhuyaliang/images/blob/master/006.png)
![Group add:](https://github.com/zhuyaliang/images/blob/master/007.png)
# Explain

Rewrite an interface similar to user management tools in gnome-system-tools and gnome-control-center, displayed in the control center.
```
/etc/mate-user-admin/nuconfig 
```
Default configuration for new users

## Interface reference

https://askubuntu.com/questions/66718/how-to-manage-users-and-groups

http://ubuntuhandbook.org/index.php/2014/05/install-users-groups-management-tool-ubuntu1404/

http://linuxbsdos.com/2012/04/03/creating-and-managing-user-accounts-in-a-gnome-3-or-ubuntu-desktop/

## Code reference

http://ftp.gnome.org/pub/GNOME/sources/gnome-system-tools/
https://github.com/GNOME/gnome-control-center/

Now there are accountservice DBUS services, which provide many user management related functions, and code can be implemented in DBUS.

## Compile

```
meson build -Dprefix=/usr
ninja -C build
sudo ninja -C build install
```

## Create deb package on Ubuntu MATE 22.04 LTS

Note: you have to build and install deb-package of *group-service* first, then run below commands.

```
sudo apt-get update
sudo apt-get install dpkg-dev debhelper-compat meson cmake pkg-config libgtk-3-dev libpwquality-dev libaccountsservice-dev libmate-desktop-dev

dpkg-buildpackage -uc -us
sudo apt-get install ../user-admin*.deb
```
