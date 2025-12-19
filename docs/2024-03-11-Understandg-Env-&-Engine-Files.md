---
layout: default
title: 🔥 Understandg EnvFiles,& where Compiler IsSaved when Pgm,eg Py IsInstalled + Django set-up cmd +PEP-668? +Lib n Framework Diff
category: Programming
tags: [Programming]

---

<img width="1036" height="1127" alt="image" src="https://github.com/user-attachments/assets/ae085a36-7c0d-40b5-8e09-fff8cc606cb0" />

---
<img width="717" height="950" alt="image" src="https://github.com/user-attachments/assets/655b205a-d4fe-4432-a22d-060417cb600e" />

yo mathi ko image ma before compilation, k thyo, after compilation k vayo, her, tye ho runtime.

When you run a Python script, the Python interpreter is loaded, along with any necessary libraries (runtime environment), before executing the script.

db ko context ma db ma data load hunuparyo ni paila, tye data load hune samay lai loading runtime data vanxa- aru context ma ni estai estai, kunai bela config file load hunu parla.

 dherai curious cat scientist nabana, etti bujha, sakyo kura

---
SHOWING HOW DJANGO IS INSTALLED INSIDE VENV after CREATING VENV

<img width="698" height="491" alt="image" src="https://github.com/user-attachments/assets/02d7bde6-ace7-4d0a-b220-cfc7191af466" />

---
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

---
![image](https://github.com/user-attachments/assets/cf6753d7-9cda-4f14-87a0-f88dae1908cb)

so, jun sukai karyakram ko lagi stage banaye tyo BOOTSRAP vayo,
karyakram ma pani aja specific vayera manaau sarswati pooja karyakram ko lagi maile stage tayar pardai xu, tyo chai BOILERPLATE vayo. ie. Django framework euta boilerplate nai vayo

---
you can skip this below img:

<img width="447" height="597" alt="image" src="https://github.com/user-attachments/assets/535cd6d7-e166-4033-b42f-9d22681f2664" />


