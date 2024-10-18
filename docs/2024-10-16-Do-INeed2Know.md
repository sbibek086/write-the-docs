---
layout: default
title: Do I need to know all b4 + Abstraction diff in math & cs +..
category: Cryptography
tags: [Cryptography]
---

We are victims of our own faulty habits and thought patterns. So, I spent most of my 20s in pressure cooker conventional exam conditions, which demand that you need to know all formulas by heart (what rubbish?), all principles like second natured. So, it shaped my preconditioning in such a way that I need to know all parts by heart before I dare to wet my feet in problem solving ocean. 
     But real world or lets be confined to programming challenges does not work like that. We need to have that problem solving methodology - thats it. Lots of knows are learnt while on the flow of problem solving. Tho I breathe it consciously, my subconscious brain masks me - Vivek, you need to know all parts beforehand, you need to know all parts beforehand.
    Below conversation exemplifies this - post-er seems to be know-it-all-before kind of guy and commenter is not.
    
![image](https://github.com/user-attachments/assets/e10752ee-bbde-478a-bc96-397f9880b849)

---
integrate from x =3 to 4 the log(sinx^2) dx

lai pgm ma lekhda tala esto:

import numpy as np
import scipy.integrate as integrate

def sine_of_x(x):
    return np.sin(x)

def sine_squared(x):
    return sine_of_x(x) ** 2

def log_of_sine_squared(x):
    return np.log(sine_squared(x))

def integrand(x):
    return log_of_sine_squared(x)

#1shot ma below lekhnu better. 
#just want2show how args passed in above
#def integrand(x):
 #   return np.log(np.sin(x)**

lower_limit = 3
upper_limit = 4

result, error = integrate.quad(integrand, lower_limit, upper_limit)

# Output the result and error margin
print(f"The result of the integral is: {result}")
print(f"The error margin is: {error}")

---
passing above my brain - what its trying to say; please help me with PR-ing explanation below this image:

![image](https://github.com/user-attachments/assets/693010cc-33cb-4b31-bb64-36a07355cb1b)
