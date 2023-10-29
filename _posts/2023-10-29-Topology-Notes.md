---
layout: article
tag: notes
title: "Notes: Topology"
mathjax: true
excerpt_type: html
location: "Nan'ao Island, Shantou, China, Feb 2023"
show_location: true
article_header:
  type: overlay
  theme: dark
  background_color: '#203028'
  background_image:
    gradient: 'linear-gradient(135deg, rgba(34, 139, 87 , .4), rgba(139, 34, 139, .4))'
    src: /assets/images/cover/DSC_2781.JPG
---

Notes of *Topology* course, Autumn 2023, taught by Prof. Zong Zhengyu. <!--more-->

P is called a **limit point** of A, if every neighborhood of P contains at least one point of $A-\{P\}$.

Zariski topology: A subset of $X = \mathbb{C}$ is open, if its complement is finite of $X$. Let $f(t) \in \mathbb{C}[t]$ be a polynomial $\Rightarrow$ $f(t) = a(t-a_1)(t-a_2)\cdots(t-a_n)$ with $a_1,a_2,\cdots,a_n \in\mathbb{C}$.

- $A\subset X$ is closed $\Leftrightarrow$ $|A|$ is finite or $A=X$ $\Leftrightarrow$ A is the zero locus of some $f(t) \in \mathbb{C}[t]$.
- If $|A|$ is finite then $A$ has no limit point; if $|A|$ is infinite, then $\forall p \in X$ is a limit point of $A$.

- More generally, we can define Zariski topology on $\mathbb{C}^n$. A subset $A \subset \mathbb{C}^n$ is closed iff $A$ is the zero locus of some polynomials $f_1,f_2,\cdots,f_m \in \mathbb{C}[t_1,t_2,\cdots,t_n]$.

*Thm.* A set if closed iff it contains all its limit points

*Def.* The union of $A$ and all its limit points is called the **closure** of A, and is denoted by $\bar A$.

*Thm.* $\bar A$ is the smallest closed set containing $A$. In other words $\bar A = \cap_{B\supset A, B \text{ is closed}} B$. ($\Leftrightarrow$ $\bar A$ is closed and for any closed set $B \supset A$ we always have $A\subset \bar A \subset B$.)

*Cor.* Let $A\subset X$, then $A$ is closed iff $A=\bar A$.

*Def.*

- $A\subset X$ is called **dense** in $X$ if $\bar A = X$.

- $x\in A$ is an interior point of $A$ is $\exists$ a neighborhood $U$ of $x$ s.t. $U\subset A$. $\mathring{A} = \{x\in A: x \text{ is an iterior point of $A$}\}$.
- $x\in X$ is a frontier(boundary) point of $A$ is $x$ is neither an interior point of $A$ nor an interior point of $X\setminus A$. 



*Def.* Let $\beta$ be a collection of some open subsets of $X$, suppose every open set in $X$ is a union of members of $\beta$, then $\beta$ is called a basis of $X$ and elements in $\beta$ are called basic open sets.

*Thm.* Let $X$ be a set and let $\beta$ be a nonempty collection of subsets of $X$. Suppose $\bigcup_{B \in\beta}B = X$, and $\forall B_1,B_2 \in \beta, \forall x\in B_1\cap B_2$, $\exists B_3 \in\beta$ s.t. $x\in B_3 \subset B_1\cap B_2$. Define the open subsets of $X$ to be the arbitrary unions of members in $\beta$, then this gives a topology on $X$.

### Continuous function

*Def.* $f:X\to Y$ is continuous $\Leftrightarrow$ $f^{-1}(\text{open}) = \text{open}$.

*Thm.* Let $f:X\to Y, g:Y\to Z$ be continuous, then $g\circ f: X\to Z$ is continuous.

*Thm.* Let $f:X\to Y$ be continuous and let $A\subset X$ have the subspace topology, then $f|_A:A\to Y$ is continuous.

*Thm.* The followings are equivalent:

1. $f:X\to Y$ is continuous

2. If $\beta$ is a basis for the topology of $Y$, the inverse image of every member of $\beta$ is open in $X$.
3. $f(\bar A) \subset \overline{f(A)}$ forall $A\subset X$. 

4. $\overline{f^{-1}(B)} \subset f^{-1}(\overline B)$ forall $B \subset Y$.
5. $f^{-1}(A)$ is closed for any closed set $A\subset Y$.



