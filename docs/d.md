---
layout: page
title: ~
category: Programming
tags: [Programming] 

---

hub.docker.com >>3.6.76. pw: 3..8 

![dockerWorkFlow](https://user-images.githubusercontent.com/11883023/209544204-48c30b20-48e6-47b5-972c-af4b98ddb45c.png)
![image](https://github.com/user-attachments/assets/c19bf5b6-ca81-4e79-ad85-3dd2e729da3c)

docker-compose.yml way as below: 

![image](https://github.com/user-attachments/assets/1ed007d7-da59-4b91-af69-c3ea864b20cb)

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

_btw, dockerfile, app.py wa index.html kunai change garepaxi tesko effect dekhna docker-compose lai down garera feri up garna pardaina, just refresh gare hunxa; for deeper changes ko effect herna chai rarely matra garnu parna sakxa,_

 Then, how does app.py as client interacts w mysql server & also about how port expose is co-ordinated
![image](https://github.com/user-attachments/assets/3a19d5d4-4610-49b4-b5e1-3c149695d703)

---
  oh, btw:
  sudo docker-compose ps   // to check if my container services are running
  ![image](https://github.com/user-attachments/assets/2333b688-ab8f-4344-8e00-f4d0c69095a3)

   sudo docker-compose down // if only I want to stop services n remove containers
   
  &, Making docker image persistent on url -meaning I dont need to have sudo docker-compose up in my machine to come in browser, [then look here even tho I have to find another way to put sudo docker-compose up everytime ON in cloud](https://developer.okta.com/blog/2018/09/27/test-your-github-repositories-with-docker-in-five-minutes) 

