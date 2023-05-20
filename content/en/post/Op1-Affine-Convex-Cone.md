---
title: "Op1. Affine, convex and cone"
description: "Line, Line segment, Affine combination/Set/Hull, Convex combination/Set/Hull, Conic combination/Set/Hull"
author: "Clifford Chan"
date: "2023-05-12"
featured_image: "/images/cover/ConvexOpCover.PNG"
toc: true
tags: [Optimization]

---

## Line (Type::Set)
 
- Prerequisites：$x_{1} \neq  x_{2}$ are two points in $R^{n}$

- Description in algebra：

    Type Affine: 
    $\\\{y|y = θx_1 + (1 − θ)x_2,  θ ∈ R\\\}$ or
    $\\\{y| y=x_{2}+\theta( x_{1}-x_{2})，θ ∈ R\\\}$ 
- Description in geometry：form the line passing through $x_1$ and $x_2$
    ![Line](/images/Mathfolder/Line-and-LineSegment.PNG)
- Description in statistics：Distribution of average of $x_1$ and $x_2$ vectors with various weight $θ\in R$
- Specially：
    1. Search one point: The parameter value $θ = 0$ corresponds to $y = x_2$, and the parameter value $θ = 1$ corresponds to $y = x_1$
    2. **Describe a line segment**: (closed) line segment between $x_1$ and $x_2$ if $θ \in [0, 1]$ Line segment is a line with normalized weight. 
    - Coding：Draw a line segment in julia:
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

## Affine combination (Type::Vector)

- Prerequisites：Scalar $θ_1,...,θ_k$ where $\sum_i^k\theta_i = 1$
- Description in algebra：$x = θ_1x_1 + · · · + θ_kx_k$ a combination of the points $x_1, . . . , x_k$
- Description in geometry：**A point** based on vectors $x_1, . . . , x_k$
- Description in statistics：Average point of $x_1...x_k$ with weight $θ_1...θ_k \in R$ and $ \sum_i^k\theta_i=1$

## Affine sets (Type::Set)
    
A set $C ⊆ R^n$ is affine if $C$ contains the linear combination of any two points in $C$, provided the coefficients in the linear combination sum to one.
    
- Prerequisites：$\forall x_1,..., x_k ∈ C$, $θ_1,...,θ_k ∈ R$ and $\sum_i^kθ_i=1$
- Description in algebra：$\forall x = \sum_i^kθ_ix_i ∈ C$
- Description in geometry：The line determined by any two points in the set, all points on the straight line passing through the two points belong to this affine set.

### Affine linear subspace
An affine linear subspace is an affine set that also satisfies the requirements of being a vector space, meaning it contains the zero vector (origin) and is closed under addition and scalar multiplication.

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
![Affine linear space](/images/Mathfolder/Affine-linear-subspace.PNG)

Example：

1. If $C$ is an affine set and $x_0\in C$, then the set $V=C-x_0=\{x-x_0|x\in C\}$ is a subspace closed under sums and scalar multiplication. 

    We can imagine that 2-dim plane removes a point. 
    ![answer](/images/Mathfolder/Exercise-Line-Affine.PNG)
    ![V](/images/Mathfolder/V-x-x0.PNG)

_An affine set $C$ is a set obtained by adding the same fixed vector ($x_0$ in picture above) to each point of a vector space($\forall v_i \in V$). $C$ is a result of $l$ translated by $x_0$_

$$
V=\\\{x-x_0|x\in C\\\} \forall x_0 \in C \\\ = \\\{x-x_0|Ax=b\\\}, Ax_0=b \\\ = \\\{x-x_0|A(x-x_0)=0\\\} \\\ = \\\{y|Ay=0\\\}
$$
$V$ is the **null space** of $A$. **$C=\\\{x|Ax=b\\\}$ is a translation of $V$**.

2. Every affine set can be expressed as the solution set of a system of linear equations.

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
### Affine Transformation

An affine transformation is a transformation that is widely used in geometry, which preserves the linear structure of vector spaces while allowing translations. Simply put, an affine transformation is a transformation composed of a linear transformation and a translation.  

In two-dimensional space, an affine transformation can be represented by a 2x3 matrix, or an extended 3x3 matrix (where the third column is [0,0,1]). For a 2D point P(x,y), we can represent an affine transformation using the following equation:
```
[x']   [a, b]   [x]   [tx]
[y'] = [c, d] * [y] + [ty]  
```
Or using the extended 3x3 matrix:   
```
[x']   [a, b, tx]   [x]
[y'] = [c, d, ty] * [y]     
[1]    [0, 0,  1]   [1]
```
Where a, b, c and d are elements of the linear transformation matrix, and tx and ty are the translation vectors. An affine transformation typically includes operations like scaling, rotation, shearing and translation. Affine transformations have wide applications in fields like computer graphics, image processing and computer vision.  

There is a close relationship between affine transformations and affine sets. First, let's understand the definition of an affine set.  

