# Homework 2

## Problem 1

定义事件 $A = \{ \exists t < t^*,X_t =  Y_t \}$，则

$$
\mathbf{Pr}[X_{t^*} = Y_{t^*}] = \mathbf{Pr}[X_{t^*} = Y_{t^*}\mid A]\mathbf{Pr}[A] + \mathbf{Pr}[X_{t^*} = Y_{t^*}\mid \overline{A}]\mathbf{Pr}[\overline{A}]
$$

再定义 $X'_t$ 和 $Y'_t$ 满足：

- $X_0' \sim \mu_0, Y_0' \sim \nu _0$
- $X_t'$ 和 $Y_t'$ 互相独立，且都按照转移矩阵 $P$ 独立演化。

再定义事件 $A' = \{ \exists t < t^*,X'_t =  Y'_t \}$，则

$$
\mathbf{Pr}[X_{t^*} = Y_{t^*}\mid A] = 1 \ge \mathbf{Pr}[X_{t^*}' = Y_{t^*}' \mid A'] \\
\mathbf{Pr}[X_{t^*} = Y_{t^*} \mid \overline{A}] = \mathbf{Pr}[X_{t^*}' = Y_{t^*}' \mid \overline{A}] \\
\mathbf{Pr}[A'] = \mathbf{Pr}[A]
$$

故

$$
\begin{align*}
\mathbf{Pr}[X_{t^*} = Y_{t^*}] &\ge \mathbf{Pr}[X_{t^*}' = Y_{t^*}'\mid A']\mathbf{Pr}[A'] + \mathbf{Pr}[X_{t^*}' = Y_{t^*}'\mid \overline{A'}]\mathbf{Pr}[\overline{A'}] \\
&= \mathbf{Pr}[X_{t^*}' = Y_{t^*}'] \\
&= \sum_{i \in [n]}^{}\mathbf{Pr}[X_{t^*}' = Y_{t^*}' = i] \\
&\ge \delta ^2
\end{align*} 
$$

得证。

## Problem 2

### 2.1

可以构造转移矩阵 $P$，易证。

### 2.2

$$
P(i, j) = \begin{cases}
    \frac{1}{2} & i=j \land d(i) > 0 \\
    1 & i=j \land d(i) = 0 \\
    \frac{1}{2d(i)} & i \neq j \land d(i) > 0 \land (i,j) \in E \\
    0 & (i \neq j \land d(i) = 0) \lor (i \neq j \land d(i) > 0 \land (i,j) \notin E)
\end{cases} 
$$

### 2.3

irreducible $\Leftrightarrow$ state graph $G'$ 是强连通的，而 $G'- \{ (i,i): i\in V \}$ 去除方向后与 $G$ 相同，知 $G$ 是连通的，得证。

### 2.4

当存在独立点时（度数为 0 的点），该点上赋以任意概率均稳定。下考虑每个点的度均不为 0 的情况。

记 $N(j) = \{ i\in V:(i,j) \in E \}$，假设 $\pi$ 为一个稳态分布，则对任意 $j$

$$
\begin{align*}
    \pi P(j) &= \sum_{i \in [n]} \pi(i)P(i, j) \\
    &= \pi(j) \cdot \frac{1}{2} + \sum_{i \in N(j)}\pi(i) \frac{1}{2d(i)} = \pi(j)
\end{align*} 
$$

整理得

$$
\sum_{i \in N(j)}\frac{\pi(i)}{d(i)} = \pi(j)
$$

因此任意满足上述 $n$ 个方程（秩为 $n-1$）的解 $\pi$ 均是稳态分布。

### 2.5

硬算即可。

## Problem 3

仍然记 $N(j) = \{i \in V: (i, j)\in E \}$，转移矩阵 

$$
P(i,j) = \begin{cases}
    \frac{1}{2d(i)} \min(1, \frac{g(j)}{g(i)}) & i \neq j, (i,j)\in E \\
    1 -\sum_{i \in N(j)} \frac{1}{2d(i)} \min(1, \frac{g(j)}{g(i)}) & i = j
\end{cases} 
$$

又因为

$$
\frac{g(j)}{g(i)} = \frac{f(j)}{f(i)} \frac{d(i)}{d(j)} = \frac{\pi(j)}{\pi(i)} \frac{d(i)}{d(j)}
$$

故

$$
\begin{align*}
    \pi P(j) &= \sum_{i \in [n]}^{} \pi(i) P(i, j) \\
    &= \pi(j) P(j, j) + \sum_{i \in N(j)}^{} \pi(i) \frac{1}{2d(i)}\min\left\{ 1, \frac{\pi(j)}{\pi(i)} \frac{d(i)}{d(j)} \right\} \\
    &= \pi(j) P(j, j) + \sum_{i \in N(j)}^{} \min\left\{ \frac{\pi(i)}{d(i)}, \frac{\pi(j)}{d(j)} \right\} \\
    &= \pi(j) P(j, j) + \sum_{i \in N(j)}^{} \pi(j) \frac{1}{2d(j)}\min\left\{ 1, \frac{\pi(i)}{\pi(j)} \frac{d(j)}{d(i)} \right\} \\
    &= \pi(j) P(j, j) + \sum_{i \in N(j)}^{} \pi(j) P(j, i) \\
    &= \sum_{i \in [n]}^{} \pi(j)P(j, i) = \pi(j)
\end{align*} 
$$

得证。

## Problem 4

**Irreducible**：对任意两个状态 $A$ 和 $B$，可以通过首先将 $A[1]$ 变换为 $B[1]$， 接着保持 $A[1]$ 不动，操作 $A[2]$。以此类推，最终就可以得到 $A = B$，得证。

**Aperiodic**：对任意一个状态 $A$，由于存在一条 $A \rightarrow A$ 的链，所以自然为 aperiodic 的。

**Stationary Distribution**：对任意两个状态 $A, B$，转移概率 $P(A,B)$ 满足：

$$
P(A, B) = \begin{cases}
    \frac{1}{n} & A = B \\
    \frac{2}{n^2} & A, B 只有两个位置上不同 \\
    0 & otherwise
\end{cases} 
$$

容易算出，uniform distribution 确实是一个稳态分布，又因为 irreducible 且 aperiodic，知稳态分布唯一，得证。

**Equivalent**：显然。

## Problem 5
