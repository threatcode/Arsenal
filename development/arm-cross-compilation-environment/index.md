---
title: ARM Cross-Compilation
description:
icon:
weight: 71
author: ["steev",]
---

The following guide will demonstrate how to set up an ARM cross-compilation environment in Kali Linux. This guide is the starting point for many of our contributed "Custom ARM Images" articles.

{{% notice info %}}
You'll need to have root privileges to do this procedure, or the ability to escalate your privileges with the command "sudo su".
{{% /notice %}}

### Setting Up Your Development Box

Compiling kernels and generating images usually comes at the cost of disk space. Make sure you have at least 50 GB of disk space available on your Kali development machine as well as ample RAM and CPU juice.

### Install Dependencies

Start off by installing the required dependencies for ARM cross-compilation:

```console
kali@kali:~$ sudo apt install -y git-core gnupg flex bison gperf libesd0-dev build-essential zip curl libncurses5-dev zlib1g-dev gcc-multilib g++-multilib
```

If you are running a 64-bit Kali Linux system, add i386 architecture support to your development environment as follows:

```console
kali@kali:~$ dpkg --add-architecture i386
kali@kali:~$ sudo apt update
kali@kali:~$ sudo apt install -y ia32-libs
```

### Download Linaro Toolchain

Download the Linaro cross-compiler from our Git repository:

```console
kali@kali:~$ cd ~/
kali@kali:~$ mkdir -p arm-stuff/kernel/toolchains/
kali@kali:~$ cd arm-stuff/kernel/toolchains/
kali@kali:~$ git clone git://gitlab.com/kalilinux/packages/gcc-arm-eabi-linaro-4-6-2.git
```

### Set Environment Variables

To use the Linaro cross-compiler, you will need to set the following environment variables in your session:

```console
kali@kali:~$ export ARCH=arm
kali@kali:~$ export CROSS_COMPILE=~/arm-stuff/kernel/toolchains/gcc-arm-eabi-linaro-4.6.2/bin/arm-eabi-
```

Now your ARM cross-compilation environment is complete and you can proceed with building your own ARM kernels as described in [the article on preparing a Kali Linux ARM chroot](/docs/development/kali-linux-arm-chroot/).
