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

Since admin.0001_initial depends on app.0001_initial, and since most of the times generating up-to-date version of latest

app.000x_initial happens under the hood {If we think carefully, then we can infer: auth.000x_initial latest version is 

auto-generated w every latest app.000x_initial in order to keep up with the changes and make sure every such tables - of app.000x,

admin.000x,.. are in sync}

Now problem would obviously occur if I forcefully reset only:
python manage.py migrate zero 
because I INFER THAT
this command has ONLY reset app.0001_initial all the way to initial state

and other like admin.0001_initial are still on earlier latest version.

So, I SENSE that I have to reset back admin.0001_initial all the way to initial state.
```

I think this explains below error:
![image](https://github.com/user-attachments/assets/78eb101d-d10b-4f9a-b1ea-2c6bddc15980)

---
Btw, 
a)postgres:15 is docker container

b)Inside this container, I have me-User as django-user out of 100 other users.

c)Under this me-User, I had earlier django_db database which was f**ked up because of inconsistent migration
and as in below screenshot, I created afresh virgin postgres database out of 10s-other-can-be-created databases


docker exec -it vivekproject2_db_1 bash before psql -U , to enter inside db container
![image](https://github.com/user-attachments/assets/c1264ea6-1c02-4793-a137-c45af072dc55)

[yes, stackoverflow is still relevant - cause I came to know dropping that database as soln from this- thanx to me googling main error statament](https://stackoverflow.com/questions/65562875/migration-admin-0001-initial-is-applied-before-its-dependency-app-0001-initial-o), n then I gpt-ed 'command to drop database'

and now hurray I got below, which is exactly according to what I have in models.py

d) Under this database, I can have 10 other tables like auth_user table etc
![image](https://github.com/user-attachments/assets/b3730a39-c4a7-4872-adbc-4ef1366941d4)
