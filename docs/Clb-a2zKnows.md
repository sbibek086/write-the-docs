---
layout: default
title: clb- Restart session can mess up vars state, tc!
category: ml
tags: [ml]

---

 ![image](https://github.com/user-attachments/assets/3074ce13-c5a5-4740-9e2f-848b1505a220)

---
 whenever line goes off -> wifi off {_so buy inverter, vivek_}, 
then colab runtime is disconnected n on restart, UNFORTUNATELY colab doesnt restore local variable, code outputs (tho previous run code output is saved, n also stays when importing such files to new platform) and all previous program data (time-consuming to load dataset every time n PAIN-lot-of-time-FUL when I have to load GB data)

What I can do:

- I can save datasets n trained models on G Drive; Mount it n use it as required. 
Only runtime local variables and program data for that session are destroyed.

- I can use "Connect to hosted runtime" and "Manage Sessions" to use free resources effectively.

---
to make data persistent in clb using Github or Google Drive,
I can get access to full SSH terminal from Colab instance using Clouderizer. From there, I can check in my code changes to git repo as many times I wish. however, I havent tried it but this solution is available.

---
DO(NT)s:
- DONT TOUCH PROJECTS w GBs and GBs of input data.
- never open clb file in two tab, no matter how hard to scroll top-to-bottom-to-bottom, to keep track bottom and top of codebase, coz clb is confused, 'well u opened me in another tab too, i wont auto-save'
- never mount google drive unnecessarily- (earlier i was forced to coz i didnt know to download from K's VM to clb VM, but now I know it), mounting forces clb to say, again, rerun my cells
- if I sleep my laptop, then on next-wake-up-laptop-session, VM hasnt sleep UNLESS it says, 'compute disconnected'- which means I have to rerun all the way from top. And VM cloud compute hasnt slept means I dont have to rerun from top cell (yes all the way from apt-get etc etc)
- VM keeps notifying in small rectangular bottom, 'Do you want to change runtime to standard type? do you want to change runtype to standard type'- does this mean standard runtime would be cheaper ,and now I am being charged every hr 0.8$- if so, holy****, i should learn to change it to std runtime - bookmarked that fast-disappearing notification btw

---
![image](https://github.com/user-attachments/assets/4992edb5-6a74-4ee6-80c0-4f68775a692a)



