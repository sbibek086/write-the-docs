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
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/99f31dfe-ce81-4547-a5fd-8b323ad328a3)

So, how do we decide which is principal component1 and which is principal component2?

It is by:
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/c49cfe9b-fba1-41c8-bfef-0397bd234663)

Now, that eqn covariance matrix * lambda = sthg * lambda doesnt make sense, right?

[watch](https://www.youtube.com/watch?v=i8FukKfMKCI)
