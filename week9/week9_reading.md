# Week 9: Rotating systems

Rotation is important in many astrophysical flows. It enters the equation of motion for the fluid in two ways. In the rotating frame, we need to add the **Coriolis force**,
$$-\rho 2\vec{\Omega}\times\vec{u}$$
(this is the force per unit volume) and the **centrifugal force**
$$-\rho \vec{\Omega}\times (\vec{\Omega}\times \vec{r}) = \rho\left|\Omega\right|^2\vec{r}_\perp,$$
where $\vec{r_\perp}$ is in a direction perpendicular to the rotation axis. You can get the sign for the Coriolis force if you remember that the acceleration is always to the right in the northern hemisphere.

## Centrifugal balance

The centrifugal force can be written as a gradient
$$\vec{\Omega}\times\left(\vec{\Omega}\times\vec{r}\right) = -\vec{\nabla}\left({1\over 2}\left|\vec{\Omega}\times\vec{r}\right|^2\right),$$
and absorbed into the gravitational potential. In spherical coordinates,
$$\Phi \rightarrow \Phi + {1\over 2}\Omega^2 r^2\sin^2\theta.$$

In the case of a star or planet, this gives rise to a rotational bulge. Because of the outwards centrifugal force, the effective gravity at the equator is smaller than at the pole by an amount $\approx R\Omega^2$, ie. at the equator $$g\approx {GM\over R^2}- R\Omega^2 = {GM\over R^2}\left(1 - {\Omega^2\over \Omega_B^2}\right),$$ where $\Omega_B$ is the breakup rotation frequency given by
$$\Omega_B^2={GM\over R^3}$$ (equivalent to the Keplerian orbital frequency at the surface of the object). We can use this to estimate the size of the rotational bulge. For Earth, $2\pi/\Omega_B\approx 90$ min (the orbital period of low Earth orbit). Therefore
$${\Omega^2\over \Omega_B^2} \approx \left({90\ \mathrm{min}\over 24\ \mathrm{h}}\right)^2\approx 0.3\% \approx {\Delta R\over R}.$$ The giant planets have much larger bulges. For Jupiter, $2\pi/\Omega_B= 2.4\ \mathrm{h}$ and the rotation period is close to 10 hours, giving $\Delta R/R\approx 6$\%. For Saturn, $2\pi/\Omega_B=3.6\ \mathrm{h}$ and rotation period of 11 hours gives $\Delta R/R \approx 10$\%.

