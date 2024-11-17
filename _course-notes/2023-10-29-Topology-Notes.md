---
layout: article
tag: notes
title: "Notes: Topology"
mathjax: true
excerpt_type: html
location: "Songhua River, Jilin, China, Jan 2024"
show_location: true
article_header:
  type: overlay
  theme: dark
  background_color: '#203028'
  background_image:
    gradient: 'linear-gradient(135deg, rgba(34, 139, 87 , .4), rgba(139, 34, 139, .4))'
    src: /assets/images/cover/DSC_0988.JPG
---

2023秋数学系《拓扑学》笔记，教师：宗正宇

Notes of DMS *Topology* course, Autumn 2023, taught by Prof. Zhengyu Zong. <!--more-->

P is called a **limit point** of A, if every neighborhood of P contains at least one point of $A-\{P\}$.

Zariski topology: A subset of $X = \mathbb{C}$ is open, if its complement is finite of $X$. Let $f(t) \in \mathbb{C}[t]$ be a polynomial $\Rightarrow$ $f(t) = a(t-a_1)(t-a_2)\cdots(t-a_n)$ with $a_1,a_2,\cdots,a_n \in\mathbb{C}$.

- $A\subset X$ is closed $\Leftrightarrow$ $\lvert A\rvert$ is finite or $A=X \Leftrightarrow A$ is the zero locus of some $f(t) \in \mathbb{C}[t]$.
- If $\lvert A\rvert$ is finite then $A$ has no limit point; if $\lvert A\rvert$ is infinite, then $\forall p \in X$ is a limit point of $A$.

- More generally, we can define Zariski topology on $\mathbb{C}^n$. A subset $A \subset \mathbb{C}^n$ is closed iff $A$ is the zero locus of some polynomials $f_1,f_2,\cdots,f_m \in \mathbb{C}[t_1,t_2,\cdots,t_n]$.

*Thm.* A set if closed iff it contains all its limit points

*Def.* The union of $A$ and all its limit points is called the **closure** of A, and is denoted by $\bar A$.

*Thm.* $\bar A$ is the smallest closed set containing $A$. In other words $\bar A = \bigcap_{B\supset A, B \text{ is closed}} B$. ($\Leftrightarrow$ $\bar A$ is closed and for any closed set $B \supset A$ we always have $A\subset \bar A \subset B$.)

*Cor.* Let $A\subset X$, then $A$ is closed iff $A=\bar A$.

*Def.*

- $A\subset X$ is called **dense** in $X$ if $\bar A = X$.

- $x\in A$ is an interior point of $A$ is $\exists$ a neighborhood $U$ of $x$ s.t. $U\subset A$. Interior of A: $\mathring{A} = \{x\in A: x \text{ is an iterior point of $A$}\}$.
- $x\in X$ is a frontier(boundary) point of $A$ is $x$ is neither an interior point of $A$ nor an interior point of $X\setminus A$.

*Def.* Let $\beta$ be a collection of some open subsets of $X$, suppose every open set in $X$ is a union of members of $\beta$, then $\beta$ is called a basis of $X$ and elements in $\beta$ are called basic open sets.

*Thm.* Let $X$ be a set and let $\beta$ be a nonempty collection of subsets of $X$. Suppose $\bigcup_{B \in\beta}B = X$, and $\forall B_1,B_2 \in \beta, \forall x\in B_1\cap B_2$, $\exists B_3 \in\beta$ s.t. $x\in B_3 \subset B_1\cap B_2$. Define the open subsets of $X$ to be the arbitrary unions of members in $\beta$, then this gives a topology on $X$.

### Continuous function

*Def.* $f:X\to Y$ is continuous $\Leftrightarrow$ $f^{-1}(\text{open}) = \text{open}$.

*Thm.* Let $f:X\to Y, g:Y\to Z$ be continuous, then $g\circ f: X\to Z$ is continuous.

*Thm.* Let $f:X\to Y$ be continuous and let $A\subset X$ have the subspace topology, then $f\vert_A:A\to Y$ is continuous.

*Thm.* The followings are equivalent:

1. $f:X\to Y$ is continuous
2. If $\beta$ is a basis for the topology of $Y$, the inverse image of every member of $\beta$ is open in $X$.
3. $f(\bar A) \subset \overline{f(A)}$ forall $A\subset X$.
4. $\overline{f^{-1}(B)} \subset f^{-1}(\overline B)$ forall $B \subset Y$.
5. $f^{-1}(A)$ is closed for any closed set $A\subset Y$.

*Def.* $f:X\to Y$ is a **homeomorphism** if $f$ is continuous and $\exists g:Y\to X$ continuous s.t. $f\circ g = id$ and $g\circ f = id$. 同胚

*Remark.* If $f:X\to Y$ is continuous and bijective, $f$ doesn't need to be a homeomorphism (the inverse may not be continuous)

*Theorem.* (Local formulation of continuity) (1) $f:X\to Y$ is continuous if $X$ can be covered by open sets $U_\alpha$ (i.e. $X \subset \bigcup_\alpha U_\alpha$) such that $f\vert_{U_\alpha}$ is continuous for all $\alpha$. (Infinite open covering)

(2) $f:X\to Y$ is continuous if $X = \bigcup_{i=1}^n F_i$, $F_i$ closed for all $i$ and $f\vert_{F_i}$ is continuous for all $i$. (finite closed covering)

### Limit

Let $X$ be a set and let $\beta$ be collection of subsets of $X$ s.t. (1)$\forall B \in \beta, B\ne \varnothing$; (2) $\forall B_1,B_2 \in \beta$, $\exists B_3 \in \beta$ s.t. $B_3 \subset B_1\cap B_2$. Then $\beta$ is called a basis of the set $X$.

*Def.* Let $f:X\to Y$ be a map of a set $X$ with a basis $\beta$ to a topological space $Y$. The point $p\subset Y$ is called the limit of $f$ over basis $\beta$ if for all neighborhood $V$ of $p$, $\exists A \in \beta$ s.t. $f(A) \subset V$, we denote this by $\lim_\beta f(x) = p$.

### Metric Space extension

For metric space $X$, subset $X\subset A$, $f:A\to \mathbb{R}$ is continuous. Q: Can we extend $f$ to the space $X$ continuously?

- In general, no

*Def.* Let $d$ be the metric on $X$ and $A\subset X$. For all $x\in X$ define $d(x,A) = \inf_{a\in A}d(x,a)$.

*Lemma.* The function $x\mapsto d(x,A)$ is continuous

*Lemma.* $A,B\subset X$ closed and $A\cap B = \varnothing$. Then $\exists f:X\to\mathbb{R}$ continuous s.t. $f\vert_A = 1, f\vert_B = -1$ and $f(X \setminus (A\cup B)) \subset (-1,1)$.

*Theorem. (Tietze extension theorem)*. Let $X$ be a metric space and $C\subset X$ closed. If $C\to \mathbb{R}$ is continuous, then $f$ can be extended to $X$ continuously.

### Complete metric space

Let $(X,d)$ be a metric space,

*Def.* A sequence $\{x_n \vert n\ge 1\}$ of points in $X$ is called a Cauchy sequence if for all $\epsilon > 0$ $\exists N$ s.t. $d(x_m,x_n) < \epsilon$ for all $m,n>N$.

*Def.* A sequence $\{x_n\}$ of points in $X$ converges to a point $a\in X$ if $\lim_{n\to\infty} d(a,x_n) = 0$. The point $a$ is called the limit of $\{x_n\}$.

*Def.* A metric space $(X,d)$ is called complete if every Cauchy sequence is convergent.

Ex1. Continuous function set $C[a,b]$ with metric $d(f,g) = \max_{a\le x\le b}\lvert f(x) - g(x)\rvert$ is complete.

Ex2. Continuous function set $C[a,b]$ with metric $d(f,g) = \int_a^b \lvert f-g\rvert d x$ is not complete

Completion of a metric space: Let $(X,d)$ be a metric space. We want to find a "smallest" complete metric space $(Y,d)$ s.t. $X\subset Y$.

*Def.* If $(X,d)$ is a subspace of $(Y,d)$ which is complete and $X$ is dense in $Y$. Then $(Y,d)$ is called the **completion** of $(X,d)$.

*Def.* We say that the metric space $(X_1,d_1)$ is isometric to $(X_2,d_2)$ if $\exists$ bijection $f:X_1 \to X_2$ s.t. $d_2(f(a),f(b)) = d_1(A,b)$ for all $a,b\in X_1$. The map $f$ is called an **isometry**.

*Lemma.* Let $(X,d)$ be a matrix space and $a,b,u,v\in X$. Then $\lvert d(a,b) - d(u,v)\rvert \le d(a,u) + d(b,v)$

*Thm.* **(Uniqueness of Completion)** If $(Y_1,d_1)(Y_2,d_2)$ are completions of $(X,d)$, then $(Y_1,d_1)$ is isometric to $(Y_2,d_2)$.

*Thm.* **(Existence of Completion)** If we identify two isometric metric space, then every metric space has a completion.

## Compactness

Heine-Borel Theorem: $I = [a,b]\subset \mathbb{R}$ is closed interval. Let $I \subset \bigcup_\alpha U_\alpha$ open in $\mathbb{R}$, then $\exists U_1,U_2,\cdots, U_n \subset\{U_\alpha\}$ s.t. $I \subset \bigcup_{i=1}^n U_i$.

Generalization: *Def.* Let $X$ be a topological space, $X$ is called compact if for any open covering $X = \bigcup_\alpha U_\alpha, U_\alpha \subset X$ open, we can find a finite covering $X = \bigcup_{i=1}^n U_i$.

A subset $A\subset X$ is called a compact set if $A$ is compact with the subspace topology induced from $X$.

**Main Theorem.** A subset $X\subset \mathbb{R}^n$ is compact id and only if $X$ is closed and bounded.

### Properties

- Let $f:X\to Y$ be continuous. If $X$ is compact, then $f(X)$ is a compact subset of $Y$.
  - proof: use the property that $f^{-1}$(open) is open.
- Let $C\subset X$ be a closed subset. If $X$ is compact, then $C$ is compact.
  - proof: if $C = \bigcup U_\alpha$, then $X = \bigcup U_\alpha \cup (X\setminus C)$ can be finitely covered $\Rightarrow C$ can be finitely covered by $\bigcup U_n$.
- *Def.* A topological space $X$ is called a **Hausdorff** space if $\forall x_1\ne x_2 \in X$, $\exists$ neighborhoods $U_1$ of $x_1$, $U_2$ of $x_2$ s.t. $U_1 \cap U_2 = \varnothing$.
- *Theorem.* Let $f:X\to Y$ be a map from a set $X$ to a Hausdorff space $Y$. Let $\beta$ be a basis of $X$. If $\lim_\beta f(x)$ exists  then it is unique.
  - proof: Two distinct limit points -> exists non-overlapping neighborhoods $V_1,V_2$. $\exists  B_1,B_2 \in \beta$ s.t. $f(B_1) \subset V_1, f(B_2) \subset V_2$ while $B_1\cap B_2 \ne \varnothing$.
