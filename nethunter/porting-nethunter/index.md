---
title: Porting NetHunter to New Devices manually
description:
icon:
weight: 15
author: ["g0tmi1k", "yesimxev",]
---

In order to port NetHunter to a new device, it's important to understand how NetHunter is separated. NetHunter is divided by the rootfs (also known as the chroot but will be referred to here as rootfs) and the kernel. For the most part, the rootfs is not important to your Android device as it only contains Kali Linux. The kernel is integral to getting things like Bluetooth, wireless USB, and HID keyboard (etc) working.

You also need a device with an unlocked bootloader, for flashing the kernel, and you must be able to get root on the device. Root is needed so we can write applications to system, such as busybox and bootkali, and execute commands that allow us to get Kali running.

**If you are looking to port a device, it's all about the kernel. Device must be unlockable/rootable**.

## Getting Started

Let's assume that you've already followed the directions on the [main docs page](/docs/nethunter/building-nethunter/). You have all the dependencies met and you are ready to go. The first thing we want to do is build a test kernel.

## Kernel Version

If your device is older, please check to make sure your kernel version is 3.4+ and above. With the switch to kali rolling we are starting to see errors inside chroot where the kernel is not able to support loading Kali.

## Finding Kernel Sources

One of the reasons why Nexus was chosen is because all kernel sources are made available through [Google's own website](https://android.googlesource.com). Finding sources can be easy or difficult depending on the manufacturer. A good resource is usually the [XDA forums](https://forum.xda-developers.com/) as someone else has probably already built a working kernel and they must provide the sources under GPL. Most kernel development pages on XDA must provide a link to their sources.

## Making a Test Kernel

Assuming you don't have a toolchain downloaded already, you can download it by running the following commands:

For older devices that are not 64-bit, use:

```console
kali@kali:~$ git clone https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/arm/arm-eabi-4.7 toolchain
kali@kali:~$ export ARCH=arm
kali@kali:~$ export SUBARCH=arm
kali@kali:~$ export CROSS_COMPILE=`pwd`/toolchain/bin/arm-eabi-
kali@kali:~$ make your_device_codename
kali@kali:~$ make -j$(nproc)
```

For 64-bit devices, use the appropriate toolchain:

```console
kali@kali:~$ git clone https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9 -b android10-release toolchain64
kali@kali:~$ export ARCH=arm64
kali@kali:~$ export SUBARCH=arm64
kali@kali:~$ export CROSS_COMPILE=`pwd`/toolchain64/bin/aarch64-linux-android-
kali@kali:~$ make your_device_codename                         
kali@kali:~$ make -j$(nproc)
```

When ready you can build a test kernel installer. Add your device to your cloned devices repo as per the instructions, then build a zip:
You can see how the device files are added, some has modules and additional patches, some don't. Mainly, your are fine with a boot image if you don't have modules, like [in this commit](#https://gitlab.com/kalilinux/nethunter/build-scripts/kali-nethunter-devices/-/commit/3665052d125e09e8652144a03056d9c396c3fc9e)

```console
kali@kali:~$ cd nethunter-installer
kali@kali:~$ ./build.py -k -d your_device_codename --your_android_version 
```