An interesting consequence of the centrifugal force in stars is **meridional circulation**. The latitude-dependence of the effective gravity leads to a specific latitude-dependence of the radiative flux, with a larger flux at the poles than at the equator (this is known as the von Zeipel theorem). In general, this will not match the distribution of energy generation rate inside the star. To achieve thermal equilibrium requires a circulation inside the star to redistribute energy. The circulation is on meridional planes ($r$-$\theta$ plane, $u_\phi=0$) and so is known as meridional circulation. In an isolated star, the circulation timescale is the Eddington-Sweet time $t_{ES}\approx t_{KH}(\Omega_B/\Omega)^2$, where $t_{KH}$ is the Kelvin-Helmholtz timescale $GM^2/RL$. In the Sun the timescale is actually shorter than this because angular momentum loss in the solar wind drives an additional circulation that redistributes angular momentum in the interior (e.g. see [Wood & Brummell (2012)](https://ui.adsabs.harvard.edu/abs/2012ApJ...755...99W/abstract)).

## The role of the Coriolis force

The Coriolis force is often more important to consider than the centrifugal force because it gives rise to several new effects. The **Rossby number** $\mathrm{Ro}$ is a dimensionless number that measures the important of the Coriolis term compared to advection:
$$\mathrm{Ro} = {V^2/L\over 2 V\Omega} = {V\over 2\Omega L},$$
where $L$ and $V$ are characteristic length and velocity scales in the flow. **Rotation is important when $\mathrm{Ro}\ll 1$**. 

Adding the Coriolis force to the momentum equation and with the centrifugal term absorbed into the potential, we have
$${D\vec{u}\over Dt}  + 2\vec{\Omega}\times\vec{u} = -{\vec{\nabla}P\over \rho} + \vec{\nabla}\Phi.$$
When $\mathrm{Ro}\ll 1$, we can neglect the inertia terms and therefore
$$2\vec{\Omega}\times\vec{u} =  -{\vec{\nabla}P\over \rho} + \vec{\nabla}\Phi.$$
Now take the curl of this equation. The potential term vanishes because the curl of a gradient vanishes. The curl of the Coriolis term is
$$2\vec{\nabla}\times (\vec{\Omega}\times\vec{u}) = -2(\vec{\Omega}\cdot\vec{\nabla})\vec{u} + 2\vec{\Omega}(\vec{\nabla}\cdot\vec{u}).$$
The curl of the pressure gradient term is
$$-\vec{\nabla}\times \left({\vec{\nabla} P\over\rho}\right) = \vec{\nabla}P\times \vec{\nabla}\left({1\over \rho}\right) = {\vec{\nabla}\rho\times\vec{\nabla}P\over \rho^2} \propto  {\vec{\nabla}\rho\times\vec{\nabla}T\over \rho^2}.$$
This vector is known as the **baroclinic vector**. It is non-zero when the surfaces of constant pressure and density (or surfaces of constant temperature and density) are misaligned. This can happen in a planetary atmosphere for example, where differential heating between pole and equator leads to a temperature gradient along constant pressure surfaces.

Putting these terms together, taking the curl of the momentum equation in the limit of strong rotation gives
$$-2(\vec{\Omega}\cdot\vec{\nabla})\vec{u} + 2\vec{\Omega}(\vec{\nabla}\cdot\vec{u}) = {\vec{\nabla}\rho\times\vec{\nabla}P\over \rho^2}.\label{eq:momstrongrotation}$$
If $\vec{\nabla}\cdot\vec{u} = 0$ (incompressible flow) and $\vec\nabla P\parallel\vec{\nabla}\rho$ (no baroclinicity), then we have
$$\boxed{(\vec{\Omega}\cdot\vec{\nabla})\vec{u} = 0},$$ the **Taylor-Proudman theorem**. This says that there is no variation of the fluid velocity along the rotation axis. So for example in a [rotating tank](https://www.youtube.com/watch?v=DPN2CaUXyI0) where the rotation axis is vertical, an object placed at the bottom of the tank will cause fluid to flow "around" it throughout the entire height of the tank. This kind of flow is known as a *Taylor column*.

The Taylor-Proudman theorem implies that in a rapidly-rotating star the rotation should occur on cylinders, i.e. $\Omega$ should be a function of cylindrical radius only. We'll see in the [paper presentations](week9-papers) that one of the puzzles that arose when the Solar interior rotation profile was first measured is that rotation in the convection zone does not seem to follow cylinders, except near the equator, which is telling us something interesting about angular momentum transport in the convection zone. Another consequence of Taylor-Proudman is that rapidly-rotating flows become quasi-two-dimensional (in the sense that the flow doesn't vary along the rotation axis). This has many interesting implications, for example turbulence in a rapidly-rotating system shows an **inverse cascade** (e.g. see [Smith & Waleffe (1999)](https://ui.adsabs.harvard.edu/abs/1999PhFl...11.1608S/abstract)). Kinetic energy flows up to larger scales, generating large vortices or large scale organized flows.

If we stick to incompressible flow but relax the assumption of no baroclinicity, we get something known as the **thermal wind**. To see this, consider horizontal motions, for example in an atmosphere. In the vertical direction, we have hydrostatic balance $\partial P/\partial z = -\rho g$. The vertical component of $\vec{\Omega}$ is $\Omega\sin\theta$, where $\theta$ is the latitude (angle from the equator). Defining the **Coriolis parameter**
$$f = 2\Omega\sin\theta,$$
equation {eq}`eq:momstrongrotation` becomes
$$-f {\partial u_\perp\over \partial z} = {1\over \rho^2} \vec{\nabla}\times \left(-\rho g\hat{z}\right)$$
or
$$\boxed{ {\partial u_\perp\over \partial z} = {g\over f\rho} \hat{z}\times \vec{\nabla}\rho}.$$
This shows that *horizontal density gradients are associated with vertical shear* of the horizontal flow, the thermal wind.

The dynamical balance when $\mathrm{Ro}\ll 1$ is **geostrophic balance**,
$$2\vec{\Omega}\times\vec{u} = -{\vec{\nabla}P\over \rho}.$$
Again looking at horizontal winds in an atmosphere and writing the horizontal velocity as $\vec{u}_\perp = (u,v)$, we have
$$f u = -{1\over \rho}{\partial P\over \partial y}$$
$$-f v = -{1\over \rho}{\partial P\over \partial x},$$
or in vector form
$$f\vec{u}_\perp = {1\over \rho} \hat{z} \times \vec{\nabla}_\perp P$$
This shows that the flow is perpendicular to the pressure gradient, i.e. the flow is along isobars. An example is a high pressure region in the northern hemisphere: winds flow clockwise around the high pressure region, so that the Coriolis force on the wind balances the pressure gradient radiating out from the centre. This is known as a *anticyclone*. Similarly, a low pressure region forms a *cyclone* in which the winds are anticlockwise. You've probably seen these kind of flows on a weather map.

The Coriolis force also plays a role in oscillations, for example modifiying the frequencies of g-modes. Referring back to equation {eq}`eq:mom1` from Week 7 and adding the Coriolis force, the horizontal components of the momentum equation become
$$-\rho \omega^2 \xi_x - \rho 2\Omega (-i\omega\xi_y) = -ik_x \delta P$$
$$-\rho \omega^2 \xi_y + \rho 2\Omega (-i\omega\xi_x) = -ik_y \delta P.$$
If you set $\vec{k}\cdot\vec{\xi}=0$ (incompressible perturbations, this removes the sound waves to make things simpler) and then calculate the dispersion relation, you should find
$$\omega^2 = N^2\left({k_\perp\over k}\right)^2 + (2\Omega)^2 \left({k_z\over k}\right)^2.$$
We see that rotation adds an extra term to the dispersion relation. This extra term is present even when $N^2\rightarrow 0$. It represents a new class of modes, **inertial waves** coming from the rotation.

Rotation also causes **rotational splitting** of oscillation modes with different azimuthal wavenumbers $m$. Consider a mode with frequency much larger than the rotation frequency, $\omega\gg\Omega$. This means that rotation is not large enough to affect the mode in the rotating frame. However, transforming from the rotating frame to the observers frame gives
$$e^{im\phi} e^{-\omega t}\rightarrow e^{im(\phi+\Omega t)} e^{-\omega t}$$
or
$$e^{im\phi} e^{-i(\omega-m\Omega)t}$$
so the observed frequency of the oscillation is
$$\omega(\mathrm{observed}) = \omega\pm m\Omega.$$
This would be seen as sidebands in the oscillation mode spectrum. We'll see an example of this in the [paper presentations](week9-papers) where seismology of red giants has been used to measured the rotation rate of the stellar core.

The Coriolis force also leads to entirely new set of waves known as r-modes or Rossby waves, but before getting to those we first need to discuss vorticity.

## Vorticity

The vorticity $\vec{\omega}$ is an important quantity in fluid dynamics generally, but particularly in rotating flows. It is defined as the curl of the velocity field,
$$\vec{\omega} = \vec{\nabla}\times \vec{u}$$
so it tells you something about the local circulation of the fluid, and in fact you can show that the magnitude of vorticity is twice the local angular velocity of the fluid at any given point.
Not every system that appears to be rotating has a non-zero vorticity. One way to visualize what is happening is to imagine placing a small "vorticity meter" into the fluid. The vorticity meter consists of two rods fixed perpendicular to one another, forming a right-angle. When placed into the flow, the meter will rotate with angular velocity $|\vec{\omega}|/2$. For example, a rigidly rotating fluid has $\vec{\omega}=2\vec{\Omega}$, we will see the vorticity meter rotate exactly once for every rotation period of the fluid. This must be the case, because if we go into the rotating frame the vorticity meter should appear stationary. However, in the case of a flow around a point with $u_\phi\propto 1/r$ (this corresponds to a *line vortex*), the vorticity meter is carried around by the flow without any local rotation. If you take the curl of this velocity field, you'll see that $\vec{\omega} =0$. To see such a vorticity meter in action, including the two cases just mentioned, you can look at the [NCFM movie on vorticity](https://www.youtube.com/watch?v=loCLkcYEWD4&list=PL0EC6527BE871ABA3&index=9) from around minute 3 to around minute 5.

To get some feel for how vorticity behaves, first consider a non-rotating fluid. An evolution equation for vorticity can be derived by taking the curl of the momentum equation. A useful identity is
$$(\vec{u}\cdot \vec{\nabla})\vec{u} = -\vec{u}\times(\vec{\nabla}\times\vec{u}) + \vec{\nabla}\left({1\over 2}u^2\right),$$
which we can use to rewrite the non-linear term in the momentum equation. This helps because the first term already includes a factor of $\vec{\nabla}\times\vec{u}=\vec{\omega}$, and the second term is a gradient, so it vanishes when we take the curl. The resulting equation is the **vorticity equation**
$${\partial\vec{\omega}\over\partial t} = \vec{\nabla}\times (\vec{u}\times\vec{\omega}) + {\vec{\nabla}\rho\times\vec{\nabla}P\over \rho^2}.$$
The final term is the baroclinic vector that we met earlier, coming from taking the curl of the pressure gradient term.

For a barotropic flow, the baroclinic vector vanishes, and we have
$${\partial\vec{\omega}\over\partial t} = \vec{\nabla}\times (\vec{u}\times\vec{\omega}).$$
If you compare with the magnetic induction equation, you'll see that this is exactly the same form as the advection term in the induction equation. This tells us that just as magnetic field lines are advected by the flow (flux freezing), so too are the lines of vorticity or **vortex lines**. The vortex lines move with the fluid. An integral version of this statement is **Kelvin's theorem**
$${D\over Dt}\oint \vec{u}.d\vec{\ell} = {D\over Dt}\int \vec{\omega}\cdot d\vec{S} =0,$$
where the first integral is over a close material loop in the fluid, and the second is over a material surface. (Material meaning fixed in the fluid, in the Lagrangian sense).

The advection term can also be rewritten as
$${\partial \vec{\omega}\over \partial t} = \vec{\nabla}\times (\vec{u}\times\vec{\omega}) = -(\vec{u}\cdot\vec{\nabla})\vec{\omega} + (\vec{\omega}\cdot\vec{\nabla})\vec{u}$$
or
$${D\vec{\omega}\over Dt} = (\vec{\omega}\cdot\vec{\nabla})\vec{u}.\label{eq:stretchtilt}$$
This gives us another way to think about how vortices move in a flow. First consider the case where the  velocity is perpendicular to the local vorticity. Then equation {eq}`eq:stretchtilt` says that if the velocity varies along the vortex direction, a horizontal component of vorticity will start to grow. This will change the direction of vorticity; you can think of the vortex being tipped over by the shearing flow. This effect is known as **vortex tilting**. If on the other hand the velocity is along the vortex, then the vorticity will increase or decrease according to whether the vortex is being stretched or squeezed. This is known as **vortex stretching**. For example, if  the velocity is along the vortex direction and is getting larger moving up the vortex, then the vortex is stretched along its length. Conserving mass, the fluid column must get narrower. Angular momentum conservation then implies the vortex will spin faster.

If we now introduce rotation, the left-hand side of the momentum equation now becomes
$${\partial\vec{u}\over\partial t}  + (\vec{u}\cdot\vec{\nabla})\vec{\omega} + 2\vec{\Omega}\times\vec{u}.$$
After using the identity above to rewrite the nonlinear term and removing the gradient term, we get
$${\partial\vec{u}\over\partial t} - \vec{u}\times\vec{\omega} + 2\vec{\Omega}\times\vec{u} = {\partial\vec{u}\over\partial t} + (\vec{\omega}+2\vec{\Omega})\times\vec{u}.$$
We see that the effect of adding rotation is to introduce an extra term in the vorticity. The **absolute vorticity**
$$\vec{\omega_a} = \vec{\omega} + 2\vec{\Omega}$$
obeys the same vorticity equation as before. We refer to $\vec{\omega}$ (without the component from rotation) as the **relative vorticity**.

This distinction has important consequences for fluid motion on a sphere. Consider for example a cyclone moving in the northern hemisphere. As we discussed, the fluid flow will be anti-clockwise around the low pressure centre of the cyclone, so the relative vorticity will be in the same direction as the local radial component of rotation $\hat{r} \Omega\sin\theta$ (where $\theta$ is the latitude measured from the equator). If the cyclone moves towards the north pole, $\theta$ grows and therefore so does the contribution to the absolute vorticity from the rotation term. In order to conserve absolute vorticity, the cyclone will reduce its relative vorticity and spin down to compensate for the fact it moved closer to the rotation axis. These kind of considerations are crucial for understanding the dynamics of vortices on a rotating sphere. The trade of between relative vorticity and rotation also provides a restoring force for a new kind of wave, the Rossby wave, which we discuss in the next section.

## Rossby waves in atmospheres

As a final application of the Coriolis force, we can dervie the dispersion relation for Rossby waves in an atmosphere.

It is common in atmospheric dynamics to make a local Cartesian approximation near some latitude $\theta_0$. The Coriolis parameter can then be expanded as
$$f = 2\Omega \sin\theta\approx f_0 + \beta y,$$
where $f_0 = 2\Omega\sin\theta_0$ is a constant and the second term accounts for the variation with latitude, $y = R(\theta-\theta_0)$ and $\beta = 2\Omega\cos\theta/R$. If we keep the first term only, $f=f_0$, this is known as the **$f$-plane**; if we keep both terms, $f=f_0+\beta y$, this is known as the **$\beta$-plane**.

Consider making perturbations around a stationary background state with the $\beta$-plane approximation. Also assume the perturbations are incompressible, so
$${\partial u\over \partial x} + {\partial v\over \partial y} = 0.\label{eq:rossby1}$$
The horizontal momentum equations are
$${\partial u\over\partial t} -(f_0+\beta y)v = -{1\over \rho}{\partial P\over \partial x}$$
$${\partial v\over\partial t} +(f_0+\beta y)u = -{1\over \rho}{\partial P\over \partial y}.$$
Differentiate the first one with respect to $y$ and the second with respect to $x$:
$${\partial\over\partial t}{\partial u\over \partial y} -(f_0+\beta y){\partial v\over \partial y} - \beta v = -{1\over \rho}{\partial^2 P\over \partial x\partial y}$$
$${\partial\over\partial t}{\partial v\over\partial x} +(f_0+\beta y){\partial u\over \partial x} = -{1\over \rho}{\partial^2 P\over \partial x\partial y}.$$
Subtracting these gives
$${\partial\over\partial t}\left({\partial u\over \partial y}-{\partial v\over \partial x}\right) -\beta v = 0\label{eq:rossby2}$$
(we could have also got this by perturbing the vorticity equation directly).

Now look for solutions $\propto e^{ik_x x} e^{ ik_y y}e^{-i\omega t}$. Equations {eq}`eq:rossby1` and {eq}`eq:rossby2` then give
$$ik_x u + i k_y v = 0$$
$$-i\omega (ik_y u - i k_x v) - \beta v = 0$$
$$\Rightarrow -i\omega (-ik_y {k_y\over k_x} v  - i k_x v) - \beta v = 0$$
$$\Rightarrow \omega (k_y^2  +k_x^2) = -\beta k_x$$
$$\Rightarrow \boxed{\omega  = -{\beta k_x\over k_x^2+k_y^2}}. \label{eq:rossbydispersion}$$
which is the dispersion relation for the waves. Note that (i) $\omega\propto \beta$ which shows that the origin of these waves is in the variation of Coriolis parameter with latitude, and (ii) the phase velocity in the azimuthal direction $v_{p,x} = \omega/k_x$ is negative, so **Rossby waves travel westward** only. The physics of the wave is entirely due to the conservation of absolute vorticity we discussed earlier. A fluid element perturbed towards the pole changes its vorticity, and the resulting change in the flow advects neighbouring vortices in such a way as to cause a restoring force for the first vortex.

There is a similar dispersion relation for $r$-modes, which are essentially Rossby waves in a rotating sphere. For a slowly-rotating ($\Omega\ll \Omega_B$) star, the $r$-mode dispersion relation in the rotating frame is 
$$\omega = -{2m\Omega\over \ell(\ell+1)}$$
(with $m>0$ and $\ell\geq m$). This is the equivalent of equation {eq}`eq:rossbydispersion` but now in spherical geometry. In the inertial (observer's) frame, the frequency is
$$\omega_\mathrm{obs} = \omega + m\Omega = m\Omega\left[1 - {2\over \ell(\ell+1)}\right].$$ For example, if we take $\ell=2$ and $m=2$, we get $\omega=-(2/3)\Omega$ in the rotating frame and $\omega = +(4/3)\Omega$ in the inertial frame. The wave is retrograde in the rotating frame and prograde in the inertial frame. This is the basis of the CFS instability that we will hear more about in the [paper presentations](week9-papers).


## Reading questions

Coming soon ...