*Def.* $f:X\to Y$ is a **homeomorphism** if $f$ is continuous and $\exists g:Y\to X$ continuous s.t. $f\circ g = id$ and $g\circ f = id$. 同胚

*Remark.* If $f:X\to Y$ is continuous and bijective, $f$ doesn't need to be a homeomorphism (the inverse may not be continuous)



*Theorem.* (Local formulation of continuity) (1) $f:X\to Y$ is continuous if $X$ can be covered by open sets $U_\alpha$ (i.e. $X \subset \bigcup_\alpha U_\alpha$) such that $f|_{U_\alpha}$ is continuous for all $\alpha$. (Infinite open covering)

(2) $f:X\to Y$ is continuous if $X = \bigcup _{i=1}^n F_i$, $F_i$ closed for all $i$ and $f|_{F_i}$ is continuous for all $i$. (finite closed covering)





### Limit

Let $X$ be a set and let $\beta$ be collection of subsets of $X$ s.t. (1)$\forall B \in \eta, B\ne \varnothing$; (2) $\forall B_1,B_2 \in \beta$, $\exists B_3 \in \beta$ s.t. $B_3 \subset B_1\cap B_2$. Then $\beta$ is called a basis of the set $X$.

*Def.* Let $f:X\to Y$ be a map of a set $X$ with a basis $\beta$ to a topological space $Y$. The point $p\subset Y$ is called the limit of $f$ over basis $\beta$ if for all neighborhood $V$ of $p$, $\exists A \in \beta$ s.t. $f(A) \subset V$, we denote this by $\lim_\beta f(x) = p$.

 

### Metric Space extension

For metric space $X$, subset $X\subset A$, $f:A\to \mathbb{R}$ is continuous. Q: Can we extend $f$ to the space $X$ continuously?

- In general, no

*Def.* Let $d$ be the metrix on $X$ and $A\subset X$. For all $x\in X$ define $d(x,A) = \inf_{a\in A}d(x,a)$.

*Lemma.* The function $x\mapsto d(x,A)$ is continuous

*Lemma.* $A,B\subset X$ closed and $A\cap B = \varnothing$. Then $\exists f:X\to\mathbb{R}$ continuous s.t. $f|_A = 1, f|_B = -1$ and $f(X \setminus (A\cup B)) \subset (-1,1)$.

*Theorem. (Tietze extension theorem)*. Let $X$ be a metric space and $C\subset X$ closed. If $C\to \mathbb{R}$ is continuous, then $f$ can be extended to $X$ continuously.

### Complete metric space

Let $(X,d)$ be a metric space,

*Def.* A sequence $\{x_n | n\ge 1\}$ of points in $X$ is called a Cauchy sequence if for all $\epsilon > 0$ $\exists N$ s.t. $d(x_m,x_n) < \epsilon$ for all $m,n>N$.

*Def.* A sequence $\{x_n\}$ of points in $X$ converges to a point $a\in X$ if $\lim_{n\to\infty} d(a,x_n) = 0$. The point $a$ is called the limit of $\{x_n\}$.

*Def.* A metric space $(X,d)$ is called complete if every Cauchy sequence is convergent.

Ex1. Continuous function set $C[a,b]$ with metric $d(f,g) = \max_{a\le x\le b}|f(x) - g(x)|$ is complete.

Ex2. Continuous function set $C[a,b]$ with metric $d(f,g) = \int_a^b |f-g|dx$ is not complete

Completion of a metric space: Let $(X,d)$ be a metric space. We want to find a "smallest" complete metric space $(Y,d)$ s.t. $X\subset Y$.

*Def.* If $(X,d)$ is a subspace of $(Y,d)$ which is complete and $X$ is dense in $Y$. Then $(Y,d)$ is called the **completion** of $(X,d)$.

*Def.* We say that the metric space $(X_1,d_1)$ is isometric to $(X_2,d_2)$ if $\exists$ bijection $f:X_1 \to X_2$ s.t. $d_2(f(a),f(b)) = d_1(A,b)$ for all $a,b\in X_1$. The map $f$ is called an **isometry**.

