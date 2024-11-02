---
layout: page
title: 🐳 + y(a)ml combo
category: Programming
tags: [Programming] 
---

hub.docker.com >>3.6.76. pw: 3..8 is My First GoTo when building app or sthg. Below shows WHY HOW :)
my words- yes, doing docker way is 10step to 5step thing but need to know port mapping etc concept expertly. so not recommended unless know these.
So, unless know, do localhost way primary way

[yo sab gareko WordpressCamp'sTut](https://www.facebook.com/mishra.aananta/videos/307497993616073)

![dockerWorkFlow](https://user-images.githubusercontent.com/11883023/209544204-48c30b20-48e6-47b5-972c-af4b98ddb45c.png)
![dockerWFlow](https://github.com/sbibek086/write-the-docs/assets/11883023/7b4b7003-e40b-4a67-9cb3-3d9e7e18b875)

![dockerCmds](https://user-images.githubusercontent.com/11883023/226905071-689ef9cc-36be-4d97-8a29-fe38de12edba.png)

```
docker run -d -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=mysite -e MYSQL_PASSWORD=password --name mysitedb -v "$PWD/database":/var/lib/mysql mysql
```
![docker2](https://user-images.githubusercontent.com/11883023/192002125-893e6b7e-eaf9-4f3e-a16d-b5e5a70b3fe7.png)

```
docker pull wordpress
docker run -d -e WORDPRESS_DB_NAME=mysite -e WORDPRESS_DB_USER=mysite -e WORDPRESS_DB_PASSWORD=password --name wordpress --link mysitedb -p 80:80 -v "$PWD/html":/var/www/html wordpress
```
IdontKnow why but while doing, mathi ko command rakhda athena tara tala ko
```
docker run -d --name wordpress --link mysitedb -p 81:80 -v "$PWD/html":/var/www/html wordpress
```
rakhda chai aathyo

Now, alternatively, lets do w docker-compose.yml way of what we tried to do CLI way of docker in github.com/sbibek086 

![image](https://github.com/user-attachments/assets/943e01f7-a93e-4872-a451-f80adeed6ab1)


[How does depends_on work?](https://stackoverflow.com/questions/73727944/when-depends-on-is-being-used-in-docker-compose-yml)

![IaC](https://github.com/user-attachments/assets/00e53816-27cf-44e7-87a5-fea71ee8587d)

---
by RPyi- breakdown in gpt
![image](https://github.com/sbibek086/sbibek086.io/assets/11883023/202fe845-0d23-4264-a884-d5a282692304)

---
---
A)Additional notes: 
https://www.docker.com/blog/how-to-build-and-test-your-docker-images-in-the-cloud-with-docker-hub/

![image](https://user-images.githubusercontent.com/11883023/129465953-70a13d01-e17f-4399-8774-22ab70b19f5c.png)
What it does is- It pulls docker host of url tutum/hello-world from its port 80 and maps it to port 3000 of my local machine {-p is for portmapping }, so that after this command, when I open localhost://3000, I can look at its webpage. 

Tutum/hello-world has written this fantastic code of web server inside it, which maynot be true for others.
Take for eg, another docker host which just throws to terminal itself

![image](https://user-images.githubusercontent.com/11883023/129466016-ea8a5dcd-ca41-44a0-a127-e05020c5f333.png)

B) Making docker image persistent on url no matter my dockerDektop is Off:
If I want such that -when I turn off docker, which I had to start app n run it. I mean that docker image of website always coming on URL no matter I switch off my machine, termed persistency.   If I want such, [then look here](https://developer.okta.com/blog/2018/09/27/test-your-github-repositories-with-docker-in-five-minutes)
as AB suggested me, I should make batch .bat file of that docker commands and save it as .bat So that All i need to do is go to its location from terminal ,and then ThatFile.bat ENTER

C) [dockerTut](https://www.slideshare.net/vincenzoferme/using-docker-containers-to-improve-reproducibility-in-software-and-web-engineering)

---
---
---
CI/CD aka devOps from Techworld with Nana YT not rel to above

![gitActions](https://user-images.githubusercontent.com/11883023/120933150-82a62080-c718-11eb-9667-0ede1aad1b33.jpg)
[thisYT](https://www.youtube.com/watch?v=R8_veQiYBjI) powerGist
Open source prj are mostly agile (means there is no such thing as 100% final; there's always improvement- relate that with facebook, it improves even to this day) ,and there can be 1000+ contributors as it grows big.

So, its practically impossible to accept every pull req. (PR) code, edit with issues , check its validity(TEST), merge it etc etc. as written by Merged Code, Test, Build, Deploy in above pic. Every incoming PR to your open source repo is called EVENTS and things you do in its response (Mer., T, B, D is act of Continuous Integration/ Continuous Deployment = CI/CD) is called ACTIONS, which can be automated. Hence, the name Actions with CI/CD pipeline.

Though ci cd is superset of action.

1. Merged code (i will do it via git tools in Vstudio)
2. Test
3. Build (I will do 2, 3 in Vstudio)
4. Deploy (I will do it thru. XAMPP to localhost in my browser)
(amateur me understood, deploy to server is always thru xampp, which is true for php dev. But it can be facilitated entirely from packages which in turn is called by terminal scripts. Eg. Xxxxxx in create-react-app)
5. Then I will push to repo
These all can be automated writing few lines code in .YAML file (superset of json file)

Mind you! Github Actions run on github server itself.

