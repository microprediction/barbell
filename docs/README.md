
### A Note on the Interpretation of Barbell Zero-Coupon Bond Portfolios

Here's a litte curiosity I might get around to publishing some day: a bar-bell portfolio maximizes modified excess return. At first I thought it maximized excess return (in the sense of Stochastic Portfolio Theory) but felt that couldn't be right. Sure enough I made a mistake and thus was born "modified excess return", a shamelessly reverse engineered criteria to make what follows work.



Assume a lattice of zero coupon bonds with prices $B^i(t) = B(t;t+\tau^{i})$ and integer time to maturities \(\tau^{i}=i\) as \(i\) ranges from \(1\) to \(n\) years. We assume that all bonds are priced off the same piecewise constant forward curve with knot points also at integer years. We write 

$$
    B^{i}(t) = \exp\left(- \int_t^{t+i} f(t,s) ds \right)
$$
