---
layout: post
title:  "Diffusion Map for manifold learning, Theory and Implementation"
categories: [python, ML]
comments: true
---

-----------------------
### Introduction
-----------------------
'Curse of dimensionality' is a well known problem in Data Science which often causes poor performance, inaccurate results and similarity measure break-down, etc. High dimensional datasets are typically sparse and data is often embedded in a lower dimensional structure or Manifold. Manifold learning is an approach to non-linear dimensionality reduction. Algorithms for this task are based on the idea that the dimensionality of many data sets is only artificially high[^fn1]. In this note, we will see one of the many techniques in manifold learning called Diffusion Maps.

The key to all manifold learning method is the realisation that Euclidean Distance, which is often used as measure of similarity, make sense only 'locally'. Therefore, assuming there is a lower dimensional structure or manifold to the data, it would be appropriate to measure similarity over this structure rather that in the coordinate space itself. Following figure depicts the reason for the same. Similarity measured in Figure C makes more sense that the one measure in Figure C, which is the classic 'Euclidean distance' way. 

![alt](static/img/Diffusion_Map/original_figA.png)

-----------------------
### Configuring Cuckoo Sandbox
-----------------------

**Diffusion map for manifold learning**

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$


-----------------------
### Configuring Kioptrix for Pentesting practice
-----------------------



-----------------------
### References:
-----------------------
[^1]: Prof. Sandeep Shukla  and Mr. Nitesh Kumar (C3i center, IIT Kanpur)
[^2]: https://smallbusiness.chron.com/open-vmdk-virtualbox-28847.html
[^3]: https://www.hypn.za.net/blog/2017/07/15/running-kioptrix-level-1-and-others-in-virtualbox/
