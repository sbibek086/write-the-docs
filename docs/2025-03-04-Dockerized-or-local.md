---
layout: page
title: dockerized or localway
category: Programming
tags: [Programming] 

---

I thought why not do dockerized way as I didnt want to have headache of virtual environment setpu after bitten by pip pipx confusions when my ubuntu troubles me - if you want to install it as debian os packages or application packages. You know what I'm talking about, ubuntu-ian.

So, I thought- lets minus this headache and directly do [dockerized way](https://sbibek086.github.io/write-the-docs/dockerized-django.html), but turns out- whenever I have to make minor changes, then ci/cd check it aka unit test it, then I have to docker compose down n up every time.
Moreover, to see whats happening inside say postgresql container or web container, then we need to go inside that container which is again bit of lingo headache {which would have been matter of seeing in bash section in vscode if it were done on localmachine's venv way} 

unit test are too much important as I had that feel of pytest leverage while back as QA. moreover, the GOAT himself pitches unit test etc in [here](https://simonwillison.net/2022/Jan/12/how-i-build-a-feature/#development-environment)

What to do, what not to, so I deepseeked n then got

![image](https://github.com/user-attachments/assets/9f4ff79f-1e6b-4f87-93c2-342fed8f5e4e)

OK. so hybrid approach is it what I should aim for - idk now!

