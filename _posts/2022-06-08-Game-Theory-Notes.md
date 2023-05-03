---
layout: article
tag: notes
title: "Notes: Game Theory"
mathjax: true
excerpt_type: html
article_header:
  type: overlay
  theme: dark
  background_image:
    src: /assets/images/cover/IMG_1220.JPG
---

Notes of IIIS *Game Theory* course, Spring 2022, taught by Prof. Zhixuan Fang. <!--more-->

## Lecture 1: Introduction

First part (Basic concepts)

- Strategic
- Extensive
- Repeated

Second Part (Advanced topics)

- Bayesian Game
- Mechanism Design
- Various Game Models

Examples of Games

What is a Game? A **game** is a formal representation of a situation in which a number of individuals interact with strategic interdependence.

- Each individual’s payoff depends not only on his own choice, but also on the choices of other individuals;

- Each individual is rational (self-interested), whose goal is to choose the actions that produce his most preferred outcome.
- Key concepts: Players, Rules, Outcomes, Payoffs

### Preliminaries: Convexity

*Def.*

- **(Convex Set)** A nonempty set $\chi \in \mathbb{R}^n$ is convex if $\forall x_1,x_2\in \chi$ and any $\theta \in [0,1]$, we have:
  $$
  \theta x_1 + (1-\theta)x_2 \in \chi
  $$
  
- **(Convex Combination)**A convex combination of points $x_1,x_2,\cdots,x_k$ can be expressed as
  $$
  y = \sum_{i=1}^k \theta_ix_i
  $$
  with $\sum_i\theta_i = 1$ and $\theta_i \ge 0, i = 1,2,\cdots,k$.

- **(Convec Hull)** The convex hull $\mathcal{H}(X)$ of a set $X$, is the smallest convex set that contains $X$. Properties:

  - $\mathcal{H}(X)$ is always convex
  - $X \in \mathcal{X}$
  - If $X$ is a convex set, then $\mathcal{H}(X)=X$.
  - If $Y$ is a convex set with $X\subset Y$, then $\mathcal{H} \subseteq Y$.

- Intersection and Affine Mapping preserves the convexity of Sets.

- **(Convex function)** A function $f:\mathbb{R}\to\mathbb{R}$ is convex if

  - $\textbf{dom} f$ is convex;

  - $\forall x,y\in \textbf{dom} f, \forall \theta \in [0,1]$, we have:
    $$
    f(\theta x + (1-\theta)y) \le \theta f(x) + (1-\theta) f(y)
    $$

  - If equality doesn't hold for all $\theta \in (0,1)$, then the function is called **strictly convex**.

- **(Sublevel Set)** The $\alpha$-sublevel set of a function $f:\mathbb{R}^n \to \mathbb{R}$ is defined as:
  $$
  C_\alpha = \{x\in \textbf{dom} f: f(x)\le \alpha\}.
  $$
  Sublevel of convex functions are convex for all $\alpha$.

- **(Quasi-convex functions)** A function $f:\mathbb{R}^n \to \mathbb{R}$ is called quasi-convex (or uni-modal) if its domain and all sublevel sets $C_\alpha = \{x\in \textbf{dom} f: f(x)\le \alpha\},\forall \alpha \in \mathbb{R}$ are convex.
  - A function $f$ is quasi-linear iff both $f$ and $-f$ are quasi-convex.

### Cournot Competition

Two companies, product level $q_1,q_2$, market command (price) $1-q_1-q_2$.

Response $q_1^\ast= \dfrac{1-q_2}{2}, q_2^\ast = \dfrac{1-q_1}{2}$

## Lecture 2: Utility and Rationality

### Simple case: Decision under Certainty

We denote $X$ as the set of our choices, we make decisions based on out preferences:

- **Preferences** are relationships defined on two choices $x,y\in X$ for a specific agent;
- $x \succeq y$ means the agent prefers $x$ to $y$
- $x\succ y$ means $x\succeq y$ but not $y\succeq x$;
- $x\sim y$ means indifference between $x$ and $y$ i.e. $x\succeq y$ and $y\succeq x$
- All preferences relations between two elements in $X$ constitutes a preference relation on $X$

Preferences describes pairwise relationship of choices. These relationships explode with increasing choices.

For simplicity, we can use *Utilities* to describe *Preferences*, as if the following axioms holds:

- **Completeness**: $\forall x,y\in X$, we have either $x\succeq y$ or $y\succeq x$, or both.
- **Transitivity**: If $x\succeq y, y\succeq z$, then $x\succeq z$. (Plausible?)

With these two axioms, we can define the agent's best choice rule on $X$ as:
$$
C(X;\succeq) = \{x\in X: x\succeq y, \forall y \in X\}
$$
**Proposition(Exsitence)**:

- For every *finite non-empty* set $B$, we have $C(B;\succeq) \ne \varnothing$
- If $x,y\in A\cap B$, and $x\in C(A;\succeq), y\in C(B;\succeq)$, then we have $x\in C(B;\succeq), y\in C(A;\succeq)$.

- If $X$ is infinite, then $C(X;\succeq)$ may be empty.

### Utility

*Def*. A utility function $\mu:X\to \mathbb{R}$ is consistent with a preference relation $\succeq$ on $X$ if $\forall x,y\in X$, we have $x\succeq y$ if and only if $\mu(x)\ge \mu(y)$.

*Thm.* If $X$ is finite, and the preference relation $\succeq$ on $X$ is complete and transitive, then there exists a utility function $\mu$ that is consistent with it.

- *Remark*: Similar results can be extended to infinite countable $X$ or infinite continuous $X$.

- *Proof*: Induction

### Rationality

*Def*. An agent is rational if the agent always maximizes his utility.

### Choice under Uncertainty: **Lottery Model**

 Define $\chi$ as the set of possible *outcomes, prizes* or *consequences*. Each outcome is attached to a prospect $p$.

- **(Lottery)**  A simple lottery over $\chi$ is a vector $p = (p_1,p_2,\cdots,p_n)$ with $p_i\ge 0$ for all $i$ and $\sum_ip_i = 1$, where $p_i$ is the probability that outcome $x_i$ occurs.
- Given a space of outcome $\chi$, denote the relevant set of lotteries over $\chi$ as $\mathcal{P} = \Delta(\chi) = \{(p_1,p_2,\cdots,p_n): p_i\ge 0, \sum_ip_i = 1\}$.

- **(Compound lottery)** Given two lotteries $p$ and $p'$, any convex combination of them: $\alpha p + (1-\alpha)p'$ with $\alpha \in[0,1]$ is also a lottery.

Preference over lotteries:

- Utility $U$ assigns utility numbers $u_1,\cdots,u_n$ to the $n$ outcomes $x_1,x_2,\cdots,x_n\in \chi$, but gives a utility $U(p) = U(p;u_1,u_2,\cdots,u_n)$ on $p \in P$. Then it satisifes:
  $$
  p \succeq q \Leftrightarrow U(p) = \sum_{x\in \chi} p(x)u(x) \ge U(q) = \sum_{x\in \chi} q(x)u(x)
  $$

- *Def.* **A utility function** $U : P \to \mathbb{R}$ is called **an Expected Utility Function** (or equivalently, a von Neumann-Morgenstern (VNM) expected utility function) if there is an assignment of numbers $(u_1, \cdots, u_n)$ to the $n$ outcomes $(x_1,\cdots, x_n)$ such that for every simple lottery $p \in \mathcal{P}$, $U(p) = u_1p_1 + \cdots + u_np_n$

Preferences Aioms:

- **(Independence)** A preference relation $\succeq$ on the space of lotteries $\mathcal{P}$ satisfies independence if $\forall p,p',p'' \in\mathcal{P}$ and $\alpha \in [0,1]$, we have:
  $$
  p\succeq p' \Leftrightarrow \alpha p + (1-\alpha) p'' \succeq \alpha p' + (1-\alpha)p''
  $$
  Adding another outcome with equal probability does not matter

