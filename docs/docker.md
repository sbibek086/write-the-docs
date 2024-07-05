---
layout: default
title: 🐳
category: Programming
tags: [Programming] 
---

DOCKER is My First GoTo when building app or sthg. Below shows WHY HOW :)
my words- yes, doing docker way is 10step to 5step thing but need to know port mapping etc concept expertly. so not recommended unless know these.
So, unless know, do localhost way primary way

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
[Do all this wholesome in DockerCompose.yml way](https://sbibek086.github.io/write-the-docs/2022-04-30-YML-HowToWrite-ItsA2Zusage.html)

---
https://www.docker.com/blog/how-to-build-and-test-your-docker-images-in-the-cloud-with-docker-hub/

![image](https://user-images.githubusercontent.com/11883023/129465953-70a13d01-e17f-4399-8774-22ab70b19f5c.png)
What it does is- It pulls docker host of url tutum/hello-world from its port 80 and maps it to port 3000 of my local machine {-p is for portmapping }, so that after this command, when I open localhost://3000, I can look at its webpage. Tutum/hello-world has written this fantastic code of web server inside it, which maynot be true for others.
Take for eg, another docker host which just throws to terminal itself

![image](https://user-images.githubusercontent.com/11883023/129466016-ea8a5dcd-ca41-44a0-a127-e05020c5f333.png)
