---
title: Numerics
layout: ../layouts/Base.astro
---

# Numerics

SAPIC combines a particle-in-cell (PIC) method with adaptive mesh refinement (AMR) to efficiently resolve plasma dynamics across multiple length scales.

## Particle-in-cell method

In the PIC method, macro-particles are advanced using the Lorentz force:

$$
m \frac{d\mathbf{v}}{dt} = q\left(\mathbf{E} + \mathbf{v} \times \mathbf{B}\right)
$$

Positions and velocities are updated with the Boris integrator, which is second-order accurate and conserves phase-space volume. The electric field is obtained by solving Poisson's equation on the mesh:

$$
\nabla^2 \phi = -\frac{\rho}{\varepsilon_0}, \qquad \mathbf{E} = -\nabla \phi
$$

## Adaptive mesh refinement

AMR allows the grid to be refined locally where gradients are large, reducing the total cell count compared to a uniform mesh. The refinement criterion is based on the local charge density gradient $|\nabla \rho|$, and the mesh is organised as an octree in 3D.
