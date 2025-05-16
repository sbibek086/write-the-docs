---
layout: default
title: Perfect GitCommit 
category: Software Development
---

While cross collaborating thru github, commit that we do should have:

-implementation of code
-unit test (pytest stuffs, which I had done earlier in yilab) --related to this blog's Pytest post, I cant tell exactly how it cog fits as for now - I maynt care
-documentation update (this philosophy of docu present in code repo itself rather than seperate entity resting somewhere else makes more sense coz docus are 'peas and carrots' to code itself)
- link to an issue thread (as any code update is done so as to solve problem, or feature addition request, which originally begins from Issue in github) (and developer should bother to write whether that issue was solved n thus can be CLOSED now in main branch after merger)

![image](https://github.com/user-attachments/assets/60369497-840d-48a9-8ed3-693bf21473d2)

---
![image](https://github.com/user-attachments/assets/fe9b1201-9a25-45fa-a49c-1a262dce6909)

In py apps, this hook point is often facilitated, using the pluggy library — the same system used by pytest, Datasette, and others.
