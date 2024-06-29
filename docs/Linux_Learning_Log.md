---
layout: default
title: linux
category: Developer
tags: [Developer]
---

Root directory path is simply (/). Everything in file system is organized under this root directory. meaning: if I access say one Linux OS machine, then its default path is /

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/5d4d6889-2762-434d-8335-7b180a702a0e)

_However, in above screenshot, my slight confusion is: I am confirmed that this screenshot is of inside- application, that means Is system configuration in another place?_

Notice striking similarity of above File Structure (starting from lib32 lib64) from above screenshot to that of below Kaggle's VM (ofcourse nobody uses windows, everybody uses Linux)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/ae84168b-8680-43ae-9f8f-9d90570148f2)

---
I must not had paid attention to kernel. otherwise how clear its to me now.
![image](https://user-images.githubusercontent.com/11883023/267250299-73389113-31e9-4af0-889c-23fad0118403.png)

kernel is middle tier which connects to hw resources. kernel doesnt always have to be terminal or bash CLI stuffs. It can be os (thanks to Linus who must have painstakingly written all those lines which lets you control w mouse). 

all those linux cmds like sudo, apt are recognized because Linus had written defined it as packages in C and assembly lang while writing Linux kernel. btw he didnt write it from scratch tho. he wrote on top of GNU framework, which was revolution against all proprietary locked Unix. [very related my next article](https://sbibek086.github.io/write-the-docs/2024-03-11-Understandg-Env-&-Engine-Files.html)

[Windows cant be said kernel but Linux is both kernel n os](https://www.youtube.com/watch?v=HbgzrKJvDRw) is both kernel and OS).

While Linux doesn't have a central registry, tools and utilities are available for managing system configuration. These include:

a) Package Managers: Tools like apt, yum, dnf, etc., often handle configuration files as part of package installation and removal.

b) Configuration Management Systems: Tools like Ansible, Puppet, Chef, and SaltStack provide ways to automate configuration management across multiple systems, enforcing desired states defined in configuration files.


Windows:
registry is centralized hierrachical database of windows os which stores config, settings etc configuration. jasto maile aaja taskbar vertical align gare vane tespachi kholda vertical nai vayera basira hunchh -ho yestai yestai vividh, yi sbae kura registry ma store hunchh.

HKLM= HKEY_LOCAL_MACHINE, is a Windows Registry tree that contains configuration data that is used by all users in Windows. This includes information about Windows services, drivers, programs that automatically run for every user, and general OS settings.---
while using remotes in aws job

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/08e2712a-ffaa-4602-b961-ec6be9ff5fcd)