*Lemma.* Let $(X,d)$ be a matrix space and $a,b,u,v\in X$. Then $|d(a,b) - d(u,v)| \le d(a,u) + d(b,v)$

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
- *Def.* A topological space $X$ is called a Hausdorff space if $\forall x_1\ne x_2 \in X$, $\exists$ neighborhoods $U_1$ of $x_1$, $U_2$ of $x_2$ s.t. $U_1 \cap U_2 = \varnothing$.
- *Theorem.* Let $f:X\to Y$ be a map from a set $X$ to a Hausdoff space $Y$. Let $\beta$ be a basis of $X$. If $\lim_\beta f(x)$ exists  then it is unique.
  - proof: Two distinct limit points -> exists non-overlapping neighborhoods $V_1,V_2$. $\exists  B_1,B_2 \in \beta$ s.t. $f(B_1) \subset V_1, f(B_2) \subset V_2$ while $B_1\cap B_2 \ne \varnothing$.
- *Theorem.* A compact subset of a Hausdorff space is closed.
  - proof. For compact subset $A$ of Hausdorff space $X$. Let $x\notin A$, for all $z\in A$, we can find neighborhood $U_z,V_z$ of $x,z$. $A$ compact => $A \subset \bigcup_{i=1}^n V_{z_i}$. Define $U_\alpha = \bigcup_{i=1}^n U_{z_i}$ => $U_\alpha \cap A = \varnothing$, and $U_\alpha$ is a neighborhood of $x$ => $X\setminus A = \bigcup_{x\in X\setminus A}U_\alpha$ is open => $A$ is closed.
- *Theorem.* Let $f:X\to Y$ be continuous and bijective. If $X$ is compact and $Y$ is Hausdoff then $f$ is a homeomorphism.
- *Theorem.* An infinite subset of compact space must have a limit point.
- *Theorem.* Let $A\subset \R^n$ be compact, then $A$ is closed ($\R^n$ is Hausdoff) and bounded (can be finite covered by open balls).
- *Theorem.* Let $f:X \to \R$ be continuous, if $X$ is compact then $f$ is bounded and attains its bounds.
  - proof: $f(X)\subset \R$ is compact (bounded and closed)
- Lebesgue's Lemma: Let $X$  be a compact metric space and $X = \bigcup_\alpha U_\alpha$ an open covering. Then $\exists \delta > 0$ (called a Lebesgue number of $\{U_\alpha\}$) s.t. any subset of $X$ of diameter less than $\delta$ is contained in some $U_\alpha$.

### Product Topology

Product topology: X, Y -> $X\times Y$. $U\times V$ is open if $U$ is open in $X$, and $V$ is open in $Y$.

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

Sufficiency of main theorem: $X\subset \R^n$ is closed and bounded, then $X$ is compact.

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



*Theorem.* $\R$ is connected.

*Theorem.* The continuous image of a connected space is connected.

$Z\subset X$ dense and $Z$ is connected, then $X$ is also connected.

*Theorem.* $\varnothing \ne X \subset R$ is connected $\Leftrightarrow$ $X$ is an interval.



### Path Connnectedness

*Theorem.* A path connected space is connected.

*Theorem.* A connected open subset of a Euclidean space is path-connected.



## Identification Spaces

$\R P ^2$: real projective plane

glue opposite points on a circle

orientable

*Def.* Let $X$ be a topological space and let $X = \bigcup_{i\in I} P_i$, $P_i$ are disjoint and not empty. Let $Y = \{P_i | i \in I\}$ and let $\pi : X\to Y, \pi (x) = P_i$ if $x\in P_i$. Define a topology on $Y$ s.t. $U\subset Y$ is open $\Leftrightarrow$ $\pi^{-1}(U) \subset X$ is open.

This topology is called the identification topology on $Y$, and $Y$ is called the identification space associated with the partition $X = \bigcup_{i\in I}P_i$.



*Theorem.* Let $Y$ be an identification space of $\pi:X\to Y$ and let $z$ be a topological space. A map $f:Y\to Z$ is continuous iff $f\circ \pi: X\to Z$ is continuous.



*Def.* Let $f:X\to Y$ be surjective and continuous. Suppose $U\subset Y$ is open $\Leftrightarrow$ $f^{-1}(U) \subset X$ is open. Then we call $f$ an identification map.

*Theorem.* Let $f:X\to Y$ be surjective and continuous. If $f$ maps open sets of $X$ to open sets of $Y$, or closed sets to closed sets, then $f$ is an identification map.

