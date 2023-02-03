---
title: "Upgrading Kali Linux to latest version"
date: "2021-05-14"
tags: 
  - "kali"
---

Had to re-install my Kali Linux machine lately. Usually after a fresh install you will have to update the packages to the latest versions.

<!--more-->

## Check the source list

Open a terminal and switch to a root console by typing

```bash
# Switch to root terminal 
sudo -i

# Check source list 
cat /etc/apt/sources.list 
```

Check, if you have this entry (if not, add it to the list)

```bash
deb http://http.kali.org/kali kali-rolling main non-free contrib
```

## Update Kali Linux

Now we can execute the actual update/upgrade

```bash
# Update apt packages 
apt update 

# Start update of kali 
apt full-upgrade -y
```

## Conclusion

Here we go. A fresh install of Kali Linux with the latest tools.

So long...
