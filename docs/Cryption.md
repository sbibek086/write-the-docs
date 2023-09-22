---
layout: default
title: En/De- Cryption
category: SoftwareDev
tags: [SoftwareDev]
---
![ffffff](https://user-images.githubusercontent.com/11883023/269960201-79fa895e-35f4-4915-81d3-02fc4a9c2ef0.jpeg)

Encryption and decryption of intransit data and session keys (which lets server and client ensure each other they are on same timestamp and same session, put simply, session keys lets both s and c know it is happening on same single sitting when i open transact on say esewa pathao etc.) is tricky.

now, how do server and client know that they have same encryption decryption protocol, put simply, how do both know that for eg. when server says balanalanala , then client should understand banana.

welcome to SSL/TLS certificate stds that are set by Public.Key.Infrastructure body.

now, how pub/priv key operates, - i will attach one of my pinterest foto ,n which i had youtubed cover earlier (there are asymm style aka AES, symm style ).

now, to main point, whats so tricky. its as below:

ssl tsl certificate works below while on ssl tsl handshake betn s and c:

a. browser opens ssl tsl secure website n connects to webserver when we open say amazon.

b. browser attempts to verify authenticity of web server by requesting identifiable information?

c. web server sends ssl tsl certificate that contains pubKey as reply

d. browser then verifies ssl tls cert, ensuring it is valid and matches website domain. and once browser is satisfied w ssl tsl cert, it uses pubKey to encrypt n send message that contains secret sessionkey.

e. webserver then uses privKey to decrypt message and retrieve sessionkey. it then uses sessionkey to encrypt and send acknowledgement messagr to browser.

f. finally both browser and webserver switch to using same session key to exchange message safely.

now, when we are tunnelling ie to say making our local machine as server endpoint, then we are shortcutting all certificate provisioning so that we dont have to do all this process again. its now one shortcut. this paragraph might have some inaccuracies but sthg like that