- proof. Suppose f(open) = open, let $U \subset Y$ s.t. $f^{-1}(U) = X$ is open. Then since $f$ is surjective, $f(f^{-1}(U)) = U$, then $U$ is open in $Y \Rightarrow U\subset Y$ is open iff $f^{-1}(U) \subset X$ is open (i.e. continuous). So $f$ is an identification map.

*Cor.* Let $f:X\to Y$ be continuous and surjective. If $x$ is compact and $Y$ is Hausdoff, then $f$  is an identification map.

- proof. Let $A\subset X$ be closed $\Rightarrow$ $A$ is compact $\Rightarrow$ $f(A) \subset Y$ is compact.
- $Y$ is Hausdoff $\Rightarrow f(A)\subset Y$ is closed. By the theorem above, $f$ is an identification map.



*Theorem.* Let $f:X\to Y$ be a map s.t. $f_{X_\alpha}$ is continuous for all $\alpha$. If $j:\tilde X \to X$ is an identification map, then $f$ is continuous.

- proof. Since $j$ is an identification map, $f$ is continuous $\Leftrightarrow f\circ j : \bigcup_\alpha X_\alpha \to Y$ is continuous $\Leftrightarrow f\circ j|_{X_\alpha}$ is continuous i.e. $f_{X_\alpha}$ is continuous.



### Construction of $\R P^n$

- $\R P^n$ is the idetification space of $R^{n+1}\setminus \{0\}$ which identifies points on the same straight line through the origin.
- Let $B^n$ be the n-dimensional unit ball. Identify antipodal points of its boundary -> get $\R P^n$.  

The construction gives us te construction of the complex projective space $\C P^n$, by identifying points in $\C\setminus \{0\}$ which lie in the same 1-d $\C$-linear subspace of $\C^{n+1}$.

*Example.* (1) **(Cone)** Let $X$ be a topological space and $I=[0,1]$. Let $CX = (X\times I) / (X \times \{1\})$, which is the identification space which idetifies $X\times \{1\}$ to a point. $CX$ is called a cone.

(2) **(Suspension)** Let $X$ be a topological space, let $SX$ be the identification space of $X\times I$ which identifies $X\times \{0\}$ to a point and identifies $X\times \{1\}$ to another point.

(3) **(Wedge Sum)** Let $X,Y$ be topological spaces, and let $x_0 \in X, y_0 \in Y$. Identify $x_0$ and $y_0$ to a single point in $X\sqcup Y$, we obtain $X\vee Y$ called wedge sum of $X,Y$. 

(4) **(Attaching maps)** Let $A\subset Y$ be a subspace and $f:A\to X$ a continuos map. Consider the identification space from $X\sqcup Y$ which identifies $a$ and $f(a)$ for all $a\in A$. This identification space is denoted by $A\cup_f Y$, and $f$ is called attaching map.

(5) **(Mappping Cones)** Let $f:X\to Y$ be a map. The mapping cone $C_f = Y \cup_f CX$ is obtained by attach $X\times\{0\} \subseteq (X\times I) / (X\times \{I\}) = CX$ to $Y$ via $f$.

## Topologocal Group

*def.* A topological group $G$ is both a (Hausdoff) topological space and a group, such that multiplication $m:G\times G\to G, (g_1,g_2)\mapsto g_1g_2$ is continuous, and inverse $i:G\to G, g\mapsto g^{-1}$ is continuous.

Let $G_1,G_2$ be two topological groups, $f:G_1\to G_2$ is called an isomorphism if $f$ is a homeomorphism and $f$ is an isomorphism of groups. If $G$ is a topological group and $H\subseteq G$ is a subgroup. Equip $H$ the subspace topology, then $H$ is a topological group .

*Example.* (1) $(\R^n, +)$ is a topological group.

(2) Let $S^1 = \{e^{2\pi i \theta} : 0\le \theta < 1\}$ is a topological group.

(3) Let $T$ be the torus, $T = S^1\times S^1$ is a topological group.

(4) $GL(n,\R), SL(n,\R), O(n), SO(n)$ are topological groups.



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

$Mat_{n\times n}(\R) = \{n\times n \text{ real matrices}\} \simeq \R^{n^2}.$ not a group under multiplication.

$GL(n,\R) = \{M \in Mat_{n\times n}(\R) | \det M \ne 0\} \subseteq \R^{n^2}$ is open.



