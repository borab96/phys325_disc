# Hamilton-Jacobi theory

## Basic motivation

We begin with the notion of a phase space. At time $t$ we speak of a dynamical system as being in some state that lives in this phase space. Classically, this state is specified by providing a generalized coordinate $q_i$ along with an associated (conjuage) momentum $p_i$. In general, the potential may be time dependent so we extend the phase space to be parameterized by $(q_i, p_i; t)$ but let's ignore this possibility for now. For $n$ degrees of freedom, this means the phase space will have dimension $2n$. Call this space $\mathcal P^{2n}$.

We can define the smooth function $H:\mathcal P^{2n}\to\mathbb R$ which obeys 
$$
\dot p = -\frac{\partial H}{\partial q},\quad \dot q = \frac{\partial H}{\partial p}.
$$
This data defines a flow on $\mathcal P$. To make this fact less formal, one has to make sense of this notion of conjugacy. The $q_i$ parameterize the configuration space and have associated EOM
$$
\frac{\partial L}{\partial q} = \frac{d}{dt}\frac{\partial L}{\partial \dot q}
$$
in the Lagrangian formalism. A typical Lagrangian will have kinetic term $\dot q_i M^{ij}\dot q_j$ (a quadratic form). To simplify things, let's assume $M=\mathbb I/2$. Hence, the RHS becomes
$$
\ddot q = \frac{\partial L(q,\dot q)}{\partial q}
$$
We can reduce the order of this ODE with the definition $p_i=\dot q_i$ and write
$$
\dot p_i = \frac{\partial L}{\partial q^i}
$$
for the EOM. Also note that 
$$
p_i =\frac{\partial L}{\partial \dot q^i}
$$
by definition. This is the conjugacy relation between the generalized coordinate and the generalized momentum. 

Without knowing some differential geometry, we have to take a bit of a logical leap here: The dynamical equivalent of a Lagrangian in terms of the phase space coordinates is the total energy, 
$$
H:=T+U = p^i\dot q_i - L.
$$
Using this, one can now check that indeed
$$
\dot p = -\frac{\partial H}{\partial q},\quad \dot q = \frac{\partial H}{\partial p}.
$$
## Basic motivation, symplectic geometry edition

Let $(\mathcal P, \omega)$, a symplectic manifold, be the phase space. Physically, is is the cotangent bundle of configuration space, $M$, $T^*M$. The Lagrangian is defined on the tangent bundle (technically the jet bundle), $TM$, and encodes the dynamics of the system through the princple of least action. The same dynamical data can be encoded by a function on the cotangent bundle.

......

## Poisson brackets

The canonical equations are given by 
$$
\dot q = \frac{\partial H}{\partial p}\quad \dot p = -\frac{\partial H}{\partial q}.
$$
Notice that this is a vector field on $\mathbb R^{6n}$ (for n bodies moving in $\mathbb R^3$). Call this $\Phi:\mathbb R^{6n}\to \mathbb R^{6n}$. This vector field is associated to diff eq
$$
\Phi(q, p) = -J\nabla H(q, p)
$$
where $J$ is the canonical anyismmetric matrix (i.e. $\omega(u, v) = (u, Jv) $ is the symplectic 2-form).

> A symplectic structure on the phase space uniquely defines a Hamiltonian vector field corresponding to a map $H:\mathbb R^{6n}\to\mathbb R$.

Let $f:\mathbb R^{6n}\to\mathbb R$ be a function on the phase space interpreted as a symplectic vector space. 

One can parameterize this function as $f(q, p)$ and construct the differential
$$
\begin{aligned}
\frac{d}{dt} f(q, p) &= \frac{\partial f}{\partial q} \dot q+\frac{\partial f}{\partial p} \dot p\\
&=  \frac{\partial f}{\partial q} \frac{\partial H}{\partial p}-\frac{\partial f}{\partial p} \frac{\partial H}{\partial q}\\
&:=\{H, f\}
\end{aligned}
$$
This is the Poisson bracket. Formally,
 > A Poisson bracket on manifold $P$ is the skew symmetric bilinear form $$ \{\cdot, \cdot\}:C^{\infty}(P)\times C^\infty (P) \to C^\infty (P)$$ satisfying the Jacobi identity (it's a bracket) and Leibniz rule (it's a derivation).


It is an extension of the symplectic structure in the following sense:

> Let $\Phi$ and $\Psi$ be two unique vector fields associated to maps $f,g:\mathbb R^{6n}\to\mathbb R$, Then, $$ \{f, g\}_\omega = \omega(\Phi, \Psi)$$ is a Poisson bracket.

### Constants of motion

Let's extend our function $f$ so that there is also a time dependence: $f(q, p;t)$. Now, 
$$
\frac{d}{dt} f(q, p;t) = \{H, f\}+\dot f
$$
>The function (observable) is said to be a *constant of motion* if it is not an explicit function of time $$\{H, f\}=0\iff \frac{df}{dt}=0$$

We have the slogan,
> Constants of motion commute with the Hamiltonian. 

The Poisson bracket makes sense for any smooth function on a symplectic manifold, not just the Hamiltonian. In general,
> $$\{f,g\} = \sum_{i=1}^{n} \left(\frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q_i} -\frac{\partial f}{\partial q_i}\frac{\partial g}{\partial p_i} \right)$$

We can now state Poisson's thm

> If $\frac{df}{dt}=\frac{dg}{dt}=0$ (observables $f$ and $g$ are constants of motion) $$\{f, g\}=\text{const.}$$

*Example:* Suppose $\vec L$ is conserved. Then $\{L_x, L_y\}=\text{const.}$ Is a constant of motion (it's $-L_z$).