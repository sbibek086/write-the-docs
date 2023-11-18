---
layout: default
title: Y(a)ml - How to write it and its A2Z Usage
category: DevOps
---
First of all, lets start with this docker-compose.yml of what we tried to do CLI way of docker in github.com/sbibek086 

 _some writes '3.3', some writes "3.3", its just matter of which format linting is in package.json. Thats all, nothing serious._

![openARUN_MaileGarirako-ko-DockerComposeYML](https://user-images.githubusercontent.com/11883023/167805462-8c71bbf5-a2ba-4ffa-a6c9-b181f26b0ca9.jpg)

_for more such docker-compose.yml, there's one privPost on DevPros_

Now, lets explore usage of YML:
Why Infrastructure.as.Code? Traditionally if you have codebase, then for deploying to server, system admin or Operations task of starting configuring server, running firewall security etc have to be done. These all are modularized and automated started by writing IaC yml.

But pink screen shows important problem- code conflict that occurs in big websites while many many devs, 

as for this eg., say dev A- react frontend dev & dev B- backend dev happen to work concurrently.

Say dev A feels like removing 'Submit' button, replace it w sthg., asks Ops people to fetch him TEST copies of production env's web page codebase & web server, pushes his patch ci/cd to prod. env. What if so, happens dev B had asked Ops to fetch him .. before A did (of course dev A & B neednt be on same table) & pushes ci cd to prod. BUT it entirely CONFLICTS with what A's patch updated to latest page/server.

Now as soln, what IaC does is: it ensures that such dont happen by updating latest patch integration to each and every servers. ie. of dev A's , of dev B's ..

bottomest screen shows how commonly, Terraform is used for Initial Infra setup to Appli setup while Ansible for ..

PS: any valid json file is also valid yml [json is subset of yml] & Yml is lang must-know-lang to use docker, kubernetes, even writing actions in github repo, & obviously IaC, PaC.
![1628264300549](https://user-images.githubusercontent.com/11883023/166114380-e0842ea6-2433-47c3-8d70-c9b1e1fe2892.jpg)

---
2nd gold nuggets from Techworld with Nana YT, not rel to above

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
