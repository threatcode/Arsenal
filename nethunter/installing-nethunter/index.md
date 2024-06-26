---
title: Installing NetHunter
description:
icon:
weight:
author: ["re4son",]
---

## Overview

Installing NetHunter requires the following steps:
1. [Download a pre-built image or build your own image](#1-nethunter-support-and-pre-built-images)
2. [Put your device in developer mode](#2-putting-your-device-in-developer-mode)
3. [Unlock your device](#3-5-unlocking-rooting-and-installing-a-custom-recovery-on-your-android-device)
4. [Install TWRP](#3-5-unlocking-rooting-and-installing-a-custom-recovery-on-your-android-device)
5. [Flash Magisk](#3-5-unlocking-rooting-and-installing-a-custom-recovery-on-your-android-device)
6. [Android 9 and above: Format "data" and flash Universal DM-Verity & ForceEncrypt Disabler](#6-flashing-universal-dm-verity-forceencrypt-disabler)
7. [Install NetHunter](#7-9-installing-the-nethunter-image)
8. [Android 10 and above: Update NetHunter App from the NetHunter Store](#7-9-installing-the-nethunter-image)
9. [Run the NetHunter App to finish the installation](#7-9-installing-the-nethunter-image)

&nbsp;
## 1. NetHunter support and pre-built images

You can confirm that your device and Android version is supported via our gitlab live reports:

- [List of quarterly published NetHunter images](https://nethunter.kali.org/images.html)
- [NetHunter kernel statistics](https://nethunter.kali.org/kernel-stats.html)
- [NetHunter kernel table with](https://nethunter.kali.org/kernels.html)

The NetHunter team builds and publishes images for a selected list of devices, on the [official NetHunter download page](/get-kali/).

If you devices is supported by NetHunter but not available as a pre-build image, you can easily build your own image by following the steps in our ["Building NetHunter" documentation](/docs/nethunter/building-nethunter/)

&nbsp;
## 2. Putting your device in "Developer Mode"

Before the installation begins, you must enable _Developer mode_ on your device. This is done by navigating to _Settings_ -> _About_ and tapping on the _Build number_ field 7 times until you receive the notification that developer mode has been enabled. Go back to the main settings page and you will have a new section titled _Developer options_. Tap on the new _Developer options_ section and enable both the _Advanced Reboot_ and _Android Debugging_ options.

&nbsp;
## 3. - 5. Unlocking, rooting, and installing a custom recovery on your android device

NetHunter supports over 60 different devices running Android versions from Kitkat though to Android Q.
Whilst we have standardised the NetHunter installation procedure, the steps to unlock, root, and install a custom recovery varies from device to device and even differs between Android versions.
The preferred custom recovery for NetHunter is [TWRP](https://twrp.me/Devices/).
The preferred software to root the device for NetHunter is [Magisk](https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445).
Please refer to the appropriate guide to unlock, root, and install a custom recovery on your device from your preferred internet resource, such as the [XDA Developers Forum](https://forum.xda-developers.com/)

&nbsp;
## 6. Flashing Universal DM-Verity & ForceEncrypt Disabler

**IMPORTANT NOTE** for Android 9, 10, & 11 users: Please ensure that you flash the [Universal DM-Verity, ForceEncrypt Disabler](https://forum.xda-developers.com/android/software/universal-dm-verity-forceencrypt-t3817389) and format the data partition prior to installing NetHunter.
Magisk does not support user context changes on encrypted data partitions, which leads to errors when connecting to the Kali rootfs via ssh (i.e. "Required key not available") if the data partition is encrypted.

&nbsp;
## 7. - 9. Installing the NetHunter Image

Now that your Android phone is ready, transfer the NetHunter image to it, reboot in recovery mode, and flash the zip on your phone. Once done, reboot and launch the NetHunter app to complete the setup!

**IMPORTANT NOTE** for Android 10 & 11 users: Please update the NetHunter app from the NetHunter store after flashing NetHunter. Android 10 introduced "scoped storage" restrictions which prevents NetHunter from using the storage location we traditionally used to save configuration files. We are in the process of moving the location and implementing an import/export function but updating the app after flashing NetHunter provides a workaround that allows us to continue accessing the current storage location until the new features are implemented.
