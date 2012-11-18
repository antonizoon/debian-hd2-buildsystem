# Debian Linux on HD2 Buildsystem

This file outlines the Debian buildsystem in this git repository from top to bottom, so you can make your own system for HD2. 

More info about the build can be found in the `BUILD_INFO.md` file in this git repository, or at the [Original thread on XDA](http://forum.xda-developers.com/showthread.php?t=1729130).

## Quick Build

These steps will create a Debian Unstable E17 system.

If you want to add more packages, add their names to the `packages` file. If you want to mess with options, edit the `options.conf` file. If you want to have some files placed into the image, put them in the `rootfs-overlay`.

Run these steps in Debian/Ubuntu to make a Linux filesystem image:

		# Become Root
		sudo su
		# Install dependencies
		apt-get install binfmt-support qemu-arm-static debootstrap
		# Build a filesystem image
		`./createrootfs -r && ./createrootfs -p`
		
You will get a `.rootfs.ext4` file. Just move this image to the `sd-startup` folder, and copy the whole folder to your HD2's sdcard. After that, set your bootloader to boot using this directory, and you will get Linux on HD2!

More detailed information about this buildsystem can be found in the `docs` folder of this repository.

### Kernel Sources

The kernel sources are in a seperate file found in the links below or in this (link needed) git repository.

[Please refer to this htc-linux wiki page for compiling](http://htc-linux.org/wiki/index.php?title=QuickDeveloperStartGuide#Kernel). Use htcleo-gnu_defconfig (it's in arch/arm/configs/ directory). 

## Features:

* It's full Debian GNU/Linux - 15901141666 packages to `apt-get`!
* Touchscreen, UI works perfectly fine
* Wifi works perfectly fine too
* Sound kinda works (playback is too fast for me, please test)

## Important To-Do:

* Phone functionality & suspend/resume (all of this should be supported! sadly, fso-deviced in Debian repositories is currently broken)
* Landscape mode (easy)
* Hardware buttons (easy)
* Bluetooth (at least partial support should be easy)
* ??? to be continued

## Wish-list (the less important stuff):

* Switch to armhf for performance gains (should be easy)
* At least partial hardware acceleration (should be possible thanks to xf86-video-msm driver)
* Bully someone into cooking newer kernel (2.6.32 is old)
* If the above doesn't work, backport brcmfmac wifi driver to current kernel
* Compass, GPS, camera, multitouch (aka the stuff not many really care about)
* Have an option for NativeSD support
* ??? to be continued

## Various technical info

* Kernel based on `linux_on_wince_htc` from gitorious with some modifications:
  - applied USB host patch by liiochen
  - applied patch from tytung kernel that enables ALSA driver to be compiled as module (without that it wouldn't work at all)
  - custom defconfig
* Rootfs size is 1GB. Filesystem is ext4 (to avoid data corruption).
* Window manager is E17, it's optimized for phones, very beautiful, and very impressive overall. Network manager is Wicd.
* Also installed: Xterm, SSH server.
* Default username is `htcleo`. Default password for this account is `htcleo`. Default root password is...`htcleo`.
* As it is Debian Unstable, anything can break at any time and not much can be done about it. I also recommend using `aptitude` over `apt-get` (it is better at solving dependency problems).
