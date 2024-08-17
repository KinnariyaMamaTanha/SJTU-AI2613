# Review of Probability

## The Probability Space

!!! note $\sigma$-Algebra
    对于集合 $\Omega$, 以及 $\mathcal{F} \in 2^{\Omega}$，如果满足：
    - $\empty, \Omega \in \mathcal{F}$
    - $\forall A \in \mathcal{F}, A^c \in \mathcal{F}$
    - 对任意可数（无限）集合序列 $A_1, \ldots, A_n, \ldots \in \mathcal{F}$，有 $\cup_i A_i\in \mathcal{F}$

    那么称 $\mathcal{F}$ 是一个 $\sigma$-algebra

!!! note Probability Space
    对于元组 $(\Omega, \mathcal{F}, \mathrm{P})$，如果满足：
    - The universe $\Omega$ is the outcomes
    - The set $\mathcal{F}$ is a $\sigma$-algebra, which represents all possible “events”.
    - The probability $\mathrm{P}: \mathcal{F}\rightarrow [0,1]$ assigns a real to each event and must satisfy
      - $\mathrm{P}(\emptyset) = 0, \mathrm{P}(\Omega)=1$ 
      - $\mathrm{P}(A^c) = 1 - \mathrm{P}(A)$ for every $A \in \mathcal{F}$
      - For any **finite or countable** sequence of **disjoint** sets $A_1,A_2,\dots\in\mathcal{F}$, $\mathrm{P}(\cup_{i\ge 1}A_i) = \Sigma_{i=1}^\infty\mathrm{P}(A_i)$

    那么称该元组为一个 probability space。

## Random Variable
