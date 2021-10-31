# Poisson brackets and angular momentum

(Without having to manipulate the Levi-Civita symbol)

  - [Algebra of 3 dimensional rotations.](#algebra-of-3-dimensional-rotations)
    - [Case I: $\{L_x, L_y\}$](#case-i-l_x-l_y)
    - [Case II: $\{L_x, L_z\}$](#case-ii-l_x-l_z)
    - [Case III: $\{L_y, L_z\}$](#case-iii-l_y-l_z)
  - [Quadratic Casimir ($L^2$)](#quadratic-casimir-l2)
    - [Case I: $i\equiv x$](#case-i-iequiv-x)
    - [Case II: $i\equiv y$](#case-ii-iequiv-y)
    - [Case III: $i\equiv z$](#case-iii-iequiv-z)
  - [Angular momentum - energy brackets](#angular-momentum---energy-brackets)
    - [Spherical symmetry](#spherical-symmetry)
    - [Planar rotational symmetry](#planar-rotational-symmetry)


---
$$ \dot q = \frac{\partial H}{\partial p}, \quad \dot p = -\frac{\partial H}{\partial q}$$
$$\{f, g\} = \frac{\partial f}{\partial q}\frac{\partial g}{\partial p} - \frac{\partial f}{\partial p}\frac{\partial g}{\partial q}$$
$$\{f,f\}=0$$
$$\{f, g\}=-\{f,g\}$$
$$ \{f^2,g\} = 2f\{f,g\}$$
$$\{fg,h\} = f\{g,h\}+g\{f, h\}$$
$$ \{f, q\}=\partial_p f$$
$$\{f, p\}=-\partial_q f$$

---

## Algebra of 3 dimensional rotations.

Let's show that $\vec L : = \vec r\times \vec v$ is a constant of motion (by brute force computation) if any two components of the vector are constants of motion. We are going to need the following angular momentum components:
$$
\begin{aligned}
L_x &= y p_z - zp_y\\
L_y&= zp_x-xp_z\\
L_z&=xp_y-yp_x
\end{aligned}
$$

Note that none of these quantities depend explicitly on time: $\frac{d}{dt}L_i= 0$. Hence, the bracket $\{L_i, L_j\}$ *must* be a constant of motion. Let us compute it:

### Case I: $\{L_x, L_y\}$
Note the following vector derivatives:
$$
\begin{aligned}
\frac{\partial L_x}{\partial \vec q} &= (\partial_x [ y p_z - zp_y], \partial_y[ y p_z - zp_y], \partial_z [ y p_z - zp_y])^T=(0, p_z,-p_y)^T\\
\frac{\partial L_x}{\partial \vec p} &= (0, -z, y)^T\\
\end{aligned}
$$
and
$$
\begin{aligned}
\frac{\partial L_y}{\partial \vec q} &= (-p_z, 0,p_x)^T\\
\frac{\partial L_y}{\partial \vec p} &= (z, 0, -x)^T\\
\end{aligned}
$$
Then, we can construct explicitly
$$
\begin{aligned}
\{L_x, L_y\} &= \frac{\partial L_x}{\partial q}\frac{\partial L_y}{\partial p} - \frac{\partial L_x}{\partial p}\frac{\partial L_y}{\partial q} \\
&=(0, p_z,-p_y)^T\cdot(z, 0, -x)-(0, -z,y)^T\cdot(-p_z, 0, p_x)\\
&=p_yx - p_x y\\
&= L_z
\end{aligned}
$$

### Case II: $\{L_x, L_z\}$
We are going to need the additional data:
$$
\begin{aligned}
\frac{\partial L_z}{\partial \vec q} &= (p_y, -p_x,0)^T\\
\frac{\partial L_z}{\partial \vec p} &= (-y, x, 0)^T\\
\end{aligned}
$$
Then,
$$
\begin{aligned}
\{L_x, L_z\} &= \frac{\partial L_x}{\partial q}\frac{\partial L_z}{\partial p} - \frac{\partial L_x}{\partial p}\frac{\partial L_z}{\partial q} \\
&=(0, p_z,-p_y)^T\cdot(-y, x, 0)-(0, -z,y)^T\cdot(p_y, -p_x,0)\\
&=p_zx - zp_x\\
&= -L_y
\end{aligned}
$$

### Case III: $\{L_y, L_z\}$

We have everything we need to construct this bracket. You might see a pattern here and guess $\pm L_x$. Here's the computation:

$$
\begin{aligned}
\{L_y, L_z\} &= \frac{\partial L_y}{\partial q}\frac{\partial L_z}{\partial p} - \frac{\partial L_y}{\partial p}\frac{\partial L_z}{\partial q} \\
&= (-p_z, 0,p_x)^T\cdot (-y, x, 0)- (z, 0, -x)^T\cdot (p_y, -p_x,0)\\
&= p_zy-zp_y\\
&= L_x
\end{aligned}
$$
> If two components of angular momentum are conserved, the third component and hence the whole vector is conserved. This structure is called the algebra of three dimensional rotations, or, more formally, the special orthogonal Lie algebra of three generators (the $L_i$'s), $\mathfrak{so}(3)$. It is defined by the relation $$\{L_i, L_j\} = \varepsilon^{ijk}L_k$$,
> where $\varepsilon^{ijk}$ is the maximally anti-symmetric/Levi-Civita symbol. You will learn more about this algebraic (and geometric) structure later. 

## Quadratic Casimir ($L^2$)

Now let's take a look at $\{L^2, L_i\}$. Notice that this is 
$$
\{\sum_j L_j^2, L_i\}=\sum_j\{L_j, L_i\}
$$
by the (bi)linearity of the bracket. We can now use the identity
$$
\{f f, g\}=2f\{f, g\}
$$
to write 
$$
\{L^2, L_i\} = 2\sum_j L_j\{L_j, L_i\}
$$

### Case I: $i\equiv x$

Explicitly, 
$$
\begin{aligned}
\{L^2, L_x\} &= 2\sum_j L_j\{L_j, L_x\}\\
&= 2(L_x\{L_x, L_x\}+ L_y\{L_y, L_x\}+L_z\{L_z, L_x\}) \\
&=2(0+L_y(-L_z)+L_zL_y)\\
&=0
\end{aligned}
$$

### Case II: $i\equiv y$

Now,
$$
\begin{aligned}
\{L^2, L_y\} &= 2\sum_j L_j\{L_j, L_y\}\\
&= 2(L_x\{L_x, L_y\}+ L_y\{L_y, L_y\}+L_z\{L_z, L_y\}) \\
&=2(L_xL_z+L_z(-L_x))\\
&=0
\end{aligned}
$$

### Case III: $i\equiv z$

Finally,
$$
\begin{aligned}
\{L^2, L_z\} &= 2\sum_j L_j\{L_j, L_z\}\\
&= 2(L_x\{L_x, L_z\}+ L_y\{L_y, L_z\}+L_z\{L_z, L_z\}) \\
&=2(-L_xL_y+L_yL_x)\\
&=0
\end{aligned}
$$

> We have found that the squared magnitude of angular momentum Poisson commutes with the angular momentum. Hence, a system with Hamiltonian $$H=L^2$$ has $\{H,L_i\}=0$ and hence conserves angular momentum, as expected. 

> $L^2$ is the quadratic Casimir of the (Lie) algebra of 3 dimensional rotations, $\mathfrak{so}(3)$. The Casimir element of a Lie algebra is quadratic in the generators and commutes with every generator.

## Angular momentum - energy brackets
### Spherical symmetry
Suppose we have a Hamiltonian of the form 
$$
H= L^2+U(|\vec q|).
$$
We know this system to conserve angular momentum. So it must be that $\{H, \vec L\}=0$. We have already seen $\{L^2, L_i\} =0 $ so let's focus on the radial potential. 
$$
\begin{aligned}
    \{U(r), L_x\} &= \{U(r), y p_z - zp_y\}\\
                  &= \{U(r), yp_z\} - \{U(r), z p_y\}\\
                  &= (\{U(r), y\}p_z +\{U(r), p_z\}y) - (\{U(r), z\}p_y+\{U(r), p_y\}z)\\
                  &=\{U(r), p_z\}y-\{U(r), p_y\}z, \quad\quad [\{U(r), q_i\}=0]\\
                  &= -\partial_z U(r)y - \partial_y U(r)z\\
                  &= -U'(r)\frac{\partial r}{\partial z}y - U'(r)\frac{\partial r}{\partial y}z\\
                  &=-U'(r)\left(\frac{z}{r}y-\frac{y}{r}z \right)\\
                  &=0
\end{aligned}
$$
I'll leave the other components up to you. In the last step, I used the fact that $\frac{\partial r}{\partial q_i} = \frac{q_i}{r}$ with $r=\sqrt{q_iq^i}$. 

> We have shown that $L_z$ is a constant of motion. Take my word (or show) that this is true for $L_y$ and $L_z$. Hence, $$\{H,L_i\}=0\implies \frac{d\vec L}{dt}=0,$$ as we expect

### Planar rotational symmetry

Now let 
$$
H= L^2+U(q_1).
$$
The potential that depends on a single component of $\vec q$ breaks the full rotational symmetry of $L^2$. So the only invariant rotations of this system are those that fix $q_1$. Let's prove this.

$$
\begin{aligned}
    \{U(x), L_x\} &= \{U(x), y p_z - zp_y\}\\
                  &= \{U(x), yp_z\} - \{U(x), z p_y\}\\
                  &= (\{U(x), y\}p_z +\{U(r), p_z\}y) - (\{U(x), z\}p_y+\{U(r), p_y\}z)\\
                  &=\{U(x), p_z\}y-\{U(x), p_y\}z\\
                  &= -\partial_z U(x)y - \partial_y U(x)z\\
                  &= 0
\end{aligned}
$$
The central object of the computation is the $\{U(x), p_z\}$ and $\{U(x), p_y\}$ which both vanish because $U(x)$ doesn't depend on $z$ or $x$. But the term
$$
\{U(x), p_x\} = -U'(x)\neq 0
$$
is generated in the brackets $\{U(x), L_y\}$ and $\{U(x), L_z\}$. So only rotations around $\hat x$ generated by $L_x$ are symmetries and hence only $L_x$ is a constant of motion.

