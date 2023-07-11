# realvnc-server-aarch64-kali
RealVNC Server Install Setup for Kali ARM64/AARCH64 Raspberry Pi 4

This repository is for installing RealVNC Server ARM64 edition on Kali version 2023.x (and above) ARM64 (aarch64) for your Raspberry Pi device. Has been tested using a Pi4 with 8gb RAM.

RealVNC Server Version: 7.5.1

IMPORTANT INFO::

With the latest 2023.x Kali OS ARM64 images, the official .deb RealVNC package can now be installed relatively easily comparing to the prevoius years.  There are steps that will be needed before installing the Deb package which will be listed below.  So make sure you are running the latest Kali ARM64 image for the Raspberry PI 4 before attempting to install.

I've included the offical RealVNC Server Deb package for the Raspberry Pi in the repository for ease of use but you can download the file direct from RealVNC if you wish.  There are no speical setup scripts or altered Deb package needed anymore so this will purely be a text instructional setup.


INSTALLATION::

```**Works on Xorg session only!  Logging in using a Wayland session will not work so make sure you login to Ubuntu using Xorg and not Wayland!**```

On many Debian based distro's, tightvncserver is installed by default.  This needs to be removed before installing RealVNC Server:
```
$ sudo apt remove tightvncserver
```
Next step and VERY IMPORTANT step is to refresh apt so it knows what repositories it has access to (if you do not do this step, you will not be able to install the package 'libraspberrypi0' so don't skip this step):

```
$ sudo apt update
```
Then you can now clone this GIT repo and install the DEB package with this 'apt' command:
```
$ git clone
$ cd realvnc-server-aarch64-kali
$ sudo apt -f install ./VNC-Server-7.5.1-Linux-ARM64.deb
```

This will install the required dependencies aswell without having to do manually if we would have used dpkg.  
Note:  There will be a 'warning note' at the end of the installation as apt is complaining about a non sandboxed install - this is informational and can be ignored.

Now enable and start the RealVNC service:
```
$ sudo systemctl enable --now vncserver-x11-serviced
```
No activation key is needed if using on a Raspberry Pi device. ** This is intended for Personal Use only! **
Please note - This free Raspberry Pi edition of RealVnc Server will let clients connect via TCP direct mode rather than UDP direct mode. You need an Enterprise License to connect via UDP!

And that is it!  A working RealVNC Server ARM64 bit edition running on Kali Linux ARM64 :)
