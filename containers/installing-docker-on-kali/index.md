---
title: Installing Docker on Kali Linux
description:
icon:
weight:
author: ["gamb1t", "elreydetoda",]
edit: ["gad3r"]
---

To install Docker on Kali you need to remember that there is already a package named "docker", therefore Docker has to be installed under a different name. If you install `docker` you will not end up with the container version. The version we will be installing is named `docker.io`. All commands are the same however, so running `docker` on the command line will be the appropriate command:

```console
kali@kali:~$ sudo apt update
kali@kali:~$
kali@kali:~$ sudo apt install -y docker.io
kali@kali:~$
kali@kali:~$ sudo systemctl enable docker --now
kali@kali:~$
kali@kali:~$ docker
kali@kali:~$
```

You can now get started with using docker, with `sudo`. If you want to add yourself to the docker group to use `docker` without `sudo`, an additional step is needed:

```console
kali@kali:~$ sudo usermod -aG docker $USER
kali@kali:~$
```

The final thing is to **logout and in again**.

If you would like to use a Kali Docker image, we have a doc page for that [here](/docs/containers/using-kali-docker-images/).

##### Installing docker-ce on Kali Linux

`docker-ce` can be installed from Docker repository. One thing to bear in mind, [Kali Linux is based on Debian](/docs/policy/kali-linux-relationship-with-debian/), so we need to use [Debian's current stable version](https://www.debian.org/releases/stable/) (even though Kali Linux is a [rolling distribution](/docs/general-use/kali-branches/)). At the time of writing (Dec. 2023), its "bookworm":

```console
kali@kali:~$ echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list 
```

Import the gpg key:

```console
kali@kali:~$ curl -fsSL https://download.docker.com/linux/debian/gpg |
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Install the latest version of `docker-ce`:

```console
kali@kali:~$ sudo apt update
kali@kali:~$ sudo apt install -y docker-ce docker-ce-cli containerd.io
```

##### References

[Install Docker Engine on Debian](https://docs.docker.com/engine/install/debian/)
