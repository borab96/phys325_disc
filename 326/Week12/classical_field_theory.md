# Classical field theory

## Derivation of classical field equations

In the continuum setting, one replaces the Lagrangian with a Lagrange density, $L\to\mathcal L$, so that 
$$
S = \int dt d^{d-1}x \mathcal L[\phi, \dot \phi, \nabla \phi]
$$
is the action that gets minimized. Here $\phi(x, t)$ is a field defined on $M\times \mathbb R$ and is valued in some vector space which we may take to be $\mathbb R$ right now.

> Geometrically, $\phi$ is the section of some fiber bundle, in this case the trivial bundle. 

Our objective is to determine the dynamics obtained by minimizing this action. Hamilton's principle tells us 
$$
\delta S[\phi] = 0
$$
and we know that the $\phi$ for which this is true, the E-L equation holds. Let's prove this by working through the variational calculus involved. 



Pedantically, 
$$
\delta S = \int dt d^{d-1}x \delta\mathcal L[\phi, \dot \phi, \nabla \phi]
$$
Let's inspect the variation of the density $\mathcal L$:
$$
\begin{aligned}
\delta \mathcal L[\phi, \dot \phi, \nabla \phi] &=\delta \phi \frac{\partial \mathcal L}{\partial \phi}+\delta\dot \phi\frac{\partial \mathcal L}{\partial \dot \phi}+\delta \nabla \phi\frac{\partial \mathcal L}{\partial \nabla \phi} 
\end{aligned}
$$
this is simply the chain rule. The last two terms are not immediately useful because these are variations of derivatives of $\phi$ while we are interested in variations of $\phi$. Notice however the following fact
$$
\begin{aligned}
\delta \nabla \phi &=\nabla \phi(x)-\nabla \phi(x+\epsilon)\\
\nabla \delta \phi &=\nabla[\phi(x)-\phi(x+\epsilon)]
\end{aligned}
$$
and hence 
$$
\nabla \delta\phi = \delta\nabla \phi.
$$
The same holds for the time derivative too, of course. 

Then,
$$
\begin{aligned}
\delta \mathcal L[\phi, \dot \phi, \nabla \phi] &=\delta \phi \frac{\partial \mathcal L}{\partial \phi}+\delta\dot \phi\frac{\partial \mathcal L}{\partial \dot \phi}+\delta \nabla \phi\frac{\partial \mathcal L}{\partial \nabla \phi} \\
&= \left[\delta\phi\frac{\partial \mathcal L}{\partial \phi}+\partial_t\left\{\delta \phi\right\}\frac{\partial \mathcal L}{\partial \dot \phi}+\nabla\left\{\delta \phi\right\} \frac{\partial \mathcal L}{\partial \nabla \phi}\right]
\end{aligned}
$$
Returning to our action and integrating by parts,
$$
\begin{aligned}
\delta S &= \int dtd^{d-1}x\left[\delta\phi\frac{\partial \mathcal L}{\partial \phi}+\partial_t\left\{\delta \phi\right\}\frac{\partial \mathcal L}{\partial \dot \phi}+\nabla\left\{\delta \phi\right\} \frac{\partial \mathcal L}{\partial \nabla \phi}\right]\\
&= \int dtd^{d-1}x\delta \phi\left[\frac{\partial \mathcal L}{\partial \phi}-\partial_t\left\{\frac{\partial \mathcal L}{\partial \dot \phi}\right\}-\nabla\left\{ \frac{\partial \mathcal L}{\partial \nabla \phi}\right\}\right]+\underbrace{\delta \phi\frac{\partial \mathcal L}{\partial \dot \phi}+\delta \phi\frac{\partial \mathcal L}{\partial \nabla \phi}}_{\text{boundary terms}}\\
\end{aligned}
$$
If we assume the variation vanishes at the boundary or that the boundary is infinitely far away, we can throw these terms out. We are left with something familiar:
$$
\delta S=0\implies \frac{\partial \mathcal L}{\partial \phi}-\partial_t\left\{\frac{\partial \mathcal L}{\partial \dot \phi}\right\}-\nabla\left\{ \frac{\partial \mathcal L}{\partial \nabla \phi}\right\}=0.
$$
This is the continuum version of the Euler-Lagrange equation (now also called a classical field equation). If we take
$$
\mathcal L = \dot \phi^2+(\nabla \phi)^2+m^2\phi^2
$$
the corresponding field equation reads
$$
(\partial_t^2+\nabla^2+m^2)\phi(x, t).
$$
This is the Euclidean Klein-Gordon equation.

