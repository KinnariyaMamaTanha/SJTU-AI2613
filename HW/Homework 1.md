# Homework 1

> hw url: <https://notes.sjtu.edu.cn/s/3sIWiFqXN>
> answer url: <https://notes.sjtu.edu.cn/s/KCHMsGztf>

## Problem 1

记 $\hat{p}_1 = \# \{ X_i = 1 \} / T$，由 Chernoff Bound 可得

$$
\mathrm{Pr}[|\hat{p}_1 - p_1| > \epsilon] \le 2 e^{-\frac{\epsilon^2T}{3p}} \le 2 e^{-\frac{\epsilon^2T}{3}} = \delta
$$

那么就有 $T = O(\frac{3}{\epsilon ^2}\log \frac{2}{\delta})$

## Problem 2

记 $I = \{ i : p(i) > \hat{p}(i) \}, J = [n] / I$，则

$$
\mathrm{RHS} = \sum_{i \in I} (p(i) - \hat{p}(i)) \\
\begin{align*}
    \mathrm{LHS} &= \frac{1}{2}\sum_{i \in I}(p(i) - \hat{p}(i)) + \frac{1}{2}\sum_{i \notin I}(\hat{p}(i) - p(i)) \\
    &=\frac{1}{2}\sum_{i \in I}(p(i) - \hat{p}(i)) + \frac{1}{2}\left((1 - \sum_{i \in I} \hat{p}(i)) - (1 - \sum_{i \in I} p(i))\right) \\
    &=\sum_{i \in I}(p(i) - \hat{p}(i)) = \mathrm{RHS}
\end{align*} 
$$

证毕。

## Problem 3

由 Chernoff Bound 有：

$$
\begin{align*}
    \mathrm{LHS} &= \mathbf{Pr}\left[\hat{P}(S) \le P(S) - \epsilon \right] \\
    &= \mathbf{Pr}\left[N(S) \le TP(S) - T \epsilon \right] \\
    &= \exp\left( -\frac{1}{2} \frac{(T \epsilon)^2 }{T P(S)} \right) \\
    &= \exp\left( -\frac{1}{2} \frac{T \epsilon^2 }{P(S)} \right) \\
    &\le \exp \left( -\frac{T \epsilon ^2}{2} \right) 
\end{align*} 
$$

这里 $N(S) = T \sum_{j \in S}^{}P(j)$。因此取 $c = 1/2$ 即可。

## Problem 4

由前几个问题，记 $I = \{ i : p(i) > \hat{p}(i) \}$，则有

$$
\begin{align*}
    \mathbf{Pr}\left[ \operatorname{dist}(p, \hat{p}) > \epsilon \right] &= \mathbf{Pr}\left[\sum_{i \in S}^{}(p(i) - \hat{p}(i)) > \epsilon\right] \\
    &= \mathbf{Pr}\left[p(I) - \hat{p}(I) > \epsilon\right] \\
    &\le \mathbf{Pr}\left[ \forall S \subseteq [n], p(S) - \hat{p}(S) > \epsilon \right] \\
    &\le 2^n\exp\left( -cT \epsilon ^2 \right) = \delta
\end{align*} 
$$

则 $T = \frac{1}{c \epsilon ^2}\left( n + \log \frac{1}{\delta} \right)$，得证。

## Problem 5

时间 $\epsilon _2$ 表示 $\max_{1 \le t \le T^*}\left| \sum_{j=1}^{t}x_j \right| \le \sqrt{2T^*}$，则

$$
\begin{align*}
    P_0(\epsilon_2) &= 1 - \mathbf{Pr}\left[\max_{1 \le t \le T^*}\left| \sum_{j=1}^{t}x_j \right| > \sqrt{2T^*}\right] \\
    &\ge 1 - 2\exp\left( -\frac{2 * 2T^*}{T^* \cdot (1 - 0)^2} \right) \\
    &= 1 - 2e^{-4} > \frac{3}{4}
\end{align*} 
$$

得证。

## Problem 7

$$
P_1(\epsilon _1 \cap \epsilon _2) = \sum_{w \in \epsilon _1 \cap \epsilon _2}^{}P_1(w) = \sum_{w \in \epsilon _1 \cap \epsilon _2}^{} P_0(w) \frac{P_1(w)}{P_0(w)} \ge \sum_{w \in \epsilon _1 \cap \epsilon _2}^{}P_0(w) \min_{w \in \epsilon _1 \cap \epsilon _2} \frac{P_1(w)}{P_0(w)} = P_0(\epsilon _1 \cap \epsilon _2) \min_{w \in \epsilon_1 \cap \epsilon_2} \frac{P_1(w)}{P_0(w)}
$$