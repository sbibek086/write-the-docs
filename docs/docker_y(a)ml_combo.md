---
layout: page
title: 🐳
category: Programming
tags: [Programming] 
---

hub.docker.com >>3.6.76. pw: 3..8 

![dockerWorkFlow](https://user-images.githubusercontent.com/11883023/209544204-48c30b20-48e6-47b5-972c-af4b98ddb45c.png)
![image](https://github.com/user-attachments/assets/c19bf5b6-ca81-4e79-ad85-3dd2e729da3c)

docker-compose.yml way as below: 
![image](https://github.com/user-attachments/assets/575479b6-21b4-4804-9098-8ab07e4ee0dc)

---
**Doing more Grand Project than earlier, using docker-compose**

A.  Problems faced & debug-how:  So, when 404 error came on localhost:5000, I did  docker-compose logs app

then it showed below error:

```
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 791, in urlopen
    response = self._make_request(
               ^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 497, in _make_request
    conn.request(
  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 395, in request
    self.endheaders()
  File "/usr/lib/python3.12/http/client.py", line 1331, in endheaders
    self._send_output(message_body, encode_chunked=encode_chunked)
  File "/usr/lib/python3.12/http/client.py", line 1091, in _send_output
    self.send(msg)
  File "/usr/lib/python3.12/http/client.py", line 1035, in send
    self.connect()
  File "/usr/lib/python3/dist-packages/docker/transport/unixconn.py", line 27, in connect
    sock.connect(self.unix_socket)
PermissionError: [Errno 13] Permission denied
```
is /usr/lib/python3.12/http/client.py referring to path inside container?

Chatgpt: So, /usr/lib/python3.12/http/client.py in the error message is not referring to a path inside the Docker container. It’s actually a path on your host machine (Ubuntu) where Python’s standard library files are located.
Breakdown of the Error

This error occurs because:

    PermissionError: [Errno 13] Permission denied: This indicates that a process on your host (not inside the container) is trying to access a Unix socket without the necessary permissions.

    Docker Unix Socket: The line sock.connect(self.unix_socket) in docker/transport/unixconn.py shows that this process is trying to connect to Docker’s Unix socket (usually located at /var/run/docker.sock). The Unix socket allows the Docker client to communicate with the Docker daemon, and the permission error means the user trying to access it doesn’t have permission to use this socket.

Why This Happens in Docker Compose ? - In Docker Compose, if your application code (or some package it depends on) tries to interact with the Docker API or other Docker services, it needs permission to access the Docker socket. When running Docker commands or interacting with Docker from a process, permissions are required for /var/run/docker.sock

![image](https://github.com/user-attachments/assets/5449073e-4d17-488d-962d-fb03f07948db)

now, we can see above, docker-compose logs app RESULT is lot cleaner

B. Then after, 

So, docker-compose.yml is LHS-of-3rd-pic-from-top and lets see how it compiles:
![image](https://github.com/user-attachments/assets/7638cc70-33ca-4b71-a380-31fcb5b8d059)

Then, how does app.py as client interacts w mysql server & also about how port expose is co-ordinated
![image](https://github.com/user-attachments/assets/b4f88e17-c468-49a4-a320-858e3ea8be61)

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

