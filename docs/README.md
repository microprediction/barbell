
# A Note on the Interpretation of Barbell Zero-Coupon Bond Portfolios

I show that a barbell zero coupon bond portfolio can be interpreted as the solution to an optimization problem, where the objective is a modified excess return. 

### Bond price model

Assume a lattice of zero coupon bonds with prices $B^i(t) = B(t;t+\tau^{i})$ and integer time to maturities $\tau^{i}=i\$ as $i$ ranges from $1$ to $n$ years. We assume that all bonds are priced off the same piecewise constant forward curve with knot points also at integer years. We write 

$$
    B^{i}(t) = \exp\left(- \int_t^{t+i} f(t,s) ds \right)
$$

and assume further that the changes in forward rates \( f(t,s) \) at time \(t\) for different years are *independent* (I do not defend these assumptions, merely point out an analytical implication of them). The rates may have non-trivial drift.

It will suffice to note that the vector of bonds has dynamics given by

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
for scalar constant \(\eta\), an \(n\) by \(n\) matrix \(J\) (implicitly defined by the above) and some drift coefficients \(\gamma\) that we don't care too much about in this particular exercise. 
