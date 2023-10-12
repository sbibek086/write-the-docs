---
layout: default
title: Pytest classes and main.py + ssh cloning from gitlab to localMachine
category: Software Development
---

![image](https://user-images.githubusercontent.com/11883023/274704954-2e9853a4-ee94-487f-9830-26b436742dbc.png)

So, today, I tried to create class.py in playwright such that another mainMightBeTest_anothername.py would call this class.py

Day before, I had been simply creating test_TestThis1Scenario.py , test_TestThisAnotherScenario2.py and simply running this .py(s) with pytest test_TestThis..py

But, doing with class.py and calling this in main.py is more structured way of doing things. (which is std-ly called Page.Object.Model in Playwright). Why it is better? because lets say we are trying to make one test-suite folder of say esewa for eg.

Then test-suite would look like below:

![image](https://user-images.githubusercontent.com/109033173/274681797-82e9bb70-54f8-4a4a-b7c5-ce88f9df8b7b.png)

So, here's what I did:

![image](https://user-images.githubusercontent.com/11883023/274701452-fdee01c0-1fab-41b7-99ff-b576691b6c76.png)

First, it would terminal as 'No test ran in xxx sec'. It turned out that I slow_mo ed to little time as 2000 ms, when I changed it to little longer at 10,000 ms, browser would open long enof for whole test to actually carry out.

___

Now, before all this POM thing, I wanted to test localhost files of ndrrma.yilab.org - ndrrma website which yilab contracted to build, so, I used to do w https way , its cmd would look like

git clone ndrrmaGitLabRemoteRepoURL AlsoGIveUserNamePasswordOfMyGitlabWhichHasBeenAccessedNdrrmaRepo 

but today, I downloaded zip and extracted- which is bad practice. Why? idc but there are strong reasons why its bad practice

So, RajanG- BE dev fren advised - why not SSH clone as its more effiient than http cloning as its better than https way.

So, we did- 

![image](https://user-images.githubusercontent.com/109033173/274687718-3b0e5134-595b-4ede-b9e6-6d65b3350894.png)

Then,

![image](https://user-images.githubusercontent.com/109033173/274688099-510d0f35-9f02-4600-8ccb-3b933861e33c.png)

Then,

![image](https://user-images.githubusercontent.com/11883023/274696566-8615885a-4e4d-4da5-8f2a-85cdad5f3ceb.png)


with all this, also things wouldnt work. I was frustrated, asked Dipesh- FE ,and he would remind me to create and put .env as these are .gitignored

![image](https://user-images.githubusercontent.com/11883023/274704121-d518b307-c8a9-4f01-a1d1-d387b83ba761.png)
