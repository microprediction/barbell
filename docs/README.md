
# A Note on the Interpretation of Barbell Zero-Coupon Bond Portfolios

I show that a barbell zero coupon bond portfolio can be interpreted as the solution to an optimization problem, where the objective is a modified excess return. 

### Bond price model

Assume a lattice of zero coupon bonds with prices $B^i(t) = B(t;t+\tau^{i})$ and integer time to maturities $\tau^{i}=i\$ as $i$ ranges from $1$ to $n$ years. We assume that all bonds are priced off the same piecewise constant forward curve with knot points also at integer years. We write 

$$
    B^{i}(t) = \exp\left(- \int_t^{t+i} f(t,s) ds \right)
$$

and assume further that the changes in forward rates $ f(t,s) $ at time $t$ for different years are *independent* (I do not defend these assumptions, merely point out an analytical implication of them). The rates may have non-trivial drift. It will suffice to note that the vector of bonds has dynamics given by

$$
   d \left[ \begin{array}{c} log B^{1}(t) \\ 
                             log B^{2}(t) \\ 
                             \dots  \\
                             log B^{n}(t) 
     \end{array} \right] = \left[
                \begin{array}{c} 
                         \gamma^1(t) \\ 
                         \gamma^2(t) \\
                         \vdots \\
                         \gamma^n(t)
           \end{array}
  \right] \ dt 
    +  \eta \left[ \begin{array}{cccc} 1 &amp; 0 &amp; \dots &amp; 0 \\ 
                                  1 &amp; 1 &amp; \dots &amp; 0 \\
                                  \vdots &amp; \vdots &amp; \ddots &amp; 0 \\
                                  1 &amp; 1 &amp; 1 &amp; 1 
         \end{array} \right] 
      \left[ \begin{array}{c} dW^1(t) \\ 
                              dW^2(t) \\ 
                             \dots  \\
                              dW^n(t)
         \end{array} \right] 
$$

or more succinctly

$$
   d (log B) = \gamma \ dt + \eta J \ dW
$$

for scalar constant $\eta$, an $n$ by $n$ matrix $J$ (implicitly defined by the above) and some drift coefficients $\gamma$. The observation, however, is that here we don't actually need to worry about the $\gamma$'s. 

### Modified excess return 

Consider a portfolio of these bonds with weights \(\pi\) summing to unity. By analogy with Stochastic Portfolio theory, but with no other motivation for now, I consider a modified excess return given by 

$$
     {modified\ excess\ return} = \sum_{i=1}^n \pi_i \sigma_{ii} - 2 \sum_{i,j=1}^{n} \pi_i \pi_j \sigma_{ij} + \sum_{i=1}^n \pi_i^2 \sigma_{ii}
$$  

where, following Stochastic Portfolio Theory notation, $\sigma_{ij}$ is the log-asset covariance, here equal to $\eta^2$ multiplied by the $i$,$j$'th element of $J J^{\top}$. 
   
