---
layout: default
title: (T) classes used in Django
category: Software Development

---

A. Metaclasses: Powerful ORM like Django leverage metaclasses to seamlessly link classes to database tables.

Django utilize metaclasses to forge model classes and uphold business logic with ease.


B.

Anyway, context now here is in django language:

![image](https://github.com/user-attachments/assets/0990d4a9-ab13-428f-af09-13078de42a3d)

In above, now that I have created CustomUser, there are limitless possibilities just like in English language, after you write Alex, you can go to V O language or is Adj format- its upto me.

Anyway, after CustomUser is created, I can go:
```
class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    # ya oneToOneField laako chai Account ka sabai fields UserProfile ma satta tanna ho. 1to1 field ka more useCase lai gpt
    ROLE_CHOICES = [
        ('Customer', 'Customer'),
        ('Manager', 'Manager'),
    ]
    role = models.CharField(max_length=20, choices=ROLE_CHOICES, default='Customer')
```

sothat I can then access role via the Profile as below:
role = user.profile.role

ALSO, MEANWHILE:
Ensure the database contains role values for users. 
For eg:Add role when creating users via the Django admin panel or in your signup process.

---
C.
But there's more shortcut way to B- using built-in class of Django.

so, django has inbuilt User class which can be imported by

import django.contrib.auth.models 

in models .py

and then its just matter of 

<img width="662" height="75" alt="image" src="https://github.com/user-attachments/assets/338963c1-1218-4eaa-be4a-ca83e4296974" />

n this would have done job - no headache as built-in User model is already integrated into Django admin panel. You can manage users from there or extend its functionality if needed.

but thisInBuilt User 's authenticate method only supports (request, username = username, password =password).

So, we had to use AUTH_USER_MODEL 's abstractUser way . ani yesai lai get_user_model bata extend garera garne

---
D. Now, since initially, I wasnt aware about all tools beforehand, my way of using ROLE_CHOICES sucked. 

But my specific business requirement could have be managed by below, as it uses AbstractBaseUser - more scratch reboot way than AbstractUser way (directly look class Account line):

<img width="1139" height="499" alt="image" src="https://github.com/user-attachments/assets/77fe17a8-e12f-433c-bed7-0faf171e77d4" />