$SL(n,\R) = \{m \in GL(n,\R) | \det M = 1\}, SL(n,\R) \subseteq GL(n,\R)$ is a subgroup. 

- $SL(n,\R)$ is not compact since it's an unbounded subset of $\R^{n^2}$.

- $SL(n,\R)$ is connected



$O(n) = \{M \in GL(n,\R) | M^TM = I\} \subset GL(n,\R)$ is a subgroup

$SO(n) = \{M \in O(n) | \det M  1\} \subset SL(n,\R)$ is a subgroup.

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

- Example: Let lattice $\Lambda = \Z\cdot v_1 \oplus \Z \cdot v_2 \cong \Z^2$, then torus is homeomorphic to $\R^2 / \Lambda$.

### Projective Space

Ex. (projective space) Let $S^n \subseteq \R^{n+1}$ be the unit sphere, $\Z/2\Z = \{1,-1\}$. Define an action $\Z/2\Z \curvearrowright S^n$, then $S^n / (\Z / 2\Z) = \R P^n$. Let $\R^\ast - \R\setminus\{0\}$. Define an action $\R^\ast \curvearrowright (\R^{n+1}\setminus\{0\})$ as $\lambda \cdot (x_1,\cdots, x_{n+1}) := (\lambda x_1,\cdots, \lambda x_{n+1})$ for $\lambda \in \R^\ast$ and $(x_1,\cdots,x_{n+1}) \in \R^{n+1}\setminus\{0\}$.

We can see $(\R^{n+1} \setminus\{0\}) / \R^\ast = \R P^n = \{[x_1 : x_2: \cdots : x_n] | (x_1,\cdots, x_n) \in \R^{n+1}\setminus\{0\} \}$. (homogeneous coordinates)

There are $(n+1)$ canonical charts of $\R P^n$. Let $U_i \subseteq \R P^n, U_i = \{[x_1:\cdots :x_{n+1}] \in \R P^n | x_i \ne 0\} \subseteq \R P^n$ is open. Then $U_i$ is hemeomorphic to $\R^n$, and $\{U_i\}_{i=1}^{n+1}$ is an open covering of $\R P^n$.

Let $\C^\ast = \C \setminus \{0\}$, define an action $\C^\ast \curvearrowright \C^{n+1}\setminus \{0\}$, $\lambda (x_1,x_2,\cdots,x_{n+1}) = (\lambda x_1,\cdots, \lambda x_{n+1}) \Rightarrow (\C^{n+1} \setminus \{0\}) / \C^\ast = \C P^n$ is the complex projective space. Let $U_i = \{[x_1:x_2:\cdots:x_{n+1} \in \C P^n | x_i \ne 0\}\subseteq \C P^n$ for $i=1,2,\cdots, n+1$. Then $U_i$ is homeomorphic to $\C^n$ and $\{U_i\}_{i=1}^{n+1}$ is an open covering of $\C P^n$.



Zariski topology on $\C P^n$.



Ex. Let $G$ be a topological group, $H\subset G$ is a subgroup. Then $\exists$ action $H\curvearrowright G$ with $h\cdot g = hg$ (multiplication in $G$) for $h\in H$ and $g\in G$. $G/H$ is the set of right cosets of $H$ in $G$, $G / H = \{H \cdot g | g\in G\}$.

Consider the action $O(n) \curvearrowright S^{n-1} \subseteq \R^n$. This action is transitive i.e. for $\forall x\in S^{n-1}$ the $O(n)$-orbit of $x$ is $S^{n-1}$ i.e. for $\forall x,y \in S^{n-1}$ $\exists A \in O(n)$ s.t. $x = Ay$.



Consider the embeddng $O(n-1) \to O(n)$ as $B \mapsto \left(\matrix{1 & 0 \\ 0 &B}\right)$. Under this embedding, $O(n-1)$ is a subgroup of $O(n)$. Let $e_1 = (1,0,0,\cdots, 0),\cdots$ be a standard basis of $\R^n$, then $A \cdot e_1 = e_1 \Leftrightarrow A = \left(\matrix{1 & 0 \\ 0 &B}\right)$ for some $B\in O(n-1)$. $O(n-1)\subseteq O(n)$ is called the **stabilizer** of $e_1$. Let $\pi \cdot O(n) \to S^{n-1}$ as $\pi (A) = A\cdot e_1$, $\pi$ is continuous and surjective.