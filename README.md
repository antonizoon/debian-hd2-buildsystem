# Debian Linux on HTC HD2 (HTC Leo) with E17

> *[Original thread on XDA](http://forum.xda-developers.com/showthread.php?t=1729130)*

## Foreword from bardzudny

Lately I have found myself experimenting with Debian on my beloved Leo. It's very much WIP, but even right now it may be fun to play around for some. And most of the stuff that *doesn't* work, well, solutions are in the line of sight.

I won't have time to finish it anytime soon. So, partly in hope someone will join the effort, and partly to simply make sure I won't lose effects of my work in the darkest corners of my hard drive, I upload it as it is.

It's very much bare-bones Debian Unstable system. To install it, copy all three unpacked files (rootfs.ext4, zImage, initrd.gz) to "debian" directory on your SD card. Then, choose this directory in MAGLDR settings. Then boot from SD.

It boots directly into an Enlightement 17 Mobile desktop and allows you to connect to wifi and launch terminal (and install any software you want using `apt-get`/`aptitude`).

## Features:

* Touchscreen, UI works perfectly fine
* Wifi works perfectly fine too
* Sound kinda works (playback is too fast for me, please test)
* It's full Debian GNU/Linux - 15901141666 packages to `apt-get`!

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

## Important To-Do:

* Phone functionality & suspend/resume (all of this should be supported! sadly, fso-deviced in Debian repositories is currently broken)
* Landscape mode (easy)
* Hardware buttons (easy)
* Bluetooth (at least partial support should be easy)
* Have an option for NativeSD support
* ??? to be continued

## Wish-list (the less important stuff):

* Switch to armhf for performance gains (should be easy)
* At least partial hardware acceleration (should be possible thanks to xf86-video-msm driver)
* Bully someone into cooking newer kernel (2.6.32 is old)
* If the above doesn't work, backport brcmfmac wifi driver to current kernel
* Compass, GPS, camera, multitouch (aka the stuff not many really care about)
* ??? to be continued

## Help out

If you want to help me in the effort to make this port work perfectly, this git repository has all the sources you need to reconstruct my rootfs on your own. There are some files and there is a dirty bash script ("createrootfs") that does everything that has to be done. Instructions are inside of it.

There is a lot of valuable information on [htc-linux wiki](http://htc-linux.org). I'm available in this topic, on pm, and on #htc-linux freenode channel.

Big thanks to #htc-linux, Cotulla, liiochen, tytung, dcordes, many others I forgot about and will add later.

### Kernel Sources

The kernel sources are in a seperate file found in the links below or in this (link needed) git repository.

[Please refer to this htc-linux wiki page for compiling](http://htc-linux.org/wiki/index.php?title=QuickDeveloperStartGuide#Kernel). Use htcleo-gnu_defconfig (it's in arch/arm/configs/ directory). 

## Links, Files and Mirrors

### Debian Linux for HD2 with E17

MD5: 9f5a9961d8ace10d38f7ea493a12ab4a

* [Multiupload.nl {broken}](http://www.multiupload.nl/8D7ZS99UTX)
* http://depositfiles.com/files/vinahlreg
* http://www.putlocker.com/file/28C8D9BC78297F7D
* http://www.uploadboost.com/gzj2wuhrzi4q/debian_hd2_v0.1_alpha.tar.gz
* http://turbobit.net/0456ajzoskha.html
* http://freakshare.com/files/rifre0d6/debian_hd2_v0.1_alpha.tar.gz.html
* http://www.filefactory.com/file/4zinabznaplb/debian_hd2_v0.1_alpha.tar.gz
* http://oron.com/yuqqf116hopw
* http://bayfiles.com/file/eneR/zQ2A99/debian_hd2_v0.1_alpha.tar.gz

### Source Code

This is the original source code from bardzudny. However, I (antonizoon) have made a number of modifications to it, all of which can be found in this git repository. 

* http://www.multiupload.nl/N7BNQVR02K
* http://www.putlocker.com/file/066BAD34ADB41C7A
* http://www.uploadboost.com/yx2xyz7nvbth/debian_hd2_v0.1_alpha_diy.7z
* http://turbobit.net/ytv4osp0sue6.html
* http://freakshare.com/files/9mofvzu7/debian_hd2_v0.1_alpha_diy.7z.html
* http://www.filefactory.com/file/2b4v06nzyye7/debian_hd2_v0.1_alpha_diy.7z
* http://oron.com/vzwltl06p9mr
* http://bayfiles.com/file/entZ/5u1zQP/debian_hd2_v0.1_alpha_diy.7z

### Kernel Source Code

MD5: c698454af38ad7ed3dbec120eae84daa

* http://www.multiupload.nl/IWL07GL78D