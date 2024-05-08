---
layout: default
title: ml
category: ML
tags: [ML]
---

If this post doesnt make sense to everyone or learners, its ok as its purpose is not that but simply as my personal powerNotes.

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/ca8a7fd7-c315-4849-9f57-9745be10d70a)

These above algos are present in Scikit-learn libraries, which I stick to. so, idc about alternate libraries like keras, pyTorch etc.

---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/4f573144-e2a7-4067-957e-cc930257076d)

---
 _I will understand then write Explain it in free time_

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/c80131c0-6859-48e2-be6d-591291b259af)

---
data leakages in models fools one in such bad way that you are proud, about to yell to whole city that model is 90% accurate this, that

but in-fact 90% accuracy was not because of ml accurately tracing underlyling functions aka eqn that is mapping x to y.

I will give simple example:
Lets say, we are trying to predict if Joe says yes or no, if we ask him to eat sthg

based on 
X:
x1: are we asking him to eat pizza or rice.
x2: are we asking him when he is alone or he is in group w other person
x3; What he has already answered in True or False to 'Will you devour some food'

then,
Y aka (Joe's ans in yes or no to eat sthg) = 

f('askingHimEatPizzaOrRice', 'AreWeAskingHimAloneOrGroup','HisAnsofWillYouDevourSomeFood', )

If we train this above equation on train data's X, Y, then this ML will give 100% accuracy on test data

WHY?
Its because whether he will eat or not is already pre-answered by Whether he will devour some Food
This type of leakage is leaking correct prediction or ground truth ie Y into X of train data. 

so, knowing that this feature can be x not y ,or knowing that this feature can or cant be x or pre-checking this x is in fact just aliased y is very important. This is called feature engineering or feature selection.

btw, our 2019 mistake was, as far as I could infer was: leaking info from future into past- it was time series data

other leakage causes are:  

leaking test data in to training data. btw, who would make such silly mistakes , haha

any of above-mentioned faults in 3rd party data joined to training set. rational mistake

---
Big data (>10 GB) , how to make ML model fit to it as it's now downloadable in pc


