# Week 5: Introduction to Numerical Methods

These notes give an introduction to numerical methods for solving the fluid equations, specifically *finite differencing* which is used often in astrophysics. They draw upon material from section 19.1 of *Numerical Recipes* by Press \& Teukolsky and the [course on hydrodynamics](http://www.ita.uni-heidelberg.de/~dullemond/lectures/num_fluid_2011/index.shtml) by P.~Dullemond at the University of Heidelberg, so I recommend you look at both of those if you want more details. At the end, I also briefly discuss other methods such as spectral methods and smoothed-particle hydrodynamics (SPH).

## Finite difference approximation for derivatives

We solve for fluid properties on a numerical grid, at locations $x_j = j\Delta x$ where $j$ labels the grid point. For simplicity here, we assume constant grid spacing $\Delta x$, although the results can be generalized to non-constant spacing.
Quantities on neighbouring grid points are related by a Taylor expansion
$$f_{j+1} = f_j + \Delta x f_j^\prime + {(\Delta x)^2\over 2}f_j^{\prime\prime}+{\mathcal O}(\Delta x^3)$$
$$f_{j-1} = f_j - \Delta x f_j^\prime + {(\Delta x)^2\over 2}f_j^{\prime\prime}+{\mathcal O}(\Delta x^3).$$
Considering either of these gives a first order expression for the first derivative,
$$f_j^\prime = {f_j-f_{j-1}\over \Delta x}+{\mathcal O}(\Delta x) \hspace{1cm} f_j^\prime = {f_{j+1}-f_{j}\over \Delta x}+{\mathcal O}(\Delta x).$$
Adding and subtracting instead gives a second order expression for the derivative and second derivative,
$$f_j^\prime = {f_{j+1}-f_{j-1}\over 2\Delta x} + {\mathcal O}(\Delta x^2)$$
$$f_j^{\prime\prime} = {f_{j+1} -2f_j + f_{j-1}\over (\Delta x)^2} + {\mathcal O}(\Delta x^2).$$
The idea of finite differencing is to replace partial derivatives in our equations with these discrete versions.

## The advection equation; numerical stability and numerical diffusion

If we are going to solve the fluid equations, we need to be able to solve the advection term $\partial/\partial t + \vec{v}\cdot\vec{\nabla}$. For example, consider advection of some function $f(x,t)$ with constant velocity $v$: $${\partial f\over \partial t}+v{\partial f\over\partial x}=0.$$
Using our expressions for the derivatives, a natural differencing scheme to write down is
$${f_j^{n+1}-f^n_j\over \Delta t} = - v {f_{j+1}^n-f_{j-1}^n\over 2\Delta x},$$
where $n$ labels the timestep. This gives an expression for the quantity $f$ at the next timestep $n+1$ in terms of the value at the current timestep $n$:
$$f_j^{n+1} = f^n_j - {v\Delta t\over 2\Delta x} \left(f_{j+1}^n-f_{j-1}^n\right).$$
This is known as the forward-time centered-space (FTCS) scheme. This kind of scheme is referred to as *explicit* because the new values are written explicitly in terms of the old ones.

In fact, it turns out that this scheme is always numerically unstable. You can see this by looking for a solution 
$$f_j^n = (\xi)^n e^{ikx_j},$$ where $k$ is the wavevector and $\xi$ is a complex amplitude. If $\left|\xi\right|>1$ for any value of $k$, that mode will grow exponentially with increasing timestep $n$, and the numerical scheme is unstable. Trying a solution like this for the FTCS scheme gives
$$\left|\xi\right|^2 = 1 + \left({v\Delta t\over \Delta x}\right)^2 \sin^2 \left(k\Delta x\right),$$
which is indeed greater than unity for any value of $k$.

Fortunately, there is a simple way to write a stable method, the Lax method:
$$f_j^{n+1} = {1\over 2}\left(f^n_{j+1}+f^n_{j-1}\right) - {v\Delta t\over 2\Delta x} \left(f_{j+1}^n-f_{j-1}^n\right).$$
This has 
$$\left|\xi\right|^2 = 1 + \left[\left({v\Delta t\over \Delta x}\right)^2 -1\right]\sin^2 \left(k\Delta x\right),$$
and so is stable for all $k$ as long as 
$${v\Delta t\over \Delta x}\leq 1.$$
This condition on the timestep is the *Courant-Friedrichs-Levy criterion* sometimes called just the  *Courant condition* or *CFL criterion*. The criterion states that our timestep must not exceed the fluid travel time between two grid points, which makes sense physically because the information about fluid quantities is advected at that speed. Larger timesteps require information from grid points further away than $\Delta x$, not included in our update.

A way to understand why the scheme is stable is to separate out the FTCS part and see what additional terms have been added. The Lax method can be rewritten
$${f_j^{n+1}-f^n_j\over \Delta t} = - v {f_{j+1}^n-f_{j-1}^n\over 2\Delta x} + \left({\Delta x^2\over 2\Delta t}\right){f_{j+1}^n -2f_j^n + f^n_{j-1}\over (\Delta x)^2}.$$
The additional term on the right is a diffusion term with diffusivity $(\Delta x)^2/2\Delta t$. This is known as *numerical diffusion*, it provides numerical dissipation that stabilizes the method. The damping is largest for short wavelengths where $k\Delta x\sim 1$ which are most unstable.

The Lax scheme provides a good illustration of different types of error:
- When $v\Delta t<\Delta x$, $\left|\xi\right|<1$, giving an *amplitude error*: the amplitude of any given mode $k$ decreases over time (it should stay constant under advection).
- *Phase error*. The factor $\xi$ in the Lax scheme can be rewritten as
$$\xi = e^{-ik\Delta x} + i\left(1-{v\Delta t\over\Delta x}\right)\sin k\Delta x.$$ For a timestep $\Delta t = \Delta x/v$, the phase of each mode is shifted by $k\Delta x$, equivalent to advecting by one grid point. But for timesteps $\Delta t<\Delta x/v$ the phase shift depends on $k$, so that different modes are advected at different speeds. Again, this should not happen under advection. This means that the numerical method introduces *dispersion* as the component waves of the profile we are trying to advect move with different speeds. 
- *Transport errors*: in the Lax scheme, the information from cells $j-1$ and $j+1$ propagates to cell $j$ in the next timestep. But physically, if the velocity is to the right for example, only information in cell $j-1$ should be used to update cell $j$. A way around this is *upwind differencing* which avoids this problem, but at the expense of being first order. The idea is to update either from the left or from the right, depending on the direction of the velocity:
$${f^{n+1}_j-f^n_j\over \Delta t} = -v_j {f_j^n-f_{j-1}^n\over \Delta x}\hspace{1cm} v_j^n>0$$
$${f^{n+1}_j-f^n_j\over \Delta t} = -v_j {f_{j+1}^n-f_j^n\over \Delta x}\hspace{1cm} v_j^n<0.$$

Everything we've discussed here is first order in time, but there are higher order methods that you can read about in Numerical Recipes. A useful one is *staggered-leapfrog* which uses a second-order time-derivative
$$f_j^{n+1} =f^{n-1}_j - {v\Delta t\over 2\Delta x} \left(f_{j+1}^n-f_{j-1}^n\right).$$ Numerically this requires storing the previous two timesteps in order to do the update. This method has the advantage that $\left|\xi\right|=1$ for all modes no matter what timestep is used: the stability analysis gives
$$\xi = -i{v\Delta t\over \Delta x}\sin k\Delta x\pm \sqrt{1-\left({v\Delta t\over \Delta x}\sin k\Delta x\right)^2},$$
so while there is dispersion (the phase evolution is different for different modes), the amplitude of each mode stays constant, much better than the very dispersive first order Lax method. Note that staggered leapfrog also has a limit $\Delta t\leq \Delta x/v$ for stability.

## The diffusion equation: implicit methods

Another operator that appears in the fluid equations is diffusion. Whereas for advection our first attempt at writing down a differencing scheme was completely unstable, here the simplest differencing that you might write down does work! It is stable as long as we take small enough timesteps. The update is
$${f_j^{n+1}-f^n_j\over \Delta t} = D {f_{j+1}^n -2f_j^n + f_{j-1}^n\over (\Delta x)^2},$$
with $${D\Delta t \over (\Delta x)^2} \leq {1\over 2}$$ for stability. The physical interpretation is that the timestep is constrained by the diffusion time between grid cells.

Solving diffusion problems with explicit schemes is particularly slow, because the distance diffused in time $t$ grows slowly with time, as $L\propto t^{1/2}$. Diffusion across a scale $L$ takes a time $L^2/D$, so the number of timesteps needed is $L^2/D\Delta t \geq 2 (L/\Delta x)^2\sim N^2$ where $N$ is the number of grid points. 

An alternative scheme that allows larger timesteps, at the expense of accuracy on small scales, is an *implicit* scheme
$${f_j^{n+1}-f^n_j\over \Delta t} = D {f_{j+1}^{n+1} -2f_j^{n+1} + f_{j-1}^{n+1}\over (\Delta x)^2},$$
in which we write the update in terms of the values at the next timestep rather than at the current timestep (hence the name implicit). Rearranging, we can write this as
$$ -\alpha f_{j+1}^{n+1} +(1+2\alpha)f_j^{n+1} - \alpha f_{j-1}^{n+1} = f^n_j$$
where $\alpha = D \Delta t / (\Delta x)^2$. Written as a matrix equation this is
$$A f^{n+1} = f^n$$
for the vectors $f^{n+1}$ and $f^n$, where the matrix $A$ is tridiagonal, with entries $1+2\alpha$ on the diagonal and $-\alpha$ on the upper and lower diagonals. This system can be solved by finding the inverse of the matrix $A$, since then $f^{n+1}=A^{-1}f^n$. 

This *fully-implicit* scheme has the feature that it goes to the steady-state solution for large time-steps $\Delta t\rightarrow \infty$. Although small scales are not followed accurately for large timesteps, they go the correct steady-state solution. An alternative *semi-implicit* scheme is Crank-Nicholson
$${f_j^{n+1}-f^n_j\over \Delta t} = {D\over (\Delta x)^2} \left[ {1\over 2}\left(f_{j+1}^n -2f_j^n + f_{j-1}^n\right) + {1\over 2}\left(f_{j+1}^{n+1} -2f_j^{n+1} + f_{j-1}^{n+1}\right)\right]$$
which is also stable for large timesteps. It has the advantage that it is second order in both space and time, whereas fully-implicit is second order in space, but first order in time.

## Operator splitting

You will often have multiple operators in the equation you are solving. A simple example is the *advection-diffusion* equation
$${\partial f\over\partial t} = - v{\partial f\over\partial x} + D {\partial^2 f\over\partial x^2}.$$
One way to deal with this is to calculate the update for each operator separately. Starting with $f^n$, generate $f^{n+\frac{1}{2}}$ by updating with the diffusion operator with timestep $\Delta t$, then update $f^{n+\frac{1}{2}}$ with the advection operator with timestep $\Delta t$ to obtain the final values $f^n$. So for example, you could use an implicit scheme for diffusion and an explicit scheme for advection; the timestep would then be limited by the CFL condition from the fluid velocity.

## Flux-conservative schemes

In week 1, we talked about the idea that the fluid equations are conservation laws for mass, momentum, and energy, and can be written in flux-conservative form. Working with the equations in this form allows us to write a numerical method that exactly conserves these quantities.

In *finite-volume methods*, we divide the volume into cells such that the grid points $x_j$ are the locations of the cell centres, and the cell boundaries are at locations $x_{j\pm 1/2} = (1/2)(x_j + x_{j\pm 1})$. We then solve the equation
$${\partial f\over \partial t} = -{\partial J\over \partial x},$$
or in discretized form
$${f_j^{n+1}-f_j^n\over \Delta t} = -{J^{n+\frac{1}{2}}_{j+\frac{1}{2}}-J^{n+\frac{1}{2}}_{j-\frac{1}{2}}\over \Delta x},$$
where the $J$'s represent the flux of quantity $f$ at the cell boundaries ($j\pm 1/2$) averaged over the timestep:
$$J_{j+\frac{1}{2}}^{n+\frac{1}{2}} = {1\over \Delta t}\int_t^{t+\Delta t} dt\ J_{j+\frac{1}{2}}(t).$$
This formulation automatically conserves the quantity $f$, since the flux *out of* one cell equals the flux *into* the neighbouring cell. 

The simplest choice for the flux $J$ is to write
$$J_{j+\frac{1}{2}} = v_{j+\frac{1}{2}}f_j^n\hspace{1cm} v_{j+\frac{1}{2}}>0$$
$$J_{j+\frac{1}{2}} = v_{j+\frac{1}{2}}f_{j+1}^n\hspace{1cm} v_{j+\frac{1}{2}}<0$$
$$J_{j-\frac{1}{2}} = v_{j-\frac{1}{2}}f_{j-1}^n\hspace{1cm} v_{j-\frac{1}{2}}>0$$
$$J_{j-\frac{1}{2}} = v_{j-\frac{1}{2}}f_j^n\hspace{1cm} v_{j+\frac{1}{2}}<0$$
which is known as *donor cell advection* (equivalent to the upwind differencing discussed earlier). Depending on the sign of the velocity, the contents are either advected out of cell $j$ or into cell $j$ from the left or right neighbour. The assumption here is that the profile of $f$ within the cell is well-approximated by a constant (given by the value at the center $f_j$). More accurate assumptions about the profile of $f$ within each cell give rise to higher order methods. For example, assuming $f$ is linear across the cell (with slope chosen to be consistent with the difference in $f$ between cell $j$ and its neighbours) gives a scheme that is 2nd order in $\Delta x$. These piecewise linear schemes are discussed in detail in Chapter 4 of the Heidelberg notes I linked to earlier (see footnote on page 1). Carefully handling the fluxes between cells is particularly important for accurate treatment of shocks and other discontinuities in the flow. 

## Other methods

Finite differencing is the basis for many codes used to simulate astrophysical fluids (I included a [list of notable codes](outline#useful-books-and-other-resources) in the course outline), but there are a couple of other methods that are also very common and worth knowing about.

- **Spectral methods**. A spectral method involves expanding in terms of a set of basis functions and then following the amplitudes of the different basis functions over time. A simple example that can be solved analytically is the diffusion equation in 2D:
$${\partial f\over \partial t} = {\partial^2T\over \partial x^2}+ {\partial^2T\over \partial y^2}.$$
We take the Fourier transform of $f(x,y,t)$,
$$F(k_x, k_y, t) = \int f(x,y,t) e^{-ik_xx} e^{-ik_yy} dxdy,$$
and substitute this into the diffusion equation to obtain an equation for $\partial F/\partial t$:
$${\partial F\over \partial t} = - (k_x^2 + k_y^2) F = -k^2F.$$
Notice how the derivative terms are easy to compute in $k$ space, we just multiply by $k$, so the derivatives can be computed exactly!
In this particular case there is an analytic solution $F\propto e^{-k^2t}$, but in general we could integrate $F(k_x,k_y,t)$ forwards in time using a numerical method. Then once we've followed the evolution of each mode, we reconstruct $f(x,y,t)$ with an inverse transform
$$f(x,y,t) = {1\over (2\pi)^2}\int F(k_x,k_y,t) e^{ik_xx} e^{ik_yy} dk_x dk_y.$$
In a numerical spectral method, these transforms would become sums over a discrete set of modes (so in this case we would use a discrete Fourier transform). Just like we have to decide how many grid points to use in a finite difference calculation, in a spectral calculation we have to decide how many modes to include. The advantages of these methods are that they can converge very quickly, often exponentially in the number of modes. There are many choices of basis functions, depending on the particular geometry and situation you are looking at. A good example of this kind of solver is [Dedalus](https://dedalus-project.org/).

- **Smoothed-particle hydrodynamics (SPH)**. This is a Lagrangian particle-based alternative to grid-based methods, commonly used in situations with a large dynamic range in lengthscales, e.g. cosmological simulations. The idea is to use particles to represent different regions of the fluid. The particles carry the average properties of the fluid at different locations, such as density, pressure, mass and energy. Fluid quantities and their gradients are estimated from neighbouring particles using a *smoothing kernel*. For example the pressure gradient can be calculated from neighbouring particles and used to determine the acceleration of each particle. Examples of codes that use this kind of Lagrangian approach are [GIZMO](http://www.tapir.caltech.edu/~phopkins/Site/GIZMO.html) or [AREPO](https://arepo-code.org/).

- **Stellar evolution codes**. Stellar evolution codes are designed to solve the equations of stellar structure including detailed input physics such as thermonuclear reaction rates, opacities, and equations of state. These are all very non-linear functions, so the way these codes typically work is that each timestep involves making a guess for what the next solution looks like and then iteratively improving the guess until the solution obeys the stellar structure equations to within some tolerance. If you want to read more about this, a good place to look is [Paxton et al. 2011](https://ui.adsabs.harvard.edu/abs/2011ApJS..192....3P/abstract) which introduces the open source [MESA](https://mesastar.org/) code.

- **Particle-in-cell** or PIC codes follow charged particles and solve for their associated electromagnetic fields in plasmas. The particles are evolved using their equations of motion in response to the fields, and in turn the electromagnetic fields are solved on a grid using the particle densities as source terms. This kind of calculation is particularly useful for collisionless plasmas, where a fluid description may not be appropriate. Examples of open source PIC codes are [Smilei](https://smileipic.github.io/Smilei/index.html) or [VPIC](https://github.com/lanl/vpic-kokkos/tree/hybridVPIC).




## Reading questions

- What is the difference between explicit and implicit methods? What are some advantages and disadvantages of each?
- Explain what is meant by (i) numerical diffusion, (ii) upwind differencing.
- What is the difference between amplitude and phase errors? How might each of them manifest themselves in a numerical solution?
- Explain how finite volume methods are able to guarantee that quantities like mass, momentum, and energy are exactly conserved by the numerical method.


