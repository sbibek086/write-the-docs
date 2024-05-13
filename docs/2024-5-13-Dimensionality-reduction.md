---
layout: default
title: Dimensionality reduction- 1 way to deal w Big files by decreasing its size
category: ML
tags: [ML]
---
Dimensional reduction by removing negative correlated features (features which can be cols in csv or can be rows in parquet)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/6d1f50dd-88a2-459b-8c72-5f0b83485ba1)

Now, in above image last, I ask- what might be that PCA component1 or component2 in X or Y axis respectively?

That is covariance matrix elements.

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/27244a2b-229c-4b00-a279-f9d6705900a0)

---
So, how do we decide which is principal component1 and which is principal component2?

It is by:
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/6416d09e-315f-4077-a11d-753e6ce26bae)

Hopefully, no math headache, code as below, however math process bujheko ramro

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/b5a6f20f-60fb-4555-a354-9eec8ecfa8a4)

PS: Heatmaps, t-SNE Plots, Multi-dimensional Scaling are just alternatives to Dimensional Reduction method
yt Zach Star, Stratum
