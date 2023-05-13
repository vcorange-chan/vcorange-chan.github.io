---
title: "Affine and convex sets"
description: "Ch2"
author: ""
date: "20023-05-12"
featured_image: ""

tags: [Optimization]
toc: true
---

- 名词：线 Line (Type::Set)
    
    通俗定义：
    Points of the form $y = θx_1 + (1 − θ)x_2$, where $θ ∈ R$.
    
    属性：
    
    - 成立条件：$x_{1} \neq  x_{2}$ are two points in $R^{n}$
    - 代数描述：

        仿射定义类型 Affine: 
        
        $\{y|y = θx_1 + (1 − θ)x_2,  θ ∈ R\}$ 或$\{y| y=x_{2}+\theta \left( x_{1}-x_{2}\right)，θ ∈ R\}$ 
        
        Line is a set.
    - 几何描述：form the line passing through $x_1$ and $x_2$
    ![Line](/images/Mathfolder/Line-and-LineSegment.PNG)
    - 统计描述： Distribution of average of $x_1$ and $x_2$ vectors with various weight $θ\in R$
    - 例题：
        1. Search one point: The parameter value $θ = 0$ corresponds to $y = x_2$, and the parameter value $θ = 1$ corresponds to $y = x_1$
        2. **Describe a line segment**: (closed) line segment between $x_1$ and $x_2$ if $θ \in [0, 1]$ Line segment is a line with normalized weight. 
    - 代码：
    Draw a line segment:

    ```julia
    using Revise
    using Plots
    function Combine(x1, x2, theta)
        y = theta .* x1 .+ (1-theta) .* x2
        return y
    end

    x1 = [1,0]
    x2 = [0,1] 
    theta = 0.5
    y = Combine(x1, x2, theta)

    scatter([x2[1],y[1]], [x2[2],y[2]], label=["x2" "y"], xlims=(0,2), ylims=(0,2))
    plot = plot!([x2[1],y[1]], [x2[2],y[2]], label="line", xlims=(0,2), ylims=(0,2))
    display(plot)
    wait()
    exit()
    ```

- 名词：仿射组合 affine combination (Type::vector)
    
    通俗定义：We refer to **a point** of the form $θ_1x_1 + · · · + θ_kx_k$, where scalar $θ_1 + · · · + θ_k = 1$, as an affine combination of the points $x_1, . . . , x_k$. 
    
    属性：
    
    - 成立条件：scalar $θ_1 + · · · + θ_k = 1$
    - 代数描述：$x \in \{x \in R^k| x = θ_1x_1 + · · · + θ_kx_k\}$
        
        Affine combination is a vector in a line set.
    - 几何示例：**A point** based on vectors $x_1, . . . , x_k$
    - 统计描述：Average point of $x_1...x_k$ with weight $θ_1...θ_k \in R$ and $ \sum_i^k=1$

- 名词：仿射集 Affine sets
    
    通俗定义：A set $C ⊆ R^n$ is affine if $C$ contains the linear combination of any two points in $C$, provided the coefficients in the linear combination sum to one.
    
    属性：
    
    - 成立条件：$\forall x_1,..., x_k ∈ C$, $θ_1,...,θ_k ∈ R$ and $\sum_i^kθ_i=1$
    - 代数描述：$\sum_i^kθ_ix_i ∈ C$
    - 几何示例：For instance, all the lines defined by all pairs of two points. 任意两点连成的直线也在这个集合之内。
- 名词：凸集 Convex sets
    
关系：

仿射组合构成仿射空间, 平面$P$上由两点位置决定的一条线$l_1$是仿射空间，$l$也是向量空间$P$的子集。空间中三个点相互连线组成的直线$l_2$(1~3条)及其铺开的平面是仿射空间，也是这个空间$P$的子集。空间中两条直线确定的一个平面，由两线上诸点线性组合而成，这个平面也是个仿射空间，构成仿射集合。

而凸集是点间线段构成的，不是直线构成的。仿射集与凸集的关系，类似直线和线段的关系，整体成立（是一条直线），部分一定成立（直线上必有线段），部分成立（存在线段），整体未必成立（未必是条直线）。仿射集的交也是仿射集。仿射集的并未必是仿射集合。仿射集合都是连通集合。


Sure! An affine set is a set that, given any two points in the set, also contains the line segment connecting those two points. An affine linear subspace is an affine set that also satisfies the requirements of being a vector space, meaning it contains the zero vector (origin) and is closed under addition and scalar multiplication.

