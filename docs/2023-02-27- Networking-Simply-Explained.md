---
layout: default
title: Network Basics Simply Explained
category: Techology
tags: [Technology]
---

![Nw](https://user-images.githubusercontent.com/11883023/221647157-ecf74482-b68f-4a9b-8db7-607d56e4a783.png)

So, 1st let's focus on blue color diagram:  

Local.Area.Network is what is inside say, one office. 
Analogy: Inside Boundry of school == LAN.
So, class X == one IP  

_{now lets not complicate this analogy, ok so class X's Ram is one IP, then what is IP equivalent for class X's Syam. For now, lets just say, whoever is from class X==1 IP}_

Class X student can talk w class XI student or also w class XII student. So, class X message if it is for class XI or XII. That's where peon comes in. 
Peon == SWITCH == multiplexer.          

 Peon ensures class X student message is for class XI, NOT class XII.

Now, what if some student from one of class wants to communicate outside of his school ie. outside of LAN. Outside of LAN? that means we've come to Wide.Area.Network
and how does 192.168.10.20 know that 192.168.1.2 is in its LAN and 62.13.29.50 is outside? 

Welcome to NETMASK's concept.
so, 192.168.1.2 subnet w 255.255.0.0 produces 192.168.1.2 as inside its LAN. How? 
because 

binary of 192   .  binary of 168   . 0000  0001 . 0000 0010

1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1  . 0000  0000 . 0000 0000  <= this is binary of 255.255.0.0

makes 192.168 identifiable as inside its LAN.  so, 192.168.1.2 is identified as one, inside its LAN and 62.13.29.50 is identified as not.

![Nw](https://user-images.githubusercontent.com/11883023/221634022-a34639ca-ca31-4974-9df8-6ba4ef306d36.png)

```
How? There's some maths how its resolved but DONT BOTHER TO UNDERSTAND IT N EVERYTHING, Vivek. Just memorize, this is how its done. 
If you cant kill stupid curiosity, then >> https://user-images.githubusercontent.com/109033173/183240652-76f9f489-b36b-4b9c-952a-49189d5c789c.png
```

Now lets cover green color.
Now for 192.168.10.20 to communicate w 62.13.29.50, we now need Router == Security guard. 

Router should serve as

a. NAT 

b. Firewall is WALL that protects our LAN from incoming FIRE traffic from WAN. ie. adhoc requests are to be blocked and only specific set of communications
ie. which port to open and/or which ip range are allowed for incoming traffic.
 Its Aws equivalent is Network.Access.Control.List + Sec gp
 
c. now to disallow Firewall for some specific section of subnets, we can assign such subnets as DeMilitarize.Zone DMZ.

 It's like in our school, if we allow some students to be visited by outsider, then security guard can put certain students in  
'No Restriction, outsider can come visit them' room.    

Accurately put, DMZ is subnet that exposes device to outside WAN.

d. now to disable Firewall, we can also do 'PORT FORWARDING' rules on firewall. This is equivalent to AWS security group rules. This statement was about setting up 
port forwarding rules for incoming traffic in device of our LAN.

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/a946a931-c4d3-4bf4-95e2-30db5b4c8cf6)

NOTICED, how all this above concept is what is setup in AWS itself. There might be new terminologies, but it is recreating all this.

Think of it this way -

We got home garden home path etc. etc. manually setup in real soil == having buying computer, giving IP, connecting to Internet.

Now, we got all these home garden, home path evrything to real thing now DELIVERED in truck and we rent evrything and set it up truck soil === AWS

---
Some related context while aws labs

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/81548406-e3a1-41cb-ad4a-4317acc37068)