- *Theorem.* A compact subset of a Hausdorff space is closed.
  - proof. For compact subset $A$ of Hausdorff space $X$. Let $x\notin A$, for all $z\in A$, we can find neighborhood $U_z,V_z$ of $x,z$. $A$ compact => $A \subset \bigcup_{i=1}^n V_{z_i}$. Define $U_\alpha = \bigcup_{i=1}^n U_{z_i}$ => $U_\alpha \cap A = \varnothing$, and $U_\alpha$ is a neighborhood of $x$ => $X\setminus A = \bigcup_{x\in X\setminus A}U_\alpha$ is open => $A$ is closed.
- *Theorem.* Let $f:X\to Y$ be continuous and bijective. If $X$ is compact and $Y$ is Hausdoff then $f$ is a homeomorphism.
- *Theorem.* An infinite subset of compact space must have a limit point.
- *Theorem.* Let $A\subset \mathbb{R}^n$ be compact, then $A$ is closed ($\mathbb{R}^n$ is Hausdoff) and bounded (can be finite covered by open balls).
- *Theorem.* Let $f:X \to \mathbb{R}$ be continuous, if $X$ is compact then $f$ is bounded and attains its bounds.
  - proof: $f(X)\subset \mathbb{R}$ is compact (bounded and closed)
- Lebesgue's Lemma: Let $X$  be a compact metric space and $X = \bigcup_\alpha U_\alpha$ an open covering. Then $\exists \delta > 0$ (called a Lebesgue number of $\{U_\alpha\}$) s.t. any subset of $X$ of diameter less than $\delta$ is contained in some $U_\alpha$.

### Product Topology

Product topology: X, Y $\to X\times Y$. $U\times V$ is open if $U$ is open in $X$, and $V$ is open in $Y$.

- projection: $p_1(x,y) = x, p_2(x,y) = y$
- The product topology is the smallest topology to make $p_1,p_2$ continuous.

*Theorem.* $f:Z\to X\times Y$ is continuous $\Leftrightarrow$ $p_1\circ f:Z\to X$ and $p_2\circ f:Z\to Y$ are continuous.

- proof. $f^{-1}(U\times V) = (p_1\circ f)^{-1}(U) \cap (p_2\circ f)^{-1}(V)$ is open

*Theorem.* $X,Y\ne \varnothing$, $X\times Y$ is Hausdoff $\Leftrightarrow$ $X,Y$ are Hausdoff.

- Necessity: $(x_1,y)(x_2,y)$ has non-overlapping neighborhood $\Rightarrow$ $X$ is Hausdoff;
- Sufficiency: We may assume $x_1 \ne x_2$ $\Rightarrow$ Non-overlapping neighborhoods $U_1,U_2$, then $(U_1\times V)\cap (U_2\times V) = \varnothing$

*Lemma.* Let $\beta$ be a basis of a topological space $X$, then $X$ is compact $\Leftrightarrow$ For any open covering $X = \bigcup_\alpha B_\alpha, B_\alpha \in \beta$, there exists $B_1,B_2,\cdots,B_n\in\{B_\alpha\}$ s.t. $X = \bigcup_{i=1}^n B_i$.

*Theorem.* $X,Y\ne \varnothing$, $X\times Y$ is compact $\Leftrightarrow$ $X,Y$ are compact.

- Necessity: Let $p_1:X\times Y\to X, p_2:X\times Y \to Y$ be projections, then $X = p_1(X\times Y), p_2(X\times Y)$. Note $p_1,p_2$ are continuous and $X\times Y$ is compact, so $X,Y$ are compact.
- Sufficiency:

Sufficiency of main theorem: $X\subset \mathbb{R}^n$ is closed and bounded, then $X$ is compact.

- proof. $\exists M>0$ s.t. $X\subset [-M,M]^n$. By Heine-Borel Theorem, $[-M,M]$ is compact $\Rightarrow$ $[-M,M]^n$ is compact. Since $X$ is closed $\Rightarrow$ $X$ is closed in $[-M,M]^n \Rightarrow$ $X$ is compact.

### Infinite Product

box topology

product topology

## Connectedness

Intuitions:"connected": $X=A\cup B$ and $\bar A \cap B \ne \varnothing, A\cap\bar B\ne \varnothing$.

"path-connected": for $p,q\in X$, $\exists f:I\to X$  continuous s.t. $f(0) = p,f(1)=q$. (Sufficient of connectedness)

*Theorem.* The following conditions are equivalent:

- $X$ is connected.
- The only subsets of $X$ which are both open and closed are $X$ and $\varnothing$.
- $X$ cannot be expressed as the union of two disjoint open sets.

(1)=>(2): $A\subset X$ is open and closed, then $B=X\setminus A$ is too. $A=\bar A,B=\bar B$ and so $A\cap \bar B = \bar A\cap B = \varnothing$, then $A=X$ or $A = \varnothing$.

(2)=>(3): $X=A\cup B$, $A,B$ open => closed, then $A=X$ or $A=\varnothing$.

(3)=>(1):

*Theorem.* $\mathbb{R}$ is connected.

*Theorem.* The continuous image of a connected space is connected.

$Z\subset X$ dense and $Z$ is connected, then $X$ is also connected.

*Theorem.* $\varnothing \ne X \subset R$ is connected $\Leftrightarrow$ $X$ is an interval.

### Path Connnectedness

*Theorem.* A path connected space is connected.

*Theorem.* A connected open subset of a Euclidean space is path-connected.

## Identification Spaces

$\mathbb{R}P ^2$: real projective plane

glue opposite points on a circle

orientable

*Def.* Let $X$ be a topological space and let $X = \bigcup_{i\in I} P_i$, $P_i$ are disjoint and not empty. Let $Y = \{P_i \vert i \in I\}$ and let $\pi : X\to Y, \pi (x) = P_i$ if $x\in P_i$. Define a topology on $Y$ s.t. $U\subset Y$ is open $\Leftrightarrow$ $\pi^{-1}(U) \subset X$ is open.

This topology is called the identification topology on $Y$, and $Y$ is called the identification space associated with the partition $X = \bigcup_{i\in I}P_i$.

*Theorem.* Let $Y$ be an identification space of $\pi:X\to Y$ and let $z$ be a topological space. A map $f:Y\to Z$ is continuous iff $f\circ \pi: X\to Z$ is continuous.

*Def.* Let $f:X\to Y$ be surjective and continuous. Suppose $U\subset Y$ is open $\Leftrightarrow$ $f^{-1}(U) \subset X$ is open. Then we call $f$ an identification map.

*Theorem.* Let $f:X\to Y$ be surjective and continuous. If $f$ maps open sets of $X$ to open sets of $Y$, or closed sets to closed sets, then $f$ is an identification map.

- proof. Suppose f(open) = open, let $U \subset Y$ s.t. $f^{-1}(U) = X$ is open. Then since $f$ is surjective, $f(f^{-1}(U)) = U$, then $U$ is open in $Y \Rightarrow U\subset Y$ is open iff $f^{-1}(U) \subset X$ is open (i.e. continuous). So $f$ is an identification map.

*Cor.* Let $f:X\to Y$ be continuous and surjective. If $x$ is compact and $Y$ is Hausdoff, then $f$  is an identification map.

- proof. Let $A\subset X$ be closed $\Rightarrow$ $A$ is compact $\Rightarrow$ $f(A) \subset Y$ is compact.
- $Y$ is Hausdoff $\Rightarrow f(A)\subset Y$ is closed. By the theorem above, $f$ is an identification map.

*Theorem.* Let $f:X\to Y$ be a map s.t. $f_{X_\alpha}$ is continuous for all $\alpha$. If $j:\tilde X \to X$ is an identification map, then $f$ is continuous.

- proof. Since $j$ is an identification map, $f$ is continuous $\Leftrightarrow f\circ j : \bigcup_\alpha X_\alpha \to Y$ is continuous $\Leftrightarrow f\circ j\vert_{X_\alpha}$ is continuous i.e. $f_{X_\alpha}$ is continuous.

### Construction of $\mathbb{R}P^n$

- $\mathbb{R}P^n$ is the identification space of $R^{n+1}\setminus \{0\}$ which identifies points on the same straight line through the origin.
- Let $B^n$ be the n-dimensional unit ball. Identify antipodal points of its boundary -> get $\mathbb{R}P^n$.

The construction gives us te construction of the complex projective space $\mathbb{C} P^n$, by identifying points in $\mathbb{C}\setminus \{0\}$ which lie in the same 1-d $\mathbb{C}$-linear subspace of $\mathbb{C}^{n+1}$.

*Example.* (1) **(Cone)** Let $X$ be a topological space and $I=[0,1]$. Let $CX = (X\times I) / (X \times \{1\})$, which is the identification space which idetifies $X\times \{1\}$ to a point. $CX$ is called a cone.

(2) **(Suspension)** Let $X$ be a topological space, let $SX$ be the identification space of $X\times I$ which identifies $X\times \{0\}$ to a point and identifies $X\times \{1\}$ to another point.

(3) **(Wedge Sum)** Let $X,Y$ be topological spaces, and let $x_0 \in X, y_0 \in Y$. Identify $x_0$ and $y_0$ to a single point in $X\sqcup Y$, we obtain $X\vee Y$ called wedge sum of $X,Y$.

(4) **(Attaching maps)** Let $A\subset Y$ be a subspace and $f:A\to X$ a continuous map. Consider the identification space from $X\sqcup Y$ which identifies $a$ and $f(a)$ for all $a\in A$. This identification space is denoted by $A\cup_f Y$, and $f$ is called attaching map.

(5) **(Mappping Cones)** Let $f:X\to Y$ be a map. The mapping cone $C_f = Y \cup_f CX$ is obtained by attach $X\times\{0\} \subseteq (X\times I) / (X\times \{I\}) = CX$ to $Y$ via $f$.

## Topological Group

*def.* A topological group $G$ is both a (Hausdoff) topological space and a group, such that multiplication $m:G\times G\to G, (g_1,g_2)\mapsto g_1g_2$ is continuous, and inverse $i:G\to G, g\mapsto g^{-1}$ is continuous.

Let $G_1,G_2$ be two topological groups, $f:G_1\to G_2$ is called an isomorphism if $f$ is a homeomorphism and $f$ is an isomorphism of groups. If $G$ is a topological group and $H\subseteq G$ is a subgroup. Equip $H$ the subspace topology, then $H$ is a topological group .

*Example.* (1) $(\mathbb{R}^n, +)$ is a topological group.

(2) Let $S^1 = \{e^{2\pi i \theta} : 0\le \theta < 1\}$ is a topological group.

(3) Let $T$ be the torus, $T = S^1\times S^1$ is a topological group.

(4) $GL(n,\mathbb{R}), SL(n,\mathbb{R}), O(n), SO(n)$ are topological groups.

Let $G$ be a topological group and $x\in G$. Define $L_x:G\to G$ with $L_x(g) = x\cdot g$. $L_x$ is called left translation by $x$, then $L_x$ is bijective.

$L_x$ is continuous and similarly $L_{x^{-1}}$ is continuous and is the inverse of $L_x$, so $L_x$ is a homeomorphsim ($L_{x_1x_2} = L_{x_1}\circ L_{x_2}, L_e = id_G$)

Let $R_x:G\to G, R_x(g) = g\cdot x$ called the right translation, then $R_x$ is also a homeomorphism.

*Thm.* Let $G$ be a topological group and let $K$ be the connected component of $G$ which contains the identity $e\in G$. Then $K$ is a closed normal subgroup of $G$.

- proof.

