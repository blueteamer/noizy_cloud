---
title: "How to install Onion Share on Kali Linux"
date: "2021-09-22"
categories: 
  - "the-stuff"
tags: 
  - "kali"
  - "linux"
---

Just realized that Kali Linux does not come with Onion Share at its hand out of the box. How comes?

Nevermind. Let's see how to get it up and running.

## Prepare Kali

First, we need to configure snapd for the installation. This is the service required for the installation.

```bash
sudo apt update
sudo apt install -y snapd
```

After that, we need to enable the service to run on Kali.

```bash
sudo systemctl enable --now snapd apparmor
```

**Note |** The documentation of Kali Linux recommends a reboot or at least a logout to have everything run properly.

```bash
reboot
```

## Install Onion Share

Next, we're going to install the required binaries.

```bash
sudo snap install core
sudo snap install onionshare
```

![](images/2021-09-22_20h38_10-1024x753.png)

That's it. And now: Happy sharing!

## References

[\[1\] Installing snapd on Kali Linux | kali.org](https://www.kali.org/docs/tools/snap/)  
[\[2\] Install OnionShare on Debian | snapcraft.io](https://snapcraft.io/install/onionshare/debian)
