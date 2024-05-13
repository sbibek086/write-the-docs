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

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/40e80dbb-b72c-4d16-aa03-b9f8975224c2)

---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/99f31dfe-ce81-4547-a5fd-8b323ad328a3)

So, how do we decide which is principal component1 and which is principal component2?

It is by:
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/c49cfe9b-fba1-41c8-bfef-0397bd234663)

