---
title: "How to update Kali Linux to latest version"
date: "2021-07-12"
tags: 
  - "kali"
---

In case you have installed Kali Linux using an older ISO, you can easily update all packages doing like this:

<!--more-->

```bash
# update the installed packages 
john@kali:~$ sudo apt update 
# upgrade kali linux 
john@kali:~$ sudo apt full-upgrade -y
```

As Kali Linux is continuously providing updated packages you might want to do the update every now and then. I usually do that once a week.

**Hint** | You can shorten the above statements in one line and just type:

```bash
john@kali:~$ sudo apt update && apt -y full-upgrade
```

## References

\[1\] [https://kali.org/docs/general-use/updating-kali/](https://kali.org/docs/general-use/updating-kali/) (Official Kali Linux Documentation)
