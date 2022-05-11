---
layout: posts
title: Y(a)ml - How to write it and its A2Z Usage
category: DevOps
---
First of all, lets start with this docker-compose.yml of what we tried to do CLI way of docker in github_com/sbibek086 
![openARUN_MaileGarirako-ko-DockerComposeYML](https://user-images.githubusercontent.com/11883023/167805462-8c71bbf5-a2ba-4ffa-a6c9-b181f26b0ca9.jpg)

Now, lets explore usage of YML:
Why Infrastructure.as.Code? Traditionally if you have codebase, then for deploying to server, system admin or Operations task of starting configuring server, running firewall security etc have to be done. These all are modularized and automated started by writing IaC yml.

But pink screen shows important problem- code conflict that occurs in big websites while many many devs, as for this eg., say dev A- react frontend dev & dev B- backend dev happen to work concurrently. Say dev A feels like removing 'Submit' button, replace it w sthg., asks Ops people to fetch him TEST copies of production env's web page codebase & web server, pushes his patch ci/cd to prod. env. What if so, happens dev B had asked Ops to fetch him .. before A did (of course dev A & B neednt be on same table) & pushes ci cd to prod. BUT it entirely CONFLICTS with what A's patch updated to latest page/server.

Now as soln, what IaC does is: it ensures that such dont happen by updating latest patch integration to each and every servers. ie. of dev A's , of dev B's ..

bottomest screen shows how commonly, Terraform is used for Initial Infra setup to Appli setup while Ansible for ..

PS: any valid json file is also valid yml [json subset of yml] & Yml is lang must-know-lang to use docker, kubernetes, even writing actions in github repo, & obviously IaC, PaC.
![1628264300549](https://user-images.githubusercontent.com/11883023/166114380-e0842ea6-2433-47c3-8d70-c9b1e1fe2892.jpg)
