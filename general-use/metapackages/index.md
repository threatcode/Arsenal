---
title: Kali Linux Metapackages
description:
icon:
weight: 5
author: ["gamb1t", "g0tmi1k", "daniruiz",]
---

# What are metapackages

[Metapackages](/tools/kali-meta/) are used to install many packages at one time, created as a list of dependencies on other packages. Kali Linux uses these in a few ways. One way is allowing users to decide how many packages out of the total Kali list they would like to install. Need just enough to use Linux? Want enough to conduct Pentests? Perhaps nearly every package available in Kali?

To install a metapackage, we are going to first update the system. While not mandatory, this step is highly recommended to make sure the metapackages can be installed without any unexpected side-effects. The procedure to update Kali is documented in details on the page [Updating Kali](/docs/general-use/updating-kali/), but in short, it boils down to two commands:

```console
kali@kali:~$ sudo apt update
kali@kali:~$
kali@kali:~$ sudo apt full-upgrade -y
kali@kali:~$
```

The step above might take a while, depending on how many packages need to be updated. After it's complete, installing a metapackage (`kali-linux-default` in this example) is simply a matter of running one command:

```console
kali@kali:~$ sudo apt install -y kali-linux-default
kali@kali:~$
```

Alternatively we can use `kali-tweaks` to install metapackage groups for us. We first run the following command:

```console
kali@kali:~$ kali-tweaks
```

From here we will navigate into the "Metapackages" tab. Now we just select which metapackages we want and then we cant hit "Apply" then "OK" and finally supply our password.

## System

- `kali-linux-core`: Base Kali Linux System – core items that are always included
- `kali-linux-headless`: Default install that doesn't require GUI
- `kali-linux-default`: "Default" desktop images include these tools
- `kali-linux-arm`: All tools suitable for ARM devices
- `kali-linux-nethunter`: Tools used as part of Kali NetHunter

## Desktop environments/Window managers

- `kali-desktop-core`: Any key tools required for a GUI image
- `kali-desktop-e17`: Enlightenment (WM)
- `kali-desktop-gnome`: GNOME (DE)
- `kali-desktop-i3`: i3 (WM)
- `kali-desktop-kde`: KDE (DE)
- `kali-desktop-lxde`: LXDE (WM)
- `kali-desktop-mate`: MATE (DE)
- `kali-desktop-xfce`: Xfce (WM)

## Tools

- `kali-tools-gpu`: Tools which benefit from having access to GPU hardware
- `kali-tools-hardware`: Hardware hacking tools
- `kali-tools-crypto-stego`: Tools based around Cryptography & Steganography
- `kali-tools-fuzzing`: For fuzzing protocols
- `kali-tools-802-11`: 802.11 (Commonly known as "Wi-Fi")
- `kali-tools-bluetooth`: For targeting Bluetooth devices
- `kali-tools-rfid`: Radio-Frequency IDentification tools
- `kali-tools-sdr`: Software-Defined Radio tools
- `kali-tools-voip`: Voice over IP tools
- `kali-tools-windows-resources`: Any resources which can be executed on a Windows hosts
- `kali-linux-labs`: Environments for learning and practising on

## Menu

- `kali-tools-information-gathering`: Used for Open Source Intelligence (OSINT) & information gathering
- `kali-tools-vulnerability`: Vulnerability assessments tools
- `kali-tools-web`: Designed doing web applications attacks
- `kali-tools-database`: Based around any database attacks
- `kali-tools-passwords`: Helpful for password cracking attacks – Online & offline
- `kali-tools-wireless`: All tools based around Wireless protocols – 802.11, Bluetooth, RFID & SDR
- `kali-tools-reverse-engineering`: For reverse engineering binaries
- `kali-tools-exploitation`: Commonly used for doing exploitation
- `kali-tools-social-engineering`: Aimed for doing social engineering techniques
- `kali-tools-sniffing-spoofing`: Any tools meant for sniffing & spoofing
- `kali-tools-post-exploitation`: Techniques for post exploitation stage
- `kali-tools-forensics`: Forensic tools – Live & Offline
- `kali-tools-reporting`: Reporting tools

## Others

- `kali-linux-large`: Our previous default tools for images
- `kali-linux-everything`: Every metapackage and tool listed here
- `kali-desktop-live`: Used during a live session when booted from the image
