# Compound Interest (and Physics)

This repo investigates the mathematical formulation of compound interest and its relation to topics in physics. It started as a side project for fun. If you spot any mathematical mistakes or grammatical errors, please let me know.

## Compound Interest

### Historical background
Compound interest has long been of interest to mathematicians as well as merchants and traders of both the modern era and antiquity. For example, there exists a tablet from the Babylonian civilisation which historians believe to be one, if not the first, example of a formulation of compound interest. As well as this, Jacob Bernoulli discovered the constant $e$ while investigating compound interest. 

### Definitions and Basics
What is compound interest? Compound interest is a type of interest where each period’s interest is added to the balance, and future interest is earned on this new balance. For example, imagine you invest £1 (God’s currency) with a monthly interest rate of 100% over 12 months. After the first month you would have £2. In the second month, this interest would apply to your new balance. So, after the second month you would have £4, after the third £8, and so on.  If I were to write this out mathematically, for a month’s worth of interest I would have
$$T = P(1+1)$$
where $T$ is the total and $P$ is the principal investment. This can quite clearly generalise to

$$T = P\left(1 + \frac{r}{n} \right)^{tn}  ,$$

where $r \in \mathbb{R}$ is the annual interest rate, $n \in \mathbb{N}_0$ is the compounding frequency (i.e. how many times it is applied in years, months, weeks, etc), and $t \geq 0$ is the duration that this interest is applied. For the example mentioned previously we would have $n = 12$, $t = 12$, and $r = 1$. For simplicity, moving forward I will take $P = 1$. With this we can define the *accumulation function*:

$$a(t) = \left(1 + \frac{r}{n} \right)^{tn}.$$ 

### The Continuum Limit

As stated it is often the case that $t$, and $n$ are often measured in units like weeks, months, or years, months, or years. In this case, as in the definition above, we take them to be elements of $\mathbb{N}_0$. But, if we imagine our compounding frequency and time became non-negative reals we can take $n \rightarrow \infty$ smoothly. To see what this equals, look at the accumulation function as 

$$a(t) = \left[\left( 1 + \frac{r}{n} \right)^n\right]^t.$$

With this form we may take the limit (i.e. a continuous compounding frequency) and define 

$$T(t) := \lim_{n \rightarrow \infty} a(t) = e^{rt}.$$

A graphical example of this process can be seen in the corresponding Jupyter notebook. Similarly, this function is the solution to the ODE
$$\frac{\text{d}T}{\text{d}t} = rT(t).$$

After taking the limit, the compounding interest rate is referred to as the *force of interest*, and is given by 

$$\delta_t = \frac{\dot{T}(t)}{T(t)} = \frac{\text{d}}{\text{d}t} \ln(T(t)),$$

where $\dot{}$ represents differentiation w.r.t $t$. With this we can write 

$$T(t) = \exp\left(\int_{0}^t \text{d}s \hspace{0.15cm} \delta_s\right),$$

as $T(0) = 1$. In practice, these formulas apply discounting cash flows, yield curves, and continuous-time models used throughout quantitative finance.

### Relation to Physics

These kinds of evolution equations are ubiquitous throughout physics, one common example is radioactive decay. Given a radioactive sample, the activity of the sample can be modelled by

$$A(t) = A_0 e^{-\lambda t},$$

with $A_0$ the initial activity, $\lambda$ the decay constant, and $t$ the time. This is mathematically identical to compound interest with a negative “interest rate.” Similarly, if we analytically continue (also called Wick rotating within theoretical physics) our time coordinate $t \rightarrow \tau = -it$ the differential becomes 

$$\frac{\text{d}}{\text{d}t} = \frac{\text{d}\tau}{\text{d}t} \frac{\text{d}}{\text{d}\tau} = -i\frac{\text{d}}{\text{d}\tau},$$


and hence our ODE for compound interest is

$$-i\frac{\text{d}}{\text{d}\tau}T(\tau) = rT(\tau).$$

If you know any quantum theory, this looks essentially identical to the time-dependent (but strictly not space-dependent) Schrodinger equation (SE) with $\hbar = 1$

$$i\frac{\text{d}\psi(t)}{\text{d}t} = H\psi(t).$$

In this 0+1D system the SE equation can be solved easily to yield,

$$\psi(t) = e^{-iHt}\psi(0).$$

This is actually the evolution operator (in the quantum case), however, for our compound interest system this is *not* an operator, i.e. it is not a linear isomorphism on the Hilbert space of our quantum theory. This time-evolution structure underlies the standard separation-of-variables approach used to solve the Schrödinger equation for systems like the Hydrogen atom. Specifically, it shows that we can separate variables when solving this ODE, which is exactly the technique that yields the analytic solutions for this quantum system. This applies directly to our equation for the compound interest ODE to yield the solution

$$T(\tau) = e^{-iH\tau}T(0),$$

with $H = -r$. This would physically correspond to a rather trivial quantum system with a single constant energy level. Hence, this does not carry any physical information, but it is a nice mathematical similarity. Notice also that if we Wick rotate back we get the exact same solution as one would get just by solving the original (real time) ODE. Another link is within quantum field theory, more specifically the path integral, 

$$\mathcal{Z} = \int \mathcal{D}\phi e^{iS[\phi]},$$

where $\mathcal{D}$ means we are integrating over all fields, and $S$ is the *action* which is defined as 

$$S:= \int dt \mathcal{L},$$

where $\mathcal{L}$ is the Lagrangian density associated with our theory. To see the correspondence, lets look at 

$$T(\tau) = e^{ir\tau} = e^{i \int^\tau_0 d\tau^\prime r} .$$

With this, our interest rate $r$ is identified with our Lagrangian density. Once again, not interesting physically, but an interesting enough relationship. 


## Conclusion

Now, the aim of this repo was to cover Compound interest briefly and show its relations to ideas within physics, we do not claim any physical significance of this correspondence. It does, however, show the wide reaching applications of ideas within mathematics. To paraphrase Eugene Wigner, mathematics is "unreasonably effective within the physical sciences" and this topic proves that in a clear and insightful way. 
