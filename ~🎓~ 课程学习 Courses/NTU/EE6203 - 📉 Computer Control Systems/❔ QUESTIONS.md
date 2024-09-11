
---
## Z Transform

> [!FAQ] Is it possible that I use Partial Fraction Expansion for Inverse Z Transform but can not find a proper form on the transform table for my terms? What kind of signals or systems will result in that?
> Actually, all the Z Transform of a causal signal can be inversed using Partial Fraction Expansion. If you get stuck in the calculation process, track back and check your previous steps for possible mistake. By the way, the sampling period $T$ can be considered a normal constant in the expression.

> [!FAQ] The sampling formula of signal $x(t)$ is $x^*(t)=\sum^\infty_{k=0}x(kT)\delta(t-kT)$. But since $\delta(0)=\infty$ , wouldn't every term of the series become as large as infinity?
> The result that sampling formula seems counterintuitive is the special definition of delta impulse function $\delta(t)$. The function actually represents an extremely narrow sampling square pulse $h(t)$ which has an area of 1. So the delta impulse has a infinity value on where $t=0$, but its integration remains $1$.
> $$\delta(t)=\lim_{\Delta \to 0}\begin{cases} \frac{1}{\Delta} & 0\leq t<\Delta \\ 0& t>\Delta \end{cases}$$
> So there's no need to struggle with the equation, it's just a special definition for engineering convenience