- **(Continuity)** A preference relation $\succeq$ on the space of lotteries $\mathcal{P}$ is continuous if $\forall p,p',p'' \in\mathcal{P}$ with $p\succeq p' \succeq p''$, there exists some $\alpha \in [0,1]$ s.t.
  $$
  \alpha p + (1-\alpha)p'' \sim p'
  $$
  (Remark: sometimes doubtful)

**Expected Utility Theorem.** A preference relation $\succeq$ on lottery space $\mathcal{P}$ admits an expected utility representation if and only if it satisfies axioms of completeness, transitivity, continuity and independence.

That is, for a complete, transitive, continuous and independent preference $\succeq$​ on $\Delta(\chi)$​, we can assign a number $u_1, ...u_n$​ to each outcome $x_1, ..., x_n$​ in such a manner that for any two lotteries $p$​ and $p' $​ , we have:
$$
p \succeq p' \Leftrightarrow \sum_{i=1}^n u_ip_i \ge \sum_{i=1}^n u_ip_i'
$$

- Suppose that $U : P \to R$ is a VNM expected utility function for the preference relation $\succeq$ on $\mathcal{P}$. Then $V : P \to R$ is another VNM utility function for $\succeq$ if and only if there are scalar $a$ and scalar $b > 0$ such that $V (p) = a + b U(p)$ for all $p \in P$.

### Risk Aversion

Define $δ_x$ to be a degenerate lottery that gives $x$ for certain, and $E(p)$ be the expected value (amount of money) of a lottery $p$. We say that a decision maker is

- **risk-averse** if for every lottery $p$, $δ_{E(p)}\succeq p$.
- **risk-neutral** if for every lottery $p$, $δ_{E(p)} ∼ p$.
- **risk-loving** if for every lottery p, $δ_E(p) \preceq p$.

*Thm.* Risk-averse $\Leftrightarrow$ $u$ is concave.

## Lecture 3-4 : Strategic Form Game

### Strategic Form Game

*Def.* **(Strategic Form Game/Normal Form Game)** A triplet
$$
G = \{\mathcal{I}, (S_i)_{i\in \mathcal{I}}, (u_i)_{i\in\mathcal{I} }\}
$$
s.t.

- $\mathcal{I}$ is a finite set of **players**
- The **pure-strategy space** $S_i$ is the set of available actions for player $i$
- **Pay-off functions**: $(u_i)_{i\in\mathcal{I}} : S_1\times S_2\times \cdots\times S_I \to\mathbb{R}$.
  - $u_i(s)$ is player $i$'s VNM utility function for each profile $s=(s_1,s_2,\cdots,s_I)$ of strategies for all players.
- Simultaneous-move, One-shot
- In addition, denote $-i$ as all players except $i$, that is, player $i$'s opponent.

$$
s_{-i} = \{s_j\}_{j\ne i}, S_{-i} = \prod_{j\ne i}S_j, s = (s_1,s_2,\cdots,s_I) = (s_i,s_{-i})
$$

- Common knowledge: Every agents kows all other agent's actions, utilities, and that everyone is rational. And (everyone knows)^k everyone knows it.

### Dominant Strategy

*Def.* **(Strategy)** A complete description of responses in playing the game. Require responses in all possible situations. A **pure strategy** is a deterministic plan of actions.