### Maximizing the modified excess return
Whatever the modification contemplated may imply, we proceed towards its surprising implication by mentally multiplying $J$ above and noting that $(J J')_{i,j} = min(i,j)$ because 

$$
     \left[ \begin{array}{cccc} 1 & 0 & \dots & 0 \\ 
                                  1 & 1 & \dots & 0 \\
                                  \vdots & \vdots & \ddots & 0 \\
                                  1 & 1 & 1 & 1 
         \end{array} \right] 
       \left[ \begin{array}{cccc} 1 & 1 & \dots & 1 \\ 
                                  0 & 1 & \dots & 1 \\
                                  \vdots & \vdots & \ddots & 1 \\
                                  0 & 0 & 0 & 1 
         \end{array} \right] =  \left[ \begin{array}{cccc} 1 & 1 & \dots & 1 \\ 
                                  1 & 2 & \dots & 2 \\
                                  \vdots & \vdots & \ddots & \vdots \\
                                  1 & 2 & \dots & n 
         \end{array} \right] 
$$

Thus in this slightly contrived forward rate model we have modified excess return proportional to 

$$
       \psi(\pi) = \sum_{i=1}^n i \pi_i  - 2\sum_{i,j=1}^{n} min(i,j) \pi_i  \pi_j + \sum_{i=1}^n i \pi_i^2 
$$

This leaves us with a cute little optimization. I claim that $\psi(\pi)$ is maximized (and hence also modified excess return) subject to \(\sum_{i=1}^n \pi_i = 1\), by setting the portfolio equal to a barbell. Half the portfolio is invested in the first (shortest maturity) bond and the other half on the last (longest maturity) bond. That is,

$$
  \pi^* = \left[ \begin{array}{c} 1/2 \\ 0 \\ \vdots \\ 0 \\ 1/2   \end{array}  \right]
$$ 

corresponding to a modified excess return of $\psi(\pi^*) = \frac{n-1}{4}$. To prove this observe that $\psi(\pi)$ can be re-written as follows (count the number of times each $\pi_i$ and $\pi_i \pi_j$ occurs)

$$
 \begin{eqnarray*}
\psi(\pi) & = &  - 2 \sum_{i,j=1}^{n} min(i,j) \pi_i  \pi_j + \sum_{i=1}^n i \pi_i^2 + \sum_{i=1}^n i \pi_i \\
   & = &    -(\pi_1 + \pi_2 + ... + \pi_n)^2 + (\pi_1 + \pi_2 + ... + \pi_n) \\
 &  & -  (\pi_2 + ... + \pi_n)^2 + (\pi_2 + ... + \pi_n)\\
    & &  \vdots \\
    & & - (\pi_{n-1}+\pi_{n})^2 + (\pi_{n-1}+\pi_{n}) \\
    &  & - (\pi_n)^2 + \pi_n \\
   & = &  \sum_{i=0}^{n-1} (-u_i^2 + u_i) \\
   & = &  \sum_{i=1}^{n-1} (-u_i^2 + u_i) \\
   & = &  \sum_{i=1}^{n-1} \left(-(u_i-1/2)^2+1/4 \right) \\
   & = & \frac{n-1}{4} - \sum_{i=1}^{n-1} (u_i-1/2)^2
\end{eqnarray*}
$$


where we have introduced $u_i = \sum_{j=i+1}^n \pi_j$ as the sum of portfolio weights leaving out the first $i$ and applied the constraint $u_0=1$. The expression is clearly maximized by setting $u_1 ... u_n$ equal to $1/2$. By back substitution beginning with $\pi_n$ this implies $\pi = \pi^*$ as claimed. 

### Interpretation

We make no statement as to what modified excess return represents, except to compare it to

$$
     excess\ return  =  \sum_{i=1}^n \pi_i \sigma_{ii} - \sum_{i,j=1}^{n} \pi_i \pi_j \sigma_{ij}
$$

which is most certainly meaningful. Indeed, the log-optimal investor may seek to maximize excess return. In contrast, the modified excess return makes the covariance term more important so one might reason that, all else being equal, choosing this modification over the bone fide excess return represents a sacrifice of long term growth in exchange for reduced portfolio variance 
- though the difference picks up the between-asset terms only, not the variances.   

$$
\begin{eqnarray*}
     modified\ excess\ return - excess\ return & = & - \sum_{i,j=1}^{n} \pi_i \pi_j \sigma_{ij} + \sum_{i=1}^n \pi_i^2 \sigma_{ii} \\
     & = & -\sum_{i \not= j} \pi_i \pi_j \sigma_{ij}
\end{eqnarray*}
$$

A similar tradeoff is made, also inadvertently, by those constructing minimum variance portfolios in the tradition of Markowitz and de Finetti. In the minimum variance prescription only the portfolio variance term 

$$
 \sum_{i,j=1}^{n} \pi_i \pi_j \sigma_{ij}
$$
 
is contemplated, not 

$$
   \sum_{i=1}^n \pi_i \sigma_{ii}
$$.   
