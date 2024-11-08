---
layout: page
title: 🐳
category: Programming
tags: [Programming] 
---

hub.docker.com >>3.6.76. pw: 3..8 

[yo sab gareko WordpressCamp'sTut](https://www.facebook.com/mishra.aananta/videos/307497993616073)

![dockerWorkFlow](https://user-images.githubusercontent.com/11883023/209544204-48c30b20-48e6-47b5-972c-af4b98ddb45c.png)
![image](https://github.com/user-attachments/assets/c19bf5b6-ca81-4e79-ad85-3dd2e729da3c)
![image](https://github.com/user-attachments/assets/1cbe6318-c1cc-4d54-bbeb-e26aba1deb13)

```
docker run -d -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=mysite -e MYSQL_PASSWORD=password --name mysitedb -v "$PWD/database":/var/lib/mysql mysql
```

```
docker pull wordpress
docker run -d -e WORDPRESS_DB_NAME=mysite -e WORDPRESS_DB_USER=mysite -e WORDPRESS_DB_PASSWORD=password --name wordpress --link mysitedb -p 80:80 -v "$PWD/html":/var/www/html wordpress
```
IdontKnow why but while doing, mathi ko command rakhda athena tara tala ko
```
docker run -d --name wordpress --link mysitedb -p 81:80 -v "$PWD/html":/var/www/html wordpress
```
rakhda chai aathyo

Now, lets do all above w docker-compose.yml way 

![image](https://github.com/user-attachments/assets/58b33a3b-db98-4347-95aa-a7143d54a951)
![image](https://github.com/user-attachments/assets/61d23796-746d-4605-82c7-d5e9d95aaa62)

---
**Doing more Grand Project than earlier, using docker-compose**

So, docker-compose.yml is LHS-of-4th-pic-from-top and lets see how it compiles:
![image](https://github.com/user-attachments/assets/7638cc70-33ca-4b71-a380-31fcb5b8d059)

Then, how does app.py as client interacts w mysql server & also about how port expose is co-ordinated
![image](https://github.com/user-attachments/assets/ec000146-7807-4059-96ad-574013ab6822)

---
   Making docker image persistent on url -meaning I dont need to have sudo docker-compose up in my machine to come in browser, [then look here even tho I have to find another way to put sudo docker-compose up everytime ON in cloud](https://developer.okta.com/blog/2018/09/27/test-your-github-repositories-with-docker-in-five-minutes) 

---
But why is docker-compose.yml (can be said more Infrastructure as code) more seeked n practical efficient than docker way

![IaC](https://github.com/user-attachments/assets/00e53816-27cf-44e7-87a5-fea71ee8587d)

---
CI/CD aka devOps not rel to above:

![gitActions](https://user-images.githubusercontent.com/11883023/120933150-82a62080-c718-11eb-9667-0ede1aad1b33.jpg)

there can be 1000+ contributors on one project as it grows big. 
So, its practically impossible to accept every pull req. (PR) code, edit with issues , check its validity(TEST), merge it etc etc. as written by Merged Code, Test, Build, Deploy in above pic. Every incoming PR to your open source repo is called EVENTS and things you do in its response (Mer., T, B, D is act of Continuous Integration/ Continuous Deployment = CI/CD) is called ACTIONS, which can be automated. Hence, the name Actions with CI/CD pipeline, altho ci cd is superset of action.

cicd pipeline:

1. Merge code by git --2.Test -- 3. Build -- 4.Deploy (I can do it thru. XAMPP to localhost but other ways too) _{amateur me understood, deploy to server is always thru xampp, which is true for php dev. But it can be facilitated entirely from packages which in turn is called by terminal scripts. Eg. Xxxxxx in create-react-app}_
 5. Then I will push to repo

These all can be automated writing few lines code in .yml

Mind you! Github Actions run on github server itself.

