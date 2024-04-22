---
title: Kali Linux User Policy
description:
icon:
weight:
author: ["g0tmi1k",]
---

In order to execute commands at a privileged level, Kali uses two methods todo so:

- pkexec (GUI & cli)
- sudo (cli)

It is also worth bearing in mind, some tools may perform differently without super-user privileges. An example of this is [nmap](https://nmap.org/book/man-port-scanning-techniques.html). As stated on the website:

> By default, Nmap performs a SYN Scan, though it substitutes a connect scan if the user does not have proper privileges to send raw packets (requires root access on Unix).

This means:

- SYN scan (`-sS`) is the default for a root user. This is quicker as it only sends a SYN packet, but it requires special capabilities in order to perform this, requiring root.
- Connect scan (`-sT`) is the default for a non-root user. This will complete the 3-way handshake, as a result takes longer and uses more packets than a SYN scan.

If you wish to restore how Kali previous operated, you can install the following package:

```console
kali@kali:~$ sudo apt update
kali@kali:~$
kali@kali:~$ sudo apt install -y kali-grant-root
kali@kali:~$
```

- - -

This policy is since Kali Linux 2020.1. Here is our [previous root policy](/docs/policy/kali-linux-root-user-policy/).