## Relativistic classical field theory

We will now construct an action that is Lorentz invariant. A Lagrangian density is said to be *manifestly* Lorentz invariant if it is constructed out of objects that transform `correctly' under the Lorentz transform.

For instance, $(\partial_t+\nabla)\phi$ does not transform as a Lorentz 4-vector but $(-\partial_t+\nabla)\phi$ does. We write this Lorentz covariant differential operator as
$$
\partial_\mu\equiv\frac{\partial}{\partial x^\mu}=\left(-\frac{\partial }{\partial t}, \frac{\partial }{\partial x^1},\cdots, \frac{\partial }{\partial x^{d-1}}\right).
$$
Now, something like $\eta_{\mu\nu}\partial^\mu\phi\partial^\nu\phi = \partial_\mu \phi \partial^\mu \phi$ is a Lorentz scalar. So the Lagrangian density
$$
\mathcal L =\partial_\mu\phi\partial^\mu\phi+m^2\phi^2
$$
is Lorentz invariant. The corresponding field equation is the relativistic Klein Gordon equation:
$$
(\square +m^2)\phi(x)=0
$$

## Non-standard Lagrangian densities

The standard scalar Lagrangian density is of the form
$$
g_{\mu \nu}\partial^\mu\phi\partial^\nu\phi+V(\phi)
$$
where $V$ is some polynomial. Lorentz invariance fixes the kinetic energy to be the invariant object $g_{\mu \nu}\partial^\mu\phi\partial^\nu\phi$ like we discussed. Typically we are interested in the quantized versions of these field theories. Concerns over the manageability of divergences fixes the potential to be a polynomial of some order (the order depends on the dimension of spacetime among other things).

When we work in the non-relativistic and non-quantized setting, we need not abide by these limitations. For instance, one can consider something like 
$$
 \mathcal L[\phi,\dot\phi, \nabla \phi, \nabla\dot \phi]
$$
which has no Lorentz-invariant analog because $\nabla \dot \phi$ explicitly breaks Lorentz invariance even if we assemble the other terms in a Lorentz invariant way. Here, the chain rule dictates
$$
\delta \mathcal L[\phi, \dot \phi, \nabla \phi,\nabla \dot \phi] =\left[\delta\phi\frac{\partial \mathcal L}{\partial \phi}+\partial_t\left\{\delta \phi\right\}\frac{\partial \mathcal L}{\partial \dot \phi}+\nabla\left\{\delta \phi\right\} \frac{\partial \mathcal L}{\partial \nabla \phi}+\nabla \partial_t\{\delta \phi\}\frac{\partial^2 \mathcal L}{\partial\nabla \dot\phi}\right]
$$
Let's focus on the new second order term that has appeared and see how it interacts with integration by parts:
$$
\begin{aligned}
\int dtd^{d-1}x\nabla \partial_t\{\delta \phi\}\frac{\partial \mathcal L}{\partial\nabla \dot\phi}&=-\int dtd^{d-1}x\nabla \delta \phi \partial_t\left\{\frac{\partial \mathcal L}{\partial \nabla \dot \phi }\right\}+\cdots\\
&=\int dtd^{d-1}x \delta \phi \nabla\partial_t\left\{\frac{\partial \mathcal L}{\partial \nabla \dot\phi}\right\}+\cdots
\end{aligned}
$$
which means the E-L equation becomes 
$$
\frac{\partial \mathcal L}{\partial \phi}-\partial_t\left\{\frac{\partial \mathcal L}{\partial \dot \phi}\right\}-\nabla\left\{ \frac{\partial \mathcal L}{\partial \nabla \phi}\right\}+\nabla\partial_t\left\{\frac{\partial \mathcal L}{\partial \nabla \dot\phi}\right\}=0.
$$