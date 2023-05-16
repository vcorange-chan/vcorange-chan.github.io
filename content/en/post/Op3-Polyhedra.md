---
title: "Polyhedra"
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
- Description in Algebra: $C = conv\\\{v_0, . . . , v_k\\\} = \\\{θ_0v_0 + · · · + θ_kv_k | θ \ge 0, 1^Tθ = 1\\\}$

单纯形是空间中的子集，
是仿射平面上的线段(给定2个向量，表示1维线段)；
是仿射立体空间上的平面（给定3个向量，表示2维平面）。。。

单纯形是仿射定义的，给了n+1个向量，它们仿射线性独立。仿射线性独立的目的是：单纯形内的点只有唯一一组线性组合。用最低的维数表示单纯形中的点。例如：线段用v1-v0表示，平面用v1-v0和v2-v0表示。

单纯形是线段，三角形，三角体...比所给空间低一个维度，因此仿射A变换单纯形成为单位子空间，分两个部分变换，$A^{nn}=(A_1^{kn} , A_2^{(n-k)n})$.$A_1^{kn}$将三角形$B_{nk}$变换为过原点的三角形，同时只保留有效维度$k \times k$，同时多余的$n-k$维度经过$A_2$变换后为0。

单纯形是凸包，但四边形不是单纯形，因为同一个点可用v1 v2 v3表出，也可以用v1 v2 v4表出。四边形时称单纯形退化。

概率空间是凸的，是单纯形。

证明单纯形是多边形的办法：

