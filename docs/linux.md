---
layout: default
title: 🐧
category: Developer
tags: [Developer]
---

Root directory path is simply (/). Everything in file system is organized under this root directory. meaning: if I access say one Linux OS machine, then its default path is /

![image](https://github.com/user-attachments/assets/134ff627-5c7d-4115-b7a0-803542d68f34)

above dgm is not 100% accurate as I had 5yr old understanding but is not wrong either to del.
So, understanding more to how linux adds files - yes, its kind of fractal, look below:
![image](https://github.com/user-attachments/assets/e083cfff-3e62-4dcc-98ae-a9459db66ab2)

```
Also, note:  Permissions: Since /usr/local is typically a system-wide directory,
using sudo is necessary for creating files and directories there.
Be cautious with permissions to avoid affecting system files.

System-Wide Implications: Creating a virtual environment in /usr/local makes it accessible system-wide,
BUT THIS MIGHT NOT BE ideal if you're managing project-specific dependencies.
Consider creating virtual environments in home directory unless you have specific reason for using /usr/local.
```
![image](https://github.com/user-attachments/assets/b51f03f5-4c37-42fe-82ec-daf71d24d397) 

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

HKLM= HKEY_LOCAL_MACHINE, is a Windows Registry tree that contains configuration data that is used by all users in Windows. This includes information about Windows services, drivers, programs that automatically run for every user, and general OS settings.

---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/846e352f-12b6-4726-b505-d1c6e1b6e694)

---

![linuxx(1)](https://github.com/user-attachments/assets/d1cacb64-e777-4a2d-bdb3-17032b38d291)

---
Image Ka: 
![image](https://github.com/user-attachments/assets/b4882270-5bf3-472a-baf0-18607df00e14)

then, I wanted to install vscode as I had manually downloaded vscode from it official website
instead of 
```
sudo apt update

#1.Install dependencies
sudo apt install software-properties-common apt-transport-https wget

#2.Import Microsoft GPG key:
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -

#3.Enable vscode repository
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"

#4.install vscode
sudo apt update
sudo apt install code
```
n so had missed 4th step.

I faced this-> issue while doing 4th step manually
![image](https://github.com/user-attachments/assets/988fc413-3e30-4298-adcb-eb7d19b4e7e5)

---
shortcuts for bash:
- Ctrl Alt T to bring bash aka terminal
- Ctrl Shift V to paste clipboard to terminal

![image](https://github.com/user-attachments/assets/a671fbc0-41e7-41a0-833d-4c51758b2c90)

sudo apt purge package_name_forEg_python3-pip removes package+ configFiles but remove just removes package

then after sudo apt autoremove removes any dependencies that were installed with the package but are no longer needed.  

---
![image](https://github.com/user-attachments/assets/04faecdd-b5e3-4eb1-808e-8d89918554df)


