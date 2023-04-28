---
layout: article
tag: notes
title: "Notes: Numerical Analysis (zh-cn)"
mathjax: true
excerpt_type: html
---

线性方程组的直接解法、最小二乘、线性方程组的迭代解法、特征值问题、非线性方程（组）、插值方法、函数逼近、数值积分、ODE初值问题的数值方法 <!--more-->

## Chapter 2 线性方程组的直接解法

- Gauss消元法，LU分解

- Doolittle分解方法，（对称矩阵）Cholesky分解方法，加边Cholesky，三对角矩阵分解，循环三对角矩阵，稀疏矩阵

- 矩阵的条件数：对任意一种从属范数，定义为
  $$
  \text{cond}(A) = ||A||\cdot ||A^{-1}||
  $$

  - 七条性质

  - *Thm.* 若 $A$ 可逆，则
    $$
    \min_{A+\delta A奇异}\frac{||\delta A||_2}{||A||_2} = \frac{1}{\text{cond}(A)_2}.
    $$
    即条件数越大，矩阵越接近于奇异。

  - *Thm.* 设$x'$是方程 $Ax = b$ 的近似解，$r = b - Ax'$，则有
    $$
    \frac{1}{\text{cond}(A)} \frac{||r||}{||b||} \le \frac{||x'-x||}{||x||}\le \text{cond}(A)\frac{||r||}{||b||}
    $$

- 预处理：降低条件数

## Chapter 3 最小二乘

### 3.1 最小二乘问题

- 问题：求 $x\in \mathbb{R}^n$，使得 $\lVert b-Ax \rVert_2 = \min_{y\in\mathbb{R}^n} \lVert Ay-b \rVert_2$

  - *Thm.* $\text{rank}(A) = \text{rank}[A\ b]$，则$Ax=b$有解
  - *Thm.* $Ax=b$ 的最小二乘解总是存在。当且仅当$N(A) = 0$时，解唯一。

- *Thm.* $x$ 是 $Ax=b$ 的最小二乘解，当且仅当x是*法方程*
  $$
  A^TA x = A^Tb
  $$
  的解。若$A$列满秩，则可以用Cholesky分解求解。
  
- 误差分析：考虑 $\tilde b = b + \delta b$ 有一处扰动，此时新的解为 $\tilde x = x + \delta x$，则

  - *Thm.* 考虑 $b_1, \tilde b_1$ 分别为 $b$ 和 $\tilde b$ 在 $A$ 的列空间 $R(A)$ 上的投影，则
    $$
    \frac{||\delta x||_2}{||x||_2} \le K_2(A) \frac{||b_1 - \tilde b_1||_2}{||b_1||_2}
    $$
    其中 $K_2(A) = ||A||_2 || A^\dagger||_2$ ，$A^\dagger$ 定义为 $A$ 的Moore-Penrose广义逆（这里 $A^\dagger = (A^TA)^{-1}A^T$ ）。

  - *Thm.* 若$A$ 列满秩，则 $K_2(A)^2 = \text{cond}_2(A^TA)$.

### 3.2 QR分解

- 初等正交变换：HouseHolder变换（反射），Givens变换（旋转）

- *Thm.* 若 $A$ 是 $m\times n$ 矩阵，$m>n$，则存在 $n\times n$ 的正交矩阵 $Q$ 和上三角矩阵 $R$，使得
  $
  A = Q\begin{bmatrix}
  R \\ 0
  \end{bmatrix}.
  $

- Gram-Schmit正交化

## Chapter 4 线性方程组的迭代解法

### 4.1 单步定常线性迭代

*Thm.* 设 $x^\ast$ 是方程 $x=Bx + f$ 的唯一解， $\lVert B \rVert = q<1$，则迭代法 $x^{(k+1)} = Bx^{(k)} + f$ 收敛，且

$$
||x^{(k)} - x^\ast|| \le \frac{q}{1-q}||x^{(k)} - x^{(k+1)}||. \\
||x^{(k)} - x^\ast|| \le \frac{q^K}{1-q}||x^{(1)}-x^{(0)}||. \\
||e^{(k)}|| \le ||B||^k||e^{(0)}||.
$$

*Def.* 上述迭代的前 $k$​ 步的平均收敛率：

$$
R_k(B) = -\ln||B^k||^{1/k}
$$

渐进收敛率
$$
R(B) = \lim_{k\to\infty}R_k(B) = -\ln\rho(B)
$$

### 4.2 Jacobi迭代和G-S迭代

- Jocobi迭代：$B_J = D^{-1}(L+U),f_J = D^{-1}b$
- G-S迭代：$B_G = (D-L)^{-1}U, f_G = (D_L)^{-1}b$

*Thm.* 若 $A$ 严格对角占优或不可约弱对角占优，则Jacobi迭代和G-S迭代均收敛。

*Thm.* $A$ 对称，对角线元素非负，则 $Ax=b$ 的Jacobi迭代收敛 $\Leftrightarrow$ $A,2D-A$ 均正定。

*Thm.* $A$ 对称非奇异，对角线元素大于0，则 $Ax=b$ 的G-S迭代收敛 $\Leftrightarrow$ $A$ 正定。

### 4.3 超松弛迭代法SOR

- SOR方法：$x_i^{k+1} = \omega \bar x_i^{(k+1)} + (1-\omega)x_i^{(k)}$ （将G-S的结果和 $x_i^{(k)}$ 加权平均）

- 矩阵形式：$B_\omega = (D-\omega L)^{-1}\left[(1-\omega)D + \omega U\right],\ f_\omega = \omega(D-\omega L)^{-1}b.$

  - *Thm.* $\rho(B_\omega) \ge \lvert\omega - 1\rvert$.

  - *Thm.* $A$ 对称正定，$0<\omega<2$，则 $Ax=b$ 的SOR迭代收敛。

- 最优松弛因子 $\omega_0 = \arg\min_{0< \omega < 2} \rho(B_\omega)$

### 4.4 多重网格法

### 4.5 对称矩阵：共轭梯度法

对于对称正定矩阵 $A$， 定义 $\varphi(x) = \dfrac12 x^TAx - b^Tx$，则 $Ax=b$ 的解 $\Leftrightarrow$ $\varphi$ 的极小值点

#### 4.5.1 最速下降法

沿着梯度方向下降：
$$
r^{(k)} = b - Ax^{(k)}; \\
\alpha^{(k)} = \frac{\left<r^{(k)}, r^{(k)}\right>}{\left<r^{(k)}, Ar^{(k)}\right>};\\
x^{(k+1)} = x^{(k)} + \alpha^{(k)}r^{(k)}.
$$
*Thm.* 在迭代过程中，有
$$
||x^{(k)}-x^\ast||_A \le \left(\frac{\lambda_n - \lambda_1}{\lambda_n + \lambda_1}\right)^k ||x^{(0)}-x^\ast||_A
$$
其中 $||x||_A = \sqrt{x^TAx}$.

#### 4.5.2 共轭梯度法

- 此时下降方向取为共轭向量组张成的子空间 $\text{span}(p^{(0)},p^{(1)},\cdots)$, 满足 $\left<Ap^{(i)},p^{(j)}\right> = 0$

- 迭代方法：$x^{(k+1)} = x^{(k)} + \alpha_kp^{(k)}$, 其中 $\alpha_k = \text{argmin}_{\alpha \in \mathbb{R}^n} \varphi(x^{(k)} + \alpha p^{(k)}) = \dfrac{\left<r^{(k)}, p^{(k)}\right>}{\left<r^{(k)}, Ap^{(k)}\right>}$.

- 子空间的确定：可以根据余项 $r^{(k)}$​ 来取：

$$
p^{(k)} = r^{(k)} - \dfrac{\left<r^{(k)}, Ap^{(k-1)}\right>}{\left<p^{(k-1)}, Ap^{(k-1)}\right>}p^{(k-1)}
$$

- 子空间的性质：Krylov子空间，可以看出 $n$ 步之后可以得到精确解

$$
\text{span}\{r^{(0)},r^{(1)},\cdots,r^{(k)}\} = \text{span}\{p^{(0)},p^{(1)},\cdots,p^{(k)}\} = \text{span}\{r^{(0)},Ar^{(0)},\cdots,A^{(k-1)}r^{(0)}\}
$$

- 误差估计：

$$
||x^{(k)} - x^\ast||_A \le2 \left(\frac{\sqrt{K_2}-1}{\sqrt{K_2}+1}\right)^k||x^{(0)}-x^\ast||_A
$$

- 预处理：改善条件数

### 4.6 GMRES方法

基本想法：$Ax = b \Leftrightarrow \min_{x\in\mathbb{R}^n}||Ax-b||^2$，计算
$$
x^{(k)} = \text{argmin}_{x \in x^{(0)}_K(A,r^{(0)},k)} ||Ax-b||^2
$$
寻找Krylov子空间的一组单位正交基 $Q_k = \{q_0,q_1,\cdots,q_{k-1}\}$:

## Chapter 6 特征值问题

### 6.1 特征值估计与扰动

- Gershgoin圆盘定理

- 设 $A$ 的正交对角化为 $A = X^{-1}DX$，则 $A$ 特征值问题的条件数定义为
  $$
  K_\lambda(A) = ||X||\cdot||X^{-1}||
  $$

- 而 $A$ 关于特征值 $\lambda_1$ 的条件数定义为
  $$
  K_{\lambda_1}(A) = \frac{1}{|y^Hx|}
  $$

- *Thm.* 设 $\mu$ 是 $A+E\in\mathbb{C}^n$的特征值，则
  $$
  \min_{\lambda\in\sigma(A)}|\lambda - \mu| \le ||X^{-1}||_p||X||_p||E||_p = K_\lambda(A) ||E||
  $$

- *Thm.* 设 $\lambda(\varepsilon)$ 是 $A+\varepsilon E$ 的特征值，$x(\varepsilon)$ 是对应的单位特征向量，$||E||_p = 1$，则
  $$
  |\lambda'(0)| \le \frac{1}{|y^Hx|}.
  $$

### 6.2 幂法

- 对于初始估计$v_0$，不断左乘$A$并归一化，最终可以近似得到A的绝对值最大的特征值（主特征值）。
- 逆幂法，原点位移逆幂法
- 收缩方法，Wielandt收缩

### 6.3 QR 算法

- 算法：对$A_k$做QR分解，计算$A_{k+1}$：

$$
A_k = Q_kR_k \\
A_{k+1} = R_kQ_k
$$

这样序列$\{A_k\}$基本收敛到上三角矩阵。

- 变种：上Hessenberg矩阵。先将矩阵相似对角化为上Hessenberg形式，这样迭代中每一个矩阵都为上Hessenberg形式，可以更快进行QR分解
- 隐式Q定理
- 上Hessenberg矩阵的QR方法：原点位移、双重步

### 6.4 对称矩阵方法

- Rayleigh商迭代：
  $$
  \mu_k = \left<Av^{(k)}, v^{(k)}\right> \Big/\left<v^{(k)}, v^{(k)}\right>;\\
   y^{(k+1)} = (A-\mu_k I)^{-1}v^{(k)}; \\
   v^{(k+1)} = y^{(k+1)} / ||y^{(k+1)}||_2;
  $$
  
- Jacobi方法：将$A$进行正交相似变换。利用Givens变换，每次将最大的非对角线元素置为0。这样非对角线元素平方和以等比数列速度减少，故最终收敛到一个对角矩阵。

## Chapter 5 非线性方程（组）

### 5.1 不动点迭代理论

### 5.2 迭代加速

### 5.3 Newton迭代法和割线法

### 5.4 非线性方程组

### 5.5 拟Newton法

Newton法: 考虑方程组 $F(x) = 0$, 我们可以做多元函数的Taylor展开: $0 = F(x^\ast) \approx F(x^(k)) + F'(x^k)(x^\ast - x^(k)) \Rightarrow x^{(k+1)} = x^{(k)} - (F'(x^{(k)}))^{-1}F(x^{(k)})$