*Thm.* In a connected topological group $G$, any neighborhood of $e\in G$ is a set of generators of $G$.

- proof. Let $e\in U\subseteq G$ be a neighborhood of $e$. Let $K = \langle U\rangle$. For all $g\in K, g\cdot U = L_g(U) \subseteq K$ since $L_g$ is a homeomorphism. $L_g(U)$ is a neighborhood of $g$.

- For all $g \in G\setminus K$, consider $g\cdot U$. Suppose $(gU) \cap K \ne \varnothing$, let $h\in (gU)\cap K$, there exsits $g' \in U$ s.t. $gg' = h$, so $g = h(g')^{-1}$ thus $g \in K$.
- So $gU$ is a neighborhood of $g$ in $G\setminus K$.

### Matrix Groups

$Mat_{n\times n}(\mathbb{R}) = \{n\times n \text{ real matrices}\} \simeq \mathbb{R}^{n^2}.$ not a group under multiplication.

$GL(n,\mathbb{R}) = \{M \in Mat_{n\times n}(\mathbb{R}) : \det M \ne 0\} \subseteq \mathbb{R}^{n^2}$ is open.

$SL(n,\mathbb{R}) = \{m \in GL(n,\mathbb{R}) : \det M = 1\}, SL(n,\mathbb{R}) \subseteq GL(n,\mathbb{R})$ is a subgroup.

- $SL(n,\mathbb{R})$ is not compact since it's an unbounded subset of $\mathbb{R}^{n^2}$.
- $SL(n,\mathbb{R})$ is connected

$O(n) = \{M \in GL(n,\mathbb{R}) : M^TM = I\} \subset GL(n,\mathbb{R})$ is a subgroup

$SO(n) = \{M \in O(n) : \det M = 1\} \subset SL(n,\mathbb{R})$ is a subgroup.

### Group Action and Quotients

*Def.* Let $G$ be a topological group and let $X$ be a topological space. A $G$-action on $X$ is a map $G\times X \to X$ as $(g,x)\mapsto g\cdot x$ s.t.

(1) $f$ is continuous

(2) $(hg) x = h(gx)$

(3) $e\cdot x = x, \forall x\in X, e \in G$ identity

For $\forall x,y\in X$, define an equivalence relation $x\sim y$ if $\exists g\in G$ s.t. $x = gy$

1) $x\sim x$ since $x = ex$
2) $x\sim y\Rightarrow \exists g, x = gy \Rightarrow y = g^{-1}x \Rightarrow y \sim x$.
3) $x\sim y, y \sim z \Rightarrow x = gy = g(hz) = (gh)z \Rightarrow x\sim z$.

Then $\sim$ gives a partition of $X$: The $G$-orbits. Let $X/G$ be the identification space associated with this partition. $X/G$ is called the quotient space or the orbit space.

- Example: Let lattice $\Lambda = \mathbb{Z} \cdot v_1 \oplus \mathbb{Z}  \cdot v_2 \cong \mathbb{Z} ^2$, then torus is homeomorphic to $\mathbb{R}^2 / \Lambda$.

### Projective Space

Ex. (projective space) Let $S^n \subseteq \mathbb{R}^{n+1}$ be the unit sphere, $\mathbb{Z} /2\mathbb{Z}  = \{1,-1\}$. Define an action $\mathbb{Z} /2\mathbb{Z}  \curvearrowright S^n$, then $S^n / (\mathbb{Z}  / 2\mathbb{Z}) = \mathbb{R}P^n$. Let $\mathbb{R}^\ast - \mathbb{R}\setminus\{0\}$. Define an action $\mathbb{R}^\ast \curvearrowright (\mathbb{R}^{n+1}\setminus\{0\})$ as $\lambda \cdot (x_1,\cdots, x_{n+1}) := (\lambda x_1,\cdots, \lambda x_{n+1})$ for $\lambda \in \mathbb{R}^\ast$ and $(x_1,\cdots,x_{n+1}) \in \mathbb{R}^{n+1}\setminus\{0\}$.

We can see $(\mathbb{R}^{n+1} \setminus\{0\}) / \mathbb{R}^\ast = \mathbb{R}P^n = \{[x_1 : x_2: \cdots : x_n] \vert (x_1,\cdots, x_n) \in \mathbb{R}^{n+1}\setminus\{0\} \}$. (homogeneous coordinates)

There are $(n+1)$ canonical charts of $\mathbb{R}P^n$. Let $U_i \subseteq \mathbb{R}P^n, U_i = \{[x_1:\cdots :x_{n+1}] \in \mathbb{R}P^n \vert x_i \ne 0\} \subseteq \mathbb{R}P^n$ is open. Then $U_i$ is hemeomorphic to $\mathbb{R}^n$, and $\{U_i\}_{i=1}^{n+1}$ is an open covering of $\mathbb{R}P^n$.

