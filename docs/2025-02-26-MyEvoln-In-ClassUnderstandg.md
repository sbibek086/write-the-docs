---
layout: default
title: (T) Evolution In my understanding of classes
category: Software Development

---
A.

(No need to read this) Back to C++ BE-days, where I had understanding that class is what you create when you have to codify staff persona.

OOP4pillars img below:

![image](https://github.com/user-attachments/assets/19cc0d28-ce51-42ec-85a2-00615acb5a86)

Idiot me! -It was just example of real life so that we can relate easily. Classes are used in all sorts of core files development, like if we have to inherit parent driver classes to more specific childs

---
B.

Anyway, context now here is in django language:

![image](https://github.com/user-attachments/assets/0990d4a9-ab13-428f-af09-13078de42a3d)

In above, now that I have created CustomUser, there are limitless possibilities just like in English language, after you write Alex, you can go to V O language or is Adj format- its upto me.

Anyway, after CustomUser is created, I can go:
```
class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
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
```
class WhatIhadTitledMyTableInERdgm
  someAdditionalColsBesidesUserInbuiltFields = models.ForeignkeyButCanBOneToOneField(User, on_del........CASCADE)
  someotherAdditionalCols=models.charField(max_length=50)
  ....etc etc
```
n this would have done job - no headache as built-in User model is already integrated into Django admin panel. You can manage users from there or extend its functionality if needed.

but thisInBuilt User 's authenticate method only supports (request, username = username, password =password).

So, we had to use AUTH_USER_MODEL 's abstractUser way . ani yesai lai get_user_model bata extend garera garne

---
D. Now, since initially, I wasnt aware about all tools beforehand, my way of using ROLE_CHOICES sucked. 

But my specific business requirement could have be managed by below, as it uses AbstractBaseUser - more scratch reboot way than AbstractUser way (directly look class Account line):

```
from django.db import models
from django.contrib.auth.models import AbstractBaseUser, BaseUserManager

# Create your models here.

class MyAccountManager(BaseUserManager):
    def create_user(self, first_name, last_name, username,email,password=None):
        if not email:
            raise ValueError("User must have an email address")
        
        if not username:
            raise ValueError("User must have an username")
        
        user = self.model(
            email = self.normalize_email(email),
            first_name=first_name,
            last_name=last_name, 
            username= username
        )

        user.set_password(password)

        user.save(using=self._db)
        return user

    def create_superuser(self, first_name, last_name, username,email,password):
        user = self.create_user(
            email = self.normalize_email(email),
            first_name=first_name,
            last_name=last_name, 
            username= username,
            password = password
        )

        user.is_admin = True
        user.is_active = True
        user.is_staff= True
        user.is_super_admin= True

        user.save(using=self._db)

        return user


class Account(AbstractBaseUser):

    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    username = models.CharField(max_length=50, unique=True)
    email = models.EmailField(max_length=50, unique=True)
    phone_no = models.CharField(max_length=15,blank=True)

    # required

    data_joined = models.DateTimeField(auto_now_add=True)
    last_login = models.DateTimeField(auto_now_add=True)
    is_admin = models.BooleanField(default=False)
    is_staff = models.BooleanField(default=False)
    is_active = models.BooleanField(default=False)
    is_super_admin = models.BooleanField(default=False)

    USERNAME_FIELD = 'email'
    REQUIRED_FIELDS =  ['username','first_name','last_name']

    objects = MyAccountManager()

    def full_name(self):
        return str(self.first_name).capitalize() +' '+ str(self.last_name).capitalize()

    def __str__(self):
        return self.email

    def has_perm(self, perm, obj= None):
        return self.is_admin
    
    def has_module_perms(self,add_label):
        return True

class UserProfile(models.Model):
    user = models.OneToOneField(Account, on_delete = models.CASCADE)
    # ya oneToOneField laako chai Account ka sabai fields UserProfile ma satta tanna ho. 1to1 field ka more useCase lai gpt
    address_line_1 = models.CharField(max_length=100, blank=True)
    address_line_2 = models.CharField(max_length=100, blank=True)
    profile_pics = models.ImageField(blank=True, upload_to='pics/profile_pics')
    city = models.CharField(max_length=20, blank=True)
    state = models.CharField(max_length=20, blank=True)
    country = models.CharField(max_length=20, blank=True)

    def __str__(self):
        return self.user.first_name

    def full_address(self):
        return f'{self.address_line_1} {address_line_2}'
```



