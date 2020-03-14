---
title: Diffusion Map for manifold learning, Theory and Implementation
categories:
- python
- ML
layout: post
comments: true
---

-----------------------
### Introduction
-----------------------
'Curse of dimensionality' is a well-known problem in Data Science, which often causes poor performance, inaccurate results, and, most importantly, a similarity measure break-down. The primary cause of this is because high dimensional datasets are typically sparse, and often a lower-dimensional structure or 'Manifold' would embed this data. So there is a non-linear relationship among the variables (or features or dimensions), which we need to learn to compute better similarity.

Manifold learning is an approach to non-linear dimensionality reduction. The basis for algorithms in manifold learning is that the dimensionality of many data sets is only artificially high [^1]. In this blog, we learn one of the many techniques in manifold learning called Diffusion Maps. The key idea is that Euclidean Distance, which is the most common measure of similarity, is meaningful only 'locally.' Therefore, assuming there is a lower-dimensional structure or manifold to the data, it would be appropriate to measure similarity over this structure rather than in the Euclidean space itself.

Let us begin exploring with the following example of 2D datapoints neatly arranged in **S** shape. 

![alt](/static/img/Diffusion_Map/original_figA.png)

There is a definite shape to this dataset. Now, if we have to measure the similarity of two points in this set, we measure the Euclidean Distance. If this distance is small, then we say points are similar or if this is large, otherwise. The following figure represents this scenario.

![alt](/static/img/Diffusion_Map/original_figB.png)

However, knowing the geometric structure, we know that this similarity measure is inaccurate. Since there is a non-linear relationship between 'x' and 'y' coordinates, it would be correct if we measure the similarity (or distance) over the very geometric structure itself, as shown in the Figure below.

![alt](/static/img/Diffusion_Map/original_figC.png)

With Diffusion Map, we can do a non-linear dimensionality reduction as well as learn the underlying geometry of the high dimensional data. Let's get straight to the theory and implementation, hand in hand

-----------------------
### What is the takeaway?
-----------------------
This blog aims to introduce one of the manifold learning techniques called **Diffusion Map**[^2]. This technique enables us to understand the underlying geometric structure of high dimensional dataset as well as to reduce the dimensions, if required, by neatly capturing the non-linear relationships between the original dimensions.



-----------------------
### Theory behind (very briefly)
-----------------------

The core idea is a time-dependent diffusion process, which is nothing but a random walk on the dataset where each hop has a probability associated with it. When the diffusion process runs for a time t, we get different probabilities of various paths it can take to calculate the distance over the underlying geometric structure. Mathematically, we call this the steady-state probability of the Markov Chain. 

![alt](/static/img/Diffusion_Map/randomwalk.png)

The connectivity between two data points, x, and y, is defined as the probability of jumping from x to y in one step of the random walk and is

$$
connectivity(x, y) = p(x,y)
$$

However, it is useful to express the connectivity as a row-normalized likelihood function, K using Gaussian Kernel. This will be called **diffusion kernel**

$$
k(x,y) = \exp \left ( 
-\frac{\vert x-y \vert ^2}{\alpha}
\right ) 
$$

Now we define a row-normalized diffusion matrix, P.  Mathematically, this is equivalent to the transition matrix in the Markov chain. While P denotes the probability (or connectivity in this case) of single hopping from point x to point y, P² denotes the probability of reaching y from x in two hops and so on. As we increase the number of hops or Pᵗ for increasing values of t we observe that the diffusion process runs forward. Or in other words, the probability of following the geometric structure increases.

If you would like to dig deeper into the theory behind, the [paper](https://medium.com/r/?url=https%3A%2F%2Finside.mines.edu%2F~whereman%2Ftalks%2FdelaPorte-Herbst-Hereman-vanderWalt-DiffusionMaps-PRASA2008.pdf) has explained it pretty neatly. For a quick overview, [this](https://medium.com/r/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FDiffusion_map) Wikipedia article also explains the theory well.




-----------------------
### Implementation
-----------------------

To demonstrate the algorithm, we begin with a dataset having a definite geometric structure. Let us begin by creating a 2D figure, as shown earlier. Our main aim is to find out whether the diffusion map unravels the underlying geometric structure of data or not.

![alt](/static/img/Diffusion_Map/original_figA.png)

Now, let us add a synthetic 3rd dimension (data drawn from a uniform distribution) to this 2D dataset. Thus our new 3D dataset is as follows

![alt](/static/img/Diffusion_Map/3Dset.gif)

As you might have noticed, the 3D dataset preserves the 'S' shape in one angle, and that is correct. Now our goal is to flatten the dimensions to 2 while preserving this shape. After applying the Diffusion Map, hopefully, we should see the 'S' like structure in 2D.

-----------------------
### Output
-----------------------

![alt](/static/img/Diffusion_Map/01to09.png)  

-----------------------
### Result
-----------------------

As it is evident from the above output figures, with a diffusion map applied to reduce dimension from 3 to 2, we get to understand somewhat the original geometric structure, which is the 'S' shape. With varying values for alpha, we get slightly different variations in the final structure. (alpha is the parameter in diffusion kernel described above).

-----------------------
### Source Code
-----------------------

Source code is available [here](https://medium.com/r/?url=https%3A%2F%2Fgist.github.com%2Frahulrajpl%2F36a5724d0c261b915292182b1d741393) and is open-sourced under MIT License. You can try out the code in Google Colaboratory with the link provided on top of the gist.


-----------------------
### References:
-----------------------
[^1]: Manifold Learning methods in Scikit-Learn (https://scikit-learn.org/stable/modules/manifold.html)

[^2]: Porte, Herbst, Hereman, Walt, *An introduction to Diffusion Maps*

