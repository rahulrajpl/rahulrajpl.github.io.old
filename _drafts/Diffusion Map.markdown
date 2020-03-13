---
title: Diffusion Map for manifold learning, Theory and Implementation
date: 2020-01-30 00:00:00 Z
categories:
- python
- ML
layout: post
comments: true
---

-----------------------
### Introduction
-----------------------
‘Curse of dimensionality’ is a well-known problem in Data Science which often causes poor performance, inaccurate results and similarity measure break-down, etc. High dimensional datasets are typically sparse and data is often embedded in a lower-dimensional structure or Manifold. Manifold learning is an approach to non-linear dimensionality reduction. Algorithms for this task are based on the idea that the dimensionality of many data sets is only artificially high [^1]. In this note, we will see one of the many techniques in manifold learning called Diffusion Maps.

The key to all manifold learning method is the realisation that Euclidean Distance, which is often used as a measure of similarity, make sense only ‘locally’. Therefore, assuming there is a lower-dimensional structure or manifold to the data, it would be appropriate to measure similarity over this structure rather than in the coordinate space itself.

Let us begin exploring more about Diffusion Map with following datapoints neatly arranged in **S** shape 

![alt](/static/img/Diffusion_Map/original_figA.png)

In a normal circumstance, to find the similarity of point A and point B, we find the Euclidean Distance of the points in coordinate space. That would look similar to the following :-

![alt](/static/img/Diffusion_Map/original_figB.png)

However, knowing the geometric structure about the datapoint, we know that this similarity measure is inaccurate. Since there is a non-linear relationship between datapoints, it would be correct if we measure the similarity ( or distance) along the very geometric structure itself, as shown in the picture below.

![alt](/static/img/Diffusion_Map/original_figC.png)

With Diffusion Map, we can do a non-linear dimensionality reduction as well as learn the underlying geometry of the high dimensional data. Lets get straight to the theory and implementation, hand in hand


-----------------------
### Theory behind
-----------------------

#### Why is it called Diffusion Map?

The technique is based on time-dependent diffusion process, which is nothing but a randomwalk on the dataset where each hop has a probability associated with it. When the diffusion process runs for a time t, we get different probabilities of various paths it can take to calculate distance along the underlying geometric structure. Mathematically, we call this the steady-state probability of the Markov Chain. 

![alt](/static/img/Diffusion_Map/randomwalk.png)

#### Connectivity

The connectivity between two data points, x and y is defined as the probability of jumping from x to y in one step of the randomwalk and is

$$
connectivity(x, y) = p(x,y)
$$

However, it is useful to express the connectivity as a row-normalised likelihood function, K using Gaussian Kernel. This will be called **diffusion kernel**

$$
k(x,y) = \exp \left ( 
-\frac{\vert x-y \vert ^2}{\alpha}
\right ) 
$$

Now we define a row-normalized diffusion matrix, **P**. Mathematically, this is equivalent to the transition matrix in the Markov chain. While **P** denotes the probability(connectivity in this case) of single hopping from point x to point y in single, $$P^2$$ denotes the probability of reaching y from x in two hops and so on. As we increase the number of hops or $$P^t$$ for increasing values of $$t$$, we observe that the diffusion process runs forward. Or in other words, the probability of following the geometric structure increases. 

#### Diffusion Distance




#### Connectivity



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

[^2]: Porte, Herbst, Hereman, Walt, *An introduction to Diffusion Maps*