In a vector space, a set is called an affine set if it satisfies the following condition: For any two points A and B in the set, and any real number λ, the point C = λA + (1 - λ)B also lies in the set. In other words, any linear combination of any two points in the affine set still lies in that set.

Now let us explore the relationship between affine transformations and affine sets. An affine transformation is a transformation that preserves the structure of affine sets. That is, if the image (transformed set) of a set under some affine transformation is still an affine set, then that transformation is an affine transformation.

In summary, the relationship between affine transformations and affine sets can be summarized as:

1. An affine transformation is a transformation that preserves the structure of affine sets.    
2. If a set is an affine set, then the image (transformed set) of that set under an affine transformation is also an affine set.

This relationship makes affine transformations widely applicable in fields like computer graphics, image processing and computer vision because they can effectively process and transform affine sets without disrupting their basic structure.

## Affine hull (type::set)
    
 The affine hull is the smallest affine set that contains $C$
    
- Description in algebra：
    $$
    aff C = \\\{θ_1x_1 + · · · + θ_kx_k | x_1, . . . , x_k ∈ C, θ_1 + · · · + θ_k = 1\\\}
    $$
- Description in geometry: Connect the all points in the set $C$. The points "connected by lines" form an affine hull. If there are places where it is impossible to "connect lines", then there are linear independent points in $C$, at which time supplement the zero vector.![Affine-hull](/images/Mathfolder/Affine-hull.PNG)

If a set is an affine set, then affine hull is itself, else affine hull is a set which cantains all combination of all points and itself. For instance $C=\{x_1, x_2\}$ has two points $x_1$ and $x_2$, $C$ is not an affine set, the affine hull is the line through the two points

## convex combination, convex sets, convex hull
    
Subject to the conditions of affine combination, affine set and affine hull, restrict $θ_i ≥ 0$ $θ_i ≥ 0$
图示：![凸集和凸包](/images/Mathfolder/Convex-Convexhull.PNG)

## Cones (type::set)
    
Given a vector, a ray **starting from the origin pointing** in the vector's direction.
    
- Prerequisites：$\forall x \in C, \theta \ge 0$ 
- Description in algebra：$\\\{\theta x\\\} = C$(!!!$0\in C$)

## Conic combination （type::vector）
    
- Prerequisites：$\forall x_i \in C$, $\theta_i \ge 0, i=1,...,k$
- Description in algebra: $x = θ_1x_1 + · · · + θ_kx_k$

## Convex cones （type::set）

- Prerequisites：$\forall x_i \in C$, $\theta_i \ge 0, i=1,...,k$
- Description in algebra: $C=\\\{x|x=\sum_i^k\theta_ix_i \\\}$ $C$ is a Convex cones.($0\in C$)

## Conic hull （type::set）

- Description in algebra：$\{\theta_1x_1+...+\theta_kx_k|x_1,...,x_k \in C, \theta_1,...,\theta_k \ge 0\} $
![ConicHull](/images/Mathfolder/Conic-hull.PNG)

## Summary

$C=\{x_i\}$, $\theta_i \in R$,  where $i=1,...,k$

Linear combination: $x = \sum_i^k\theta_ix_i$

- Restrict $\theta_i \ge 0$ and $\sum_i^k\theta_i=1$ as **Convex Combination**；
- Restrict $\theta_i \ge 0$ as **Conic Combination**；
- Restrict $\sum_i^k\theta_i=1$ as **Affine Combination**.

Sets:
- Convex sets：Set $C = \\\{All\ convex\ combination\ from\ C\\\}$, for instance a line segment.

- Convex cones : Set $C = \\\{All\ conic\ combination\ from\ C\\\}$, for instance a ray.

- Affine sets：Set $C = \\\{All\ affine\ combination\ from\ C\\\}$, for instance a line.

Affine set is convex set. Convex cones is Convex set.

Hull:
- Affine hull: H is an affine hull extend $C$(maybe not affine set) to the smallest affine set $H$

- Convex hull: H is an convex hull extend $C$(maybe not convex set) to the smallest convex set $H$

- Conic hull: H is an conic hull extend $C$(maybe not conic set) to the smallest conic set $H$

## Some simple exanples

- Empty set: affine(hence, convex) subsets of $R^n$
- Single point: affine(hence, convex) subsets of $R^n$
- The whole space $R^n$: affine(hence, convex) subsets of $R^n$


## References
1. [中科大凌青凸优化3/55](https://www.youtube.com/watch?v=WoPpBzG23aY&list=PLex0qwR2dnJh_7351A8HmasW1G-__le_S&index=3)
2. [中科大凌青凸优化4/55](https://www.youtube.com/watch?v=PR6S-FhOOgg&list=PLex0qwR2dnJh_7351A8HmasW1G-__le_S&index=4)
3. _Convex Optimization_ by Boyd,Vandenberg. Chapter 2.1
4. [Linear Programming, Lecture 12. Convexity.](https://www.youtube.com/watch?v=oyQjolvCIDI&t=2890s)
5. Introduction to Linear Optimization by Dimitris Bertsimas, John N. Tsitsiklis. Chapter 2.1

