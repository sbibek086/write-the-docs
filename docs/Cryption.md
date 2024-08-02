---
layout: default
title: SSH >>https way even when cloning git...
category: SoftwareDev
tags: [SoftwareDev]
---

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/a3acafa4-3716-4cb8-8626-65cc01f14ada)

In SSH (runs on Linux, macOS, Windows with appropriate software),

-strong **authentication** methods, including password-based authentication and public key authentication, which are more secure than standard HTTP authentication mechanisms.

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/0d2baa73-23ea-4430-8570-154023390893)

-cryptographic hash functions (look 1st img above carefully) to verify **integrity** of data being transmitted.
_{btw, there are asymm style aka AES and symm style. hunchha just thaha pairakh sakyo kura}_

-Remote Command Execution: allows for execution of commands on a remote machine, making it ideal for system administration and management tasks.

-File Transfer: With SCP (Secure Copy Protocol) and SFTP (SSH File Transfer Protocol), SSH supports secure file transfers.

-Tunneling aka Port Forwarding: SSH can tunnel other protocols through its encrypted connection, allowing secure forwarding of ports and services.
```
Local Port Forwarding aka (Standard or default understood Tunneling) : Forwards traffic from a local port to a remote server.  aka Forwards local port to remote destination.

Remote Port Forwarding (Reverse Tunneling): Forwards traffic from a remote port to a local machine. aka Forwards remote port to local destination.
```
-Interactive Shell Access: SSH provides direct, interactive shell access to remote machine, enabling real-time command execution and troubleshooting.

- use SSH to connect to a remote development environment, run scripts, and deploy code changes directly.

How to do it?  Just watch bottom of https://sbibek086.github.io/write-the-docs/2023-10-13-Creating-Pytest_suites.html

---
Just for curiosity cat of how https ssl/ tsl certificate works?

Encryption and decryption of intransit data and session keys (which lets server and client ensure each other they are on same timestamp and same session, put simply, session keys lets both s and c know it is happening on same single sitting when i open transact on say esewa pathao etc.) is tricky.

now, how do server and client know that they have same encryption decryption protocol, put simply, how do both know that for eg. when server says balanalanala , then client should understand banana.

welcome to SSL/TLS certificate stds that are set by Public.Key.Infrastructure body.

ssl tsl certificate works below while on ssl tsl handshake betn s and c:

![image](https://github.com/user-attachments/assets/462a3a5c-e4e0-45e0-bc57-1fd9a052f5ed)

---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/9dd9b438-7a2d-4919-85d1-34e2178d9ccc)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/d870dee5-9d66-490f-b7ab-d8f314a27888)



