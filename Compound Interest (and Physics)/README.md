# Compound Interest (and Physics)

This repo investigates the mathematical formulation of compound interest and its relation to topics in physics. It started as a side project for fun. If you spot any mathematical mistakes or grammatical errors, please let me know.

## Compound Interest

### Historical background
Compound interest has long been of interest to mathematicians as well as merchants and traders of both the modern era and antiquity. For example, there exists a tablet from the Babylonian civilisation which historians believe to be one, if not the first, example of a formulation of compound interest. As well as this, Jacob Bernoulli dicovered the constant $e$ while investigating compound interest. 

### Defintions and Basics
What is compound interest? Compound interest is a type of interest where each period’s interest is added to the balance, and future interest is earned on this new balance. For example, imagine you invest £1 (gods currency) with a monthly interest rate of 100% over 12 months. After the first month you would have £2. In the second month, this interest would apply to my new balance. So, after the second month you would have £4, after the third £8, and so on.  If I were to write this out mathematically, for a months worth of interest I would have
$$T = I(1+1)$$
where $T$ is the total and $I$ is the initial investment. This can quite clearly generalise to

$$T = I \left(1 + \frac{r}{n} \right)^{tn}  ,$$

where $r \in [0,1]$ is the annual interest rate, $n \in \mathbb{N}_0$ is the compounding frequency (i.e. how many times it is applied in years, months, weeks, etc), and $t \in \mathbb{N}_0$ is the duration that this interest is applied. For the example mentioned previosuly we would have $n = 12$, $t = 12$, and $r = 1$. For simplicity, moving forward I will take $I = 1$. With this we can define the *accumulation function*:

$$a(t) = \left(1 + \frac{r}{n} \right)^{tn}.$$ 

### The Contiuum Limit

As stated it is often the case that $t$, and $n$ are units of time like Weeks, Months, or Years. In this case, as in the defintion above, we take them to be elements of $\mathbb{N}_0$. But, if we imagine our compounding frequency and time became real, that is in $\mathbb{R}_0$, then we can take $n \rightarrow \infty$ smoothly. To see what this equals, I redefine $n = nt$, then $a(t)$ becomes

$$a(t) = \left( 1 + \frac{rt}{n} \right)^n.$$

With this form we may take the limit (i.e. a continous compounding frequency) and define 

$$P(t) := \lim_{n \rightarrow \infty} a(t) = e^{rt}.$$

A graphical example of this process can be seen in the correspodning Jupyter notebook. Anyway, in this limit the compounding interest rate is referred to as the *force of interest*, and is given by 

$$\delta_t = \frac{\dot{P}(t)}{P(t)} = \frac{\text{d}}{\text{d}t} \ln(P(t)),$$

where $\dot{}$ represents differentiation w.r.t $t$. With this we can write 

$$P(t) = \exp\left(\int_{0}^t \text{d}s \hspace{0.15cm} \delta_s\right),$$

as $P(0) = 1$.