An example of an affine set that is not an affine linear subspace is a translated line or plane that does not pass through the origin. Consider the following one-dimensional example in a two-dimensional space:

Let's say we have a line L, defined by the equation:

```
y = x
```

This line passes through the origin and is an affine linear subspace. Now, let's translate this line by adding a constant, say 2 units in the y-direction. The translated line L' is given by the equation:

```
y = x + 2
```

L' is an affine set because it still contains the line segment between any two points within it. However, L' is not an affine linear subspace because it does not pass through the origin (0, 0) and is not closed under addition and scalar multiplication with respect to the origin. If you add two points on L' or multiply a point on L' by a scalar, the resulting point may not be on L'.

例题：

1. **仿射集$C$去掉一点，所得集合$V$是$C$的子集，且满足加法数乘封闭。**
If $C$ is an affine set and $x_0\in C$, then the set $V=C-x_0=\{x-x_0|x\in C\}$ is a subspace closed under sums and scalar multiplication. 

    We can imagine that 2-dim plane removes a point. 
![answer](/images/Mathfolder/Exercise-Line-Affine.PNG)

仿射集（Affine set）是一个具有线性结构的集合，它可以看作是一个线性空间（也叫向量空间）平移的结果。一个集合是仿射集，如果它可以表示成一个线性空间的某个点加上该线性空间的所有向量。换言之，仿射集是通过将线性空间的每个点都加上一个固定向量而得到的集合。

更严格地说，设 V 是一个线性空间，x0 是 V 中的一个点，那么对于 V 中的任意点 x，我们可以得到一个向量 v = x - x0。现在考虑 V 中所有这样的向量所组成的集合，我们可以将这个集合表示为 A = {x0 + v | v 属于 V}。可以看到，A 是通过将 V 中的每个点都加上一个固定向量 x0 而得到的集合。这个集合 A 就是一个仿射集。

从这个角度来看，仿射集可以看作是线性空间的一种平移。例如，在二维平面上，一条直线可以看作是一条经过原点的直线（一个线性空间）沿某个向量平移得到的。在这种情况下，直线就是一个仿射集。

2. **线性方程组的解空间是仿射集。**Every affine set can be expressed as the solution set of a system of linear equations.

    The solution of a system of linear equations is the intersection of every equation in geometry. For example, an intersection of line-line can be writen: 
    $$
    \begin{cases}a_{11}x_{1}+a_{12}x_{2}=b_{1}\\
    a_{21}x_{1}+a_{21}x_{2}=b_{2}\end{cases}
    $$
    A line formed by the intersection of two plans:
    $$
    \begin{cases}a_{11}x_{1}+a_{12}x_{2}+a_{13}x_{3}=b,\\
    a_{21}x_{1}+a_{22}x_{2}+a_{23}x_{3}=b_{2}\end{cases}
    $$
    They are all affine set.
    ![Answer2](/images/Mathfolder/Exercise-SolutionSet-Affine.PNG)


$$V=\{x-x_0|x\in C\} \forall x_0 \in C\\=\{x-x_0|Ax=b\}, Ax_0=b\\=\{x-x_0|A(x-x_0)=0\}\\=\{y|Ay=0\}$$
$V$是$A$的化零空间。$C=\{x|Ax=b\}$是$V$的平移。

仿射变换（Affine Transformation）是一种在几何中广泛应用的变换，它既保持了向量空间的线性结构，又允许平移。简单来说，仿射变换是一种通过线性变换和平移组合而成的变换。

在二维空间中，仿射变换可以表示为一个 2x3 矩阵，或者一个扩展的 3x3 矩阵（其中第三列是 [0, 0, 1]）。对于一个二维点 P(x, y)，我们可以使用以下公式表示仿射变换：

```
[x']   [a, b]   [x]   [tx]
[y'] = [c, d] * [y] + [ty]
```

或者使用扩展的 3x3 矩阵表示：

```
[x']   [a, b, tx]   [x]
[y'] = [c, d, ty] * [y]
[1]    [0, 0,  1]   [1]
```

其中，a、b、c 和 d 是线性变换矩阵的元素，tx 和 ty 是平移向量。仿射变换通常包括缩放、旋转、错切和平移等操作。在计算机图形学、图像处理和计算机视觉等领域，仿射变换都有着广泛的应用。

仿射变换和仿射集之间存在密切关系。首先，我们来了解一下仿射集的定义。

