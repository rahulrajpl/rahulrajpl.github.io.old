---
layout: post
title:  "Diffusion Map for manifold learning, Theory and Implementation"
categories: [python, ML]
comments: true
---

-----------------------
### Introduction
-----------------------
'Curse of dimensionality' is a well known problem in Data Science which often causes poor performance, inaccurate results and similarity measure break-down, etc. High dimensional datasets are typically sparse and data is often embedded in a lower dimensional structure or Manifold. Manifold learning is an approach to non-linear dimensionality reduction. Algorithms for this task are based on the idea that the dimensionality of many data sets is only artificially high [^1]. In this note, we will see one of the many techniques in manifold learning called Diffusion Maps.

The key to all manifold learning method is the realisation that Euclidean Distance, which is often used as measure of similarity, make sense only 'locally'. Therefore, assuming there is a lower dimensional structure or manifold to the data, it would be appropriate to measure similarity over this structure rather that in the coordinate space itself. 


Following figure depicts the reason for the same. Similarity measured in between point A and point B makes more sense if it is done through the geometric structure of the data.  

<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/279503/76152157-2eaa2780-60e2-11ea-8024-e9b11f96c28f.png">
<br><em align="center">Figure 1: Euclidean Distance meausured in</br> co-ordinate space</em>
</p>

<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/279503/76152158-310c8180-60e2-11ea-8bbc-ec6a60c084d1.png">
<br><em align="center">Figure 2: Euclidean Distance meausured through</br> manifolds</em>
</p>

Because, the typical Euclidean Distance seems less and we tend to assume that the points are similar, while the actual distance through its geometric structure or manifold reveals that the distance is infact larger, and points are dissimilar. This is a typical toy example to demonstrate the importance of finding the underlying geometry.


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
[^1]: Manifold Learning methods in Scikit-Learn (https://scikit-learn.org/stable/modules/manifold.html)

