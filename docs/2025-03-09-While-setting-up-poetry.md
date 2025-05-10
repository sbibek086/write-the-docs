---
layout: default
title: 🔥 setting up poetry&.env n .gitinoring it + Dbeaver(db client)+ vscode syncing these envConfiguration 
category: Programming
tags: [Programming]

---
btw, dyk that 
![image](https://github.com/user-attachments/assets/9db2ec5d-09cf-4106-a115-403102132eb0)

---
recommendedReadInNextTab: this blog's Inconsistent Migration History.. post

_these below screenshots are continuation while prooblem-solving one after another:_

![image](https://github.com/user-attachments/assets/9823bee9-6fda-4384-9735-a57f1e5a8ee7)

![image](https://github.com/user-attachments/assets/105223de-45af-46f4-9328-cdc2463af275)

![image](https://github.com/user-attachments/assets/14731059-3338-4504-8f9f-d7c05d05ab3e)

as seen above, if I have to add any more, then I do poetry add <sthg>

![image](https://github.com/user-attachments/assets/593292f0-583b-47ec-af67-e3489b66dca0)

![image](https://github.com/user-attachments/assets/31ee5079-ff5c-4300-a9fe-f2625638d51d)

![image](https://github.com/user-attachments/assets/f611e73e-cbc2-4585-b119-19fd14985b21)

as we can see above, secret_key was put and all slash ater MEDIA_URL addressed by opening .env n putting it as below:
```
DEBUG=True
SECRET_KEY=***
ALLOWED_HOSTS=*

DATABASE_HOST=localhost
DATABASE_NAME=Agriii
DATABASE_USER=postgres
DATABASE_PASS=***
DATABASE_PORT=5432

STATIC_LOCATION=static
MEDIA_LOCATION=media
```
![image](https://github.com/user-attachments/assets/0df0faa5-8c1b-4198-bb64-2f2933cdd9a2)

---
Since migrations are applied, then I can see as below:

![image](https://github.com/user-attachments/assets/dd31f6e7-2959-42c6-977b-80b82a833775)

_appeciate it vivek! how hard was it to see it going to terminal while doing in docker._ 

This is showing tables of postgres db. 

---
![image](https://github.com/user-attachments/assets/028ab528-ab12-4afc-b02f-52649f0a769a)

---
while installing postgres locally on my machine:

![image](https://github.com/user-attachments/assets/5a2409ea-7ec8-4dda-b7a5-49c6eb08f3f3)

---
.gitignore as below so as to not put these devOps file to git:

![image](https://github.com/user-attachments/assets/08e69ff8-ee96-40ab-8b44-b491d3494850)


