---
layout: default
title: 🔥 setting up poetry&.env n .gitinoring it + Dbeaver(db client)+ vscode syncing these envConfiguration 
category: Programming
tags: [Programming]

---
recommendedReadInNextTab: this blog's Inconsistent Migration History.. post

poetry le aafai poetry.lock ra .toml file (= setup.py+ requirement.txt) banauchh. 

poetry.lock ma package version satik hunxa

pip ma jasto 'maile pip install garda latest package tanexa, tara timle project compile tyo package ko tallo version thiyo, so mero ma package dependency Conflict vayo' vanne issue nai aaudaina 

BECAUSE poetry.lock ma etti version package ho vanne lekhiyekai hunxa - tyei version ko package na vaye ma tyo package pip le garya jasto install gardaina, Suru mai rokdinchh. 

{Open [this gpt thread](https://chatgpt.com/share/6881a1a6-c008-8007-ba15-99485cd7125e) in two tabs. open using poetry template way n scratch way in two tabs side by side n observe. }

_these below screenshots are continuation while prooblem-solving one after another:_

![image](https://github.com/user-attachments/assets/4729339d-4890-4733-a2da-c5ba73da7a3e)

<img width="597" height="1419" alt="image" src="https://github.com/user-attachments/assets/537c9520-f627-46fc-8abe-de3577968167" />

<img width="562" height="580" alt="image" src="https://github.com/user-attachments/assets/b9f363a0-b3b7-40c8-9732-2b72031495f4" />

![image](https://github.com/user-attachments/assets/608e225d-d87c-41ec-ba8f-8a1d0c86894e)

after all this is fixed, then after only python manage.py makemigrations then migrate worked
![image](https://github.com/user-attachments/assets/19c90cad-b3cc-43cf-823f-250790bec9b7)

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

