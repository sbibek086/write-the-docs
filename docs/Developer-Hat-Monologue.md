---
layout: default
title: Dev Hat Monologue
category: Developer
tags: [Developer]
---

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/0fe0724e-23fd-4e94-ab39-2e16e06fcdd1)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/91c27dcb-fee0-40bf-9455-b64fff2580d2)

Do it as religion & dont feel lazy to note (rough pen notes if hurry or fatigued) all lessons learnt, mistakes made, corrections- all when I solve some pgm challenge. This note will save me tons of time when I face similar situation challenges in future.

---
so, it doesnt always have to be npm docker pip that we install globally on computer.
it can be VivekAwesomePkgs or even ElasticSearchPkgs- why not ?
One of the whole OSS enthusiasm is also about bringing up with new elegant packages.
btw, novice download softwares, or use SaaS. CHADS just install new packages from terminal n use it in VScode. they are equivalent but latter is more efficient as its not lame GUI bounded.
I remember why Brad Traversy just install new pkgs in terminal. and his Equivalent to Windowers Start menu was just terminal with customised pow commands.
it was roughly like :

BradsAwesomePkgs run Open6TabsAtOnce or BradsAwesomePkgs start Antivirus

similar to we do:

npm install -g AwesomeNPMpkgs   or  npm start server

or  curl whatWhat whatwhat  or gweth (btw it's ethereumPackages) createWallet

or  pip(btw it's Python's) install whatwhat

hmmmmmmmmm, ok

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/5e87135a-1f6f-474c-b388-20c731c4e078)

----
So, in production aka development day yesterday morning , I had pulled from say predevelop branch, then deployed.
now today evening, predevelop branch has been lot + - by now,
then obviously, I need to 

git pull origin predevelop

today too

/*so, i wasnt aware that predevelop develop etc branch exists in my local universe as is in remote universe, which I thought to only exist. silly me} .
ANYWAY more on that lateron but 1thing for sure- when I do git status, it is showing which branch I am on, in local universe*/

So, today I do as i mentioned earlier

git pull origin predevelop

lots more packages might have been added by production devs //by today

so, we will get all warning loose like-INCORRECT PEER DEPENDENCY

WHY? because packages that i had pulled yesterday, lots packages might have been added by production devs

So dont worry- Just remove old package-lock.json , NOT package.json tho. Then do

yarn

It will freshly install packages

--
package.json - I understand why should be there because it shows packages versioning that my program is using

[WHY this package-lock.json?](https://www.geeksforgeeks.org/difference-between-package-json-and-package-lock-json-files/)

![devScreens](https://user-images.githubusercontent.com/11883023/267171117-c2518bd4-3fbd-49de-bbca-99325e2d22d6.jpeg)

---
Pains of Elastic Search & lessons (Pains & lessons arent here but scattered in suitable context in different posts)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/f8b61f14-1df5-4581-b68d-528183218778)