- *Thm.* 若在 $x^\ast$ 的一个邻域内，$F'(x)$ 存在, 连续且可逆, 则在 $x^\ast$ 附近Newton迭代法局部超线性收敛, 且至少是平方收敛.

拟Newton法: 用 $A_k(x)$ 作为对 $F'(x^{(k)})$ 的估计, 则可以取迭代 $x^{(k+1)} = x^{(k)} - A_k^{-1}F(x^{(k)})$. 希望 $A_{k+1}$ 满足 $A_{k+1}(x^{(k+1)} - x^{(k)}) = F(x^{(k+1)})-F(x^{(k)})$, $\Delta A_{k} = A_{k+1} - A_{k}$.

- Broyden秩1方法: 满足上述条件中Frobenius范数最小的$\Delta A_k$: 此时
  $$
  \Delta A_k  = \frac{(q^{(k)} - A_kp^{(k)})(p^{(k)})^T}{||p^{(k)}||_2^2}
  $$
  的秩为1. 其中 $q^{(k)} = F(x^{(k+1)}) - F(x^{(k)}), p^{(k)} = x^{(k+1)} - x^{(k)}$.

## Chapter 7 插值方法

### 7.1 Lagrange插值、基础理论

*Thm.* 经过平面上 $n+1$ 个节点 $(x_i,f(x_i))$ 的插值多项式存在，且次数不超过 $n$ 的多项式唯一。
$$
L_n (x) = \sum_i \frac{\prod_{j\ne i} (x - x_j)}{\prod_{j\ne i} (x_i - x_j)} f(x_i)
$$

