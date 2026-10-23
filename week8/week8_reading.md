# Week 8: Turbulence

In [Computational Exercise 2](comp2) you have seen the steepening effect of the non-linear term in the momentum equation $\vec{u}\cdot\vec{\nabla}\vec{u}$ on sound waves. By coupling together different wavelengths, it leads to steepening of the wave profile. Another consequence of the non-linearities in the fluid equations is *turbulence* which is present in many different astrophysical flows. In these notes, we go through some of the basic properties of turbulent flows, and in the papers this week we'll look at different astrophysical examples.

## Overview of turbulence

First watch the [movie on turbulence](https://www.youtube.com/watch?v=1_oyqLOqwnI&list=PL0EC6527BE871ABA3&index=12&feature=plpp_video) from the National Committee for Fluid Mechanics[^NCFM] (you can stop it once it gets to timestamp 22:30). The style of the movie is quite dated now (made in the 1960s), but keep watching because it gives an excellent overview of turbulence. We'll elaborate on some of the points made in the movie in the notes below. One thing to watch our for are the "symptoms of turbulence" that they talk about in the movie (for the first reading question).

[^NCFM]: The [other movies](https://hml.mit.edu/NCFMF/) in this series are also worth watching and cover many different topics in fluids. There are also a set of notes for each movie that were published, but unfortunately I don't think these are online any more (let me know if you can find them!)

## Energy cascade

Turbulence involves a cascade of energy from large scales to small scales where viscosity dissipates the energy. Perhaps the most famous result is the $-5/3$ scaling of the energy spectrum for *isotropic homogeneous incompressible* turbulence. Let's see how that works.

As mentioned in the movie, the behaviour of the flow at a particular point is not predictable, but statistical quantities/averages are. One of these is the energy spectrum $E(k)$ were $E(k)dk$ is the kinetic energy density in modes of wavelength $\lambda = 2\pi/k$. A log-log plot of $E(k)$ against $k$ looks like:

:::{figure} turbulent spectrum.png
:::

The **outer scale** is where the fluid is being stirred, i.e. where energy is being injected with Reynolds number Re$=UL/\nu\gg 1$. The **inner scale** is where viscous dissipation occurs. The typical velocity $v_d$ and lengthscale $\ell_d$ there are such that the Reynolds number at that scale is of order unity, $v_d\ell_d/\nu\sim 1$.

In a steady cascade, the energy transfer rate $\varepsilon$ from scale to scale must be constant. From dimensional arguments we can write $$\varepsilon\sim {v^3\over \ell}$$ at any scale $\ell$, which gives the typical velocity at scale $\ell$ as $$\boxed{v\sim (\varepsilon\ell)^{1/3}}.$$ 
The eddy turnover time is $${\ell\over v}\sim \varepsilon^{-1/3}\ell^{2/3}$$ which is faster and faster as we go to smaller scales. At each scale, we can think of the energy at that scale being passed on to smaller scales and dissipated every turnover time $\ell/v$. In a steady cascade, this lost energy is replaced by energy coming in from even larger scales. If the stirring at the outer scale stops for some reason, the cascade will dissipate on a timescale $L/U$.

The dissipation scale can be determined by setting the energy transfer rate at each end of the inertial range equal to each other, $$\varepsilon\sim {U^3\over L}\sim {v_d^3\over\ell_d},$$
and using the expression for dissipation scale ${v_d\ell_d/\nu}\sim 1$. This gives $$\boxed{\ell_d\sim \left({\nu^3\over \varepsilon}\right)^{1/4}}\hspace{1cm}
\boxed{v_d\sim (\nu\varepsilon)^{1/4}}$$
These are the size and velocity of turbulent eddies for which the turnover time $\ell_d/v_d$ is equal to the viscous time $\ell_d^2/\nu$. Viscosity efficiently damps motions on these scales, terminating the cascade. If the stirring is kept the same but the viscosity varied, the inertial range will remain the same at large scales, but will extend down to a different scale for the viscous cutoff. This is illustrated in the movie with two turbulent jets with different Re — they look identical at large scales, but the larger Re jet has much finer small scale structure. Another point in the movie is that smaller scales decay first in freely-decaying turbulence, consistent with the turnover time becoming shorter at smaller lengthscales.



We can also get the range of lengthscales involved in the cascade by writing
$$\left({L\over \ell_d}\right)^4 = L^3\times L\times \ell_d^{-4}=L^3\times {U^3\over \varepsilon}\times {\varepsilon\over \nu^3} = \left({LU\over \nu}\right)^3 = \mathrm{Re}^3$$
$$\Rightarrow \hspace{1cm}\boxed{\ell_d = {L\over \mathrm{Re}^{3/4}}}\hspace{1cm}\boxed{v_d\sim {U\over \mathrm{Re}^{1/4}}}$$

In the reading questions, you'll estimate the range of scales when you stir a cup of coffee. To give an astrophysical example, the outer convection zone of the Sun has a size $\sim 10^{10}\ {\rm cm}$ (about 20\% of the radius of the Sun), with velocities $U\sim 10^3\ {\rm cm\ s^{-1}}$. The corresponding Reynold's number is $\mathrm{Re}\sim 10^{12}$ which then gives $\ell_d\sim 10\ {\rm cm}$ and $v_d\sim 1\ {\rm cm\ s^{-1}}$. Note the enormous range of scales! The turnover time at the dissipation scale is $\ell_d/v_d\sim 10$ seconds compared to $L/U\sim 10^7$ seconds (a few months). This makes this a difficult problem to simulate!

The scaling for $E(k)$ now follows. Since $E(k)dk$ is the kinetic energy density at scale $k$, we must have $$E(k)dk\sim v^2 {dk\over k}\sim \varepsilon^{2/3}k^{-2/3}{dk\over k}\propto \varepsilon^{2/3}k^{-5/3}dk.$$
This shows that $E(k)\propto k^{-5/3}$ which is the famous **Kolmogorov spectrum** (1941). The $5/3$ scaling was confirmed for turbulent flow in the "Seymour Narrows", a tidal channel where there is a large Re$\sim 10^8$ by [Grant et al. (1961)](https://www.cambridge.org/core/journals/journal-of-fluid-mechanics/article/abs/turbulence-spectra-from-a-tidal-channel/AFFA9E09796500E668F411DCA7C26E07). Turbulent spectra have also been measured in the solar wind and in interstellar medium. The astrophysics examples are complicated by the fact that compressibility of the fluid (eg. shocks) and magnetic fields play an important role in the turbulence, changing the slope of the turbulent spectrum. In planetary atmospheres or stellar or planetary interiors, rapid rotation and stratification also change the nature of the turbulent flow, in particular giving rise to anisotropic turbulence. We'll see some examples of these aspects in the papers this week.

## Turbulent transport

The other property of turbulence emphasized in the movie was the large increase in the transport of momentum and scalars such as temperature in a turbulent flow. Let's try to understand that. 

Decompose the fluid motion into a **mean flow** $\vec{U}$ and a **fluctuating flow** $\vec{u}^\prime$ $$\vec{u} = \vec{U} + \vec{u}^\prime$$ We do this in such a way that $$\langle\vec{u}\rangle = \vec{U} \hspace{1cm}\langle\vec{u}^\prime\rangle=0,$$ where the time-average is $$\langle\vec{u}\rangle = {1\over \tau}\int_{t_0}^{t_0+\tau} dt\  \vec{u}$$ for some suitably large $\tau$. This is called a **Reynold's decomposition**.

Now think about the fluid equations with this decomposition.
For an incompressible flow, $\vec{\nabla}\cdot\vec{u}=0$. Averaging this gives $\vec{\nabla}\cdot\vec{U}=0$, ie. the mean flow and fluctuating flow are separately incompressible.

The momentum equation is (in component form)
$${\partial u_i\over \partial t} + u_j{\partial u_i\over\partial x_j} = -{1\over \rho}{\partial P\over \partial x_i}$$
Splitting the velocity into mean and fluctuating parts and taking the average gives
$${\partial U_i\over \partial t} + U_j{\partial U_i\over\partial x_j} = -\left\langle u_j^\prime {\partial u_i^\prime\over \partial x_j}\right\rangle   -{1\over \rho}{\partial P\over \partial x_i}$$
where $P$ is now the mean part of the pressure. The velocity term on the right hand side can be written as (since $\vec{\nabla}\cdot\vec{u}=0$)
$$-\left\langle u_j^\prime {\partial u_i^\prime\over \partial x_j}\right\rangle = -{\partial \over \partial x_j}\left(\left\langle u_i^\prime u_j^\prime \right\rangle\right).$$

The momentum equation for the mean flow is therefore
$$\rho \left({\partial \over\partial t} + \vec{U}.\vec{\nabla}\right) \vec{U} = \vec{\nabla}\cdot {\bf T}$$ where $$\boxed{T_{ij} = -\delta_{ij} P - \rho \langle u_i^\prime u_j^\prime\rangle}$$ is the stress tensor. We see that the effect of the turbulence is to give a new term in the stress tensor known as the **Reynolds stress**.

The Reynolds stress describes the transport of momentum by the turbulent fluctuations. In particular, we see that *correlated velocity fluctuations* lead to a transport of momentum. For example, in the flow in a pipe shown in the movie, the average $\langle u_z^\prime u_x^\prime\rangle$ is non-zero because upwards moving fluid tends to carry an excess of horizontal momentum compared to downwards-moving fluid. The net effect is that the turbulence transports horizontal momentum towards the wall of the pipe.

If we want to solve these equations for a turbulent flow  we need a **closure relation** to relate the Reynolds stress (fluctuating part) with the mean flow. It is often assumed for simplicity that 
$$\langle u_i^\prime u_j^\prime\rangle = -D_T \left({\partial U_i\over \partial x_j}+ {\partial U_j\over\partial x_i}\right),$$
i.e. the same kind of relation as for microscopic viscosity. The coefficient $D_T$ is the **Eddy viscosity**. Note that there is a crucial difference compared to a viscous fluid however: even if a relation like this were valid (probably not — the dependence of the Reynolds stress on the mean flow is likely much more complex), the Eddy viscosity $D_T$ is a property of the *flow* unlike the microscopic viscosity $\nu$ which is a property of the *fluid*.

We can also treat the transport of a scalar using the Reynolds decomposition. An example is heat transport. The equation that describes heat transport is 
$$\rho c_P\left({\partial \over \partial t} + \vec{v}\cdot\vec{\nabla}\right) T = {\partial \over \partial x_j}\left(K{\partial T\over \partial x_j}\right)$$ where $c_P$ is the specific heat capacity at constant pressure and $K$ is the thermal conductivity. The left hand side describes advection of heat and the right hand side thermal diffusion. 

The Reynolds decomposition for the heat equation gives
$$\rho c_P\left({\partial \over \partial t} + \vec{U}\cdot\vec{\nabla}\right) \langle T\rangle = {\partial \over \partial x_j}\left( -\rho c_P \langle T^\prime u_j^\prime\rangle + K{\partial \langle T\rangle \over \partial x_j}\right)$$
The term $\rho c_P \langle T^\prime u_j^\prime\rangle$ is the **turbulent heat flux** — correlated fluctuations in temperature and velocity lead to transport of heat. For example, in turbulence with a background temperature gradient in the vertical direction, rising fluid elements are hotter than sinking fluid elements, leading to a net heat transport. 

### Mixing-length theory

Mixing-length theory is a simplified model of turbulent transport that is often used in stellar evolution calculations. In particular, it provides a way to calculate the heat flux in stellar convection zones.

The idea is that the **mixing length** $\ell$ characterizes the distance over which a fluid element maintains its identity. For example, a blob of fluid that is hotter and less dense than its surroundings in a convection zone will buoyantly rise, moving upwards to lower pressure and density and eventually mixing into the surrounding fluid.

As long as the fluid element rises slowly compared to the sound speed, the fluid element can stay in pressure balance with its surroundings, so it has $\delta P=0$. If we also assume that the entropy of the fluid element remains unchanged as it travels upwards (until it mixes and transports its excess heat to the surroundings), then we can use equation {eq}`eq:adiabatic` from Week 7 and write the equation of motion of such a fluid element as
$${\partial u^\prime\over \partial t} = -g {\delta\rho\over\rho} = -N^2\xi_z.$$
Here $N^2$ is the Brunt-Väisälä frequency which last week we wrote in terms of pressure and density gradients (see equation {eq}`eq:Brunt` from Week 7), but can also be written in terms of the temperature gradient as
$$N^2= -{g\over H}{\chi_T\over\chi_\rho}\left(\nabla-\nabla_\mathrm{ad}\right),$$
where $H$ is the pressure scale height, $\chi_\rho = \left.\partial\ln P/\partial\ln \rho\right|_{T,\mu}$, $\chi_T = \left.\partial\ln P/\partial\ln T\right|_{\rho,\mu}$ and $\nabla_\mathrm{ad} = \left.\partial \ln T/\partial\ln P\right|_S$ are thermodynamic derivatives and $\nabla = d\ln T/d\ln P$ is the temperature gradient with pressure in the star. In either way of writing $N^2$, you can see that a constant entropy background takes $N^2$ to zero (since constant entropy means $P\propto\rho^\gamma$ or $\nabla=\nabla_\mathrm{ad}$).

Using the equation of motion we can then estimate the velocity of the rising fluid element after it has accelerated upwards across a mixing length,
$$\left(u^\prime\right)^2 \approx g\ell^2 \left({\nabla-\nabla_\mathrm{ad}\over H}\right)$$
(where we use $\chi_T=\chi_\rho=1$ for ideal gas). The temperature excess of the fluid element over the background is
$${T^\prime\over T}\approx \ell \left({\nabla-\nabla_\mathrm{ad}\over H}\right)$$
and so
$$\langle u^\prime T^\prime \rangle\approx \sqrt{g} \ell^2 \left({\nabla-\nabla_\mathrm{ad}\over H}\right)^{3/2} T.$$
The heat flux will be
$$F = \rho c_P\langle u^\prime T^\prime \rangle \approx \rho c_PT \sqrt{g} \ell^2 \left({\nabla-\nabla_\mathrm{ad}\over H}\right)^{3/2}.$$

One thing to note is that
$$\left({u^\prime\over c_s}\right)^2 = {g\ell^2\rho\over \gamma P}\left({\nabla-\nabla_\mathrm{ad}\over H}\right) = \gamma^{-1}(\nabla-\nabla_\mathrm{ad})\left({\ell\over H}\right)^2$$
(since the pressure scale height is $H=P/\rho g$). So if the convective motions are subsonic it implies the temperature gradient will be close to adiabatic (or vice versa that if the temperature gradient is close to adiabatic, the convective velocity will remain subsonic). This limit is known as *efficient convection*, where only a small velocity and small temperature excess is needed to carry the heat flux.

To estimate the convective velocity in the Sun, we can first note that dropping factors of order unity, $\rho c_PT\approx P\approx \rho gH$. If we also take $\ell\approx H$, then the convective heat flux can be written
$$F\approx \rho (gH)^{3/2} (\nabla-\nabla_\mathrm{ad})^{3/2} \approx \rho (u^\prime)^3.$$ So we can estimate the convective velocity as
$$u^\prime \approx \left({F\over\rho}\right)^{1/3} \approx  \left({L\over 4\pi R^2\rho}\right)^{1/3}.$$ Plugging in $L_\odot\approx 4\times 10^{33}\ \mathrm{erg\ s^{-1}}$, $R_\odot\approx 7\times 10^{10}\ \mathrm{cm}$ and $\rho\approx 1\ \mathrm{g\ cm^{-3}}$ (mean density in the Sun) gives $u^\prime \approx 4000\ \mathrm{cm\ s^{-1}}$. This is much smaller than the sound speed $c_s\approx 30\ \mathrm{km\ s^{-1}} T_5^{1/2}$. With this ratio,
$$\nabla-\nabla_\mathrm{ad} \approx \left({u^\prime\over c_s}\right)^2 \sim 10^{-6}.$$
The temperature gradient is extremely close to adiabatic in the convection zone. Stellar evolution codes often assume adiabatic temperature gradients in convection zones for this reason[^ineffconv].

[^ineffconv]: One place this breaks down is close to the stellar surface, where radiative losses mean that the buoyant acceleration is not as efficient and the convection becomes inefficient. In these location, stellar evolution codes use a modified version of mixing length theory that takes into account the radiative losses.

## Reading questions

- Why and when are fluids turbulent?
- What are the "symptoms" of turbulence given in the movie?
- What is the energy spectrum $E(k)$ and what does it look like for incompressible, isotropic turbulence?
- When you stir a cup of coffee, what do you expect to be the smallest lengthscale associated with the motion?
- What is meant by the terms *Reynold's stress* and *Eddy viscosity*?
- Estimate the convective turnover time $H/u^\prime$ in the Sun's convection zone.



