# Debian Linux on HTC HD2 (with E17 Mobile)

> *[Original thread on XDA](http://forum.xda-developers.com/showthread.php?t=1729130)*

## Introduction

This is a project to create a modern, usable, and up-to-date build of Debian Linux on the HD2. It is supported by all HD2 bootloaders using the Android SD method, and loads up a full Debian Unstable system with E17 Mobile. The hope is that **Linux might be made into a truly viable mobile operating system.**

Linux on the HD2 has never really been healthy for development or compelling to use, so this project is also attempting to **create a solid, open base for developers to easily update and improve off of.** Just get the buildsystem to create a decent build.

This is based on the original work by **bardzuny** on XDA Developers. The buildsystem was heavily modified by **antonizoon** with an improved "profile" methodology.

## Files for Users

> **Note:** Default username is `htcleo`. Default password for this account is `htcleo`. Default root password is...`htcleo`. Also, `aptitude` is preferred over `apt-get` because it excels at resolving dependency issues.

Just download an image below, extract and move the folder to the HD2 SDCard, set your bootloader to use that folder, and you've got Linux on the HD2!

* Debian Unstable E17 - The original build from bardzuny. Currently unchanged from his implementation.

### Upcoming

The below images are under development.

* Ubuntu E17 - Same as Debian Unstable E17, but uses Ubuntu repositories.
* Kubuntu Active - KDE Plasma Active on the HD2! Works surprisingly well.
* Debian Unstable Hildon - Bringing the big feature of Maemo to the HD2! Hildon is the only Linux Mobile DE to have ever worked in practice, and is seen on the Nokia N900.

## Files for Developers

* Debian HD2 Buildsystem - Create your own Debian/Ubuntu build with just one command! The default profile is the Debian Unstable E17 build. To change or add things, just edit the files.

* Linux (Kernel) on HTC WinCE - Based on the original from Gitorious, with a few patches:
  - applied USB host patch by liiochen
  - applied patch from tytung kernel that enables ALSA driver to be compiled as module (without that it wouldn't work at all)
  - custom defconfig

## Features

* It's full Debian GNU/Linux - 15901141666 packages to `apt-get`!
* Touchscreen, UI works perfectly
* Wifi works perfectly
* Sound works in theory (playback for me was too fast)
* Window manager is E17, it's optimized for phones, very impressive overall. Network manager is Wicd.
* 1GB of space available (size can be changed by rebuilding in the buildsystem). Filesystem is ext4 (to avoid data corruption).
* Extra Apps: Xterm, SSH server.

## Help out

If you'd like to help make this build better, just see below to find out what needs to be done.

### Important To-Do:

* Landscape mode (easy)
* Hardware buttons (easy)
* Bluetooth (at least partial support should be easy)
* Phone functionality & suspend/resume 
	* all of this should be supported! sadly, fso-deviced in Debian repositories is currently broken, try Ubuntu

### Wish-list

* Switch to armhf for performance gains (should be easy, see Raspbian)
* At least partial hardware acceleration (should be possible thanks to xf86-video-msm driver)
* Bully someone into cooking newer kernel (2.6.32 is old)
* If the above doesn't work, backport brcmfmac wifi driver to current kernel
* Compass, GPS, camera, multitouch (aka the stuff not many really care about)
* Have an option for NativeSD support
