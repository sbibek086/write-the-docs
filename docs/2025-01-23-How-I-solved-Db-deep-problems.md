---
layout: default
title: How I solved postgres COntainer deep problem
category: Cryptography
tags: [Cryptography]

---

This does not need a seperate post - I think. Infact most of the things below are old concepts in new bottle (for eg, most of the things are already in db post, and some in django), I hope I will merge this post tids bits into those posts.

Btw, a)postgres:15 is docker container
b)Inside this container, I have me-User as django-user out of 100 other users.
c)Under this me-User, I had earlier django_db database which was f**ked up because of inconsistent migration
and as in below screenshot, I created afresh vrigin postgres database out of 10s-other-can-be-created databases


![image](https://github.com/user-attachments/assets/c1264ea6-1c02-4793-a137-c45af072dc55)


and now hurray I got below, which is exactly according to what I have in models.py

d) Under this database, I can have 10 other tables like auth_user table etc
![image](https://github.com/user-attachments/assets/b3730a39-c4a7-4872-adbc-4ef1366941d4)
