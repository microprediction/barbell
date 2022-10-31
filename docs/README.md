
# A Note on the Interpretation of Barbell Zero-Coupon Bond Portfolios

I show that a barbell zero coupon bond portfolio can be interpreted as the solution to an optimization problem, where the objective is a modified excess return. 

### Bond price model

Assume a lattice of zero coupon bonds with prices $B^i(t) = B(t;t+\tau^{i})$ and integer time to maturities $\tau^{i}=i\$ as $i$ ranges from $1$ to $n$ years. We assume that all bonds are priced off the same piecewise constant forward curve with knot points also at integer years. We write 

$$
    B^{i}(t) = \exp\left(- \int_t^{t+i} f(t,s) ds \right)
$$

and assume further that the changes in forward rates \( f(t,s) \) at time \(t\) for different years are *independent* (not that my point is not to defend these assumptions, merely to point out an analytical implication of them). 

### 

