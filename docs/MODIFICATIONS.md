# Linux HD2 Modifications

Most of these are not actually used in the system, but are pulled from the ubuntu-leo wikipage.

## Prebuilt kernel and modules ##

How to install prebuilt kernel and modules: [[Leo/UpdateKernel]]

## Compiling own kernel binaries ##

How to roll your own kernel and modules: [[QuickDeveloperStartGuide#Kernel]] NOTE: use `htcleo_defconfig` . it is designed for use with non-android (GNU/Linux) user space !

Available kernel sources: [[Leo#Kernel]] Use `htc-msm-2.6.32` branch kernel only! With the `evo` kernel you will run into problems with touchscreen, backlight, networking etc.

NOTE: If you ever start a new kernel/configuration from scratch and run into a problem with only root being able to use networking: turn off the android paranoid networking kernel configuration!!! 

## Kernel 

Several kernel source trees are available for the HTC HD2.
You must download or compile kernel image (zImage) and place it as explained at [[Rootfs/Userfriendly]].
In order to use kernel modules, you must download or compile them as well and install them as explained in the [[Leo/UpdateKernel]] page.

NOTE: It is possible to use USB Host mode in order to attach extra devices. This works like a charm. It is mandatory to use the `htc-msm-2.6.32` kernel with `htcleo_defconfig` . See [[Msm_Usb_Host]] for further information!

NOTE: A big kernel level problem is the lack of sound. Most of the kernels we use as a base for our ports are designed for Google Android. Android doesn't use the standard Linux sound System ALSA. An ALSA wrapper for the HD2 DSP kernel system must be written. If you want to contribute in this see [[Contact]].
If you think you totally need sound now you can use the usb host functionality of the HD2 in order to attach an USB sound device! The htc-msm-2.6.32 allows this.

### Prebuilt kernel and modules ###

How to install prebuilt kernel and modules: [[Leo/UpdateKernel]]

### Compiling own kernel binaries ###

How to roll your own kernel and modules: [[QuickDeveloperStartGuide#Kernel]] NOTE: use htcleo_defconfig . it is designed for use with non-android (GNU/Linux) user space !

Available kernel sources: [[Leo#Kernel]] Use `htc-msm-2.6.32` branch kernel only! With the "evo" kernel you will run into problems with touchscreen, backlight, networking etc.

NOTE: If you ever start a new kernel/configuration from scratch and run into a problem with only root being able to use networking: turn off the android paranoid networking kernel configuration!!!

## oem-config ##

''only interesting when using prebuilt image!''
Ubuntu uses a program called `oem-config` to add a user account, set languages and do other tasks. When using a prebuilt image instead of rootstock, it is necessary to start it the first time you boot your image. Else you cannot login.

### using oem-config ###

oem-config is only executed when the file ''/var/lib/oem-config/run'' exists. So do a

    touch /var/lib/oem-config/run

note: oem-config will not give you an on-screen keyboard which makes it impossible to use it when you only have the touchscreen as input device. This should either be fixed upstream ([Ubuntu](https://launchpad.net/onboard Launchpad) bugtracking system) or locally either a workaround TODO: find out how to add onboard in oem-config / what configuration is in charge for that.