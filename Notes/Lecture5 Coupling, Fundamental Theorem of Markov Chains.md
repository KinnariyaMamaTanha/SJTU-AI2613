# Coupling, Fundamental Theorem of Markov Chains

## Total Variation Distance (TVD)

对于两个定义在可数状态集合 $\Omega$ 上的概率分布 $\mu$ 和 $\nu$，定义

$$
D_{VT}(\mu, \nu) = \frac{1}{2}\sum_{x \in \Omega}|\mu(x) - \nu(x)|
$$

如图：

![](https://cdn.jsdelivr.net/gh/KinnariyaMamaTanha/Images@main/202408201806361.png)

还可以证明

$$
D_{VT}(\mu(x), \nu(x)) = \max_{A \subseteq \Omega}|\mu(A) - \nu(A)|
$$

这里

$$
\mu(A) = \sum_{x \in A}\mu(x)
$$

## Coupling (耦合)

**定义**：对在一个样本空间 $\Omega$ 上的概率分布 $X \sim \mu$ 和 $Y \sim \nu$，定义 $\omega$ 是 $\mu$ 和 $\nu$ 的耦合，如果 $w$ 是 $\mu, \nu$ 的 joint distribution。即

$$
\begin{align*}
    X &\sim \mu \\
    Y &\sim \nu \\
    (X, Y) &\sim \omega \in (\Omega, \Omega) \\
\end{align*}
$$

也就是说，$\mu$ 和 $\nu$ 分别是 $\Omega$ 的边缘概率分布

举例：当 $\Omega$ 为有限集时，取非负概率矩阵 $\omega$ 满足，每一行的和与 $\mu$ 相同，每一列的和与 $\nu$ 相同。例如：

$$
\begin{align*}
    \mu &= [1/2, 1/2]^T \\
    \nu &= [1/3, 2/3]^T \\
    \omega &= \begin{pmatrix}
        1/3 & 1/6 \\
        0 & 1/2
    \end{pmatrix}
\end{align*}
$$

就有 $\Omega$ 是 $\mu$ 和 $\nu$ 的 coupling

## Coupling of Markov Chain

有两个 Markov Chain $\mu_0, \mu_1, \ldots$ 和 $\nu_0, \nu_1, \ldots$。对每一个 $t$，记 $\omega_t$ 为 $\mu_t$ 和 $\nu_t$ 的 coupling，$(X_t, Y_t) \sim \omega_t$

## Foundamental Theorem of Markov Chains (Finite)

**内容**：如果一个 Markov Chain 既是 *irreducable* 的又是 *aperiodic* 的，那么三个问题的答案都是都是成立的。

**证明**：

引理：$\mathrm{Pr}_{(X,Y)\sim \omega}[X \neq Y] \ge d_{TV}(\mu, \nu)$ 且存在 coupling $w^*$ 使得取等

引理的证明：

$$
\begin{align*}
    \mathrm{Pr}_{(X, Y)\sim \omega}[X \ne Y] &\ge 1 - \sum_{i=1}^n \mu(i) \cap\nu(i) \\
    &= \sum_{i=1}^n (\mu(i) - \mu(i)\cap \nu(i)) \\
    &= \sum_{i=1}^n(\mu(i) - \nu(i)) \cup 0 \\
    &= d_{TV}(\mu, \nu)
\end{align*}
$$

回到原命题，*irreducible* 说明，$\forall i,j,\exist t, s.t. P^t(i,j) > 0$；*aperiodic* 说明，$\exist t^*, \forall t \ge t^*, s.t. \forall i,j,P^t(i,j) \gt 0$（丢番图方程的性质）。

由引理，

$$
\begin{align*}
    d_{TV}(\mu_t, \pi) &\le \mathrm{Pr}_{(X_t, Y_t) \sim \omega}[X_t \ne Y_t]
\end{align*}
$$