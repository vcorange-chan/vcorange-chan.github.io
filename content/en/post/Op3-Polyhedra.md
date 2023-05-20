---
title: "Op3. Polyhedra"
description: "Polyhedra, Simplex"
author: "Clifford Chan"
date: "2023-05-14"
featured_image: "/images/cover/ConvexOpCover.PNG"
toc: true
tags: [Optimization]

---

## Polyhedra (Type::Set, Convex set)

The solution set of a finite number of linear equalities
and inequalities

- Description in Algebra: $P = \\\{x | a^T_j x ≤ b_j, j = 1, . . . , m, c^T_j x = d_j, j = 1, . . . , p\\\}$
- Description in Geometry: $P = \\\{x | Ax .\le b, Cx = d\\\}$
![Polyhedra](/images/Mathfolder/Polyhedra.png)
- Example: 

    Affine sets (e.g., subspaces, hyperplanes, lines), rays, line segments, and halfspaces are all polyhedra.

    A system of linear inequation is a Polyhedra 
    $$
    \begin{cases}A,x\geq B_{1}\\\
    A _{2}x\leq B_{2}\\\
    A_{3}x=B_{3}\end{cases}
    $$


## Simplex (Type::set, Convex set)

- Prerequisites: $k + 1$ points $v_0, . . . , v_k ∈ R^n$ are affinely independent, which means $v_1 − v_0, . . . , v_k − v_0 are linearly independent. 
- Description in Algebra: 
$C = conv \\\{v_0, . . . , v_k \\\} = \\\{θ_0v_0 + · · · + θ_kv_k | θ \ge 0, I^Tθ = 1 \\\}$
- Description in Geometry:  

    ![Simplex](/images/Mathfolder/Simplex.PNG)
    Simplex shapes are line, triangle, tetrahedron, Simplex is a Convex Hull.

But quadrilateral is not a simplex shape because the same polygon can be formed with different combinations of vertices (e.g. $v_1- v_0$, $v_2-v_0$, $v_3-v_0$ or $v_1-v_0$, $v_2-v_0$, $v_4-v_0$). (degenerate)

- Description in Statics:
    
    Vectors in the probability simplex correspond to probability distributions on a set with n elements, with $x_i$ interpreted as the probability of the $ith$ element.

$v_1 - v_0, . . . , v_k - v_0$ are linearly independent in order to ensure each point can be formed by a combination uniquely.

- Question: Prove simplex is a polyhedra.

## Reference

1. [中科大凌青凸优化6/55](https://www.youtube.com/watch?v=wXlf3lnSY2w)
2. [中科大凌青凸优化7/55](https://www.youtube.com/watch?v=x4GzT8lAbMc)
3. _Convex Optimization_ by Boyd,Vandenberg. Chapter 2.2