*Thm.* 插值误差：$\forall x\in[a,b], \exists \xi = \xi(x) \in [a,b]$, s.t.
$$
f(x) - L_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!} \omega_{n+1}(x)
$$
其中 $\omega_{n+1}(x) = (x-x_0)(x-x_2)\cdots(x-x_n) \le \dfrac{n!}{4}h^{n+1}, h = \max|x_{i+1}-x_i|$

### 7.2 均差和Newton多项式

定义: $f[x_k,x_{k+1},x_{k+2},\cdots,x_{k+j}] = \dfrac{f[x_k,x_{k+1}, \cdots, x_{k+j-1}] - f[x_{k+1}, \cdots, x_{k+j}]}{x_{k+j} - x_k}$

性质: 1. 是关于 $f(x_i)$ 的线性组合; 2. $f[x_0,x_1,\cdots,x_n] = \dfrac{1}{n}f^{(n)}(\xi)$.

Newton插值多项式:
$$
f(x) = f(x_0) + f[x_0,x_1] (x-x_0) + f[x_0,x_1,x_2](x-x_0)(x-x_1) + \cdots + f[x_0,x_1,\cdots,x_n](x-x_0)\cdots(x-x_{n-1}) \\ + f[x,x_0,x_1,\cdots,x_n](x-x_0)(x-x_1)\cdots(x-x_n)
$$
最后一项为插值余项.

