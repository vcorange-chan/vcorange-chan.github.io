---
title: "Hyperplanes, Ball, Ellipsolids, and Norm cones"
description: "Hyperplane, Halfspace, Ball, Ellipsolid, Norm cone"
author: "Clifford Chan"
date: "2023-05-14"
featured_image: "/images/cover/ConvexOpCover.PNG"
toc: true
tags: [Optimization]

---
## Review
The solution set of a linear equation is an affine set.

## Hyperplanes (Type::Set, Affine set)

A kernel space is a affine linear subspace which transformed by vector $a^T$ so that make up the whole space. 

A hyperplane is a affine space(maybe not linear) that transformed from kernel space. 

- Prerequisites: $a ∈ R^n, a \ne 0, and\ b ∈ R$
- Description in Algebra: $ \\\{x | a^T x = b \\\} $ (hence an affine set)
- Description in Geometry: ![OB is Hyperplane](/images/Mathfolder/Hyperplane.PNG) The line $l:=a^Tx=0$ is a hyperplane and the line $l':=a^Tx=b$ is a hyperplane.

In this picture, $a$ is translated linear transformation and $b$ is offset from the origin, also as translating distance $\frac{b}{||a||}$ from the origin. The kernel vectors $ker$ of hyperplane $\\\{x|a^Tx=b\\\}$ are vectors $x-x_0$ ($ker=x-x_0, a^Tker=0$), also vectors parallel to $x \in \\\{x|a^Tx=0\\\}$. So that $ker \in \\\{x|a^Tx=0\\\}$

### motivation
A hyperplane is an (n-1)-dimensional topological plane in an n-dimensional space.

The motivation for defining hyperplanes is to decompose the high dimensional space into lower dimensional structures to simplify computation and understanding. Specifically:

1. Separation. Hyperplanes can separate data points into two half-spaces (above and below). This is useful for classification and clustering.

2. Dimension reduction. Projecting a high dimensional space onto a hyperplane can perform dimension reduction, simplifying subsequent computations.  

3. Partitioning. Hyperplanes can partition different parts of a high dimensional space, thereby partitioning the data.

4. Representation and simplification. Complex data patterns in high dimensional spaces can be represented and simplified using several hyperplanes.  

In short, hyperplanes provide a simple geometric construct that can be used to process and understand data in high dimensional spaces.

For example, in two dimensions, a line is a one-dimensional hyperplane; in three dimensions, a plane is a two-dimensional hyperplane.  

The concept of hyperplanes is widely used in machine learning, especially in support vector machines (SVM), principal component analysis (PCA) and linear regression algorithms.

## Halfspaces (Type::Set, Convex but not affine)

- Prerequisites: $a ∈ R^n, a \ne 0, and\ b ∈ R$
- Description in Algebra: The one is $ \\\{x | a^T x \le b \\\}$ and  the other one $\\\{x | a^T x \ge b \\\}$(closed halfspace)
- Description in Geometry: $OB = b$ ![Halfspaces](/images/Mathfolder/Halfspaces.PNG)

## Euclidean balls (Type::Set, Convex set)

- Prerequisites: $r > 0$, and $||\ ||$ denotes the Euclidean norm, $||u||_2 = (u^T u)^{1/2}$
- Description in Algebra: 
$B(x_c, r)= \\\{x |\ ||x − x_c||_2 ≤ r \\\} = \\\{x | (x − x_c)^T(x − x_c) ≤ r^2 \\\}$ 
- Description in Geometry: $B(x_c, r) = \\\{x_c + ru |\ ||u||_2 ≤ 1 \\\}$

## Ellipsoids (Type::Set, Convex set)

- Prerequisites: $P = P^T ≻ 0$, i.e., $P$ is symmetric and positive definite.
- Description in Algebra: $E = \\\{x | (x − x_c)^T P^{−1}(x − x_c) ≤ 1 \\\}$
- Description in Geometry: $E = \\\{x_c + Au |\ ||u||_2 ≤ 1 \\\}$ where $A$ is square and nonsingular. 

The vector $x_c ∈ R^n$
is the center of the ellipsoid. The matrix $P$ determines how far the ellipsoid extends
in every direction from $x_c$; the lengths of the semi-axes of $E$  are given by $\sqrt{λ_i}$, where
$λ_i$ are the eigenvalues of $P$. A ball is an ellipsoid with $P = r^2I$. $P$ is a weighted matrix.

- Example: $$\varepsilon = \\\{ x| x^{\tau } \begin{bmatrix}
4 & 0 \\\
0 & 1 \\\
\end{bmatrix}^{-1}x\leq 1 \\\}$$ and $x=(x_1,x_2)$
then $\varepsilon=\\\{(x_1,x_2)|\frac{x_1^2}{4}+x_2^2\le1\\\}$ 

## Norm cones (Type::Set, Convex set)

![Norm cones](/images/Mathfolder/Norm-cones.PNG)



## Reference

1. [中科大凌青凸优化5/55](https://www.youtube.com/watch?v=cVH8S94Qcds&t=186s)
2. [中科大凌青凸优化6/55](https://www.youtube.com/watch?v=wXlf3lnSY2w)
3. Convex Optimization by Boyd,Vandenberg
4. Introduction to Linear Optimization by Dimitris Bertsimas, John N. Tsitsiklis. Chapter 2.1