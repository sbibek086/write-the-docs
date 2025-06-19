---
layout: default
title: (t) prev ssh post is ssh-ing localMachine to RepoUrl, thisPost is sshing one machine to another by ip
category: SoftwareDev
tags: [SoftwareDev]

---

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/a3acafa4-3716-4cb8-8626-65cc01f14ada)

![image](https://github.com/user-attachments/assets/88060abc-ee8e-4aa3-a473-0feaed5a4c05)

ssh is: 
a) strong **authentication** method is more secure than standard HTTP authentication mechanisms.

![image](https://github.com/user-attachments/assets/58b636cd-6201-4654-8a7c-e3e624f8a869)

b) cryptographic hash functions (look 1st img above carefully) to verify **integrity** of data being transmitted.
_{btw, there are asymm style aka AES and symm style as below_

![image](https://github.com/user-attachments/assets/5cc2ae44-70d9-413f-8f8d-e9f7bbe4d28a)

c) Remote Command Execution: allows for execution of commands on a remote machine, making it ideal for system administration and management tasks.

d) File Transfer: With SCP (Secure Copy Protocol) and SFTP (SSH File Transfer Protocol), SSH supports secure file transfers.

e) Tunneling aka Port Forwarding: SSH can tunnel other protocols through its encrypted connection, allowing secure forwarding of ports and services.
```
Local Port Forwarding aka (Standard or default understood Tunneling) : 
Forwards traffic from local port to remote server. 
aka Forwards local port to remote destination.

Remote Port Forwarding (Reverse Tunneling): 
Forwards traffic from a remote port to a local machine.
aka Forwards remote port to local destination.
```
f) Interactive Shell Access: SSH provides direct, interactive shell access to remote machine, enabling real-time command execution and troubleshooting.

g) use SSH to connect to a remote development environment, run scripts, and deploy code changes directly.

How to do it?  Just watch bottom of https://sbibek086.github.io/write-the-docs/2023-10-13-Creating-Pytest_suites.html

---
![image](https://github.com/user-attachments/assets/cec0503f-84ba-48d0-a613-f556bfa397aa)

![pem](https://github.com/user-attachments/assets/93d364e1-2929-4083-9a7a-ea5d6dff7d17)
![F-permission](https://github.com/user-attachments/assets/31b5d8cf-6a73-4ad0-a1fb-35f710c87646)

Just for curiosity cat of how https ssl/ tsl certificate works?

Encryption and decryption of intransit data and session keys (which lets server and client ensure each other they are on same timestamp and same session, put simply, session keys lets both s and c know it is happening on same single sitting when i open transact on say esewa pathao etc.) is tricky.

now, how do server and client know that they have same encryption decryption protocol, put simply, how do both know that for eg. when server says balanalanala , then client should understand banana.

welcome to SSL/TLS certificate stds that are set by Public.Key.Infrastructure body.

ssl tsl certificate works below while on ssl tsl handshake betn s and c:

![image](https://github.com/user-attachments/assets/462a3a5c-e4e0-45e0-bc57-1fd9a052f5ed)

---

