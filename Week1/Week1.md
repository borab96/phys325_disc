# Week 1: Math review

## Some very basic real analysis
As you know, functions can be represented by either an infinite or finite sum of other functions. In the former case, this is true if the infinite series evaluates to something finite - it is convergent rather than divergent. In class I only went through the Taylor expansion where the convergence property is rather obvious. Let's now review the more complete picture.

**1.1** I'm assuming you all know and remember how to deal with a series of numbers. We extend that notion such that each element of the sum is a function, $u_i$, of variable $x$. The notion of a partial sum is important here:
$$
\sigma_n(x):=\sum^n_iu_i(x)
$$
Then the infinite sum is *defined* as the limit of infinite $n$, $\sigma_{n\to \infty}(x)=f(x)$. If this limit exists, the sum is *convergent*. But how does the existence of this limit depend on the variable $x$? Well, if it doesn't then the series is said to be *uniformly convergent*. 

>Let's say this exact same thing formally: 
>If $\forall \epsilon>0$ and $x\in[a,b]$, $\exists N\in \mathbb{Z}_+$ such that $|f(x)-\sigma_{n>N}(x)|<\epsilon$, the series converges to $f(x)$ uniformly on interval $[a,b]$.
> (Read as if for all positive $\epsilon$ and $x$ in interval [a,b] there exists a positive integer $N$...)

The concept of non-uniform convergence comes up usually near the boundaries of the interval of convergence where there must be some constraint on $x$ that renders the sum finite. 

>I'll remind you that series can also either be absolutely or conditionally convergent. A series, $\sum_i^\infty u_i(x)$ is absolutely convergent if $\sum_i^\infty |u_i(x)|<\infty$. If a series is convergent but not absolutely convergent, it is conditionally convergent. 
>*Absolute/conditional convergence is a distinct notion from uniform convergence!*

As you probably recall, there are tests of all kinds of convergence. Two popular tests for uniform convergence is the Weierstrass M test (very simple to prove and implement) and Abel's test (rather subtle but important for power series). 

**Uniform convergence is very important to check because it implies $f(x)$ and $u_i(x)$ are at least continuous and the series can be integrated or differentiated term-wise.**

**1.2** The first note is to remind you about the notion of convergence which you should always have in the back of your mind. Practically, what's more relevant is constructing these function series in a useful way. In physics useful will typically mean

- Approximate integrals by replacing the integrand with a series expansion
- Solve ODEs by choosing an appropriate power series expansion of the solution (this is where you care about convergence).
- Approximate ODEs by perturbation series 

Suppose a function is represented by a uniformly convergent series 
$$
f(x)=\sum_i^\infty u_i(x) .
$$
on some interval. How do we actually figure out $u_i(x)$ for a given $f(x)$? Suppose the function is such that I can differentiate it as much as I want. Consider
$$
\int_a^xdx_1f^{(n)}(x_1)=f^{(n-1)}(x)-f^{(n-1)}(a)
$$
If I keep integrating, I will eventually reach $f(x)-f(a)$:
$$
\int_a^xdx_n\int_{a}^{x_n}dx_{n-1}...\int_a^{x_2}dx_1f^{(n)}(x_1)=f(x)-f(a)-(x-a)f'(a)-(x-a)^2f''(a)/2!+...
$$
Define the LHS to be $R_n(x)$, the remainder and solve for $f(x)$:
$$
f(x)=f(a)+(x-a)f'(a)+(x-a)^2f''(a)/2!+R_n(x)
$$
The remainder can be thought of as the error incurred by truncating at order $n$. The condition for the convergence of a Taylor series to the function is simple, we just need $R_{n\to\infty}=0$. Finally, we have as the Taylor expansion:
$$
f(x) = \sum^\infty_{i=0}\frac{(x-a)^n}{n!}f^{(n)}(a)
$$
If you choose to truncate at some finite order we say the expansion is accurate to that order, for small $x$.

