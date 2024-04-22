---
title: ODROID-U2/U3
description:
icon:
weight:
author: ["steev",]
---

The [ODROID-U2](https://www.hardkernel.com/main/products/prdt_info.php?g_code=G135341370451) is a tricky piece of hardware as console output is not a given. Ideally, when purchasing an ODROID-U2, you should also get a USB UART cable, used for serial debugging of the boot process.

{{% notice info %}}
The ODROID-U2 and ODROID-U3 hardware are based on the same basic platform, so the U2 image will work with the U3 without modification.
{{% /notice %}}

By default, the Kali Linux ODROID-U2/U3 image **does not** contains the [**kali-linux-default** metapackage](/docs/general-use/metapackages/) which is often found in Kali platforms. If you wish to install extra tools please refer to our [metapackages page](/docs/general-use/metapackages/).

{{% notice info %}}
The build script for the ODROID-U2/U3 has not been converted to the new style, so builds may fail. If you are planning to build for this board, please consider updating the script to the new way, and submitting it as a merge request.
{{% /notice %}}

## Kali on ODROID-U2/U3 - Build-Script Instructions

Kali does not provide pre-built images for download, but you can still generate one by cloning the [Kali-ARM Build-Scripts](https://gitlab.com/kalilinux/build-scripts/kali-arm) repository on GitLab, and follow the _README.md_ file's instructions. The script to use is `odroid-u.sh`.

Once the build script finishes running, you will have an "img" file in the directory where you ran the script from. At that point, the instructions are the same as if you had downloaded a pre-built image.

The easiest way to generate these images is **from within a pre-existing Kali Linux environment**.

## Kali on ODROID-U2/U3 - User Instructions

To install Kali on your ODROID-U2/U3, follow these instructions:

1. Get a fast microSD card with at least 16GB capacity. Class 10 cards are highly recommended.
2. Use the **[dd](https://manpages.debian.org/testing/coreutils/dd.1.en.html)** utility to image this file to your microSD card (same process as [making a Kali USB](/docs/usb/live-usb-install-with-windows/).

In our example, we assume the storage device is located at `/dev/sdX`. Do _not_ simply copy these value, **change this to the correct drive path**.

{{% notice info %}}
This process will wipe out your microSD card. If you choose the wrong storage device, you may wipe out your computers hard disk.
{{% /notice %}}

```console
$ xzcat kali-linux-2024.1-odroid-u-armhf.img.xz | sudo dd of=/dev/sdX bs=4M status=progres
```

This process can take a while, depending on your PC, your microSD card speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, boot up the ODROID-U2/U3 with the microSD card plugged in.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

### Troubleshooting

To troubleshoot the ODROID boot process, you will need to connect a UART serial cable to the ODROID. Once the cable is connected, you can issue the following command to connect to the console:

```console
$ screen /dev/ttySAC1 115200
```
