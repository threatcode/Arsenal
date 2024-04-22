---
title: Raspberry Pi Zero
description:
icon:
weight:
author: ["steev",]
---

The [Raspberry Pi Zero](https://www.raspberrypi.org/products/raspberry-pi-zero/) is a single core 1GHz, with 512MB of RAM. Unlike the [Raspberry Pi Zero W](/docs/arm/raspberry-pi-zero/), the Raspberry Pi Zero has **no networking** on the board, so you will need to use a USB adapter for networking. Kali Linux fits on an external microSD card.

By default, the Kali Linux Raspberry Pi Zero image contains the [**kali-linux-default** metapackage](/docs/general-use/metapackages/) similar to most other platforms. If you wish to install extra tools please refer to our [metapackages page](/docs/general-use/metapackages/).

{{% notice info %}}
The Raspberry Pi images use [Re4son](https://twitter.com/re4sonkernel)'s kernel, which includes the drivers for external Wi-Fi cards, TFT displays, and the [nexmon](https://github.com/seemoo-lab/nexmon) firmware for the built-in wireless card on the [Raspberry Pi 3](/docs/arm/raspberry-pi-3/) and [4](/docs/arm/raspberry-pi-4/). You will not need to download it and install it, and doing so will likely be a downgrade over the current installed kernel.
{{% /notice %}}

## Kali on Raspberry Pi Zero - User Instructions

If you're unfamiliar with the details of [downloading and validating a Kali Linux image](/docs/introduction/download-official-kali-linux-images/), or for [using that image to create a bootable device](/docs/usb/live-usb-install-with-windows/), it's strongly recommended that you refer to the more detailed procedures described in the specific articles on those subjects.

To install a pre-built image of the standard build of Kali Linux on your Raspberry Pi Zero, follow these instructions:

1. Get a fast microSD card with at least 16GB capacity. Class 10 cards are highly recommended.
2. Download _and validate_ the `Kali Raspberry Pi Zero/Zero W` image from the [downloads](/get-kali/) area. The process for validating an image is described in more detail on [Downloading Kali Linux](/docs/introduction/download-official-kali-linux-images/).
3. Use the **[dd](https://manpages.debian.org/testing/coreutils/dd.1.en.html)** utility to image this file to your microSD card (same process as [making a Kali USB](/docs/usb/live-usb-install-with-windows/).

In our example, we assume the storage device is located at `/dev/sdX`. Do _not_ simply copy these value, **change this to the correct drive path**.

{{% notice info %}}
This process will wipe out your microSD card. If you choose the wrong storage device, you may wipe out your computers hard disk.
{{% /notice %}}

```console
$ xzcat kali-linux-2024.1-raspberry-pi-zero-w-armel.img.xz | sudo dd of=/dev/sdX bs=4M status=progress
```

This process can take a while, depending on your PC, your microSD card's speed, and the size of the Kali Linux image.

Once the _dd_ operation is complete, boot up the Raspberry Pi Zero with the microSD card plugged in.

You should be able to [log in to Kali](/docs/introduction/default-credentials/).

## Kali on Raspberry Pi Zero - Image Customization

If you want to customize the Kali Raspberry Pi Zero image, including changes to the [packages](/docs/general-use/metapackages/) being installed, changing the [desktop environment](/docs/general-use/switching-desktop-environments/), increasing or decreasing the image file size or generally being adventurous, check out the [Kali-ARM Build-Scripts](https://gitlab.com/kalilinux/build-scripts/kali-arm) repository on GitLab, and follow the _README.md_ file's instructions. The script to use is `raspberry-pi-zero-w.sh`.
