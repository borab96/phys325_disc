# Deformations of solids

Recall that a rigid solid is defined through a static relation between any given point in the solid. This ensures that the body moves as a unit. One can relax this constraint to allow for *deformations*:
$$
x\mapsto x+u(x)
$$
Notice that such a deformation encodes translations, rotations and **relative displacement**.
## Deformation tensor
The displacement, $u(x)$, is a dynamical field on its own right. We typically do not want to single out any one $x\in M$, where $M$ is our object, but rather the relative displacements that can occur during motion. 

We thus define the deformation tensor,
$$
D_{ij} = \frac{\partial u_i}{\partial x^j}.
$$
Each component encodes the relative infinitesimal displacement, $du^i$, per a given infinitesimally separated pair of points on the object, $dx^j$. 

As I mentioned in the beginning, we are still keeping track of rigid displacements - ones that respect the structural integrity of the object. 

## The role of rigid translations

The simplest displacement is $x\mapsto x+u$ where $u$ is now constant. This constant is killed by the $\partial_{x^j}$ derivative in the deformation tensor so rigid translations are ignored automatically. 

## The role of rigid rotations

Note that a particular kind of displacement is one of the form
$$
u(x) = \varepsilon_{ijk}\psi^jx^k.
$$
This is a *rigid* rotation by infinitesimal angle $\psi^j$ does not cause strain and is not eliminated by the $\partial_{x^j}$ derivative:
$$
\frac{\partial \varepsilon_{ijk}\psi^jx^k}{\partial x^l}= \varepsilon^{ijk}\psi^j\delta^k_l =\varepsilon^{ijl}\psi^j
$$
The result is a maximally anti-symmetric two-tensor of angles. Let's denote it $\Psi_{ij}$. Maximal asymmetry means
$$
\frac{1}{2}(D_{ij}-D_{ji})=\Psi
$$
Thus, the deformation tensor, ignoring rigid rotations is given by 
$$
\epsilon_{ij}:= D_{ij}-\Psi_{ij}
$$
Here is a fact: *Every 2-tensor can be decomposed into symmetric and anti-symmetric components*. Then,
$$
D_{ij} = \underbrace{\frac{1}{2}(D_{ij}+D_{ji})}_{\epsilon_{ij}}+\underbrace{\frac{1}{2}(D_{ij}-D_{ji})}_{\Psi_{ij}}
$$

## Strain

Non-rigid deformations are what are called strains. Hence,
$$
\epsilon_{ij}:= D_{ij}-\Psi_{ij} = \frac{1}{2}(D_{ij}+D_{ji})
$$
is referred to as the strain tensor. 
- $\epsilon_{ii}$ are the tensile strains (stretching in eigendirections, $\{\hat x_i\}$). 
- A homogenous tensile strain, $\epsilon = \gamma\mathbb I$, is a dilation by factor $\gamma$. It's common to factor out a strain that is a dilation. 
-  The off diagonal entries are the shear strains. 

## The stress tensor

In the realm of solid mechanics, the strain -- the deformation of the solid -- is a an observable that can be empirically related to the stress present in the system (hard to observe). This is the content of Hooke's Law (and its generalization to non-linear stress-strain relationships).

In much of modern physics we speak of the stress tensor and not so much of the strain tensor. This is because we usually have access to the microscopic theory that allows us to construct the stress tensor directly (think electromagentic stress tensor). In the case of solids, the microscopic theory is complex and usually beyond the scope of classical mechanics, hence our focus on strain.

At the end of the day, it is the stress tensor that enters into the action and hence determines the classical field equations.

For instance, the Maxwell stress tensor $F$, once assembled into action
$$
\int d^{d}x \underbrace{F^{\alpha \beta}F_{\alpha \beta}}_{E^2-B^2}
$$
and has field equations $dF=0$. These are the homogenous Maxwell equations, once written out in terms of $E$ and $B$.