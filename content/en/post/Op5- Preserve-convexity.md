---
title: "Op5. Operation that preserve convex"
description: "Intersection, Affine Function"
author: "Clifford Chan"
date: "2023-05-19"
featured_image: "/images/cover/ConvexOpCover.PNG"
toc: true
tags: [Optimization]
---

## Intersection

Convexity is preserved under intersection.

- Prerequisites: $S_α$ is convex for every $α ∈ A$
- Description in Algebra:  $\bigcap_{\alpha \in A} S_\alpha$ is convex

## Affine Functions(Linear Map)

Convexity is preserved under affine transformation.

- Definition of affine function: $f:R^n \rightarrow R^m$, $f(x)=A_{m \times n}x_{n \times 1}+b_{m \times 1}$
- Prerequisites: $S ⊆ R^n$ is convex and $f : R^n \rightarrow R^m$ is an affine function.
- Description in Algebra: $\\\{f(x) | x ∈ S\\\}$ is convex.

- Example: 

    1. Solution set of linear matrix inequality is convex: $f(x)=B-A(x)$, $A(x) = x_1A_1 + · · · + x_nA_n \le B$

    $S$ is a convex set
    
    Typical Affine functions: 
    
    2. Scaling: $f(x)=\alpha x$, then $f(S)=\alpha S=\\\{\alpha x|x \in S\\\}$ is convex.
    
    3. Translation: $f(x)=x + a$, then $f(S)=S+a=\\\{x+a|x\in S\\\}$ is convex

    4. Projection onto coordinates: $f(x)=[1,0]x$, then $f(S)=T=\\\{x_1 \in R^m|(x_1, x_2)\in S\subseteq R^m\times R^n for\ some\ x_2 \in R^n\\\}$

    Two sets:

    5. Combination of two sets:If $S_1$ and $S_2$ are convex, then $S_1 \times S_2= \\\{(x,y) | x ∈ S_1, y ∈ S_2\\\}$ is convex.

    6. Sum of two sets: If $S_1$ and $S_2$ are convex, then $S_1 + S_2= \\\{x + y | x ∈ S_1, y ∈ S_2\\\}$ is convex. Because $f(x)=\left[1,1\right] \begin{bmatrix} x \\ y \end{bmatrix}$.

    Geometric shapes: 

    7. Polyhedron: $f(x) = (b − Ax, d − Cx), x \in S$

        $\\\{x | Ax \le b, Cx = d\\\} = \\\{x | f(x) ∈ R^m \times \\\{0\\\}\\\}$ because $b − Ax\ge 0, d − Cx=0$ is convex.
    8. Ellipsoid: $x\in S$, $f(x)=P^{-\frac{1}{2}}(x-x_c)$, $E = \\\{x | (x − x_c)^T P^{−1}(x − x_c)≤1\\\}$


## Reference

1. _Convex Optimization_ by Boyd,Vandenberg. Chapter 2.3
2. [中科大凌青凸优化7/55](https://www.youtube.com/watch?v=x4GzT8lAbMc)
3. [中科大凌青凸优化8/55](https://www.youtube.com/watch?v=yGmAnZ1iNtA&t=179s)