在向量空间中，一个集合被称为仿射集（Affine Set）如果满足以下条件：对于集合中的任意两个点 A 和 B，以及任意实数 λ，点 C = λA + (1 - λ)B 也在该集合中。换句话说，仿射集中的任意两点之间的线性组合仍然在该集合中。

现在让我们来探讨仿射变换与仿射集之间的关系。仿射变换是一种保持仿射集结构的变换。也就是说，如果一个集合在某个仿射变换下的像（变换后的集合）仍然是一个仿射集，那么这个变换就是一个仿射变换。

总结一下，仿射变换和仿射集之间的关系可以归纳为：

1. 仿射变换是保持仿射集结构的变换。
2. 如果一个集合是仿射集，那么在仿射变换下，这个集合的像（变换后的集合）也是一个仿射集。

这种关系使得仿射变换在计算机图形学、图像处理、计算机视觉等领域具有广泛的应用，因为它们可以有效地处理和变换仿射集，而不会破坏其基本结构。

- 名词：仿射包 affine hull (type::set)
    
    通俗定义：The affine hull is the smallest affine set that contains $C$
    
    属性：
    
    - 代数描述：The set of all affine combinations of points in some set $C ⊆ R^n$ is called the affine hull of $C$, and denoted $aff C$:
    $$
    aff C = {θ1x1 + · · · + θkxk | x1, . . . , xk ∈ C, θ1 + · · · + θk = 1}
    $$
    - 几何含义: 令集合$C$中离散的点连通起来。补充点"连线"形成仿射包。如果出现无法"连线"的地方，则$C$中存在线性无关的点，此时补充$0$向量。
    
关系：仿射集与仿射包 Affine set and Affine hull
    若一个集合是仿射集，则其仿射包乃之本身。若一集合非仿射集，则其仿射包是各点线性组合所得集合。如$C=\{x_1, x_2\}$只有两点，不是仿射集，其仿射包为$x_1$和$x_2$两点连线组成的线段，是包含$C$本身的最小仿射集。
    If a set is an affine set, then affine hull is itself, else affine hull is a set which cantains all combination of all points and itself. For instance $C=\{x_1, x_2\}$ has two points $x_1$ and $x_2$, $C$ is not an affine set, the affine hull is the closed line segment through the two points

- 名词：凸组合 convex combination 凸集 convex sets 凸包 convex hull
    
    属性：
    
    - 成立条件：在仿射组合，仿射集，仿射包条件基础上，限定 $θ_i ≥ 0$
    - 图示：![凸集和凸包](/images/Mathfolder/Convex-Convexhull.png)
---


- 名词：锥 Cones (type::set)
    
    通俗定义：给定向量，以原点为顶点，向量正方向的射线。
    
    属性：
    
    - 成立条件：$\forall x \in C, \theta \ge 0$ 
    - 代数描述：$\theta x \in C$
    - 几何描述：发于原点确定方向的射线

- 名词：锥组合 conic combination （type::vector）
    
    属性：

    - 成立条件：$θ_1, . . . , θ_k ≥ 0$
    - 代数描述: $x \in \{x|x = θ_1x_1 + · · · + θ_kx_k\}$

- 名词：凸锥 Convex cones （type::set）

    通俗定义：锥上点的凸组合构成的凸集合。

    属性：

    - 成立条件：$\forall x_1, x_2 \in C$, $\theta_1, \theta_2 \ge 0$
    - 代数描述: $\theta_1x_1+\theta_2x_2 \in C$

- 名词：锥包 Conic hull （type::set）

    属性：

    - 代数定义：$\{\theta_1x_1+...+\theta_kx_k|x_1,...,x_k \in C, \theta_1,...,\theta_k \ge 0\} $

总结

$C=\{x_i\}$, $\theta_i \in R$,  where $i=1,...,k$

线性组合: $x = \sum_i^k\theta_ix_i$

- 限定 $\theta_i \ge 0$且$\sum_i^k\theta_i=1$者凸组合；
- 限定 $\theta_i \ge 0$者锥组合；
- 限定 $\sum_i^k\theta_i=1$者 仿射组合

凸集：凸组合的点集=C 线段
凸锥: 锥组合的点集=C 射线
仿射集：仿射组合点集=C 直线

仿射集合一定是凸集。
凸锥一定是凸集。

仿射包 将C扩展形成的最小仿射集D
凸包 将C扩展形成的最小凸集D
锥包 将C扩展形成的最小凸锥D