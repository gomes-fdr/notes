---
title: "My fresh new Debian Bullseye"
date: 2021-11-13T16:56:41-03:00
slug: "fresh-new-debian-bullseye"
tags: ["Linux, Debian"]
draft: false
---

So, new debian version on the block, I decided wait a few mounths and time comes!

## Update your source list

```
deb http://deb.debian.org/debian bullseye main contrib non-free
deb-src http://deb.debian.org/debian bullseye main contrib non-free

deb http://deb.debian.org/debian-security/ bullseye-security main contrib non-free
deb-src http://deb.debian.org/debian-security/ bullseye-security main contrib non-free

deb http://deb.debian.org/debian bullseye-updates main contrib non-free
deb-src http://deb.debian.org/debian bullseye-updates main contrib non-free

```

After that just:

    sudo apt update
    sudo apt full-upgrade
    sudo apt --purge autoremove
    sudo shutdown -r now

Lets look how it is looking like:

```
       _,met$$$$$gg.          fabiano@belchior
    ,g$$$$$$$$$$$$$$$P.       ----------------
  ,g$$P"     """Y$$.".        OS: Debian GNU/Linux 11 (bullseye) x86_64
 ,$$P'              `$$$.     Host: 20BUS3GT00 ThinkPad T450
',$$P       ,ggs.     `$$b:   Kernel: 5.10.0-9-amd64
`d$$'     ,$P"'   .    $$$    Uptime: 13 mins
 $$P      d$'     ,    $$P    Packages: 1510 (dpkg)
 $$:      $$.   -    ,d$$'    Shell: bash 5.1.4
 $$;      Y$b._   _,d$P'      Resolution: 1280x720, 1920x1080
 Y$$.    `.`"Y$$$$P"'         DE: Plasma 5.20.5
 `$$b      "-.__              WM: KWin
  `Y$$                        Theme: Breeze [Plasma], Breeze [GTK2/3]
   `Y$$.                      Icons: breeze [Plasma], breeze [GTK2/3]
     `$$b.                    Terminal: konsole
       `Y$$b.                 Terminal Font: Hack 11
          `"Y$b._             CPU: Intel i5-5300U (4) @ 2.900GHz
              `"""            GPU: Intel HD Graphics 5500
                              Memory: 1556MiB / 11676MiB

```

Just enjoy my fresh new debian!
Everything just works!
