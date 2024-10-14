---
layout: default
title: ml
category: ML
tags: [ML]
---

Dimensionality reduction- One way to deal w Big files by dec. its size

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/6d1f50dd-88a2-459b-8c72-5f0b83485ba1)

Now, in above image last, I ask- what might be that PCA component1 or component2 in X or Y axis respectively?

That is covariance matrix elements.

![image](https://github.com/user-attachments/assets/4838595f-2142-4cc9-b270-63065e8d18b8)

So, how do we decide which is principal component1 and which is principal component2?

It is by:

![image](https://github.com/user-attachments/assets/555d0ef3-f1a3-485f-bed6-357628404b12)

euclidian vanya tye shortest distance ho 

_Hopefully, no math headache, code as below, however math process bujheko ramro_

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/b5a6f20f-60fb-4555-a354-9eec8ecfa8a4)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/3c58abd1-09c5-4b3a-a809-b000f2359623)

So, here, we see visually how pca reduces data. NOTE: dimensional redn is not cols reduction, which I thought

teso vaye, ya ta principal component1 matra dekhax, feri stratum ko ma ta diuta PCA banayera khichirathyo. correct fix my this understandg loophole

_PS: Heatmaps, t-SNE Plots, Multi-dimensional Scaling are just alternatives to Dimensional Reduction method

yt Zach Star, Stratum_

---
---
Nothing to do w above context are posts from below on:
stratification means breaking down population to smaller subsets ie samples such that based on certain criteria/ features, each subset almost proportionately reflects similar distribution of criteria/ features.

eg. if I have more red about 90%, less green about 10% balls, then in smaller bowl I put red n green bowls in similar ratio. Stra s'ud be done when population is v disproportionately distributed.

---
another context - xgboostA2Z

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/2c546095-b073-4a2e-a088-ce88397c187e)

---
![logistic-Regressn-2](https://github.com/user-attachments/assets/41420ee9-b15c-4f9d-8a36-192b2958ca70)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/ca8a7fd7-c315-4849-9f57-9745be10d70a)

These above algos are present in Scikit-learn libraries, which I stick to. so, idc about alternate libraries like keras, pyTorch etc.

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/b214a15b-29a2-4acf-af0d-962413271751)

Compiler mai sabai lekhya hunchh ta. Patiently padha Vivek
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/4f573144-e2a7-4067-957e-cc930257076d)

---

![Logistic-Regressn-moreThan2](https://github.com/user-attachments/assets/cddd97e4-aa4e-4f77-9944-9daa3ca9639b)

---
---
**data leakages in models** fools one in such bad way that you are proud, about to yell that model is 90% accurate this, that

but in-fact 90% accuracy was not because of ml accurately tracing underlyling functions aka eqn that is mapping x to y.

I will give simple example: Lets say, we are trying to predict if Joe says yes or no, if we ask him to eat sthg

based on X:
-  x1: are we asking him to eat pizza or rice.
-  x2: are we asking him when he is alone or he is in group w other person
-  x3: What he has already answered in True or False to 'Will you devour some food'

then, Y aka (Joe's ans in yes or no to eat sthg) = 

f('askingHimEatPizzaOrRice', 'AreWeAskingHimAloneOrGroup','HisAnsofWillYouDevourSomeFood', )

If we train this above equation on train data's X, Y, then this ML will give 100% accuracy on test data

WHY? - Its because whether he will eat or not is already pre-answered by Whether he will devour some Food.
This type of leakage is leaking correct prediction or ground truth ie Y into X of train data. 

so, knowing that this feature can be x not y ,or knowing that this feature can or cant be x or pre-checking this x is in fact just aliased y is very important. This is called feature engineering or feature selection.

btw, our 2019 mistake was, as far as I could infer was: leaking info from future into past- it was time series data

other leakage causes are:    
-  leaking test data in to training data. btw, who would make such silly mistakes , haha
-  any of above-mentioned faults in 3rd party data joined to training set. rational mistake





