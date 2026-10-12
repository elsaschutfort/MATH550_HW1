# MATH550 Homework 1: Solving the Stokes Equations in 2D on a Staggered Grid

## System Definitions
### Why P has no boundary condition?
The velocity boundary conditions fix the normal flux so adding a pressure condition would over-determine the problem. Additionally, the equations involve only the gradient of $P$, so adding a constant doesn't change anything.

## Problem 1

### Figure 1

![Alt text](figs/problem1.png)

The computed speed $\lVert u \rVert$ with streamlines show the low moves downard everywhere, slowest at the center and fastest at the periodic edges. This matches the manufactured solution and Figure 2 in the homework pdf.

## Problem 2
### Figure 2
![Alt text](figs/problem2.png)

The relative errors in U, V, and P vs the grid size. All three decrease at the same rate as the second-order reference line. This confirms $O(h^2)$ convergence.

## Problem 3
For Problem 3, I simulated flow through a simple porous microstructure. In a porous material, fluid moves through a network of pores too small to resolve individually, so the flow is described by an averaged relation instead. Darcy's law states that the flow rate is proportional to the pressure gradient,

$$\mathbb{u} = - \frac{\kappa}{\mu} \nabla P,$$

where the permeability $\kappa$ measures how easily fluid passes through the material, large $\kappa$ corresponds to an open, loosely packed medium, and small $\kappa$ to a tightly packed one. To combine free flow and porous regions in one domain, I solved the Stokes-Darcy equations,

$$\mu\nabla^2\mathbf{u} - \alpha(x,y)\,\mathbf{u} - \nabla P = 0, \qquad \nabla\cdot\mathbf{u} = 0,$$

where $\alpha = \mu/\kappa$ is the inverse permeability. Where $\alpha = 0$ this reduces to the ordinary Stokes equations. Where $\alpha$ is large, the drag term dominates and the velocity is pushed toward zero. Numerically, this only changes the Problem 1 system by subtracting the diagonal matrix $\mathrm{diag}(\alpha)$ from $L_u$ and $L_v$, with $\alpha$ evaluated on the $U$ and $V$ grids. I kept the same boundary conditions as in Problem 1 (periodic in $x$, $U = 0$ and $V = -3.5$ on the top and bottom) and set $\mathbf{b} = 0$.

I set $\mu = 1$ and places two circular porous grains of radius $0.10$, one in the upper left (centered at (0.25, 0.75)) and one in the lower right (centered at (0.75, 0.2)). Inside the grains, $\frac{\mu}{\kappa} = 100$, and outside them $\frac{\mu}{\kappa} = 0$, so the surrounding fluid obeys the ordinary Stokes equations.

## Figure 3

![Alt text](figs/problem3.png)

Using the Stokes-Darcy equations, two low-permeability discs centered near (0.25, 0.75) and (0.75, 0.20) act as obstacles in the downward $V = -3.5$ flow. The speed drops nearly to zero inside each disc, and the fluid is diverted around them, accelerating to about 5 in the open regions between.