### 7.3 Hermite插值: 带有导数条件的插值

已知 $n$ 个插值节点 $(x_i,f(x_i))$ 和导数 $f'(x_i)$, 想求出一个 $2n+1$ 次多项式满足这些条件

想法: 构造基函数满足:
$$
\alpha_j(x_k) = \delta_{jk}, \alpha_j'(x_k) = 0, \beta_j(x_k) = 0, \beta_j'(x_k) = \delta_{jk}
$$
则 $H_{2n+1}(x) = \sum_{j=0}^n f(x_j)\alpha_j(x) + f'(x_j)\beta_j(x)$. 可以解出
$$
\begin{cases} \alpha_j(x) = [1-2l_j'(x_j)(x-x_j)] l_j^2(x) \\
\beta_j(x) = (x-x_j)l_j^2(x)
\end{cases}
$$
其中$l_j(x) = \prod_{i\ne j}\dfrac{x-x_i}{x_j - x_i}$.

*Thm.* 设 $a = x_0 <  x_1 < \cdots < x_n = b$, 则$\forall x\in[a,b], \exists \xi = \xi(x) \in [a,b]$ s.t.

$$
R_{2n+1}(x) = f(x) - H_{2n+1}(x) = \frac{f^{(2n+2)}(\xi)}{(2n+2)!}\omega_{n+1}^2(x)
$$

### 7.4 分段插值

- 分段Lagrange插值
- 分段Hermite插值: 连续可导
- 三次样条插值: 二阶可导, $C^2$连续

## Chapter 8 函数逼近

### 8.1 基础理论

函数逼近问题: 对一个给定的函数 $f$ 和区间 $I$, 寻找满足一定条件的函数 $p^\ast\in \Phi$ 使得 $f-p^\ast$ 在某种范数的的意义下最小. 本章中我们考虑2-范数最小, 并先考虑在多项式空间上逼近

**正交多项式**: $f,g\in C[a,b]$, $\rho$ 是 $[a,b]$ 上的权函数, 若
$$
\left<f,g\right>_\rho = \int_a^b \rho(x)f(x)g(x) dx = 0
$$
 则正两个函数关于权函数 $\rho$ 正交. 我们可以构造一组正交的多项式序列 (如使用Gram-Schmidt正交化).

- *Thm.* 若 $\{\varphi_n\}$ 是一组正交的多项式序列, 则 $\varphi_n$ 在 $[a,b]$ 上有 $n $ 个不同的零点.

- *Thm.* $\{\varphi_n\}$ 存在着下面的递推关系:
  $$
  \varphi_{n+1}(x) = (\alpha_n x+\beta_n)\varphi_n(x) + \gamma_{n-1}\varphi_{n-1}(x)
  $$

常见的正交多项式序列:

- Legendre多项式：取 $\rho(x) = 1, [a,b] = [-1,1]$, 相应的正交多项式为 $P_0(x) = 1, P_n(x) = \dfrac{1}{2^n n!}\dfrac{d^n}{dx^n}[(x^2 - 1)^n],n\ge 1$
- Laguerre多项式：取 $\rho(x) = e^x, [a,b] = [0,+\infty]$, 相应的正交多项式为 $L_n(x) = e^x \dfrac{d^n}{dx^n}(x^ne^{-x}),n\ge 0$
- Hermite多项式：取 $\rho(x) = e^{x^2}, [a,b] = [-\infty,+\infty]$, 相应的正交多项式为 $H_n(x) = (-1)^n e^{x^2} \dfrac{d^n}{dx^n}(x^ne^{-x^2}),n\ge 0$
- Chebyshev多项式：取 $\rho(x) = \dfrac{1}{\sqrt{1-x^2}}, [a,b] = [-1,1]$，相应的正交多项式为 $T_n(x) = \cos(n\arccos(x)),n\ge 0$

*Thm.* 对于任何 $n$ 次首一多项式，有 $\dfrac{1}{2^{n-1}} = \max_{x\in[-1,1]} \lvert T_n(x)\rvert \le \max_{x\in [-1,1]}\lvert\varphi_n(x)\rvert$

*Thm.* 对 $f(x)$ 在区间 $[0,1]$ 上进行Lagrange插值，若将插值节点选为 $n+1$ 次Chebyshev多项式的零点 $x_0,x_1,\cdots,x_n$ 则
$$
\max_{x\in[-1,1]} |f(x) - L_n(x)| \le \frac{1}{2^n (n+1)!} ||f^{(n+1)}||_{\infty}
$$

### 8.2 最佳平方逼近

*Def.* 设$f,\varphi_i \in L_\rho^2[a,b], \Phi = \text{span}\{\varphi_0,\varphi_1,\cdots,\varphi_n\}$, 若存在 $s^\ast \in \Phi$, 使得 $\lVert f - s^\ast\rVert_{2,\rho} = \inf_{s \in \Phi} \lVert f-s\rVert_{2,\rho}$, 则称 $s^\ast$是 $f$ 在 $\Phi$ 中的**最佳平方逼近**，其中
$$
||f-s^\ast||_{2,\rho} = \left(\int_a^b \rho(x)|f(x)|^2 dx\right)^{\frac12}
$$

计算：令 $s(x) = \sum_{j=0}^n a_j\varphi_j(x), F(a_0,a_1,\cdots,a_n) = \int_a^b \rho(x) [\sum_{j=0}^n a_j\varphi_j(x) - f(x)]^2 dx$. 当 $\dfrac{\partial f}{\partial a_k} = 0$ 时，我们有
$$
\sum_{j=0}^n \left<\varphi_k,\varphi_j\right>_\rho a_j = \left<f,\varphi_k\right>_\rho,\ k = 0,1,\cdots,n
$$

左侧的矩阵是Gram矩阵，由 $\{\varphi_0,\cdots,\varphi_n\}$ 线性无关知 $A$ 可逆。

### 8.3 周期函数的最佳平方逼近

取 $\{1,\sin x, \cos x, \sin 2x, \cos 2x, \cdots \}$ 为用于插值的正交多项式

Fourier级数

### 8.4 有理分式的Padé逼近

## Chapter 9 数值积分

### 9.1 基础理论、插值求积公式

找出近似公式 $\int_a^b \rho(x) f(x)dx = \sum_k A_kf(x_k)$

代数精度：求积公式对几次的代数多项式精确成立

插值型求积公式：利用Lagrange插值公式，
$$
\int_a^b \rho(x)f(x)dx = \int_a^b \rho(x)L_n(x) dx + \int_a^b \rho (x)R(x) dx = \sum_{k=0}^n \int_a^b \rho(x)l_k(x)dx \cdot f(x_k) + \int_a^b \rho(x)R(x)dx \\ = \sum_{k=0}^n A_kf(x_k) + \frac{1}{(n+1)!} \int_a^b \rho(x)f^{(n+1)}(x)
$$
对于取 $n+1$ 个求积节点的求积公式，若能达到 $n$ 次代数精度，那么一定是插值型求积公式。

### 9.2 Newton-Cotes求积公式

梯形求积公式：$\int_a^b f(x)dx = \dfrac12\left(f(a) + f(b)\right) - \dfrac{(b-a)^3}{6}\lvert f''(\xi)\rvert$

Simpson求积公式：$\int_a^bf(x) dx = \dfrac16\left( f(a) + f(b) + 4f(\dfrac{a+b}{2})\right) - \dfrac{(b-a)^5}{2880}\lvert f^{(4)}(\xi)\rvert$

更一般的Newton-Cotes求积公式：取等距的求积节点 $a = x_0 \le x_1 \le x_2 \le \cdots \le x_n = b$. Cotes系数 $C_k^{(n)} = \dfrac{1}{b-a} \int_a^b l_k(x)dx = \dfrac{(-1)^k}{k!(n-k)!n}\int_0^n\prod_{0\le j \le n,j\ne k}(t-j)dt$, 则
$$
\int_a^b f(x)dx = (b-a)\sum_{k=0}^n C_k^{(n)} f(x_k) + E_n(f)
$$

*Thm.* $n$ 阶Newton-Cotes求积公式的误差为：

（1）$n$ 为偶数时，设 $f \in C^{(n+2)}[a,b]$，则 $E_n(f) = \dfrac{C_n}{(n+2)!}f^{(n+2)}(\xi), \xi\in[a,b]$, 其中 $C_n = \int_a^b x\omega_{n+1}(x)dx < 0$.

（2）$n$ 为奇数时，设 $f\in C^{(n+1)}[a,b]$, 则 $E_n(f) = \dfrac{\bar C_n}{(n+1)!} f^{(n+1)}(\xi), \xi \in [a,b]$, 其中 $\bar C_n = \int_a^b \omega_{n+1}(x)dx < 0$.

### 9.3 复合求积法则

复合梯形求积公式

复合Simpson求积公式

复合Hermite插值求积

### 9.4 Gauss求积公式

选取合适的插值节点，使得代数精度更高

*Thm.* $\int_a^b \rho(x)f(x)dx = \sum_{k=0}^n A_kf(x_k)$ 有 (2n+1) 次代数精度，当且仅当 $x_0,x_1,\cdots,x_n$是 $[a,b]$ 上权函数为 $\rho$ 的 $n+1$ 次正交多项式的零点，且 $A_k = \int_a^b \rho(x)l_k(x) dx = \frac{1}{(\omega_{n+1}' (x_k))^2}\int_a^b\frac{\rho(x)\omega_{n+1}^2(x)}{(x-x_k)^2}dx > 0, k = 0,1,\cdots,n$.

*Thm.* 这一求积公式的误差为 $E_n(f) = \frac{1}{(2n+2)!} f^{(2n+2)}(\xi) \int_a^b \rho(x) \omega_{n+1}^2(x)dx$

*Thm.* （收敛性）

### 9.5 Romberg求积方法

### 9.6 奇异积分的数值积分

1. 区间截断，估计被截断区间的误差
2. 求可解析计算的另一个函数 $g(x)$ 使得对 $f(x) - g(x)$ 在区间上不是奇异积分。

### 9.7 Monte Carlo方法

## Chapter 10 ODE初值问题的数值方法

### 10.1 基础理论

初值问题：$\dfrac{dy}{dx} = f(x,y), y(a) = y_0, x\in[a,b]$.

- **适定性**：$D = \{(x,y) : x\in[a,b],y\in R\}$, $f$ 在 $D$ 上连续且关于 $y$ 满足Lipschitz条件.

- *Thm.* 若初值问题是适定的，则方程存在唯一解，且解的变化关于初值、右端函数的变化是有界的 $(\delta, \epsilon)$.
- 单步法公式: $y_{n+1} = y_n + h\varphi(x_n, y_n; h)$, 其中 $\varphi$ 为我们的**增量函数**.

### 10.2 误差分析

设我们使用单步法, $y(x)$ 为精确解

- 相容性

  - $T(x,y;h) = y(x+h) - y(h)-h\varphi(x_n,y_n;h)$ 为单步的**局部截断误差**.

  - 若单步截断误差满足 $\lim_{h\to 0}\dfrac1h T(x,y;h) = 0$ 则称单步法与初值问题**相容**. 若$\lvert T(x,y;h)\rvert \le Ch^{p+1}$, 则单步法至少 **$p$ 阶相容**.

  - *Thm.* 单步法相容 $\Leftrightarrow$ $\lim_{h\to 0} \varphi(x,y;h) = f(x,y)$.

- 收敛性

  - $E(h)=\max\lvert e_n(h)\rvert=\max\lvert y(x-n)-y_n\rvert $ 即最大的**整体误差**. 若 $\lim_{h\to 0} E(h) = 0$ 则称单步法**收敛**. 若 $E(h) \le Ch^p$ 则称单步法 **$p$ 阶收敛**.
  - *Thm.* 若增量函数 $\varphi$ 连续, 关于 $y$ 是Lipschitz连续, 则单步法收敛等价于相容, $p$ 阶相容则 $p$ 阶收敛.

- 稳定性

  - 存在常数$K,h_0$满足: 对于两个初值$y_0,z_0$, 使用小于$h_0$的步长得到的解满足 $\max_{n} \lvert y_n - z_n\rvert \le K \lvert y_0 - z_0\rvert$. 则单步法是**稳定的**.
  - *Thm.* 增量函数关于$y$ 是Lipschitz连续, 则单步法是稳定的.
  - *Thm.* 单步法稳定 + 相容, 则收敛.

- 绝对稳定性
  - 考虑试验方程 $y' = \lambda y$, 使用单步法得到的解为 $y_{n+1} = E(\lambda h)y_n$. 若 $\lvert E(\lambda h)\rvert<1$ 恒成立则单步法**绝对稳定**; 若在一个区域（复平面）或区间（实轴）上满足这一条件，则有对应的**绝对稳定区域/区间**。

### 10.3 Runge-Kutta方法

- 阶数：由Taylor展开公式，我们知道 $y(x+h) = y(x) + hy'(x) + \dfrac12 h^2y''(x) + \dfrac16 h^3 y'''(X) +\cdots$, 其中各阶导数可以用 $f(x,y)$ 计算。

- Runge-Kutta方法：选取的增量函数为 $\varphi(x_n,y_n,h) = \sum_{i=1}^s b_ik_i$, 其中 $s$ 称为R-K方法的**级数**，$b = (b_1, b_2, \cdots, b_s)^T$ 称为**R-K权**。其中
  $$
  k_i = f(x_n+c_ih, y_n + h\sum_{j=1}^sa_{ij}k_j),\ c_i = \sum_{j=1}^sa_{ij},\ i = 1,2,\cdots,s.
  $$
  其中$A = [a_{ij}]$ 称为**R-K矩阵**，$c = (c_1,c_2,\cdots,c_s)^T$ 称为**R-K节点**。若 $A$ 为严格下三角矩阵，则是显式RK方法；若 $A$ 是下三角矩阵，则为半隐式RK方法；否则为隐式RK方法。

### 10.4 线性多步法

- 一般形式：

$$
\sum_{j=0}^k \alpha_jy_{n+j} = h \sum_{j=0}^k \beta_j f(x_{n+j}, y_{n+j})
$$

​ $ \beta_k$ 为 $0$ 则为显式方法。

- 用数值积分构造：将$y' = f(x,y)$ 取插值节点 $(x_{n+1}),x-n,\cdots,x_{n-l}$ 对 $f(x,y)$ 再区间 $[x_{n+1-l},x_{n+1}]$ 上积分。

- 第一特征多项式：$\rho(\lambda ) = \sum_{j=0}^k \alpha_j\lambda^j$

- 第二特征多项式：$\sigma(\lambda)= \sum_{j=0}^k \beta_j\lambda^j$

- *Thm.* 相容当且仅当 $\rho(1) = 0, \rho'(1) = \sigma(1)$,  $p$ 阶相容当且仅当

- *Thm.* 多步法相容，且满足根条件（第一特征多项式零点均在单位圆盘内，且边界上的根均为单根），则多步法收敛；反之亦然。
- *Thm.* 多步法稳定当且仅当满足根条件
- *Thm.* 多步法绝对稳定，当且仅当**稳定性多项式** $\pi(r,\lambda h) = \rho(r) - \lambda h\sigma(r)$ 的根均在单位圆盘内部