> The form of the remainder is rather ugly and probably unfamiliar. By applying the [mean value theorem](https://en.wikipedia.org/wiki/Mean_value_theorem) $n$ times we get the more familiar
> $$
> R_n = \frac{(x-a)^n}{n!} f^{(n)}(\zeta)
$$
for $\zeta\in[a, x]$. As an exercise, show that this is true. The mean value theorem is very useful and you should know how to apply it.

The named functions like the exponential, trig functions, logarithm etc. are defined by their Taylor expansions around $a=0$. So, $\exp(x)$ is literally $\sum_{i=0}^\infty x^n/n!$

>Taylor series are an example of what are called power series where the $x$ dependence of the terms is monomial. Power series can be easily checked for convergence. For coefficients $a_n$, if
$$
\lim_{n\to \infty}\left|\frac{a_{n+1}}{a_n} \right| = \frac{1}{R}
$$ 
the series converges on at least $(-R, R)$ and possibly $[-R, R]$. It converges uniformly and absolutely inside $(-R+\epsilon, R-\epsilon)$. That is, power series may be term wise integrated and differentiated.

To test your understanding, prove that power series expansions of functions are unique. This is an extremely important technical result. 

**1.3** Here are some important techniques you might find useful:

- *Cauchy product:* Consider $f(x)g(x)=\sum_i a_i x^i\times \sum_jb_j x^j$. The product of power series is a *convolution*:
$$
 f(x)g(x)= \sum_{i}^\infty\sum_j^i a_j b_{i-j}x^i
$$ 
- *Binomial expansion:* Often you'll com across powers of sums. These are finite special power series where the coefficient are the binomial coefficients (n choose r):
$$
(x+a)^n = \sum_k^n C_{n}^k x^k a^{n-k}
$$

- *Inversion*: In algebraic manipulations it might be necessary to invert power series. Typically it's sufficient to brute force things. Suppose you're trying to solve $y = \sum_i^\infty a_i x^i$ for $x$. Because expansions are unique, we know
$$
x=\sum_i b_i y^i\implies x = \sum_{i}b_i \left(\sum_j a_j x^j\right)^i
$$ 
This is a mess but you can tackle it term by term: $b_1=1/a_1,$ $b_2=-a_2/a_1^3$ and so on. 

- *[Euler transformation](https://mathworld.wolfram.com/EulersSeriesTransformation.html)*: This improves convergence of alternating series and might make finding the convergence radius easier. 

- *[Partial fraction decomposition](https://en.wikipedia.org/wiki/Partial_fraction_decomposition)*: This is a very commonly employed technique especially when multiplying power series and integrating ratios.

**1.4** It's great to have power series expansions - Uniqueness of such expansions is certainly very powerful in solving ODEs (formally) exactly and the fact that we can bound error means we can get the desired accuracy with sufficient effort. What if these aren't immediately granted? Are non-unique expansions with unknown error of any use to us? Can we make use of divergent expansions? 

**It turns out such expansions are even more useful:** These are the so-called *asymptotic expansions* of which the (truncated) Taylor expansion is a particular example. Regarding the latter question, it is often the case that divergent series better approximate certain functions than convergent ones at the same order (Bessel functions usually used to illustrate this). The idea is that as long as you know of a small parameter, you can expand things and make progress regardless of the analytical details. You will be doing physics this way in no time!

>Note the leading terms in $\sin x\sim x-x^3/6$ near $x=0$. But let's also look at $\sin x\sim x+2 x^2$. Near $x=0$  it's hard to tell the two approximations apart, though third order Taylor is better (obviously). Thus, $\sin$ doesn't have unique asymptotic expansions but do you *really* care near $x=0$?



```python
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(-.05, .05, 200)
plt.plot(x, np.sin(x), label=r'$sin x$')
plt.plot(x, x-x**3/6, label=r'Third order Taylor')
plt.plot(x, x+2*x**2, label=r'Second order asymptotic')
plt.legend()
plt.grid()
```


![png](Week1_files/Week1_1_0.png)


## Differential vector calculus

**2.1** Consider a set together with two operations - addition and scalar multiplication. Roughly, such a set is a vector space with each element called a vector if the sum of of two vectors is again a vector and multiplication by a scalar rescales the vector. There is an additive inverse ($-\vec v=\vec v^{-1}$), additive identity ($\vec 0$) and scalar identity ($1$).  There are two more operators we may consider:  

- The scalar product which assigns a number to two vectors (technically one vector and one co-vector). 
- The cross product  takes two vectors into a vector normal to the plane spanned by the two vectors where normality is defined relative to the inner product.

Let's focus on vector in Euclidean space, $\mathbb{R}^d$ where a vector is, morally speaking, a direction and a magnitude. In this simple review we choose the intuitive basis
$$
\vec v =\sum_{i=1}^dv_i\hat e_i
$$
with $\hat e_i$ the unit vector pointing in direction $i$ and $v_i$ the component of the vector in that direction. The basis vectors are such that $\hat e_i\cdot \hat e_j = \delta_{ij}$. Two such vectors for which this is true are said to be orthonormal.

**2.2** We live in $\mathbb R^3$ so a vector at *a point* (technically we say it is over the point) in this space is $\vec v = a \hat x+ b\hat y+c \hat z$ (in rectangular coordinates). If we assign such a vector to each point in $\mathbb R^3$ we get a vector field on $\mathbb R^3$,
$$
\vec F(x,y,z) = a(x,y,z)\hat x+b(x,y,z)\hat y+c(x,y,z)\hat z.
$$
That is, it is a vector valued function $F:\mathbb R^3\to \mathbb R^3$. This function is assumed to be smooth.
> Here are some fancy words: *A vector field is a section of the tangent bundle over some manifold.* I've used the language of differential geometry - you might find MATH 481 to be useful if you want to get a better appreciation for the vector calculus you'll be doing. 

**2.3** At the end of the day, we want to study how things change so we should think about how to differentiate things. Note first that a vector field may already be the derivative of a scalar function. A derivation that maps a scalar to a vector at each point is a gradient, $\vec \nabla=\partial_x \hat x+\partial_y\hat y+\partial_z\hat z$.

If $\vec F(x,y,z) =\vec \nabla U(x,y,z)$ we say the vector field is a conserving field. Typically, the vector fields we consider will be gradients of scalar functions. You will see why in a week or two. 

The gradient of a scalar function vanishes at what are called critical points. Such points are either local maxima, local minima or saddles. The classification of critical points is more nuanced in higher dimensions ($d>2$) than the second derivative test (see 2.4).

With $\vec \nabla $ being a vector, we can consider inner and cross products with vector fields:
$$
\text{curl}(F) = \vec\nabla\times \vec F(x,y,z)\\
\text{div}(F) = \vec\nabla \cdot F(x,y,z)
$$

The curl tells you how quickly a vector field twists while the divergence tells you how something about the flow rate (flux) through some imaginary surface. This is all stuff you should know...

**2.4** We can also consider various second derivatives. The most important is the Laplacian of a scalar function:
$$
\nabla\cdot(\nabla U(x,y,z)):=\nabla^2U(x,y,z).
$$
>You'll probably see me write $\Delta$ for the Laplacian. 

>The geometric analog of the cross second derivative $\partial^2/\partial x\partial y$ is the Hessian. It's defined as the Jacobian of a gradient. In components, 
$$
H_{ij}f=\frac{\partial^2 f}{\partial x^i\partial x^j}.
$$
We won't use the Hessian though it has an important role in dynamics, in particular it can classify critical points (there is an entire field of geometry built around this object called Morse theory). It is morally the 'second derivative' test - you look at the sign of the Hessian eigenvalues (which you'll learn about).

## Reading recommendations 

-  *Mathematical methods for physicists* by Arfken and Weber is a great resource for learning and brushing up on the applied math used in physics. I've used it as a guide in writing the stuff on series. 

	-	If you *really* want to learn 'calculus', *Introduction to Real Analysis* by Bartle and Sherbert is pretty standard. 

- *[Introduction to the foundation of applied math](https://link.springer.com/book/10.1007/978-0-387-87765-5)* by Mark Holmes is great for learning about how to *actually* solve ODEs. There's a bit of CM in it too. I would read the first few chapters ASAP. 

> You can get all springer books for free by using the UIUC library proxy or a VPN. Just go on springer link. 



```python

```
