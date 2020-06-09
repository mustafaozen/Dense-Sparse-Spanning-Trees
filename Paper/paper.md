---
title: 'MATLAB codes for finding dense and sparse spanning trees of a given graph'
tags:
  - MATLAB
  - Graphs
  - Dense and sparse spanning trees
  - Genetic algorithm
  - Kruskal's algorithm
  - Discreate optimization
authors:
  - name: Mustafa Ozen
    orcid: 0000-0002-7708-6549
    affiliation: 1
affiliations:
 - name: Department of Electrical and Computer Engineering, New Jersey Institute of Technology
   index: 1
date: 09 June 2020
bibliography: paper.bib
---

# Summary

Finding spanning trees under various constraints is an interesting problem with applications in many fields such as 
Information Technology, Network Design, Systems Biology. Some previous works on this problem can be seen in @Narula:1980,
@Bazlamacci:2001, @Silva:2014, @Ozen:2016, and @Li:2017. Recently, a novel notion of “dense” and “sparse” 
trees, and in particular spanning trees (DST and SST respectively), are introduced [@Ozen:2020] as the structure 
that have a large and small number of subtrees, or a small and large sum of distances between vertices, respectively. 
We show that finding DST and SST reduces to solving the following discrete optimization problem, which is one of 
the proposed methods in the paper (Model 2):

\begin{equation}
\label{eq:Eq1}
	\begin{aligned}
		& \underset{\vec{h}}{\text{min}} \text{	Objective Function}(\vec{h}^{*}) \\
		\text{subject to}& \\
		& h_i \in \{1,2,\dots,|E(G)|\} \subset \mathbb{Z}^{+}, i = 1,\dots,N^{*},  \\
		& h_i \neq h_j, \forall i \neq j, \\
		& \vec{h} \text{ containing at least one edge adjacent to each } v \in V(G), \\
		& \vec{h}^{*} = \text{ Kruskal}(\vec{h}).
	\end{aligned}
\end{equation}

where $G$ is the given graph, $E(G)$ is the edge set of $G$, $V(G)$ is the vertex set of $G$. Basically, we search 
for an $(N \− 1)$-dimensional vector $\vec{h}$ with unique integer components $h_i$ such that $\vec{h}^{*}$ constructed 
using Kruskal’s algorithm from $\vec{h}$ has the optimal objective function value. 

The advantage of \autoref{eq:Eq1} is the fact that we narrow down the search space and reduce the cost of checking if 
the selected $\vec{h}$ is a tree that is guaranteed by the Kruskal’s algorithm. It can be applied to any connected, 
directed or undirected, weighted or unweighted, large or small graphs efficiently. Furthermore, with additional 
constraints, it can be applied recursively to sub-trees or spanning trees to further investigate the graphical properties 
of the graph and/or network. Computational results show that \autoref{eq:Eq1} performs faster than previously proposed 
heuristic methods and more efficient on large graphs with hundreds of vertices and edges. Several applications of 
the method to different networks such as cancer cell gene network, brain network, social networks, and so on, are 
presented in @Ozen:2020.

In this paper, our goal is to provide the source MATLAB codes of \autoref{eq:Eq1}. With the help of the comment lines 
provided within the "main.m" file, it is very easy to apply it to the datasets other than the ones included in the source 
files. We provide the datasets used in the paper, which were obtained from @Rossi:2015. By default, the code generates 
an optimal dense spanning tree that is the so-called star in \autoref{fig:fig1}B of a randomly generated graph in 
\autoref{fig:fig1}A as an introductory example. We believe that these source codes can be used by other scientists to 
analyze various types of other graphs or networks constructed in many different fields to further investigate their 
properties. 

![Introductory example and the default output of the code. A) The randomly generated graph. 
B) The optimal dense spanning tree. \label{fig:fig1}](fig1.png)

# Acknowledgements

I acknowledge contributions from Dr. Goran Lesaja and Dr. Hua Wang for their help and support on developing theoretical
background of this project.

# References