*Def.* **(Dominance)** A strategy $s_i\in S_i$ is a dominant strategy for player $i$ if
$$
u_i(s_i,s_{-i}) \ge u_i(s_i',s_{-i}), \forall s_i'\in S, \forall s_{-i}\in S_{-i}.
$$
*Def.* **(Dominant Strategy Equilibrium)** A strategy profile $s^\ast$ is a dominant strategy equilibrium if $s_i$ is a dominant strategy for every player $i$.

*Def.* **(Strictly/Weakly dominated strategy)** A strategy $s_i\in S_i$ is strictly dominated (by a pure strategy) if there exists some other $s_i'\in S_i$ s.t.
$$
u_i(s_i',s_{-i}) > u_i(s_i,s_{-i}), \forall s_{-i}\in S_{-i}.
$$
And $s_i\in S_i$ is weakly dominated (by a pure strategy) if there exists some $s_i'\in S_i$ s.t.
$$
u_i(s_i',s_{-i}) \ge u_i(s_i,s_{-i}) ,\forall s_{-i}\in S_{-i}\\
u_i(s_i',s_{-i}) > u_i(s_i,s_{-i}) ,\exists s_{-i}\in S_{-i}
$$

### Iterated Elimination of Strictly Dominated Strategy

*Def.* A game $G$ is called “**solvable by pure strategy iterated strict dominance**” if $S_\infty$ (The outcome of Iterated Elimination of Strictly Dominated Strategy) contains a single strategy profile.

- *Thm.* The order of strategy deletion in iterated elimination of strictly dominated strategy does not change the remaining strategies

Eliminating Weakly Dominated Strategy

### Nash Equilibrium

*Def.* A strategy profile $s^\ast$ is a (pure strategy) Nash equilibrium if for all players $i$, we have
$$
u_i(s_i^\ast, s_{-i}^\ast) \ge u_i(s_i',s_{-i}^\ast), \forall S_i' \in S_i
$$
In other words, no player can gain by changing strategy while other players remain unchanged. （局部极值点）

*Def.* **(Best response)** Given a belief of others’ strategy profile $s_{-i}$ , define best response as:
$$
B_i(s_{-i}) = \{s' : \arg\max_{s'\in S_i} u_i(s',s_{-i})\}
$$

### Mixed Strategy

- PSNE may not exist (e.g. Penny matching)

*Def.* For player $i$, a mixed strategy $\sigma_i$ is a probabilistic distribution over pure strategies $s_i$.

- Based on the assumption of VNM utility, player $i$’s expected payoff $u_i$ is
  $$
  u_i(\sigma_i) = \int_Su_i(s) d\sigma(s)
  $$

- We define the support of a mixed strategy $\sigma_i$ as:
  $$
  \text{support}(\sigma) = \{s_i \in S_i : \sigma_i(s_i) > 0\}
  $$

*Def.* **(Mixed Strategy Nash Equilibruim)** A mixed strategy profile $\sigma^\ast$ is a (mixed strategy) Nash equilibrium if for every player $i$​,
$$
u_i(\sigma_i^\ast, \sigma_{-i}^\ast) \ge u_i(\sigma_i', \sigma_{-i}^\ast), \forall \sigma_i' \in \Sigma_i
$$

- *Prop.* A mixed strategy profile $\sigma^\ast$ is a Nash equilibrium iff for each player $i \in I$, every pure strategy in the support of $\sigma^\ast_i$ is a best response to $\sigma^\ast_{-i}$.
- *Prop.* If $\sigma^\ast$ is a Nash equilibrium, every pure strategy in the support of $\sigma^\ast_i$ yields the same payoff.

### Iterative Elimination of Strictly Dominated Strategies with Mixed Strategy (ISD or IESDS)

*Def.* A pure strategy $s_i$ is **strictly dominated** if there exists a mixed strategy $\sigma_i' \in \sigma_i$ such that $u_i(\sigma_i' , s_{−i}) > u_i(s_i , s_{−i})$ for all $s_{−i} \in S_{−i}$ . It is equivalent to check $u_i(\sigma_i , \sigma_{−i}) > u_i(s_i , \sigma_{−i})$ for all $\sigma_{−i} \in \sigma_{−i}$.

In each step, we consider eliminate all dominated strategies.

### Social Welfare and Pareto Optimality

*Def.* A strategy profile $s$ that maximizes social welfare is a **social optimum**.

- Ingeneral, "social welfare" is hard to define since payoff for different players can't be compared.

*Def.* **(Pareto dominance)** A strategy profile $s$ Pareto dominates $s_0$ if $∀i \in I$, $u_i(s) ≥ u_i(s_0 )$, and $∃i \in I$, $u_i(s) > u_i(s_0 )$. Intuitionally, no one's payoff gets worse and someone's gets better.

A strategy profile $s$ is **Pareto optimal** if it is not Pareto dominated.

- *Prop.* There always exists at least one Pareto optimal strategy profile in a finite game, might be multiple. (Otherwise, there would be a cycle by finiteness)
- *Prop.* A social optimum strategy profile $s$ is always Pareto optimal.

- Kaldor-Hicks efficiency: When one’s improvement is larger than others’ lost, potentially reach Pareto improvement by compensation.

### Rationalizability

Iterated elimination of strictly dominated strategy tells us what a player would NOT DO. But what would a player DO?
A player will response to what he thinks other will do.

*Def.* **(Belief)** A belief $µ_i$ of player $i$ about the other player’s strategies is a probability measure on $\sigma_{−i} \in \pi_{j\ne i}\sigmaj$ . A rational player plays best response to his belief.

*Def.*  **(Never-best response)** A pure strategy $s_i$ is a never-best response if for all beliefs $\sigma_{−i}$ , there exists $\sigma_i \in \sigma_i$ such that
$$
u_i(\sigma_i , \sigma_{−i}) > u_i(s_i , \sigma_{−i})
$$
A strictly dominated strategy is a never-best response, but the inverse may not true.

*Def.* **(Rationalizable strategies)** $R^\infty_i$, which contains all strategies that survive iterative elimination of never-best response, is the set of rationalizable strategies.

- A strictly dominated strategy will not be rationalized.
- Thus, set of rationalizable strategies represent a further refinement of the strategy beyond iterated strict dominance.
- What’s left in the rationalizable set is what a rational player might play.

*Thm5.* (Pearce, 1984) Rationalizability and iterated strict dominance **coincide** in **two-player** games.

*Remark.* (1) This doesn't hold for multi-player games
(2) Only need to show a never-best pure strategy is always strivtly dominated.

*Thm6.* **(Supporting Hyperplane Theorem)** Let $C$ be a nonempty convex subset of $\mathbb{R}^n$ and let $x_0$ be a vector in $\mathbb{R}^n$ . If $x_0$ is not an interior point of $C$, there exists a hyperplane that passes through $x_0$ and contains $C$ in one of its closed halfspaces, i.e., there exists a vector $\vec a \in \mathbb{R}^n$ , $\vec a \ne 0$ s.t.
$$
a^T x_0 ≥ a^T x, ∀x \in C.
$$

### Correlated Equilibrium

*Def.* **(Correlated Equilibrium)** A correlated equilibrium of a finite game is a joint probability distribution $p$ over $\Delta(S)$ such that
$$
\sum_{s_{−i}\inS_{−i}} p(s_{−i} \vert s_i)u_i(s_i , s_{−i}) ≥ \sum_{s_{−i}\inS_{−i}} p(s_{−i} \vert s_i)u_i(s_i' , s_{−i}), ∀s_i' \in S_i .
$$
for every player $i$ and every $s_i$ with $p(s_i) > 0$.

Intuition: given a signal $s_i$ generated from $p$, and when everyone else is following the signal, then your best choice is to follow the signal.

*Prop.* Every mixed strategy Nash equilibrium is a correlated equilibrium.

## Lecture 5 : Existence of Nash Equilibrium

Review: DSE $\subset$ PSNE $\subset$ MSNE $\subset$ CE

### Nash's Theorem

*Thm1.* Every finite game has at least one MSNE.

*Thm2.* **(Brouwer's Fixed Point Theorem)** Let $C$ be a bounded convex and closed subset of the Euclidean space. If $f:C\to C$ is a continuous function, there exists $x\in C$ s.t. $f(x) = x$.

### Proof

*Def.* Suppose the strategy profile $\sigma \in \Sigma$ is given. For player $i$ and a pure strategy $s\in S_i$, define the **gain function** of player $i$ as
$$
G_i(s,\sigma) = \max\{u_i(s,\sigma_{-i})-u_i(\sigma), 0\}
$$
The gain is the increase of payoff for player $i$ if he switches to pure strategy $s$.

Define a function $f:\Sigma \to \Sigma$ as follows: for all $\sigma \in \Sigma$, $f(\sigma) = \sigma'$ , where for all $i$ and $s_i\in S_i$,
$$
\sigma_i'(s_i) = \frac{\sigma_i(s_i) + G_i(s_i,\sigma)}{1+\sum_{s_i\in S_i} G(s_i,\sigma)}
$$
$f$ is continuous, $\Sigma = \prod \Sigma_i$​ is convex, bounded and closed, so we can tell that there exists a a fixed point. Then we need to show that when $\sigma  = f(\sigma)$, we have
$$
G_i(s,\sigma) = 0, \forall i, s\in S_i
$$

### Fixed Point Theorems

*Lemma.* **(Sperner's Lemma)** Consider a triangle $T$ with vertices $v_1, v_2, v_3$. Let $T$ be a triangulation of $T$ and and $V (T )$ denote its set of vertices. Consider any coloring of $V (T )$ with $\{0, 1, 2\}$ such that

1. $v_i$ is colored with $i (i \in \{0, 1, 2\})$.

2. If $v \in V (T )$ lies on the line joining vertices $v_i,v_j$ colored in $i, j \in \{0, 1, 2\}$, the color of $v$ is either $i$ or $j$. Then, there exists at least one trianle in $T$ whose vertices are colored by all three colors, i.e., a tri-chromatic triangle.

*Remark.*

1. There is a stronger version of Sperner’s lemma that further guarantees the total number of tri-chromatic triangles in T to be odd.
2. The results holds for higher dimension case (Image a n-dimension simplex).

*proof.* Routing

*Thm.* **(Kakutani)** Let $φ$ be a correspondence on set $S$, with $x \in S \to^φ φ(x) ⊆ S$. Suppose we have the following conditions:

- $S$ is a non-empty, compact and convex subset of Euclidean space $\mathbb{R}^n$.
- $φ(x)$ is non-empty and convex-valued for all $x \in S$. That is, $\phi(x)$ is a convex set for all $x$.
- $φ$ has a closed graph. That is, $\{(x,y): y \in\phi(x)\}$ is a closed set.

Then $φ$ has a fixed point. That is, there exists some $x \in S$ such that $x \in φ(x)$.

### Proof via Kakutani's Theorem

- Recall the definition of best response
  $$
  BR_i(\sigma_{−i}) = \{\sigma_i : \arg \max \sigma_i\in\sigma_i u_i(\sigma_i , \sigma_{−i})\}
  $$

- Define the correspondence as $BR(\sigma) = \{\sigma' : \sigma_i' \in BRi(\sigma_{−i})\}, ∀i.$
- (Nash 1950) The idea is to apply Kakutani’s fixed point theorem to the best-response correspondence $BR(\sigma) : \sigma φ\to \sigma$.
- $\sigma$ is compact and non-empty.
- BR(\sigma) is non-empty and convex-valued.
- BR(\sigma) has a closed graph.
- Thus a fixed point exists, and the fixed point is a Nash equilibrium.

### More Existence Examples

*Thm.* (D-G-F) For a strategic game
$$
G = \{\mathcal{I},(S_i)_{i\in\mathcal{I}},(u_i)_{i\in\mathcal{I}}\}
$$.
If

- $I$ is a finite set;
- $S_i$ is compact and convex;
- $u_i(s_i , s_{−i})$ is continuous in $s_{−i}$ ;
- $u_i(s_i , s_{−i})$ is continuous and quasi-concave in $s_i$ ,

then there exists a pure strategy Nash equilibrium.

*Def.* A mapping $T:(M,d) \to (M,d)$ is called a **contraction mapping** if for some $0\le \beta < 1$ and $\forall x,y\in X$:
$$
d(T(x),T(y)) \le \beta d(x,y)
$$
(Lipcshitz condition)

*Thm.* **(Contration Mapping Theorem)** Let $(X, d)$ be a non-empty complete metric space, then any contraction $f : X \to X$ has a unique fixed point.

*Thm.* If the best response mapping is a contraction on the entire strategy space, then there is a unique NE in the game.

*Example*: Cournot

## Lecture 6-7 : Extensive Form Games

### Warm-up: Centipede

- A pot of money, with initial amount of \$4.
- Two players take turns. The pot gains \$1 in each turn.
- At each player’s turn and the pot has p, the player can choose to split the money, take the share of $\lfloor\dfrac{p+4}{2}\rfloor$ and leaves the rest to the other. By doing this, the game ends.
- Or, the player can choose to do nothing and pass his turn.
- When the pot reaches \$10, two players split evenly and end the game.

*Extensive Form Game*: proposed to analyze dynamic games

### Dynamic Game

In this lecture, we consider **complete information** *(describles the game itself)*  case, i.e., the following information is common knowledge to all players:

- player set,
- structure of the game,
- available actions at each state,
- the payoff of the outcomes.

We also restrict to the case of **perfect recall** that players remember all the infomation he received during the play.

Example: A simple Card Game

### Game Tree

The extensive form game can be represented by a rooted tree $T$.

- **Nodes.** Each node in $T$ represents a possible state in the game.
  - Terminal nodes (outcome) $Z$. Each leaf state results in a certain payoff for each player.
  - Decision nodes. Each decision node $v$ in $T$ is associated with one of the players, indicating that it is his turn to play when $v$ is reached.
  - Exogenous events can be treated as decisions of the player of “Nature”, i.e., the “chance nodes”.
- **Edges.** The edges from an internal node to its resulting children node represents the an action and the corresponding next state. All edges from a node shows the possible moves of the player when the game reaches that state.

We exclude loops and multiple roots. Each non-toor node has exactly one immediate parent. The goal is to predicate the path of play.

### Imformation set

**Perfect Infomation**: during play, each player knows the complete history of previous moves, and hence which state of the game he is currently at.

- IMperfect imformation: players may not know the previous actions that kept secret by other players. So the player may not be able to distinguish between states.

**Imformation set**: An information set $h$ of player $i$ are the inner nodes of the game tree.

- All information sets $h \in H$ partitions the game tree, i.e., every node is in exactly one information set.
- For an information set $h_i$ of player $i$:
  - player $i$ makes the move for any state $u \in h_i$ ,
  - available actions for any $u, v \in h$ are the same,
  - given any $u, v \in h_i$ , player $i$ cannot distinguish which state he is currently at.

- When making decisions, the player knows which information set he's in, but he doesn't know which exactly state he's in.
- Game of perfection information is the special case when all information sets are singletons.
- Perfect recall rules out the possibility that $u$ is the predecessor of $v$ while they are in the same information set.

Let $H_i$ be the set of player $i$’s information sets, and let $A_i = ∪_{h_i\inH_i}A(h_i)$ be the set of all actions for player $i$:

*Def 1.* A **pure strategy** for player $i$ is a map $s_i : H_i \to A_i$ such that $s_i(h) \in A(h)$ for all $h \in H_i$ .

### Turning into Normal Form

Turnning extensive form into normal form is like every player plans the game ahead and chooses a strategy at the beginning simultaneously. The path of play is just the implementation of the chose strategies.

*Def 2.* A **mixed strategy** $\sigma_i$ of a player $i$ in an extensive form game is a distribution over pure strategies, i.e.,
$$
\sigma_i \in \DeltaS_i = \Delta \left(\prod_{h\inH_i} A(h) \right) .
$$
Meanwhile, we can define the behavioral strategies for extensive form games. The behavioral strategy specifies a probability distribution over actions at each hi , and the probabilities at different information sets are independent.

*Def 3.* **(Behavioral strategy)** A behavioral strategy $b_i$​ of player $i$​ is a product distribution on actions $A_i$​ at each information set $h$:
$$
b_i \in \prod_{h\inH_i} \Delta(A(h)).
$$

*Def 4.* **(Realization Equivalence)** Two strategies $\sigma_i$ and $\sigma_i'$ for player $i$ in an extensive form game are **realization equivalent** if for each strategy $\sigma_{−i}$ of the opponents and every node $v$ in the game tree, the probability of reaching $v$ when $(\sigma_i , \sigma_{−i})$ is employed is the same as when $(\sigma_i' , \sigma_{−i})$ is employed.

- It is enough to verify realization-equivalence for opponent strategy profiles that are pure
- The intuition is that two strategies gives the same distributions on outcomes.

*Thm.* **(Kuhn, 1953)** In a game of perfect call, mixed and behavior strategies are equivalent.

### Subgame Perfection

*Def.* **(Subgame)** A subgrame $G'$ of extensive form game $G$ is a subtree of game tree of $G$ that:

- begins at a singleton information set,
- includes all subsequent nodes,
- and does not cut any information sets.

with perfect information, every subtree is a subgame.

*Def.* **(Subgame Perfect Equilibrium)** A (behavioral) strategy profile $\sigma^\ast$ is a subgame perfect equilibrium of $G$ if $\sigma^\ast\vert_{G'}$ is a Nash equilibrium of every subgame $G'$ of $G$.

### Backward Induction

For finite games:

1. Find terminal subgames
2. Solve terminal subgames
   - Nash Equilirium is guaranteed to exist
3. Calculate the Nash equilibrium payoffs of the terminal subgames, and replace these subgames with the Nash payoffs.
   - By calculation, a “node” of subgame becomes an outcome

*Thm 3.* Any finite extensive form game has a subgame perfect equilibrium.

- Informal proof: beckward induction

*Cor 4.* **(Zermelo's Thm)** Any finite game of perfect information has a pure strategy SPE.

### Stackelberg Game

Stackelberg game: leader and follower.

- Leader moves first (commit), and then follower moves.
- Key: leader predicts and moves, follower responses.

Formally speaking, a Stackelberg game consists of a leader (l) and a follower (f). The objective of the follower is to choose her strategy to best response the leader:
$$
BR(\sigma_l) = \arg \max_{\sigma_f \in\Delta_f} u_f (\sigma_l , \sigma_f ).
$$
 The goal of the leader can be represented as follows.
$$
\max_{\sigma_l\in\Delta_l} u_l(\sigma_l , \sigma_f ) \text{ s.t. }\sigma_f \in BR(\sigma_l).
$$

- Any problem in this optimization? $BR(\sigma_l)$ may be a set value function.

*Def.* **(Strong Stackelberg Equilibirum)** We assume that the follower breaks ties in favor of the leader. This is an optimistic (in terms of the leader) view of the play.
**(Weak Stackelberg Equilibrium)** The follower breaks the tie adversarially.

- SSE guarantees existence, while WSE doesn't.

*Thm.* **(Leader's Advantege)** In a Stackelberg game, the leader achieves weakly more utility in SSE than in any Nash equilibrium.

Example: inspection, Security game

### Multi-stage Game with Observed Actions

Multi-stage game with observed actions: The game has $K$ stages;

- in each stage $k$, every player knows all the actions that were taken at any previous stage;
- each player moves at most once within a given stage;
- In each stage everyone moves “simultaneously”.

It could be too cumbersome (exponentially increasing) to construct game tree to describe multi-stage game. We abuse $h$ to also define "history" in the multi-stage game. (history = information set)

Denote $A_i(h^{k+1})$ as player i's possible actions in stage $k+1$ with history $h^{k+1}$.

*Thm 6.* In a finite multi-stage game with observed actions, strategy profile $\sigma$ is **subgame perfect** if and only if it satisfies the **one-shot deviation condition**, i.e., there is no player $i$ and no strategy $\hat \sigma_i$ that agrees with $\sigma_i$ except at a single stage $t$ and history $h^t$, and that $\hat \sigma_i$ is a better response to $\sigma_{−i}$ than $\sigma_i$ at history $h^t$.

### Infinite Game

Some multi-stage games could contain infinite stages.
For example, consider an infinite game with discounted payoff, where player i’s payoff is of the form:
$$
u_i(\sigma_i , \sigma_{−i}) = u_{i0}(\sigma_{i} , \sigma_{−i}) + γu_{i1}(\sigma_i , \sigma_{−i}) + γ^2u_{i2}(\sigma_i , \sigma_{−i}) + ...
$$
 Interpretation of discount factor $γ \in [0, 1]$: interest rate.

*Def 7.* An infinite extensive form game $G$ is **continuous** at $\infty$ if for any two strategies $\sigma$ and $\sigma'$ such that $\sigma(h) = \sigma' (h)$ for all histories $h$ in stages $t ≤ T$​, the payoff function $u_i$ satisfies
$$
\lim_{T\to\infty} \sup_{i,\sigma,\sigma'} | u_i(\sigma) − u_i(\sigma') |  = 0.
$$

- Intuition: compare the payoffs of two strategies which are identical for all information sets up to stage $T$ and could be different thereafter. As $T$ becomes infinitely large, the maximal difference between any two such strategies becomes arbitrarily small.

*Thm 8.* **(One-shot Deviation Principle)**

## Lecture 8: Repeated Games

### Term Paper

- Topic Comfirmation: 4.30
- Final ddl: ~~6.10~~ 6.19

### Repeated Games

Bargaining (Rubinstein's model): Recursion Structure

*Def.* **(Repeated Games)** We study the repeated strategic form game
$$
G = \{I, \{A_i\}_{i\in\mathcal{I}}, \{g_i\}_{i\in\mathcal{I}}\}
$$
for $T$ periods. Denote the repeated game as $G^T$. Payoff of player i at stage t:
$$
g_i(a^t_i , a^t_{−i} )
$$
, where
$$
a^t = (a^t_i , a^t_{−i} )
$$
is the action profile at period t.

Example: Discounted Payoff

Example: Repeated Prisoner's Dilemma

- Find SPE by backward induction. "Defect" is always a dominant strategy.

*Thm.* If every stage $G$ has a unique pure strategy equilibrium $a^\ast$, then in the repeated game $G^T$ with $T<\infty$, there's a unique SPE where $a^t = a^\ast$ for all $t = 0,1,\cdots, T$.

### Tit-for-Tat Strategy

The Tit-for-Tat strategy in Iterated Prisoner’s Dilemma is the following: Cooperate in round 1. For every round $t > 1$, play what the opponent played in round $t − 1$.

### Trigger Strategies

A trigger strategy threatens other players with a punishment action if they deviate from an (implicitly agreed) action profile.

A non-forgiving trigger strategy (or grim trigger strategy) $s$ would involve this punishment forever after a single deviation from other players.

Formally writing, A non-forgiving trigger strategy (for player i) takes the following form:
$$
a_i^t = \begin{cases} \bar a_i, \text{ if $a_\tau = \bar a$ for all $\tau < t$ } \\ \underline{a}_i, \text{if $a_\tau \ne \bar a$ for some $\tau < t$}\end{cases}
$$
Here $\bar a$ is the implicitly agreed action profile and $\underline{a}_i$ is the punishment action.

- *Prop.* In the infinitely repeated Prisoner's Dilemma with $\delta \ge \dfrac12$, there exists an SPE in which the outcome is that both players cooperate in every period.

- *proof.* Consider the following symmetric trigger strategy profile:
  $$
  s_i(h_t) = \begin{cases} C, \text{ if both players have played $C$ in every period} \\ D, \text{ if one player has ever played $D$ in the past}\end{cases}
  $$
  
### Folk Theorem

*Def.* Set of **feasible payoffs** is defined as:
$$
V = Conv\{v \in R^I | \text{ there exists } a \in A \text{ s.t. } g(a) = v.\}
$$
*Def.* Player i’s **minmax payoff** is the the lowest payoff that player i’s opponent can hold him to:
$$
\underline{v}_i = \min_{\alpha_{−i}} \max_{\alpha_i} g_i(\alpha_i , \alpha_{−i})
$$
And the **Minmax strategy profile against $i$**: .
$$
m^i_{−i} = \arg \min _{a_{−i}} \left[ \max_{a_i}g_i(a_i , a_{−i})\right]
$$
 Let $m_i^i$ denote the corresponding strategy of player $i$ such that
$$
g_i(m_i^i , m_i^{−i} ) = g_i(m_i ) = v_i.
$$

*Prop.* Individual rationality (IR): In any Nash equilibrium, player i must receive at least $v_i$ .

*Thm.* **(Nash Folk Theorem)** If $(v_1, ..., v_I )$ is feasible and strictly individual rational, then there exists $\underline{δ} < 1$ such that for all $δ ≥ \underline{δ}$, there is a Nash equilibrium of $G^\infty(δ)$ with payoffs $(v_1,\cdots,v_I)/(1 − δ)$.

- *proof.* Assume there exists a profile $a = (a_1, ..., a_I )$ such that $g_i(a) = v_i,\forall i$. Consider the following strategies:

  - Play $(a_1, \cdots, a_I )$ as long as no one deviates.

  - If some player $j$ deviates, play $m_i^j$ thereafter (minmax strategy against $j$).

*Thm.* **(Friedman)** Let $a^{NE}$ be a static equilibrium of the stage game with payoffs $e^{NE}$ . For any feasible payoff $v$ with $v_i > e^{NE}_i,\forall i \in I$, there exists some $δ < 1$ s.t. $\forall δ ≥ \underline{δ}$, there exists a SPE of $G^\infty(δ)$ with payoffs $v$.

## Lecture 9: Two-player Zero-sum game

### Basic definitions

Payoff matrix: row player $R$, column player $C = -R$.

Denote the simplex of available mixed strategies of row player by $\Delta_m$ (and $\Delta_n$​ for the column player)
$$
\Delta_m =
\{x \in \mathbb{R}^m : x_i ≥ 0,\sum_{i=1}^m x_i = 1\},
\Delta_n =
\{y \in \mathbb{R}^n : y_i ≥ 0,\sum^n_{j=1} y_j = 1\}.
$$
Given a pair of mixed strategy $x \in \Delta_m$ and $y \in \Delta_n$, the expected payoff of the row and column player are $x^T Ry$ and $x^TCy$, respectively.

### Example: Conservative players

*Thm 1.* **(Von Neumann’s Minimax Theorem)** For any two-player zero-sum game with $m × n$ payoff matrices $R$, $C$, there is a number $z$, called the **value of the game**, satisfying
$$
\max_{x\in\Delta_m} \min_{y\in\Delta_n} x^T Ry = z = \min_{ y\in\Delta_n} \max_{ x\in\Delta_m} x^T Ry
$$
*Def.* **(Saddle point)** A saddle point of a payoff matrix R is a pair $(i^\ast , j^\ast)$ such that:
$$
\max_i R_{ij^\ast} = R_{i^\astj^\ast} = \min_j R_{i^\astj}
$$

- Saddle point $\Leftrightarrow$ pure strategy Nash equilibrium.

*Cor 2.* There exists a Nash equilibrium in every two-player zero-sum game. (The minimax point)

*Thm 3.* **(Separating Hyperplane Theorem)** Suppose that $K \subseteq \mathbb{R}^d$ is closed and convex. If $0\notin K$, then there exists $z \in \mathbb{R}^d$ and $c \in \mathbb{R}$ such that $0 < c < z^T v$ for all $v\in K$.

​ *Proof1.* It's obvious that
$$
\max_{x\in\Delta_m} \min_{y\in\Delta_n} x^T Ry \le \min_{ y\in\Delta_n} \max_{ x\in\Delta_m} x^T Ry
$$
​ So we only need to show the opposite inequality. Suppose that
$$
\min_{y\in\Deltan} \max_{x\in\Deltam} x^T Ry > \lambda.
$$
​ Define a new game with payoff matrix $\hat R$ given by $\hat R_{ij} = R_{ij} − \lambda$. So we have LHS of the left part is $>0$.

​ Construct set $K$ of all vectors which dominate some gain vector $\hat R y \in \mathbb{R}^m$:
$$
K = \{\hat R y + v : y \in \Delta_n, v \in \mathbb{R}^m, v ≥ 0\}.
$$
​ Set $K$ is convex and closed (check $\Delta_n$ and $v$). Thus according to the Separating Hyperplane Theorem, there exists $z \in R$ and $c > 0$ such that $z^T w > c > 0$ for all $w \in K$. That is,
$$
z^T(\hat Ry + v) > c > 0 \text{ for all }y \in \Delta_n \text{ and }v \ge 0.
$$
​ We can see that $z\ge 0$.

*Prop.* If the payoff matrix of a zero-sum game is antisymmetric, i.e., $R_{ij} = −R_{ji}$, then the game has value $0$.

### Duality

General Optimization Porblem:
$$
\min f(x)\\ \text{ s.t. } f_i(x) ≤ 0, i = 1,\cdots, m, \\ h_i(x) = 0, i = 1,\cdots, p.
$$
Convex Optimization: an optimization problem with a convex objective function and a convex feasible set.

Linear programming: special case of convex optimization when both objective function and constraint functions are all linear.

*Def.* **(Lagrangian function)** The Lagrangian function $f:\mathbb{R}^n \times \mathbb{R}^m \to \mathbb{R}$ is defined as:
$$
L(x,\lambda) = f(x) + \sum_{i=1}^m \lambda_if_i(x) + \sum_{j=1}^n \nu_i h_i(x)
$$

*Def.* **(Lagrangian dual function)** The Lagrangian dual function $g : \mathbb{R}^m × \mathbb{R}^p \to \mathbb{R}$ is defined as the minimum value of the Lagrangian function over x:
$$
g(\lambda, \nu) = \inf_x L(x, \lambda, \nu) = \inf_x \left( f(x) + \sum^m_{i=1} \lambda_if_i(x) + \sum^p_{i=1} \nu_ih_i(x)\right)
$$

- The dual function $g(\lambda)$ is always concave even if the primal problem is not convex.
- Weak duality: Given any $\lambda ≥ 0$, the dual function $g(\lambda, \nu)$ yields a lower bound of the optimal primal objective value $f(x^\ast )$.

$$
g(\lambda, \nu) ≤ f(x^\ast), \forall \lambda ≥ 0.
$$

- Strong duality holds if $d^\ast= p^\ast$.

### Linear Programming perspective

If the row player is forced to announce his strategy in advance, the corresponding LP for column player is:
$$
LP(1):\max_x z \\
\text{ s.t. }x^T R − z1^T ≥ 0,\ x^T 1 = 1,\  x_i ≥ 0,∀i
$$

Consider the dual problem of LP1:
$$
LP(2): \min_y &z' \\&\text{ s.t. } − y^T R^T + z'1^T \ge 0,\ y^T 1 = 1,\  y_j \ge 0,\forall j.
$$

Note that $C = −R$, and let $z'' = -z'$ , we can change LP(2) to the following equivalent LP.
$$
LP(3): \max z'' \\\text{ s.t. } Cy − z''1 \ge 0,\ y^T 1 = 1,\ y_j ≥ 0, \forall j.
$$
*Thm 8.* If $(x^\ast , z)$ is optimal for LP(1), and $(y^\ast , z'')$ is optimal for LP(3), then $(x^\ast,y^\ast)$ is a Nash equilibrium of the two-player zero-sum game $(R, C)$. Moreover, the payoff of the row/column player in this Nash equilibrium are $z$ and $z'' = −z$, respectively.

*Thm 9.* If $(x, y)$ is a Nash equilibrium of $(R, C)$, then $(x, x^T Ry)$ is an optimal solution of LP(1), and $(y, −x^T Cy)$ is an optimal solution of LP(2).

### Fictitious Play

In every round, each player plays a best response to the opponent’s historical strategy:
$$
i_t \in \arg \max_i\left[e_i^T R \left(\frac{1}{t-1} \sum_{\tau < t}e_\tau\right) \right], j_t \in \arg \max_j\left[\left(\frac{1}{t-1} \sum_{\tau < t}e_\tau\right)^TC e_j\right]
$$
*Thm.* If the players of a zero-sum game $(R, C)$ interact via fictitious play, then  
$$
\lim_{t\to \infty} \max_i e^T_i Ry_t = \lim_{t\to \infty} \min_j x^T_t R e_j = v,
$$
where v is the value of the row player in the game.

## Lecture 10: Bayesian Games

### Incomplete Information

Lacking infromation about the game itself.

Examples: Auctions, Signaling games, Market competition

### Example: Non-cooperate Sex game

Consider player 2 has two types: wishes to cooperate or not. Each type with probability 1/2 (common knowledge). Only the player 2 knows which type do they in.

Payoff matrices:

| Type 1 | B    | F    |
| ------ | ---- | ---- |
| B      | 2,1  | 0,0  |
| F      | 0,0  | 1,2  |

| Type 2 | B    | F    |
| ------ | ---- | ---- |
| B      | 2,0  | 0,2  |
| F      | 0,1  | 1,0  |

The pure strategy $(B,(B,F))$, i.e. meeting at ballet is an equilibrium:

- For player 2, this is always her best response to $B$;

- For player 1, the expected payoff is
  $$
  \mathbb{E}\{u_1(B,(B,F))\} = \frac12 \times 2 + \frac12 \times 0 = 1
  $$
  If he deviates, the expected payoff is
  $$
  \mathbb{E}\{u_1(F,(B,F))\} = \frac12 \times 0 + \frac12 \times 1 = \frac12
  $$

However, meeting at football, i.e. $(F,(F,B))$ is not a Bayesian Nash equilibrium.

### Definition

A Bayesian game consists of

- A set of players $\mathcal{I}$;
- A set of actions (pure strategies) for each player i: $S_i$ ;
- A set of types for each player i : $\theta_i \in \theta_i$ ;
- A payoff function for each player i : $u_i(s_1, \cdots, s_I , \theta_1, \cdots, \theta_I )$ (can be extended to mixed strategy);
- A (joint) probability distribution $p(\theta_1, \cdots, \theta_I )$ over types (or $P(\theta_1, \cdots, \theta_I )$ when types are not finite). **(Common Knowledge)**

Bayesian: Given $p(\theta_1, \cdots, \theta_I )$, player $i$ can infer the conditional distribution $p(\theta_{−i} \vert \theta_i)$ by **Bayes rule**.

*Def. (Harsanyi's transformation)* Games of imcomplete information can be thought as games of complete but imperfect information. In this game, natural makes his first move secretly, which chooses the r.v. $(\theta_1,\theta_2,\cdots,\theta_n)$, and only informs player $i$ of $\theta_i$.

### Strategy and Expected payoff

Since the payoff, types and prior distributions are common knowledge, we can compute the expected payoffs of player $i$ of type $\theta_i$ as (when types are finite):
$$
U_i(\sigma_i' , \sigma_{−i} , \theta_i) = \sum_{\theta_{−i}} p(\theta_{−i} | \theta_i)u_i(\sigma_{i}' , \sigma_{−i}(\theta_{−i}), \theta_i , \theta_{−i})
$$
*Definition 1.* The strategy profile $\sigma$ is a Bayesian Nash equilibrium if for all $i \in \mathcal{I}$ and for all $\theta_i \in \theta_i$ , we have:
$$
\sigma_i(\theta_i) \in \arg \max_{\sigma_i'\in\sigma_i} \sum_{\theta_{−i}} p(\theta_{−i} | \theta_i)u_i(\sigma_i' , \sigma_{−i}(\theta_{−i}), \theta_i , \theta_{−i})
$$

### Example: Public Good I

Each player benefits when the public good is provided, but each would prefer the other player to incur the cost of supplying it. Payoff matrix:

|            | Contribute           | Don’t            |
| ---------- | -------------------- | ---------------- |
| Contribute | $(1 − c_1, 1 − c_2)$ | $ (1 − c_1, 1) $ |
| Don’t      | $ (1, 1 − c_2) $     | $(0, 0)$         |

- Assume that the actions are chosen simultaneously and that players know only their own costs.

- Suppose the cost $c_1$ of player 1 is common knowledge, and we have $c_1 < 1/2$.
- Player 2 has cost $c$ with probability $p$, $\bar c$ with probability $1 − p$. Assume that $0 < c < 1 < \bar c$ and $p < 1/2$. The distribution $p$ is common knowledge.

BNE: (contribute, don't contribute)

### Example: Public Good II

With the same payoff matrix as in I, but $c_1,c_2$ are randomly drawn from $U(0,2)$.

### Example: Incomplete Information Cournot

Suppose that two firms both produce at constant marginal cost. Inverse demand function is given by $P(Q)$ as in the usual Cournot.

- Firm 1 has marginal cost equal to $C$ (and this is common knowledge).
- Firm 2’s marginal cost is private information. It is equal to $C_L$ with probability $\theta$ and to $C_H$ with probability $(1 − \theta)$, where $C_L < C_H$.

This game has 2 players, 2 states (L and H) and the possible actions of each player are $q_i \in [0, \infty)$, but firm 2 has two possible types. The payoff functions of the players, after quantity choices are made, are given by
$$
u_1(q_1, q_2) =q_1(P(q_1 + q_2) − C),
u_2((q_1, q_2), t) =q_2(P(q_1 + q_2) − C_t), t \in \{L,H\}.
$$

### Example: First Price Auction

Consider a first-price auction, where some risk-neutral players bid for one item.

- Each player’s valuation of the item is independently and identically distributed on the interval $[0, \bar v]$ with c.d.f $F$, with continuous density $f$ and full support on $[0, \bar v]$. The distribution $F$ is common knowledge.

- Each one observes his own valuation and decides his bid. The bidder with higher bid wins (tie breaks equally), and pay his bid Thus, the winner $i$ gets payoff $v_i − b_i$ , others get payoff $0$.

- Bidder i’s strategy is $β_i : [0, \bar v] \to [0, \infty]$.

In the simple case of two players, and the valuations are drawn from $U(0,1)$. The strategy profile $(\beta_1(v_1), \beta_2(v_2)) = (\frac12 v_1, \frac12 v_2)$ is a BNE.

In general cases: Consider $N$ bidders, with i.i.d. value $v_i$ in $[0,\bar v]$. Suppose that bidders $j  \ne 1$ follow the symmetric and differentiable equilibrium strategy $β$, where $β : [0, \bar v] \to [0, \infty]$ is increasing and differentiable.

We'll then characterize $\beta$ s.t. when all other bidders play $\beta$, then it is also a best response for bidder 1:
$$
u(b_1,v_1) = (v_1-b_1) \cdot \prod_{j>1}\mathbb{P}[b_j = \beta(v_j) \le b_1] = \max_{b_1} F^{n-1} (\beta^{-1}(b_1)) \cdot (v_1-b_1).
$$
First Order Condition Approach: Use first order dirivative to maximize this function:
$$
\frac{\partial}{\partial b_1} = (v_1-b_1)(n-1)F^{n-1}(\beta^{-1}(b_1)) f(\beta^{-1}(b_1)) \frac{1}{\beta(\beta^{-1} (b_1))} - F^{n-1}(\beta^{-1}(b_1)) = 0.
$$
Plug in $b_1 = \beta(v_1), v_1 = \beta^{-1}(b_1)$, we will finally obtain
$$
[\beta(v)F^{n-1}(v)]' = v[F^{n-1}(v)]' \Rightarrow \beta(v) = v- \frac{\int_0^v F^{n-1}(x)dx}{F^{n-1}(v)} = \mathbb{E}[\max_{j>1}v_j : \max_{j>1}v_j < v].
$$

### Perfect Bayesian Equilibrium

*Definition 2.* A Perfect Bayesian Equilibrium is a strategy profile $\sigma^\ast$ together with a belief system $µ$ such that

- At every information set, strategies are optimal given beliefs and opponents’ strategies (sequential rationality).
  $$
  \sigma^\ast_i (h_i) \in \arg \max \mathbb{E}_{µ_i(x|h_i)}u_i(\sigma_i , \sigma^\ast_{−i} | h, \theta_i , \theta_{−i})
  $$
  
- Beliefs are always updated according to Bayes rule when applicable.

## Lecture 11 Auctions

### Vickrey Auction

Notations:

- Allocation $x_{ij} \in [0,1]$, payment $p_i\in\mathbb{R}$.
- Preference

Assumptions:

- Utility

- Risk-neutral

- **Quasi-linear** & **self-interested**: the utility for each buyer is a quasi-linear function of his/her **own** outcome.

- **Additive valuation**
  $$
  u_i(o) = v_i(x_i) - p_i = \sum_j v_{ij} \cdot x_{ij} = \vec v_i \cdot \vec x_i - p_i.
  $$

$n$ buyers for 1 item, the buyer with highest price wins and pays the second-highest price.

- Optmal strategy: bid your price
- Key properties: Efficient (maximizing social welfare), Truthful ($b(v) = v$ is indeed optimal).

### Vickrey-Clarke-Groves Auction

$n$ buyers for $m$ items, non-additive valuation: $u_i(o) = v_i(\vec x_i) - p_i$.

VCG (family):
$$
\vec x^\ast = \arg\max_{\vec x' \in \mathcal{X}} \sum_i \hat v_i(\vec x_i').
$$
where $\mathcal{X}$​ is the set of feasible allocations. Price and utility
$$
p_i = - \sum_{k\ne i} \hat v_k (\vec x_k^\ast) + h_i (\hat v_{-i}) \\
u_i = v_i(x_i^\ast) + \sum_{k\ne j} \hat v_k(\vec x_k^\ast) - h_i(\hat v_{-i})
$$
here $h_i (\hat v_{-i}) = \max_{x' \in \mathcal{X}} \sum_{k \ne i} \hat v_k (\vec x_k')$.
**(Clarke pivot rule):** Best possible income of other agents.

*Prop.* Truthful, efficient, Individual rationality, no positive transfer

## Lecture 12 PBE

### Recall: Perfect Bayesian Equilibrium

A Perfect Bayesian Equilibrium is a strategy profile $\sigma^\ast$ together with a belief system $µ$ such that

- At every information set, strategies are optimal given beliefs and opponents’ strategies (sequential rationality).
  $$
  \sigma^\ast_i (h_i) \in \arg \max \mathbb{E}_{µ_i(x|h_i)}u_i(\sigma_i , \sigma^\ast_{−i} | h, \theta_i , \theta_{−i})
  $$

- Beliefs are always updated according to Bayes rule when applicable.

Requirements:

1. At each infomation set, the player to move must have a belief on which node in the infomation set has been reached by the play of the game. (Prob. distribution over the nodes in the info set)
2. Given the beliefs. the players' strategies must be sequential rational. That is, the player must take the optimal move given his belief on the information set and other players' subsequent strategies. (A complete plan covering every contingency)
3. At infomation sets on the equilibrium path, beliefs are determined by Bayes rule and players' equilibrium strategies.
4. At infomation sets off the equilibrium path, beliefs are determined by Bayes rule and players' equilibrium strategies where possible.

### Signaling game

*Def.* A signaling game involves two players: A sender (S) and a receiver (R).

- Nature draws a type $t_i$ from a set of feasible types $T = \{t_1,\cdots,t_I\}$ according to a probability distribution $p$.
- The sender observes $t_i$ and chooses a message $m_j$ from the message set $M = \{m_1,\cdots,m_J\}$.
- The receiver observes $m_j$, and chooses an action $a_k$ from a set of feasible actions $A = \{a_1,\cdots, a_K\}$

- Payoffs are given by $u_S(t_i,m_j,a_k)$ and $u_R(t_i,m_j,a_k)$.

*Example.* Two-way signaling game

- Sender's strategy: 4 possibilities

- Receiver's strategy: 4 possibilities

- PBE Requirements:

  - (1) After observing $m_j$, the receiver must have a belief on $\mu(t_i \vert m_j)$.

  - (2R) The receiver's action maximizes his expected utility according to his belief:
    $$
    a^\ast(m_j) = \arg\max_{a_k\in A} \sum_{t_i\ in T} \mu(t_i \vert m_j) u_R(t_i,m_j,a_k)
    $$

  - (2S) The sender's message maximizes his utility given the receiver's strategy $a^\ast(m_j)$:
    $$
    m^\ast(t_i) = \arg\max_{m_j \in M}u_S(t_i,m_j, a^\ast(m_j))
    $$

  - (3) For each $m_j \in M$, is there exists $t_i\in T$ s.t. $m^\ast(t_i) = m_j$, then the receiver's belief at information set $m_j$ should follow the Bayes rule and sender's strategy:
    $$
    \mu(t_i \vert m_j) = \frac{p(t_i)}{\sum_{t_i\in T_j} p(t_i)}
    $$
    Here $T_j$ denotes the set of the types that send the message $m_j$ at equilibrium.

*Example.* Spence's Job-Market Signaling

### Social Choice: Voting Schemes

Consider a set of alternatives $A$ (the candidates), a set $I$ of $n$ voters. Denote by $L$ the set of linear orders on $A$ ($L$ is isomorphic to the set of permutations on $A$). For every voter $i$, he holds a preference $\succ$ which is a complete and transitive order on $A$.

- Majority rule
- Pluality rule
- Pairwise comparison
- Borda count
- Condorcet winner criterion: If a candidate beats all other candidates in pairwise contests, then he should be the winner of the election.
- Condorcet loser criterion: The system should never select a candidate that loses to all others in pairwise contests.

*Def.* **(Social Welfare)** A function $W:L^n \to L$ is called a socail welfare function; a function $f:L^n \to A$ is called a social choice function.

Unrestricted domains: The domain of $W(\succ_1,\succ_2,\cdots,\succ_n)$ must include all possible combination of individual preference relations on $A$.

Desired properties:

- Anonymity (i.e. symmetry)
- Condorcet winner criterion
- Unanimity: if $a\succ_i b$ for all voters $i$, then $a\succ b$ in social choice.
- Independent of irrelevant alternatives (IIA): the social preference between any two alternatives a and b depends only on the voters’ preferences between a and b.
- Non dictatorial: Voter $i$ is a dictator if for all $\succ_1,\succ_2\cdots,\succ_n$, we have $W(\succ_1,\cdots,\succ_n) = \succ_i$.
- Monotone: moving $A$ higher should not move $A$ down in society ranking.

### Arrow's Impossiblity Theorem

*Thm.* Every social welfare function over a set of more than 2 candidates $(\lvert A\rvert \ge 3)$ that satisfies unanimity and independence of irrelevant alternatives is a **dictatorship**.

*Lemma.* **(pairwise neutrality)** Given unanimity and IIA of $W$, let $\pi = (≻_1, ... ≻_n)$ and $\pi'= (≻_1' ,\cdots, ≻_n' )$ be two vote profiles such that for every voter i, $a ≻_i b ⇔ c ≻_i' d$. Then $a ≻ b ⇔ c ≻'d$, where $≻= W(\pi)$ and $≻'= W(\pi' )$.

## Lecture 13 Matching

### Examples of Voting

- Plurality Voting: chooses the candidate who is ranked first by the largest number of voters.
- Runoff: If no candidate has a majority in the first round, then the two leading candidates compete in a second round (India, Brazil, and France).
  - Vulnerable: fails monotonicity
  - Satisfy Condorcet winner/loser criterion? No, Yes.

- Example: Borda Count
  - Satisfies IIA with preference strength, but does not satsify IIA and Condorcet winner criterion
  - Suffers from manipulation
- Approval voting: votes can approve as many candidates as they wish
  - satisfies monotonicity

### Stable Matching

- Centralized and Decentralized Market
- National Residency Match Program (in US): centralized
- Gale-Shapley Algorithm
  - Proposer-optimal
  - Attainability

- Preferences by Compatibility: In this case, we have a matrix
$$
A = (a_{i,j})_{n\times n}
$$
s.t.
$$
i_1\succ_j i_2 \Leftrightarrow a_{i_1,j} > a_{i_2,j} \text{ and } j_1\succ_i j_2 \Leftrightarrow a_{i,j_1} > a_{i,j_2}.
$$
  - There exists a unique stable matching.

### Matching: House Allocation

- An allocation is an n-dimensional vector $a$ whose i-th component, $a_i$, is the ID of the house assigned to agent $i$.
- Feasibility: $a_i \ne a_j$ for all $i \ne j$. Let A denote the set of all feasible allocations.
- A set S of agent is a block coalition for an allocation a if there exists a $z \in A(S)$ such that:
  - for all $i \in S$, $z_i ⪰_i a_i$.
  - exists $j \in S$ that $z_j ≻_j a_j$ .
- The set of allocations that is not blocked by any subset of agents is called the core.

#### Top Trading Cycle Algorithm (TTC)

- Each agent i points to his most preferred house (possibly i’s own, we use the same node to identify the agent and its own house).
- Give each agent in a cycle the house he points at and remove the agent from the market.
- Repeat above steps if unmatched agents remain.

*Thm.* The core of house allocation problem consists of exactly one matching.

- The outcome of the TTC mechanism cannot be blocked cannot make any agent matched in the first round better off;
- cannot make any agent matched in the second round better off without making some of the agents matched in the first round worse off;
- cannot make any agent matched in round $n$ better off without making some agents matched in earlier rounds worse off.

*Thm.* No person has an incentive to misreport his preferences.

### Congestion Game

Huge number of players and strategy space, but onlt the number matters (e.g. traffic congestion)

*Def.* A **congestion game** is defined on a tuple $(N, R, A, c)$, where

- $N$ is a set of $n$ agents;

- $R$ is a set of $r$ resources;
- $A = A_1 × ... × A_n$, where $A_i ⊆ 2^R \setminus \{∅\}$ is the set of actions for agent $i$;
- $c = (c_1, ..., c_r)$, where $c_k : \mathbb{N} \to R$ is a cost function for resource $k \in R$.

Denote $\#: R\times A \to \mathbb{N}$​ as the function that counts the number of players who took any action that involves resource $r$​ under action profile $a$​. Then we can define the utility function as:
$$
u_i(a) = -\sum_{r\in R, r\in a_i} c_r(\#(r,a)).
$$
*Thm.* Every congestion game has a pure-strategy Nash equilibrium

### Potential Game

*Def.* A game $G = (N, A, U)$ is an (exact) potential game if there exists a function $P : A \to R$ such that for all $i \in \mathbb{N}$, all $a_{−i} \in A_{−i}$ and $a_i , a_i' \in A_i$,
$$
u_i(a_i , a_{−i}) − u_i(a_i' , a_{−i}) = P(a_i , a_{−i}) − P(a_i' , a_{−i}).
$$
Ordinal potential game: $u_i(a_i , a_{−i}) − u_i(a_i' , a_{−i}) >0 $ iff $P(a_i , a_{−i}) − P(a_i' , a_{−i}) > 0$.

*Thm.* Every (finite) potential game has a pure-strategy Nash equilibrium.

*Thm.* Every congestion game is a potential game.

- By constructing a potential function $P(a) = \sum_{r\in R} \sum_{j=1}^{\# (r,a)} c_r(j)$.

### Myopic Best Response Dynamics

A straightforward way of computing Nash equilibrium in a normal form game is the myopic best response dynamics.

Myopic Best Response: While there exists an agent $i$ that is not best responding to $a_{−i}$ Do:

- $a_i' \leftarrow$ some best response by $i$ to $a_{−i}$
- $a ← (a_i' , a_{−i})$.

*Thm.* The Myopic Best Response procedure is guaranteed to find a pure-strategy Nash equilibrium of **a potential game**.

*proof.* Potential increase strictly in each step of while loop.
