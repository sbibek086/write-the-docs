---
layout: default
title: 🔥 Understandg EnvFiles,& where Compiler IsSaved when Pgm,eg Py IsInstalled + PEP-668? +Lib n Framework Diff
category: Programming
tags: [Programming]
---

![image](https://github.com/user-attachments/assets/50e02731-7c16-4781-8ccd-da93ce1de499)

![pyMachine](https://github.com/user-attachments/assets/597fb277-942f-4d1c-a4c7-638ff73b7eb3)


I can type below cmds on terminal after I install py
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/90b50ca3-7fc0-4a9a-848a-e2e6b2120a1c)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/9f1b228a-3e92-4ec3-89c1-88d2bdff3ded)

---
![image](https://github.com/user-attachments/assets/5ae22f6e-f02e-4703-8a00-7fb1a4d66878)

yo mathi ko image ma before compilation, k thyo, after compilation k vayo, her, tye ho runtime.

When you run a Python script, the Python interpreter is loaded, along with any necessary libraries (runtime environment), before executing the script.

db ko context ma db ma data load hunuparyo ni paila, tye data load hune samay lai loading runtime data vanxa- aru context ma ni estai estai, kunai bela config file load hunu parla.

 dherai curious cat scientist nabana, etti bujha, sakyo kura

---
---
![image](https://github.com/user-attachments/assets/95d8e0cf-24ff-4e08-85f9-ad2e7d8a12e9)

more such debian aka OS and non-debian aka non-Os package instllation conflict is taken care by PEP-668, which ensures that system-installed Python environments (like those provided by Linux package managers) are protected from accidental modification by tools like pip.

Why? -- so as to prevent conflicts or breakages when users install packages directly into system Python using pip, which can mess up OS-managed software.

What it does:
Introduces a marker file:
/usr/lib/pythonX.Y/EXTERNALLY-MANAGED
(or similar, depending on the OS and Python version)

If this file exists:

pip install into the system environment will fail unless:

The user uses a virtual environment OR

Adds --break-system-packages (to override)

Impact:
Encourages use of virtual environments (e.g., venv, virtualenv)

Protects system Python from unexpected breakage

--

![image](https://github.com/user-attachments/assets/8a3b9712-f2d1-4421-b46c-25ddf03749e4)

---
![image](https://github.com/user-attachments/assets/cf6753d7-9cda-4f14-87a0-f88dae1908cb)

so, jun sukai karyakram ko lagi stage banaye tyo BOOTSRAP vayo,
karyakram ma pani aja specific vayera manaau sarswati pooja karyakram ko lagi maile stage tayar pardai xu, tyo chai BOILERPLATE vayo. ie. Django framework euta boilerplate nai vayo
