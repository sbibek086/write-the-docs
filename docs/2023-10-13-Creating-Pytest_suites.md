---
layout: default
title: (P)Pytest classes n main.py + ssh connecting
category: Software Development
---

A.  Some primer & loosely connected subcontext of testing-cohort aka confusion matrix before I begin:

![image](https://github.com/user-attachments/assets/0f70d191-4969-4486-b636-80bbd46b1091)

---
B.  So, today, I tried to create class.py in playwright such that another mainMightBeTest_anothername.py would call this class.py

Day before, I had been simply creating test_TestThis1Scenario.py , test_TestThisAnotherScenario2.py and simply running this .py(s) with pytest test_TestThis..py

But, doing with class.py and calling this in main.py is more structured way of doing things. (which is std-ly called Page.Object.Model in Playwright). Why it is better? because lets say we are trying to make one test-suite folder of say esewa for eg.

Then test-suite would look like below:

![image](https://user-images.githubusercontent.com/109033173/274681797-82e9bb70-54f8-4a4a-b7c5-ce88f9df8b7b.png)

So, here's what I did:

![image](https://user-images.githubusercontent.com/11883023/274701452-fdee01c0-1fab-41b7-99ff-b576691b6c76.png)

First, it would terminal as 'No test ran in xxx sec'. It turned out that I slow_mo ed to little time as 2000 ms, when I changed it to little longer at 10,000 ms, browser would open long enof for whole test to actually carry out.

Some more pytest-Codes below:
<script src="https://gist.github.com/AWScommunity/f6bfb504275e143955701118f08aa34f.js"></script>

___
C. Now, before all this POM thing, I wanted to test localhost files of ndrrma.yilab.org - ndrrma website which yilab contracted to build, so, I used to do w https way , its cmd would look like

git clone ndrrmaGitLabRemoteRepoURL AlsoGIveUserNamePasswordOfMyGitlabWhichHasBeenAccessedNdrrmaRepo 

but today, I downloaded zip and extracted- which is bullshit primitive. So, lets ssh as below: 

<img width="1057" height="290" alt="image" src="https://github.com/user-attachments/assets/ad4b80af-fc07-44ae-aa81-a788a64baf19" />

---
D. not related to this problemSolving n done on another problemSolving just to show ssh connecting my linuxHome to github

<img width="665" height="808" alt="image" src="https://github.com/user-attachments/assets/d78cfa19-d4bb-47ad-b343-0ed390cc3cd0" />

_ekchoti mero machine lai github.com ya ni ki github ko ip sanga ssh-connect garepaxi sadhai lai vayo k, tespaxi harekchoti yo sab garnuparena k (tei pani ssh key ltd. time paxi expiry huni ta xaina, check chai garna parxa), direct mero path ma git **CLONE** githubRepoURL gare vayo k_

---
E. Then,

![image](https://user-images.githubusercontent.com/11883023/274696566-8615885a-4e4d-4da5-8f2a-85cdad5f3ceb.png)

_btw, in white rectangle note, cmds listed like git clone npm .. are list of terminal cmds that I retrieved from terminal history_

with all this, also things wouldnt work. I was frustrated, asked Dipesh- FE ,and he would remind me to create and put .env as these are .gitignored

![image](https://user-images.githubusercontent.com/11883023/274704121-d518b307-c8a9-4f01-a1d1-d387b83ba761.png)