Let $\mathbb{C}^\ast = \mathbb{C} \setminus \{0\}$, define an action $\mathbb{C}^\ast \curvearrowright \mathbb{C}^{n+1}\setminus \{0\}$, $\lambda (x_1,x_2,\cdots,x_{n+1}) = (\lambda x_1,\cdots, \lambda x_{n+1}) \Rightarrow (\mathbb{C}^{n+1} \setminus \{0\}) / \mathbb{C}^\ast = \mathbb{C} P^n$ is the complex projective space. Let $U_i = \{[x_1:x_2:\cdots:x_{n+1} \in \mathbb{C} P^n \vert x_i \ne 0\}\subseteq \mathbb{C} P^n$ for $i=1,2,\cdots, n+1$. Then $U_i$ is homeomorphic to $\mathbb{C}^n$ and $\{U_i\}_{i=1}^{n+1}$ is an open covering of $\mathbb{C} P^n$.

Zariski topology on $\mathbb{C} P^n$.

Ex. Let $G$ be a topological group, $H\subset G$ is a subgroup. Then $\exists$ action $H\curvearrowright G$ with $h\cdot g = hg$ (multiplication in $G$) for $h\in H$ and $g\in G$. $G/H$ is the set of right cosets of $H$ in $G$, $G / H = \{H \cdot g \vert g\in G\}$.

Consider the action $O(n) \curvearrowright S^{n-1} \subseteq \mathbb{R}^n$. This action is transitive i.e. for $\forall x\in S^{n-1}$ the $O(n)$-orbit of $x$ is $S^{n-1}$ i.e. for $\forall x,y \in S^{n-1}$ $\exists A \in O(n)$ s.t. $x = Ay$.

Consider the embeddng $O(n-1) \to O(n)$ as $B \mapsto \left(\matrix{1 & 0 \newline 0 &B}\right)$. Under this embedding, $O(n-1)$ is a subgroup of $O(n)$. Let $e_1 = (1,0,0,\cdots, 0),\cdots$ be a standard basis of $\mathbb{R}^n$, then $A \cdot e_1 = e_1 \Leftrightarrow A = \left(\matrix{1 & 0 \newline 0 &B}\right)$ for some $B\in O(n-1)$. $O(n-1)\subseteq O(n)$ is called the **stabilizer** of $e_1$. Let $\pi \cdot O(n) \to S^{n-1}$ as $\pi (A) = A\cdot e_1$, $\pi$ is continuous and surjective.

*Thm.* Let $G$ act on $X$, if $X/G$ and $G$ are connected then $X$ is connected too.

- proof. Suppose $X = A\cup B, A\cap B = \varnothing$. $A,B$ are open and nonempty. Since $\pi: X \to X/G$ is open, then $X/G = \pi(A) \cup \pi (B)$ with $\pi(A),\pi(B)$ being open and nonempty. So $\pi(A)\cap \pi(B) \ne \varnothing$ since $X/G$ is connected.
- Let $\pi(x) \in \pi(A) \cap \pi(B)$, then $A \cap G\cdot x \ne\varnothing, B\cap G\cdot x \ne\varnothing$ and $G\cdot x = (A\cap G\cdot x) \sqcup (B\cap G\cdot x)$. Let $f:G\to x$ with $f(g) = g\cdot x$. Then $f$ is the composition $G\to G\times X \to X$ by $g\mapsto (g,x), (g,x') \mapsto g\cdot x'$. Thus $f$ is continuous which leads to contradiction.

*Cor.* $SO(n)$ is connected.

- *proof.* $SO(1)$ as a point is connected, $SO(n+1) / SO(n) \simeq S^n$ is  connected, then by induction $SO(n)$ is connected.

## Homotopy Theory

1. To define homotopy groups; 2. To define homotopy equivalences

*Def.* Let $f,g: X\to Y$ be continuous then $f$ is homotopic to $g$ if $\exists $ a continuous map $F:X\times I \to Y$ (I = [0,1]) s.t. $F(x,0) = f(x), F(x,1) = g(x), \forall x \in X$. Denoted as $f\simeq_F g$.

- Intuition: map $f$ can be **continuously** transformed to $g$.

*Def.* Suppose $A\subset X, f\vert_A = g\vert_A$. If $\exists F:X\times I \to Y$ s.t. $F(x,0) = f(x), F(x,1) = g(x)$ for all $x\in X$ and $F(x,t) = f(x), \forall x \in A, t\in I$. Then we say that $f$ is homotopic to $g$ relative to $A$. Denoted as $f\simeq_F g $ rel $A$.

*Lemma.* The relation of homotopy is an equivalence relation on the set of continuous maps from $X$ to $Y$.

- $f\simeq_F f$, $f\simeq_F g \Rightarrow f\simeq_F f$ and $f\simeq_F g, g\simeq_F h \Rightarrow f\simeq_F h$.

*Lemma.*

1. $f,g:X\to Y$ and $h:Y\to Z$. If $f\simeq_F g$ rel $A$ then $hf \simeq_{hF} hg$ rel $A$.

2. $f:X\to Y$ and $g,h:Y\to Z$. If $g\simeq_G h$ rel $B$ then $gf \simeq_{G(f(x),t)} hf$ rel $f^{-1}(B)$.

### Fundamental Group

A path $\gamma:[0,1]\to X$ with $\gamma(0) = \gamma(1)$ is called a loop in $X$. Choose a base point $p\in X$. We consider the set of loops in $X$ based at $p$. (i.e. $\gamma(0) = \gamma(1) = p$). Let $A = \{0,1\} \subseteq [0,1]$, then homotopy relative to $A$ is an equivalence relation on this set. Let $\langle\gamma\rangle$ be the equivalence class of $\gamma$. Let $\alpha,\beta$ be two loops based at $p$. Let $\alpha\cdot \beta: [0,1] \to X$ as

$$
\alpha \cdot \beta = \begin{cases} \alpha(2t), &0\le t\le 1/2 \\ \beta(2t-1), &1/2 \le t\le 1\end{cases}
$$

- Associative? No.

We define $\langle\alpha\rangle\cdot\langle\beta\rangle = \langle\alpha\cdot\beta\rangle$. Well-defined? Yes.

*Thm.* The set of homotopy classes of loops in $X$ based at $p$ forms a group under the multiplication $\langle\alpha\rangle\cdot\langle\beta\rangle = \langle\alpha\cdot\beta\rangle$.

- proof of associativity, inverse, identity

This group is called the **fundamental group** of $X$ based at $p$, and is denoted by $\pi(x,p)$. $\forall \langle\gamma(t)\rangle\in \pi(x,p)$, $\gamma(t)$ is in the path-connected component of $X$ containing $p$. $\Rightarrow$ We will assume that $X$ is path-connected.

We have the following generalization of the above theorem. Let $\gamma_1,\gamma_2$ be two paths in $X$ with $\gamma_1(1) = \gamma_2(0)$. Then we let

$$
\gamma_1\cdot\gamma_2(s) = \begin{cases} \gamma_1(2s), &0\le s\le 1/2\\ \gamma_2(2s-1), &1/2\le s \le 1\end{cases}
$$

Then we have

- (1) If $\gamma_1 \simeq \gamma_1'$ rel $\{0,1\}$ and $\gamma_2 \simeq \gamma_2'$ rel $\{0,1\}$, then $\gamma_1\cdot \gamma_2 \simeq \gamma_1'\cdot\gamma_2'$ rel $\{0,1\}$.
- (2) If $\gamma_1(1) = \gamma_2(0), \gamma_2(1) = \gamma_3(0)$, then $(\gamma_1 \cdot \gamma_2)\cdot \gamma_3 \simeq \gamma_1 \cdot (\gamma_2 \cdot \gamma_3)$ rel $\{0,1\}$.
- (3) Let $\gamma^{-1}(s) = \gamma(1-s)$, then $\gamma\cdot\gamma^{-1} \simeq$ constant path at $\gamma(0)$ rel $\{0,1\}$.

*Thm.* Let $X$ be path-connected. Then for all $p,q\in X$, we have $\pi_1(x,p), \pi_1(x,q)$ are isomorphic. We denote them by $\pi_1(x)$.

### Computation of $\pi_1(S^1)$

*Thm.* Let $\phi: \mathbb{Z}  \to \pi_1(S^1,1)$, $\phi(n) = \langle\pi\circ \gamma_n\rangle$ (The homotopy class of the loop $\omega_n(s) = (\cos 2\pi ns, \sin 2\pi ns)$ based at $(1,0)$), then $\phi$ is an isomorphism.

*Idea.* Compare paths in $S^1$ with paths in $\mathbb{R}$ via the map $p:\mathbb{R}\to S^1$ given by $p(s) = (\cos2\pi s, \sin2\pi s)$. Observe that loop $\omega_n$ is indeed the composition $p\circ\tilde \omega_n$ where $\tilde\omega_n:I\to \mathbb{R}$  is the path $\tilde \omega_n (s) = ns$. We say that $\tilde \omega_n$ is a **lift** of $\omega_n$.

*Lemma.* (Path-lifting lemma) Let $\sigma:I \to S^1$ with $\sigma(0) = 1$. Then there exists unique $\tilde \sigma:I \to \mathbb{R}$ such that $\tilde \sigma(0) = 0$ and $p\circ \tilde \sigma = \sigma$. $\tilde \sigma$ is a lift of $\sigma$.

- *proof.* Let $U = S^1 \setminus\{-1\}, V = S^1 \setminus \{1\}$, then $\{U,V\}$ is an open covering of $S^1$ and $\pi\vert_{(n-1/2, n+1/2)}: (n-1/2, n+1/2) \to U$ is a homeomorphism and $\pi\vert_{(n,n+1)}: (n,n+1) \to V$ is a homeomorphism for all $n\in \mathbb{Z} $.

- since $[0,1]$ is compact, by Lebesgue's lemma $\exists 0 = t_0 < t_1 < \cdots < t_n = 1$ s.t. $[t_i,t_{i+1}]$ is contained in $\sigma^{-1}(U)$ or $\sigma^{-1}(V)$ for all $i$. Since $\sigma(0) = 1\not\in V$, so $\sigma([0,t_1]) \subset U$. Let $f = (\pi\vert_{(-1/2, 1/2)})^{-1}$ and let $\tilde \sigma (s) = f\circ \sigma (s)$ for $0\le s \le t_1$. Then $\pi \circ \tilde \sigma(s) = \sigma (s)$ for $0\le s\le t_1$.
- Suppose we have defined $\tilde \sigma$ on $[0,t_k]$. If $\sigma([t_k,t_{k+1}]) \subset U$ and if  $\tilde \sigma (t_k) \in (n-1/2, n+1/2)$ for some $n\in \mathbb{Z} $, we let $g:= (\pi\vert_{(n-1/2, n+1/2)})^{-1}$ and let $\tilde \sigma(s) = g\circ \sigma(s), t_k \le s\le t_{k+1}$.

*Lemma.* (Homotopy-lifting lemma) If $F:I\times I \to S^1$ is continuous with $F(0,t) = F(1,t) = 1,\forall 0\le t\le 1$. Then there exists unique $\tilde F:I\times I\to \mathbb{R}$ with $p\circ \tilde F = F$ and $\tilde F(0,t) = 0, 0\le t\le 1$.

*Thm.* The map $\phi:\mathbb{Z}  \to \pi_1(S^1,1)$, $\phi(n) = \langle\pi\circ \gamma_n\rangle$ is an isomorphism.

- proof: $\phi(m+n) = \phi(m)\cdot\phi(n)$, and that $\phi$ is onto by the path-lifting lemma (a loop in $S^1$ can be lifted to a path starting at 0 and ends at some integer n), and is one-one by the homotopy-lifting lemma (A homotopy from $\omega_m$ to $\omega_n$ lifts to a homotopy of paths starting at 0, so has same endpoint).

Application: Brouwer fixed-point Theorem in dim $\le 2$. (constucting a map: $D^2 \to S^1$ which is a retraction if there's no fixing point)

*Thm.* Let $B$ be a ball of any dimension and $f:B\to B$ continuous. Then $\exists x\in B$ s.t. $f(x) = x$.

*Thm.* Let $U,V\subseteq X$ be open and $X = U\cup V$. If $\pi_1(U) = \pi_1(V) = \{e\}$ and $U\cap V$ is path-connected, then $\pi_1(x) = \{e\}$.

Cor. $\pi_1(S^n) = \{e\}$ for $n\ge 2$.

*Theorem.* $\pi_1(X\times Y) \approx \pi_1(X) \times \pi_1(Y)$ if $X,Y$ are path-connected

### Induced Homomorphism

For topological group $X$, we have $\pi_1(x)$ as a group. For continuous map $f:X\to Y$, what will we get?

Let $p\in X, f(p) = q\in Y$, $\alpha:[0,1] \to X$ is a loop at $p$, then $f\circ \alpha$ is a loop in $Y$ based at $q$. If $\alpha \simeq \alpha'$ rel $\{0,1\}$, then $f\circ \alpha \simeq f\circ \alpha'$ rel $\{0,1\}$, thus we obtain a map.

Define $f_\ast : \pi_1(X,p) \to \pi_1(Y,q)$, then $f_\ast (\langle\alpha\rangle\langle\beta\rangle) = f_\ast (\langle\alpha\beta\rangle) = \langle(f\circ\alpha)(f\circ\beta)\rangle = f_\ast(\langle\alpha\rangle)f_\ast(\langle\beta\rangle)$. $f_\ast$ is a group homomorphism.

*Thm.* Let $f:X\to Y, g:Y\to Z$ be continuous, then $(g\circ f)_\ast = g_\ast \circ f_\ast$, and $(id_x)_\ast = id_{\pi_1(x)}$.

Cor. If $f:X\to Y$ is a homeomorphism with inverse $g$, then $f_\ast$ is an isomorphism with inverse $g_\ast$. $\pi_1(X)$ is a topological invariant.

*Ex.* $C\subset \mathbb{R}^n$ is convex, then $\pi_a(c) = \{e\}$, $X$ is simply connected if $\pi_1(x) = \{e\}$.

*Prop.* If $X$ retracts on $A$, then the homomorphism $i_\ast: \pi_1(A,x_0) \to \pi_1(X,x_0)$ induced by the inclusion map $i$ is injective. If $A$ is a deformation retract then $i_\ast$ is an isomorphism.

### Homotopy Equivalence

Recall: $X,Y$ are homeomorphic if $\exists f:X\to Y, g:Y\to X$ continuous s.t. $g\circ f = id_X, f\circ g = id_Y$.

*Def.* $X,Y$ are called **homotopy equivalent** if $\exists f:X\to Y, g:Y\to X$ continuous s.t. $g\circ f \simeq id, f\circ g\simeq id$. $f$ and $g$ are called homotopy equivalence and they are called the homotopy inverse of each other. We denote $X\simeq Y$ if $X,Y$ are homotopy equivalent.

In this case, the induced maps $f_\ast, g_\ast = {(f\circ g)}_\ast = id$, so they are inverse isomorphisms of $\pi_1(X) \approx \pi_1(Y)$.

$X,Y$ homeomorphic $\Rightarrow X\simeq Y$.

*lemma.* $\simeq$ is an equivalence relation.

Ex. (Deformation retraction). Let $A\subseteq X$. Suppose $\exists F:X\times I \to X$ s.t. $F(x,0) = x, F(x,1) \in A, F(x,t) = x$ if $x\in A$. Then $F$ is called a deformation retraction from $X$ to $A$.

$X$ is called contractable if $id_X$ is homotopic to some constant map at $p\in X$. Let $i:p\to X$ inclusion. $f=C_p:X\to p$ (constant map) Then $f\circ i = id_p, i\circ f \simeq id_X$, thus $X\simeq \{p\}$.

*Thm.* If $f\simeq_F g:X\to Y$ then $g_\ast: \pi_1(X,p) \to \pi_1(Y,g(p))$ is equal to the composition
$$
\pi_1(X,p) \xrightarrow{f_\ast} \pi_1(Y,f(p)) \xrightarrow{\gamma_\ast} \pi_1(Y,g(p))
$$
where $\gamma(s) = F(p,s)$.

*Thm.* If $X,Y$ are homotopy equivalent spaces, then $\pi_1(X) \approx \pi_1(Y)$.

- proof. Let $f:X\to Y, g:Y\to X$ s.t. $id_X\simeq_F g\circ f, id_Y\simeq_G f\circ g$. Let $p = g(q) \in X,q\in Y$. We need to show that $f_\ast: \pi_1(X,p) \to \pi_1(Y,f(p))$ is an isomorphism.
- Let $\gamma:I\to X$ with $\gamma(s)=F(p,s)$.
- By the theorem above we can see $(g\circ f)_\ast = \gamma_\ast : \pi_1(X,p)\to \pi_1(X,g\circ f(p))$ is an isomorphism.
- Since $(g\circ f)_\ast = g_\ast \circ f_\ast$, thus $f_\ast$ is injective.
- Similarly $(f\circ g)_\ast = f_\ast \circ g_\ast : \pi_1(Y,q) \to \pi_1(T,f(p))$ is an isomorphim, then $f_\ast$ is surjective thus isomorphism.

Cor. If $A\subset X$ and $\exists$ deformation retraction from $X$ to $A$ then $\pi_1(X) \simeq \pi_1(A)$. If $X$ is contractible, $\pi_1(X) = \{e\}$.

- $\pi_1(\mathbb{R}^n\setminus\{0\}) = \begin{cases} \mathbb{Z} , &n=2\\ \{e\}, &n\ge 3\end{cases}$ , $\pi_1(\text{cylinder}) = \pi_1(\text{Mobius strip}) = \mathbb{Z} $.

*Thm.* (1) $X$ is contractible $\Leftrightarrow X\simeq \{p\}$.

(2) Let $f,g:X\to Y$ and $Y$ is contractible, then $f\simeq g$.

(3) If $X$ is contractible, then $id_x$ is homotopic to the constant map at $x$ for all $x\in X$.

- proof. (1) Contraction from $id_X$ to $C_q$, where $q = g(p)$, $C(q)$ is the constant map to $q$.
- (2) $f = id_Y\circ f \simeq C_p\circ f = C_p\circ g \simeq id_Y\circ g = g$.
- (3) Let $id_X\simeq C_p$. For all $x\in X$ by (2) we have $C_x\simeq C_p \simeq id_X$.

## Van Kampen Theorem

Recall if $X=U\cup V$ is an open covering, $\pi_1(U) = \pi_1(V) = \{e\}$. If $U\cap V$ is path connected, then $\pi_1(X) = \{e\}$. Generalization

*Def.* Free product of groups $G_1\ast G_2$: A word is a sequence $g_1\cdots g_m$ s.t. $g_i\in G_1$ or $G_2$. A word is called reduced if

(1) $\forall g_i$ is not the identity in $G_1$ or $G_2$.

(2) $\forall$ adjacent $g_i,g_{i+1}$ belong to different groups $G_1,G_2$.

Then we can define

$$G_1\ast G_2 = \{\text{All reduced words}\}$$

and $(g_1g_2\cdots g_m)(h_1\cdots h_n)$ is defined as the word $g_1g_2\cdots g_mh_1\cdots h_n$ after reduction.

- Identity: empty word
- Inverse: $(g_1\cdots g_m)^{-1} = g_m^{-1}\cdots g_1^{-1}$

Get a group $G_1\ast G_2$ called the **free product** of $G_1$ and $G_2$. Let $I$ be an index set, we can define free product

$$
\ast_{\alpha \in I} G_\alpha = \{\text{reduced words } g_1,g_2\cdots g_m \vert g_i \in G_{\alpha_i}\}
$$

Let $g_1\cdots g_m \in \ast_\alpha G_\alpha, g_i \in G_{\alpha_i}$, let $\varphi(g_1\cdots g_m) = \varphi_{\alpha_1}(g_1) \cdots \varphi_{\alpha_m}(g_m)$. Let $X$ be a topological space, $X = \cup_\alpha A_\alpha$ be an open covering and $x_0 \in \cap_\alpha A_\alpha$.

*Thm.* **(Van Kampen)**

- Let $X = \cup_\alpha A_\alpha$ where $A_\alpha$ is based at point $x_\alpha$, and all intersections $A_\alpha \cap A_\beta$ are path-connected, then the homotopy $\Phi: \ast_\alpha \pi_1(A_\alpha) \to\pi_1(X)$ is surjective.
- If in addition each intersection $A_\alpha \cap A_\beta \cap A_\gamma$ is path-connected, then the kernel of $\Phi$ is the normal subgroup N generated by all elements of the form  $i_{\alpha\beta}(\omega) i_{\beta\alpha}(\omega)^{-1}$, and so $\Phi$ induces an isomorphism $\pi_1(X) \approx \ast_\alpha \pi_1(A_\alpha) / N$.

## Covering Space

*Def.* A covering space of a space $X$ is a space $\tilde X$ together with a continuous map $p:\tilde X \to X$ satisfying the following condition:

- $\exists$ an open covering $X = \bigcup_\alpha U_\alpha$ s.t. $\forall \alpha$, $p^{-1}(U_\alpha)$ is a disjoint union $\bigsqcup_\beta V_{\alpha,\beta}$ of open sets $V_{\alpha\beta} \subset \tilde X$ and $p\vert_{V_{\alpha\beta}}: V_{\alpha\beta} \to U_\alpha$ is a homeomorphism for all $\beta$, $p$ is called a covering map.
- Divide $X$ to open sets, then $p^{-1}(U_\alpha)$ consists of disjoint branches homeomorphic to $U_\alpha$.

*Thm.* **(Homotopy lifting lemma)** Let $p:\tilde X \to X$ be a covering map and $F:Y\times I \to X$. Let $\tilde f: Y\to\tilde X$ with $p\circ f(y) = F(y,0)$ then $\exists ! \tilde F:Y\times I \to \tilde X$ s.t. $\tilde F(y,0) = \tilde f(y), p\circ \tilde F = F$.

*Thm.* Let $p:\tilde X \to X$ be a covering map and $p(\tilde x_0) = x_0$, then $p_\ast:\pi_1(\tilde X, \tilde x_0) \to \pi_1(X,x_0)$ is injective. Let $\langle \alpha \rangle\in\pi_1(X,x_0)$, then the homotopy class of loop $\langle \alpha \rangle \in p_\ast(\pi_1(\tilde X, \tilde x_0))$ iff the lift of $\alpha$ starting at $\tilde x_0$ is a loop.

- The map of basic groups is injective; loop in X is in the image of $p_\ast$ iff it is lifted to a loop.

- proof. Consider an element in $\ker p_\ast$ represented by a loop $\tilde f_0:I\to \tilde X$ with a homotopy $f_t:I\to X$ from $f_0 = p\tilde f_0$ to trivial loop $f_1$. Then there is a lifted homotopy of loops $\tilde f_t$ starting with $\tilde f_0$ and ending with a constant loop. Thus $\langle \tilde f_0\rangle = 0$ in $\pi_1(\tilde X,\tilde x_0)$, so $p_\ast$ is injective.

Let $p:\tilde X\to X$ be a covering map, then $\lvert p^{-1}(x)\rvert$ (cardinality, can be infinity) is locally constant over $X$: $\forall x_0 \in X, \exists U$ neighborhood of $x_0$ s.t. $\lvert p^{-1}(x)\rvert = \lvert p^{-1}(x_0)\rvert$ for all $x\in U$. (Take $U$ s.t. $p^{-1}(U) = \sqcup_\beta V_\beta$, $p\vert_{V_\beta}: V_\beta \to U$ homeomorphism)

If $X$ is connected, then $\lvert p^{-1}(x)\rvert$ is a constant for all $x\in X$. We call $\lvert p^{-1}(x)\rvert$ the number of sheets of the covering $p$.

*Thm.* Let $p:\tilde X\to X$ be a covering map and $\tilde X,X$ are path-connected, then the number of sheets of $p$ is equal to the index of $H = p_x(\pi_1(\tilde x,\tilde x_0))$ in $\pi_1(x,x_0)$.

- proof. Let $g,h$ be loops at $x_0$ with $\langle h\rangle \in H$. Let $\tilde g, \tilde h$ be the lifts of $g,h$ starting at $\tilde x_0 \Rightarrow \tilde h$ is a loop

### Universal Covering Space

$p:\tilde X \to X$ a covering map. If $\pi_1(\tilde X) = \{e\}$, then $\tilde X$ is called a universal covering space of $X$.

*Def.* $X$ is called **locally path-connected** if for all $x\in X$ and $\forall$ neighborhood $U$ of $x$, $\exists$ a pathconnected neighborhood $V$ of $x$ s.t. $V\subseteq U$.

*Def.* $X$ is called **semilocally simply-connected** if for all $x\in X$, $\exists$ neighborhood $U$ of $x$ s.t. $i_\ast (\pi_1(U,x)) = id$, that is, the inclusion-induced map is trivial.

*Lemma.* Let $p:\tilde X \to X$ be a universal covering, then $X$ is semi-locally simply-connected.

*Thm.* Let $X$ be path-connected, locally path-connected, and semi-locally simply-connected, Then $\exists $ a universal covering space $p:\tilde X \to X$.

*Thm.* Let $X$ be path-connected, locally path-connected, and semi-locally simply-connected. Then for all subgroup $H\subset \pi_1(X,x_0)$, $\exists $ covering space $p:X_H \to X$ s.t. $p_\ast(\pi_1(X_H, \tilde x_0)) = H$ for $\tilde x_0 \in p^{-1}(x_0)$.

*Thm.* **(Uniqueness)** Let $X$ be path-connected and locally path-connected, then two path-connected covering spaces $p_1:\tilde X \to X$ and $p_2:\tilde X_2 \to X$ are isomorphic via an isomorphism $f:\tilde X_1 \to \tilde X_2$ taking a base point $\tilde x_1 \in p_1^{-1}(x_0)$ to a basepoint $\tilde x_1 \in p_2^{-1}(x_0)$ iff $p_{1\ast}(\pi_1(\tilde X_1, \tilde x_1)) = p_{2\ast}(\pi_1(\tilde X_2, \tilde x_2))$.

- proof. '=>': If $\exists$ isomorphism $f$, then $p_1 = p_2f, p_2 = p_1f^{-1} \Rightarrow p_{1\ast} = p_{2\ast}f_\ast, p_{2\ast} = p_{1\ast}(f^{-1})_\ast \Rightarrow p_{1\ast}(\pi_1(\tilde X_1, \tilde x_1)) = p_{2\ast}(\pi_1(\tilde X_2, \tilde x_2))$

- '<=': By lifting criterion, $\exists$ lift $\tilde p_1:(\tilde X_1, \tilde x_1) \to (\tilde X_2, \tilde x_2)$ s.t. $p_2\circ \tilde p_1 = p_1$, $\exists$ lift $\tilde p_2:(\tilde X_2, \tilde x_2) \to (\tilde X_1, \tilde x_1)$ s.t. $p_1\circ \tilde p_2 = p_2$. By uniqueness of lifting, $\tilde p_2\circ\tilde p_1 = id_{\tilde X_1}, p_1\circ p_2 = id_{\tilde X_2} \Rightarrow \tilde p_1, \tilde p_2$ are inverse isomorphisms.

*Thm.* **(Classification of covering space)** Let $X$ be path-connected and locally path-connected, and semilocally simply-connected. Then

(1) There is a **bijection** between the set of basepoint-preserving isomorphism classes of path-connected covering spaces $p:(\tilde X, \tilde x_0) \to (X,x_o)$ and the set of subgroups of $\pi_1(X,x_0)$, obtained by $(p:(\tilde X, \tilde x_0) \to (X,x_0))\mapsto p_\ast (\pi_1(\tilde X, \tilde x_0))$.

(2) If the base points are ignored, then this correspondence gives a bijection between isomorphism classes of path-connected covering spaces $p:\tilde X\to X$ and conjugacy classes of subgroups of $\pi_1(X,x_0)$.

*Def.* Let $p:\tilde X \to X$ be a covering map. An isomorphism $f:\tilde X \to \tilde X$ is called a **deck transformation**. All the deck transformations form a group $G(\tilde X)$ under composition.

We have a group action $G(\tilde X) \curvearrowright\tilde X$ by $f\cdot \tilde x := f(\tilde x)$ for $f\in G(\tilde X), \tilde x\in \tilde X$.

If $\tilde X$ is path-connected, this action is free: $f\cdot \tilde x = \tilde x$ iff $f = id_{\tilde x}$ by the uniqueness of lifting.

We call $p:\tilde X \to X$ a normal covering space or a regular covering space if $G(\tilde X)$ acts transitively on each $p^{-1}(x)$ for all $x\in X$: for $\tilde x, \tilde x' \in p^{-1}(x)$ there exists $f \in G(\tilde x)$ s.t.t $f\cdot \tilde x = \tilde x'$.

*Thm.* Let $X$ be path-connected, locally path-connected. Let $p:(\tilde X, \tilde x_0) \to (X,x_0)$ be a path-connected covering space. Let $H = p_\ast (\pi_1(\tilde X, \tilde x_0)) \subset \pi_1(X,x_0)$

(1) $p:\tilde X\to X$ is normal iff $H$ is a normal subgroup of $\pi_1(X,x_0)$

(2) Let $N(H)$ be the normalizer of $H$ in $\pi_1(X,x_0)$, then $G(\tilde X) \simeq N(H) / H$. In particular, if $p$ is normal, $G(\tilde X) \simeq \pi_1(X,x_0) / H$. If $p:\tilde X \to x$ is the universal covering, $G(\tilde X) \simeq \pi_1(X,x_0)$.

G acts on Y, forall $y \in Y$, there exists a neighborhood $U$ of $y$ s.t. $\forall g_1\ne g_2 \in G $ we have $g_1(U) \cap g_2(U) = \varnothing$.

*Thm.* Such $G$ acts on $Y$ then

1. The quotient map $p:Y\to Y/G$ is a normal covering map.
2. Y path-connected, then $G$ is the group of deck transformations.
3. Y path-connected, locally path-connected, then $G \simeq \pi_1(Y/G) / (p_\ast (\pi_1(Y))$

proof.

(1) For all $y\in Y/G$ choose $\tilde y \in Y$ s.t. $p(\tilde y) = y$. Choose neighborhood U of $\tilde y$ satsifying (*), then $p^{-1}(p(U)) = \bigsqcup_{g\in G} g(U)$ and $p\vert_{g(U)}:g(U) \to p(U)$ is a homeomorphism by definintion of idenfication topology.

Then $p$ is a covering map, $\forall g\in G$ acts as a deck transformation. Since $g_2g_1^{-1}(g_1(U)) = g_2(U)$ for all $g_1,g_2\in G$, so $p$ is a normal covering map.

(2) $G\subseteq G(Y)$ since $\forall g \in G$ acts as deck transformation. If $Y$ is path-connected  and $f \in G(Y)$, then forall $y \in Y$ we have $p(y) = p(f(y))\Rightarrow t,f(y)$ lie in the same orbit $\Rightarrow \exists g\in G$ s.t. $g(y) = f(y)\Rightarrow f^{-1} \circ g(y) = y \Rightarrow$ $ f^{-1}\circ g = id_Y \Rightarrow f=g \Rightarrow G(Y) = G$.

(3) By (2) and the previous theorem.

Ex. $G = \mathbb{Z} \times \mathbb{Z}, Y = \mathbb{R}^2$ Define $G$ acts on $Y$: $(m,n)\cdot (x,y) := (x+m,y+n)$, and $Y/G$ is homeomorphic to the torus, then action satisfies (*). Then $\pi_1(Y) = \{e\} \Rightarrow \pi_1(Y/G) \simeq G = \mathbb{Z}\times\mathbb{Z}$.

Ex. Let $G = \mathbb{Z}_2 = \{-1,1\}, Y = S^n$. Define $G$ acts on $Y$ as $-1 \cdot x= -x$. Then $Y/G \simeq \mathbb{R}P^n$. The action satisfies (*), and $\pi_1(S^n) = \{e\}$ for $n\ge 2$, so $\pi_1(\mathbb{R}P^n)\simeq G = \mathbb{Z}_2$ for $n\ge 2$.

## Homology Theory

Simplicial homology, singular homology, cellular homology

### Motivating example

Graph (Edges and vertices, abelianized by rechoosing basepoints)

Boundary map (as a homomorphism): $\partial_1:C_1 \to C_0$ by sending edge to (ending-starting). Cycles are in the kernel of $\partial$, as a linear combination of basic cycles $a-b,a-c,a-d$.

Attaching a 2-cell A in $C_2$, then $\partial_2:C_2 \to C_1$ maps $A$ to its boundary $a-b$. We have $a-b \in \ker\partial_0$. So $\ker \partial_0 / \Im \partial_1 = \{a-c,a-d\} = H_1(X_2)$.

### Simplicial Homology

*Def.* **Simplex** Let $v_0,v_1\cdots v_n \in \mathbb{R}^m$. Suppose $v_1-v_0,v_2-v_0,\cdots, v_n -v_0$ are linearly independent.

Let $[v_0,v_1,\cdots v_n] = \{\lambda_0 v_0 + \cdots +\lambda_nv_n : \lambda_0+\cdots +\lambda_n = 1,\lambda_i \ge 0\}$ which is the "convex hull" of $v_0,\cdots v_n$ (The smallest convex set in $\mathbb{R}^m$ containing $v_0,\cdots, v_n$). $[v_0,v_1,\cdots v_n]$ is called an n-simplex with an ordering of the vertices $v_0,\cdots ,v_n$.

Standard n-simplex: $\Delta^n = \{(t_0,\cdots ,t_n)\in \mathbb{R}^{n+1} : t_0+\cdots +t_n = 1, t_i \ge 0, i = 0,1,\cdots ,n\}$.

Let $[v_0,\cdots ,v_n]$ be an n-simplex, we have a cononical linear homeomorphism $h:\Delta^n \to [v_0,\cdots,v_n]$ with $h(t_0,\cdots ,t_n) = \sum_{i=0}^n t_iv_i$. $t_i$ are called barycentric coordinates of the point $\sum_{i=0}^n t_iv_i$ in $[v_0,\cdots ,v_n]$.

A face of a simplex is the subsimplex with vertices in a nonempty subset of $\{v_0,\cdots ,v_n\}$, the ordering of vertices of $[v_0,\cdots ,v_n]$ induces the ordering of the faces of $[v_0,\cdots, v_n]$.

### Singular homology

Let $X$ be a topological space. A **singular n-simplex** of $X$ is a continuous map $\sigma:\Delta^n \to X$. Let $C_n(X)$ be the free Abelian group with basis the set of singular n-simplices of $X$. Elements in $C_n(X)$ called **n-chains** are finite formal sums $\sum_i n_i\sigma_i$ for $n_i \in \mathbb{Z}$ and $\sigma_i:\Delta^n \to X$.

Let $\sigma: \Delta^n \to X$ continuous. Define $\partial_n(\sigma) = \sum_{i=0}^n (-1)^i \sigma \vert_{[v_0,v_1,\cdots \hat v_i \cdots v_n]}$. (remove $v_i$). Extend $\partial_n$ linearly, we get a **boundary homomorphism** $\partial_n: C_n(X) \to C_{n-1}(X)$.

*Lemma.* The composition $C_n(X) \xrightarrow{\partial_n} C_{n-1}(X) \xrightarrow{\partial_{n-1}} C_{n-2}(X)$ is zero, thus $\Im \partial_{n+1} \subseteq \ker \partial_n$.

- proof. From the definition of $\partial_n$.

*Def.* The quotient group $ \ker \partial_n / \Im \partial_{n+1}$ is called the n-th singular homology group of $X$ and is denoted by $H_n(X)$. Elements in $\ker \partial_n$ are called (n-dim) **cycles** and elements in $\Im \partial_{n+1}$ are called **boundaries**. Two cycles $a,b$ are called homologous if $a-b \in \Im \partial_{n+1}$ (belong to the same cosets of $\Im \partial_{n+1}$)

In general, if we have a sequence of homomorphisms of Abelian groups
$$
\cdots \to C_{n+1} \xrightarrow{\partial_{n+1}} C_n \xrightarrow{\partial_n} C_{n-1} \to\ \cdots
$$
s.t. $\partial_n \circ \partial_{n+1} = 0$ for all n. Then this sequence is called a chain complex. The group $H_n : \ker \partial_n / \Im \partial_{n+1}$ is called the n-th homology group of this chain complex.

homological algebra is a subject which studies chain complexes and the homology groups.

*Thm.* $H_n(\text{point}) = \mathbb{Z}$ if $n=0$ and $0$ if $n>0$.

*Thm.* (1) Let $\{X_\alpha\}_{\alpha \in I}$ be path connected components of $X$, then $H_n(X) = \oplus_{\alpha\in I} H_n(X_\alpha)$.

(2) If $X\ne \varnothing$ is path-connected, then $H_0(X) = \mathbb{Z}$. Therefore for general $X$, we have $H_0(X) = \oplus_{\alpha\in I}\mathbb{Z}$.

- proof. (1) $\sigma:\Delta^n \to X$, then $\sigma(\Delta^n)\subseteq X_\alpha$ for some $\alpha \in I$, so $C_n(X) = \oplus_{\alpha\in I}C_n(X_\alpha)$. Moreover $\partial_n(C_n(X_\alpha))\subseteq C_{n-1}(X_\alpha)$, thus $\ker\partial_n = \oplus_{\alpha}\ker \partial_n\vert_{C_n(X_\alpha)}$, $\Im \partial_{n+1} = \oplus_{\alpha\in I} \Im(\partial_{n+1}\vert_{C_{n+1}(X_{\alpha})})$.

- (2) $H_0(X) = C_0(X) / \Im \partial_1$, let $\mathcal{E}: C_0(X)\to \mathbb{Z}$ defined as $\mathcal{E}(\sum_i n_i\sigma_i) = \sum_i n_i$, we see $\mathcal{E}$ is surjective and we need to show $\ker \mathcal{E} = \Im \partial_1$. For all $\sigma:\Delta^1 \to X, \mathcal{E}(\partial_1(\sigma)) = \mathcal{E}(\sigma\vert_{[v_1]} - \sigma\vert_{[v_0]}) = 1-1 = 0$. So $\Im \partial_1 \subset \ker \mathcal{E}$.

*Def.* Consider the chain complex

$$
\cdots \to C_2 \xrightarrow{\partial_2} C_1 \xrightarrow{\partial_1} C_0(X) \xrightarrow{\varepsilon} \mathbb{Z} \to 0
$$

where $\varepsilon(\sum_i n_i\sigma_i) = \sum_i n_i$, X is required to be nonempty. We can see $\varepsilon \partial_1 = 0$, hence it induces a map $H_0(X) \to \mathbb{Z}$ with kernel $\tilde H_0(X)$.

Let $\tilde H_n(X)$ be the homology of this chain complex, called reduced homology of $X$.

$$
H_n(X) = \begin{cases} \tilde H_n(X), n\ge 1 \newline\ \tilde H_n(X) \oplus \mathbb{Z}, n = 0\end{cases}
$$

### Homotopy Invariance

Hommotopy equivalent spaces have isomorphic groups? $f:X\to Y$ induce $f_\ast:H_n(X) \to H_n(Y)$ for each $n$, and $f_\ast$ is iso. if $f$ is homotopy equivalence.

Let $f:X\to Y$ continuous, we want to define the homomorphism $f_\ast: H_n(X)\to H_n(Y)$.

Define $f_\sharp:\Delta^n \to Y$ as n-simplex of Y by $f_\sharp(\sigma):= f \circ \sigma:\Delta^n \to Y$. Extend $f_\sharp$ to $C_n(X)$ linearly by  $f_\sharp(\sum_i n_i \sigma) := \sum_i n_i f_\sharp(\sigma_i) = \sum_i n_i f\sigma_i$. So we obtain a homomorphism $f_\sharp: C_n(X) \to C_n(Y)$.

Lemma. $f_\sharp\partial = \partial f_\sharp$. proof:

$$
f_\sharp\partial(\sigma) = f_\sharp(\sum_i (-1)^i \sigma\vert_{[v_0,\cdots,\hat v_i, \cdots, v_n]}) =  \sum_i (-1)^i f \sigma\vert_{[v_0,\cdots,\hat v_i, \cdots, v_n]} = \partial f_\sharp(\sigma)
$$

Thus we have a commutative diagram:

$$
\xymatrix{
 \cdots \ar[r]& C_{n+1}(X) \ar[r]^{\partial}\ar[d]^{f_\sharp} & C_{n}(X) \ar[r]^{\partial}\ar[d]^{f_\sharp}& C_{n-1}(X) \ar[r]\ar[d]^{f_\sharp}& \cdots\\
  \cdots \ar[r]& C_{n+1}(Y) \ar[r]^{\partial}& C_{n}(Y) \ar[r]^{\partial}& C_{n-1}(Y) \ar[r]& \cdots
}
$$

The relation is also expressed by saying $f_\sharp$ defines a **chain map** from the singular chain complex of $X$ to that of $Y$. $f_\sharp$ takes cycles to cyles since $\partial \alpha =0 \Rightarrow \partial (f_\sharp\alpha) = f_\sharp(\partial \alpha) = 0$. $f_\sharp$ takes boundaries to boundaries since $f_\sharp(\partial\beta) = \partial (f_\sharp\beta)$. Hence $f_\sharp$ induces a homomorphism $f_\ast: H_n(X) \to H_n(Y)$.

Let $\alpha \in Z_n(X)$, let $[\alpha]$ be the image of $\alpha$ in $H_n(X) = Z_n(X) / B_n(X)$, then $f_\ast ([\alpha]) = [f_\sharp(\alpha)] \in H_n(Y), f_\sharp(\alpha) \in Z_n(Y)$.

Remark. Let $C_\cdot$, $D_\cdot$ be two chain complexes, a chain map $f:C_\cdot\to D_\cdot$ consists of homomorphisms $f_n:C_n\to D_n$ s.t. $\partial f_n = f_{n-1} \partial$.

Basic facts: (1): $X\xrightarrow g Y\xrightarrow f Z$, we have $(f\circ g) _\ast = f_\ast \circ g_\ast$. (2) $(id_X)_\ast = id_{H_n(X)}$.

*Thm.* Let $f,g:X\to Y$ be homotopic maps , then $f_\ast = g_\ast:H_n(X) \to H_n(Y)$

- proof. Let $F:X\times I \to Y$ s.t. $f\simeq_F g$. Want to subdevide $\Delta^n \times I$ into (n+1) simplexes.

The relationship $\partial P + P\partial = g_\sharp - f_\sharp$ is expressed by saying that $P$ is a **chain homotopy** between chain maps $f_\sharp$ and $g_\sharp$. So chain homotopic maps induce the same homomorphism on homology.

*Cor.* If $f:X\to Y$ be a homotopy equivalence, then $f_\ast: H_n(X) \to H_n(Y)$ is an isomorphism. Thus $\tilde H_n(X) = 0$ for all n if $X$ is contractible.

- proof. Let $g:Y\to X$ s.t. $f\circ g \simeq id_Y, g\circ f \simeq id_X$. Then $f_\ast g_\ast = (fg)_\ast = (id_Y)_\ast = id_{H_n(Y)}$, $g_\ast f_\ast = (gf)_\ast = (id_X)_\ast = id_{H_n(X)}$. So $f_\ast, g_\ast$ are isomorphisms.

### Homological Algebra

Consider a sequence of homomorphisms of Abelian groups

$$
A_\cdot = (\cdots \xrightarrow{} A_{n+1}\xrightarrow{f_{n+1}} A_n \xrightarrow{f_n} A_{n-1} \to\cdots )
$$

This sequence is called **exact** at $A_n$ if $\ker f_n = \Im f_{n+1}$; is called **exact** if it is exact at all $A_n$ for $n\in \mathbb{Z}$.

*Prop.* (1) $0\to A \xrightarrow{f} B$ is exact at $A$ $\Leftrightarrow$ $f$ is injective

(2) $A\xrightarrow f B \to O$ is exact at $B$ $\Leftrightarrow$ $f$ is surjective

(3) $O\to A\xrightarrow f B \to O$ is exact $\Leftrightarrow$ $f$ is an isomorphism.

(4) $O\to A \xrightarrow f B \xrightarrow g C \to O$ is exact $\Leftrightarrow$ $f$ is injective while $g$ is surjective, $\ker g = \Im f$. This is called a **short exact sequence**. In this case, $A\approx \Im f = \ker g, C \approx B / \Im f$ or $C\approx B / A$.

Let $A_\cdot, B_\cdot, C_\cdot$ be chain complexes, Consider $O\to A_{\cdot} \xrightarrow {f_\cdot} B_\cdot \xrightarrow {g_\cdot} C_\cdot \to O$ where $f_\cdot = (f_n)_{n\in\mathbb{Z}}, g_\cdot = (g_n)_{n\in \mathbb{Z}}$ are chain maps. $f_n:A_n\to B_n, g_n:B_n \to C_n, f_n\partial = \partial f_{n+1}, g_n \partial = \partial g_{n+1}$. This sequence is called a short exact sequence of chain complexes if $0 \to A_n \xrightarrow {f_n} B_n \xrightarrow {g_n} C_n \to 0$ is exact for all $n\in \mathbb{Z}$.

$f_\cdot$ andd $g_\cdot$ induces homomorphisms $f_\ast:H_n(A_\cdot) \to H_n(B_\cdot), g_\ast: H_n(B_\cdot) \to H_n(C_\cdot)$. Q: Is
$$
0\to H_n(A_\cdot) \xrightarrow {f_\ast} H_n(B_\cdot) \xrightarrow {g_\ast} H_n(C_\cdot) \to 0
$$
Exact? A: No.

We define a boundary map $\partial:H_n(C_\cdot) \to H_{n-1}(A_\cdot)$ as follows: Let $c\in C_n$ be a cycle $(\partial c = 0)$. Since $g_n$ is surjective, $\exists b\in B_n$ s.t. $g_n(b) = c$. Since $g_{n-1}\partial (b) = \partial g_n(b) = \partial c = 0$, so $\partial (b) \in\ker g_{n-1} = \Im f_{n-1}$ $\Rightarrow$ $\exists a\in A_{n-1}$ s.t. $f_{n-1}(a) = \partial b$. $f_{n-2}(\partial a) = \partial f_{n-1}(a) = \partial\partial b = 0$ since $f_{n-2}$ is injective $\Rightarrow$ $\partial a = 0$.

Define $\partial: H_n(C_\cdot) \to H_{n-1}(A_\cdot)$ by $\partial ([c])  = [a]$.

*Lemma.* $\partial : H_n(C_\cdot) \to H_{n-1}(A_\cdot)$ is well-defined and is a homomorphism.

We have a sequence

$$
\cdot \to H_{n+1}(C_\cdot) \xrightarrow \partial H_n(A_\cdot) \xrightarrow {f_\ast} H_n(B_\cdot) \xrightarrow \partial H_{n-1}(A_\cdot) \xrightarrow {f_\ast} H_{n-1}(B_\cdot) \xrightarrow {g_\ast}\cdots
$$

*Thm.* The sequence above is exact, called the **long exact sequence of homology**.

Consider the commutative diagram of chain maps:

$$
\xymatrix{
 0 \ar[r]& A_\cdot \ar[r]^{f_\cdot}\ar[d]^{\alpha_\cdot} & B_\cdot \ar[r]^{g_\cdot}\ar[d]^{\beta_\cdot}& C_\cdot \ar[r]\ar[d]^{\gamma_\cdot}& 0\\
  0 \ar[r]& A_\cdot' \ar[r]^{f_\cdot'}& B_\cdot' \ar[r]^{g_\cdot'}& C_\cdot' \ar[r]& 0
}
$$

The two rows are short exact sequences.

$$
\xymatrix{
 \cdots \ar[r]& H_n(A_\cdot) \ar[r]^{f_\ast}\ar[d]^{\alpha_\ast} & H_n(B_\ast) \ar[r]^{g_\cdot}\ar[d]^{\beta_\ast}& H_n(C_\cdot) \ar[r]^\partial\ar[d]^{\gamma_\ast}& H_{n-1}(A_\cdot)\ar[r]\ar[d]^{\alpha_\ast} & \cdots\\
  \cdots \ar[r]& H_n(A_\cdot') \ar[r]^{f_\ast'}& H_n(B_\cdot') \ar[r]^{g_\ast'}& H_n(C_\cdot') \ar[r]^{\partial} & H_{n-1}(A_\cdot') \ar[r]&\cdots
}
$$

*Thm.* **(Naturality)** The above diagiam of homology groups is commutative.

### Relative Homology

Let $X$ be a topological space and $A\subset X$. Let $C_n(X,A) := C_n(X) / C_n(A)$. Consider the boundary map $\partial:C_n(X) \to C_{n-1}(X)$. We have $\partial(C_n(A)) \subset C_{n-1}(A)\Rightarrow$ It induces a quotient boundary map $\partial:C_n(X,A) = C_n(X)/C_n(A) \to C_{n-1}(X,A) = C_{n-1}(X) / C_{n-1}(A)$.

Since $\partial^2 = 0$ in the complex $C_\cdot (X) = \{C_n(X)\}_n$, so $\partial^2 = 0$ in $C_\cdot (X,A) = \{C_n(X,A)\}_n\Rightarrow C_\cdot (X,A)$ is a chain complex. This is the definition of **relative homology groups** $H_n(X,A)$.

- Elements in $H_n(X,A)$ are represented by **relative cycles**: n-chains $\alpha \in C_n(X)$ s.t. $\partial \alpha \in C_{n-1}(A)$.

- A relative cycle $\alpha$ is trivial in $H_n(X,A)$ iff it is a relative boundary: $\alpha = \partial \beta + \gamma$ for some $\beta \in C_{n+1}(X), \gamma \in C_n(A)$.

*Def.* The relative homology group $H_n(X,A)$ is dedfined to be $H_n(C_\cdot (X,A))$. An element in $H_n(X,A)$ is represented by a relative cycle $\alpha \in C_n(X)$ s.t. $\partial \alpha \in C_{n-1}(A)$.

- A relative cycle $\alpha$ is trivial in $H_n(X,A) \Leftrightarrow$ it is a relative boundary: $\alpha = \partial \beta + \gamma$ for some $\beta \in C_{n+1}(X), \gamma \in C_n(A)$. We have a **short exact sequence**:
  $$
  0 \to C_\cdot (A) \xrightarrow{i_\cdot} C_\cdot (X) \xrightarrow{j_\cdot} C_\cdot(X,A) \to 0
  $$
  where $I_\cdot$ is the inclusion map, $j_\cdot$ is the quotient map.

- Long exact sequence

*Remark.* Consider a pair $(X,A)$ with $A\ne \varnothing$. Consider the short exact seqeunce

$$
0 \to \tilde C_\cdot (A) \xrightarrow{i_\cdot} \tilde C_\cdot(X) \xrightarrow{j_\cdot} C_\cdot(X,A) \to 0
$$

where

So we get a long exact sequence

$$
\cdots \to H_n(A) \to H_n(X) \to H_n(X,A) \to H_{n-1}(A) \to H_{n-1}(X) \to \cdots \newline \cdots\to H_0(X,A) \to 0
$$

Consider the diagram

$$
\xymatrix{
0 & C_n(A) & C_n(X) & C_n(X,A) & 0 \\
0 & C_{n-1}(A) & C_{n-1}(X) & C_{n-1}(X,A) & 0
}
$$

where i is inclusion, j is quotient map. The diagram is commutative. Let $n$ very we will obtain a **short exact sequence of chain complexes**.

$$
\xymatrix{
& 0\ar[d] & 0\ar[d] & 0\ar[d] & \\ \cdots\ar[r] & A_{n+1}\ar[d]^{i}\ar[r]^\partial & A_n\ar[d]^{i}\ar[r]^\partial & A_{n-1}\ar[d]^{i}\ar[r] & \cdots \\
 \cdots\ar[r] & B_{n+1}\ar[d]^{j}\ar[r]^\partial & B_n\ar[d]^{j}\ar[r]^\partial & B_{n-1}\ar[d]^{j}\ar[r] & \cdots \\
 \cdots\ar[r] & C_{n+1}\ar[d]\ar[r]^\partial & C_n\ar[d]\ar[r]^\partial & C_{n-1}\ar[d]\ar[r] & \cdots \\& 0 & 0 & 0 &
}
$$

This stretches out into a long exact sequence of homology groups:

$$
\cdots \to H_n(A) \xrightarrow{i_\ast} H_n(B) \xrightarrow{j_\ast} H_n(C) \xrightarrow{\partial} H_{n-1}(A) \xrightarrow{i_\ast} H_{n-1}(B) \to \cdots
$$

*Remark.* Definition of $\partial:H_n(C) \to H_{n-1}(A)$?

*Thm.* This sequence of homology groups is exact.

- proof. (1) $\Im i_\ast \subset \ker j_\ast$
- (2) $\Im j_\ast \subset \ker \partial$.
- (3) $\Im \partial \subset \ker i_\ast$.
- (4)
- (5)
- (6)

Take $A = \{x_0\}\subseteq X$. Consider the pair $(X,x_0)$ for $x_0 \in X$. We have $H_n(X,x_0) \simeq \tilde H_n(X)$ for all $n$ by the long exact sequence.

Let $f_\cdot (X,A) \to (Y,B)$ for $A\subset X, B\subset Y, f:X\to Y$ s.t. $f(A) \subset B$.

*Thm.* Let $f,g:(X,A)\to (Y,B)$ Let $F:X\times I \to Y$ s.t. $f\simeq_F g$, $f\vert_{X\times \{t\}}(A) \subseteq B$ for all $t\in I$. Then $f_\ast = g_\ast : H_n(X,A) \to H_n(Y,B)$.

Generalization: Let $B\subset A \subset X$. Consider the short exact sequence

$$
0\to C_n(A,B) \to C_n(X,B) \to C_n(X,A) \to 0
$$

Then we can obtain a long exact seqeunce from this. For example, when $B$ is a point, the long exact sequence of $(X,A,B)$ becomes the long exact sequence of reduced homology for $(X,A)$.

*Thm.* **(Excision Theorem)** Let $Z\subset A\subset X$ s.t. the closure $\bar Z$ is contained in the interior of $A$. Then the inclusion $(X-Z,A-Z) \to (X,A)$ induces isomorphisms $H_n(X-Z,A-Z) \to H_n(X,A)$ for all $n$. Equivalently let $A,B \subset X$ s.t the interiors of $A,B$ cover $X$, then the inclusion $(B,A\cap B)\to (X,A)$ induces isomorphisms $H_n(B,A\cap B) \to H_n(X,A)$ for all $n$. (Let $Z = A \setminus (A\cap B)$)

*Lemma.* Let $i : C^\beta_\cdot (X) \to C_\cdot (X)$ be the inclusion map. Then there exists a chain map $p:C_\cdot (X) \to C_\cdot^\beta(X)$ s.t. $p \circ i = id_{C_\cdot^\beta(X)}$, $\exists$ a chain homology $D:C_n(X) \to C_{n+1}(X)$ s.t. $\partial D + D \partial = id_{C_\cdot(X)} - i\circ p$. Moreover, $i$ induces isomorphisms $H_n^\beta(X) \approx H_n(X)$ for all $n$.

*Def.* Set $U$ s.t. $A\subset U \subset X$ and $A$ is a deformation retract of some neighborhood $U$, then $(X,A)$ is called a good pair.

*Thm.* Let $(X,A)$ be a good pair, then the identification map $q:(X,A) \to (X/A, A/A)$ (X/A identify A to a point, A/A is a point) induces isomorphisms

$$
q_\ast: H_n(X,A) \to H_n(X/A, A/A) \approx \tilde H_n(X/A), \forall n.
$$

Remark. $(X,A)$ be a good pair $\Rightarrow$ exists a long exact sequence

$$
\to \tilde H_n(A) \xrightarrow{i_{1\ast}} \tilde H_n(X) \xrightarrow{j_\ast} \tilde H_n(X/A) \xrightarrow{\partial} \tilde H_{n-1}(A) \to \cdots
$$

*Cor.* $H_i(S^n) = \mathbb{Z}$ for $i=0,n$,  and $0$ for other cases.

- Proof. Let $D^n$ is n-d ball, let $(X,A) = (D^n, S^{n-1})$ so $X/A = S^n$ then we derive a long exact sequence

$$
\cdots \to \tilde Hi(S^{n-1}) \to \tilde H_i(D^n) = 0 \to \tilde H_i(S^n) \xrightarrow{\partial} \tilde H_{i-1}(S^{n-1}) \to \tilde H_{i-1}(D^n)= 0\to \cdots
$$

*Cor.* Let $\varnothing \ne U \subset \mathbb{R}^m, \varnothing \ne V \subset \mathbb{R}^n$ are open sets. If $U,V$ are homeomorphic, then $m=n$.

### Degree

*Def.* The induced map $f_\ast$ of $f:S^n\to S^n$ is a homomorphism from an infinite cyclic group to itself, so $f_\ast (\alpha) = d\alpha$ for some $d\in\mathbb{Z}$. $d$ is called the **degree** of $f$, or $\deg f$.

*Prop.* If $f:S^n \to S^n$ has no fixed points, then $\deg f = (-1)^{n+1}$ (homotopic to the antipodal map)

*Thm.* $S^n$ has a continuous field of nonzero tangent vectors iff $n$ is odd.

### Celluar homology

*Lemma.* If $X$ is a CW complex, then

(1) $H_k(X^n,X^{n-1})$ is zero for $k\ne n$, is free abelian for $k=n$, with a basis one-to-one correspondent with n-cells of $X$.

(2) $H_n(X^n) = 0$ for $k>n$.

(3) The inclusion $i:X^n \to X$ induces $i_\ast:H_k(X^n) \to H_k(X)$ if $k<n$.

Euler Characteristic $\chi(X) = \sum_n (-1)^n c_n$ where $c_n$ is the number of n-cells of $X$. This depends only on the homotopy type of $X$.

*Thm.* $\chi (X)= \sum_n(-1)^n\text{rank} H_n(X)$.

### Mayer-Vietoris Sequence

For $A,B\subset X$ s.t. $X = A^\circ \cup B^\circ$, the exact sequence (M-V sequence) has the form
$$
\cdots \to H_n(A\cap B) \xrightarrow{\Phi} H_n(A)\oplus H_n(B) \xrightarrow{\Psi}H_n(X) \xrightarrow{\partial} H_{n-1}(A\cap B) \to \cdots \to H_0(X)\to 0
$$
Application: calculations, induction (A,B,A∩B) to A∪B

Formation: Short exact sequence

$$
0 \to C_n(A\cap B) \xrightarrow{\varphi} C_n(A)\oplus C_n(B) \xrightarrow{\psi} C_n(A+B) \to 0
$$

where $\varphi(x) = (x,-x)$ and $\psi(x,y) = x+y$. Exactness:

- $\ker\varphi = 0$ since a chain in $A\cap B$ is zero as a chain in A or B.
- $\ker \psi = \Im \varphi$ since $x+y = 0\Leftrightarrow x=-y$.
- $\Im \psi = C_n(A+B)$ from definition.

Boundary map $\partial:H_n(X) \to H_{n-1}(A\cap B)$.

## Cell Complex

A generali description of constructing a space as a cell complex:

(1) Start with a discrete set $X^0$ (points as 0-cells)

(2) Inductively form **n-skeleton** $X^n$ from $X^{n-1}$ by attaching *n-cells* $e_\alpha^n$ via maps $\varphi_\alpha: S^{n-1} \to X^{n-1}$. So $X^n$ is the quotient space of disjoinct union $X^{n-1} \sqcup_\alpha D_\alpha^n$ under identifications $x\sim \varphi_\alpha(x)$ for $x \in \partial D_\alpha^n$.

Each cell $e_\alpha^n$ in $X$ has a **characteristic map** $\phi_\alpha: D_\alpha^n \to X$ which extends the attaching map $\varphi_\alpha$ and is a homeomorphism from $\text{int}(D_\alpha^n)$ onto $e_\alpha^n$.

A **subcomplex** of a cell complex X is a closed subspace $A ⊂ X$ that is a union of cells of $X$. A pair $(X, A)$ consisting of a cell complex $X$ and a subcomplex $A$ will be called a **CW pair**.

Cell complex operations:

- Product: $X\times Y$ has the structure of a cell complex with cells $e_\alpha^m \times e_\beta^n$.
- Quotient: The cells of $X/A$ are the cells of $X-A$ plus one new 0-cell, then image of$A$ in $X/A$. For a cell $e_\alpha^n$ of $X-A$ attached by $\varphi_\alpha:S^{n-1} \to X^{n-1}$, the attaching map for the corresponding cell in $X/A$ is the composition $S^{n-1} \to X^{n-1} \to X^{n-1}/A^{n-1}$.
- Suspension: $CX = (X\times I) / (X\times \{0\})$, from the construction of product and quotient, $I$ given the standard cell strcuture of two 0-cells joined by one 1-cell.
- Join: $X*Y$ is defined as the quotient of $X\times Y\times I$ under identifications $(x,y_1,0)\sim (x,y_2,0)$ and $(x_1,y,1)\sim (x_2,y,1)$.
  Geometric view: all line segments connecting points in X to points in Y.
- Wedge Sum $X\vee Y$: For cell complexes $X_\alpha$ and the points $x_\alpha$ are 0-cells, we have $\bigvee_\alpha X_\alpha$ being a cell complex from $\sqcup_\alpha X_\alpha$ be collapsing a subcomplex to a point.
- Smash product: $X\wedge Y$ is defined to be the quotient $(X\times Y) / (X\vee Y)$. $X\wedge Y$ is a cell complex if $X,Y$ are cell complexes with $x_0,y_0$ 0-cells.

*Thm.* **(Collapsing subspaces)** If $(X, A)$ is a CW pair consisting of a CW complex X and a contractible subcomplex $A$, then the quotient map $X→X/A$ is a homotopy equivalence.

*Thm.* **(Attaching Spaces)** If $(X_1, A)$ is a CW pair and the two attaching maps $f,g : A→X_0$ are homotopic, then $X_0 \sqcup_f X_1 \simeq X_0 \sqcup_g X_1$.
