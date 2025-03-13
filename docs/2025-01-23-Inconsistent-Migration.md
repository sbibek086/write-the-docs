---
layout: default
title: InconsistentMigrationHistory Problem in Postgres DockerContainer how2solve
category: Programming
tags: [Programming]

---

Problem:
My problem was python manage.py makemigrations invoked by Dockerfile was failing to migrate my current dir into container, as \dt in postgresql container after psql -U django_pass -d django_db {where django_pass is meUserName n django_db is db-Name} further confirmed it - as I was having none of latest models.py's customuser model as migrated in tables form.

So, I had to make migrations/ folder inside VivekProject2/app , and also create empty _ _init_ _.py. Thanks to one time python manage.py makemigrations, 0001_initial.py was automatica created as-a-result.  


But the pity was - 
![image](https://github.com/user-attachments/assets/78eb101d-d10b-4f9a-b1ea-2c6bddc15980)

btw,  migrations let us reflect changes in models from models.py all the way deep into database table's schema.
done by enter of command: python manage.py makemigrations n migrate
{in my case, I am trying to execute my command inside database container - that's why I couldn't see all that app.0001_initial, app.0002_initial (migration logs) inside migrations/ folder in app folder}

```
THIS ALL ARE MY SPECULATION, might not be true
now comes admin.0001_initial.

Since admin.0001_initial depends on app.0001_initial, n since most of times 
generating up-to-date version of latest

app.000x_initial happens under hood {If we think carefully, then we can infer:
auth.000x_initial latest version is auto-generated w every latest 
app.000x_initial in order to keep up with the changes and make sure 
every such tables - of app.000x,admin.000x,.. are in sync}

Now problem would obviously occur if I forcefully reset only:
python manage.py migrate zero 
because I INFER THAT
this cmd has ONLY reset app.0001_initial all the way to initial state

and other like admin.0001_initial are still on earlier latest version.

So, I SENSE that I have to reset back admin.0001_initial 
all the way to initial state.
and this way, above screenshot error can be fixed.
```

---
Btw, 
a)postgres:15 is docker container

b)Inside this container, I have me-User as django-user out of 100 other users.

c)Under this me-User, I had earlier django_db database which was f**ked up because of inconsistent migration
and as in below screenshot, I created afresh virgin postgres database out of 10s-other-can-be-created databases

![image](https://github.com/user-attachments/assets/0318021b-5eff-4c36-8d99-f13e90bec2f3)

[yes, stackoverflow is still relevant - cause I came to know dropping that database as soln from this- thanx to me googling main error statament](https://stackoverflow.com/questions/65562875/migration-admin-0001-initial-is-applied-before-its-dependency-app-0001-initial-o), n then I gpt-ed 'command to drop database'

and now hurray I got below, which is exactly according to what I have in models.py

d) Under this database, I can have 10 other tables like auth_user table etc
![image](https://github.com/user-attachments/assets/b3730a39-c4a7-4872-adbc-4ef1366941d4)

---
---
So, I once again got InconsistentMigrationHistory problem this time NOT on dockerized-Django but on myLocalMachine's django.

_recommendedReadInNextTab: This blog's 'While setting up poetry' post_

![image](https://github.com/user-attachments/assets/bd6dfe13-f0b3-4c81-bf58-1b060acaa182)

Then,  rather than DROP DATABASE Agriii n then CREATE DATABASE Agriii, easierWay below:

![ezgif-6828d7e2629098](https://github.com/user-attachments/assets/4ba33938-475c-4cff-b120-e585bc43b9d5)

---
Then still, python manage.py makemigrations showed no modules named 'channels' error. enough w this shit, something must be wrong w packages - so, lets do it NOT w pip coz poetry way is smarter.

So, ![image](https://github.com/user-attachments/assets/2a6e189d-8987-48b0-a661-22cc5c158b06)

as it said to 'Please change python executable from use env', I simply chose to do clicking 'Python' written lhs of 'go live' on bottomestRight corner as below:

![qw](https://github.com/user-attachments/assets/e107b626-13ef-4140-b8f5-ad8b08031ac7)

n then click obviously .venv Poetry one's Python n NOT even .venv one's Python, _as venv just cares which Py version, but poetry cares about packaging even sub-dependencies while installing. That's where .toml comes in picture - toml records all those dependency sub-dependency._

---
But still,
![image](https://github.com/user-attachments/assets/77385dc1-b779-4a19-84f2-f42048030638)

So, I synced all changes clicking ♻️ on bottomLeft n did:

![image](https://github.com/user-attachments/assets/c7e9fd8e-cad1-4eb3-ac42-b8451fa1ae63)

but still problem, means syncing only didnt work, lets git pull
![image](https://github.com/user-attachments/assets/54f5fee4-772f-4e6a-9a22-4956ab80f8cb)

then, python manage.py makemigrations n python manage.py migrate worked.

---
now, before I deploy w python manage.py createsuperuser | runserver etc, lemme do below:

![image](https://github.com/user-attachments/assets/59ac621a-b8e3-4131-9fbf-be59b0b6d3a0)

to load all those Provinces-- Koshi, Bagmati etc etc, District-- Chitwan etc etc

Then after, I createsuperuser w sbibek086@g r.T.1! n runserver







