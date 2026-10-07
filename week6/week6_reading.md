# Week 6: Inflows and outflows

Outflows and inflows are important in astrophysics in systems with winds (star, galaxies, planets, accretion disks), jets (e.g. from accreting black holes) and accretion onto a central object (e.g. in compact binaries, star or planet formation, black hole growth). These notes discuss some different examples. We start with the simplest case of a point mass sending out a spherically-symmetric wind or, in the opposite direction, spherically-symmetric accretion flow onto a point mass. We then consider some more complex examples that break spherical symmetry: stellar wind from a magnetized star, jets, and accretion disks.

These flows have some common features that you should look out for. One is that there are conserved quantities that we can use to learn about the flow without necessarily solving for the detailed structure. Another feature is the existence of critical points at which the flow speed equals a wave speed, for example a sonic point at which the flow transitions from subsonic to supersonic.

## Bondi accretion and Parker wind

Consider spherically-symmetric, steady, radial flow either onto or away from a point mass $M$. The continuity equation $\vec{\nabla}\cdot{\rho \vec{v}}=0$ written in spherical coordinates is $${1\over r^2} {d\over d r}\left(r^2\rho v\right) = 0,$$ which shows that $r^2\rho v$ is constant throughout the flow. It is convenient to write this in terms of the mass loss rate or accretion rate $$\dot M = 4\pi r^2\rho v\label{eq:mdot}$$ (units of ${\rm g\ s^{-1}}$). The momentum equation is 
\begin{equation}\rho v{dv\over dr} = -{dP\over dr} - \rho{GM\over r^2},\end{equation}
where we assume that the gravitational acceleration is dominated by the mass of the central star, ie. there is negligible mass in the flow itself. 

As usual to simplify things we can make an assumption about the relation between $P$ and $\rho$ so that we don't have to worry about the energy equation. For an isothermal gas, $P=c_s^2\rho$ with $c_s$ constant, giving
\begin{equation}\label{eq:momentum}
v{dv\over dr} = -c_s^2{d\ln \rho\over dr} - {GM\over r^2}.
\end{equation}
From the continuity equation, 
$${d\ln\rho\over dr} = -{2\over r} - {d\ln v\over dr}$$
and so, eliminating the density gradient from the momentum equation, 
$$ \left(v - {c_s^2\over v}\right) {dv\over dr} = {2c_s^2\over r} -{GM\over r^2}.$$ 
Defining the sonic radius
$$r_s = {GM\over 2c_s^2}\label{eq:rs}$$
we can rewrite this as
$$\left(1-{v^2\over c_s^2}\right){d\ln v\over d\ln r} = 2\left({{r_s\over r}- 1}\right).\label{eq:sonicdvdr}$$
This shows that if the flow makes a transition from subsonic to supersonic or vice-versa, that must happen at the *sonic point* $r=r_s$ in order for the velocity gradient to remain finite. 

The velocity and density profiles $v(r)$ and $\rho(r)$ can be obtained by integrating the continuity and momentum equations. (In the case of an isothermal flow, this integration can be done analytically). 
Two solutions are possible which go through the sonic point: (i) an outflow ($v>0$) with subsonic flow close to the star $v<c_s$ and with $v$ increasing outwards, becoming supersonic at $r>r_s$, or (ii) an inflow ($v<0$) with subsonic flow beyond the sonic point $r>r_s$ and $|v|$ increasing inwards, becoming supersonic at $r<r_s$. Option (i) corresponds to a wind, discussed by [Parker (1958)](https://ui.adsabs.harvard.edu/abs/1958ApJ...128..664P/abstract) in the context of the Sun, whereas option (ii) with $v<0$ corresponds to accretion of mass onto the central star, first discussed by [Bondi (1952)](https://ui.adsabs.harvard.edu/abs/1952MNRAS.112..195B/abstract). 

The mass accretion rate or mass loss rate can be written in terms of the sound speed (or equivalently temperature) by evaluating equation {eq}`eq:mdot` at the sonic point where $v=c_s$ and $\rho=\rho_s$:
$$\dot M = 4\pi r_s^2 c_s \rho_s = \pi {(GM)^2\over c_s^3} \rho_s.\label{eq:Mdotrhos}$$
To find $\rho_s$ for a given situation, we map from the boundary as appropriate. Integrating equation {eq}`eq:momentum` gives
$${1\over 2}v^2 + c_s^2\ln \rho - {GM\over r}= B = {\rm constant}$$
(this is the Bernoulli constant for our problem).
For the accretion case, $v\rightarrow 0$ and $GM/r\rightarrow 0$ at large distance, so $B = c_s^2\ln \rho_\infty$, where $\rho_\infty$ is the density of the gas at a large distance from the star (so, e.g. the density of the interstellar medium). Evaluating $B$ at the sonic point therefore gives
$${1\over 2}c_s^2 + c_s^2\ln \rho_s - {GM\over r_s}= c_s^2\ln \rho_\infty\Rightarrow \rho_s = \rho_\infty e^{3/2}.$$ Substituting for $\rho_s$ in equation {eq}`eq:Mdotrhos` gives the **Bondi accretion rate** 
$$\dot M = \pi e^{3/2} {(GM)^2\over c_s^3} \rho_\infty,$$
the accretion rate onto a point mass[^hoyle] placed in a gas with sound speed $c_s$ and density $\rho_\infty$ (assuming the flow is isothermal). 
A similar argument applies for the case of a wind, but now we apply the boundary conditions at the stellar surface $r=R$ where we take $v=0$ and $\rho=\rho_\star$, giving 
$$B = c_s^2 \ln \rho_\star - {GM\over R}.$$
Therefore
\begin{equation}\label{eq:wind_rho}
\ln \left({\rho_s\over \rho_\star}\right) = {3\over 2}- {GM\over Rc_s^2} = {3\over 2} - {2r_s\over R}< 0,	
\end{equation}
and the **wind mass-loss rate** is
$$\dot M = \pi e^{3/2} {(GM)^2\over c_s^3} \rho_\star e^{-GM/Rc_s^2}.$$

[^hoyle]: Hoyle \& Lyttleton (1939) derived a similar formula but they considered accretion by a star moving through the interstellar medium (they were interested in whether accretion could power stellar luminosities). Their result is $\dot M \sim \rho_{\infty}(GM)^2/v_\star^3$, the same scalings but with $c_s\rightarrow v_\star$. The geometry of the flow is quite different in that case, with the incoming matter being gravitationally-focused behind the star (in the star's frame) and then falling in.

## Magnetized stellar wind and angular momentum loss

Magnetic fields can play an important role in stellar winds from rotating stars. In particular, through magnetic forces in the azimuthal direction, the magnetic field determines the angular momentum loss rate in the wind, and therefore how quickly the star spins down. 

[Weber \& Davis (1967)](https://ui.adsabs.harvard.edu/abs/1967ApJ...148..217W/abstract) made a simple model in which they considered only the equatorial plane and assumed that the outwards plasma flow tries to align the magnetic field with the flow, so the magnetic field also lies in the equatorial plane $$\vec{B} = B_r(r)\vec{\hat{e}}_r + B_\phi(r)\vec{\hat{e}}_\phi.$$ Everything is assumed to be axisymmetric and so only depends on $r$,not $\phi$, and also the flow is assumed to be steady. Because the magnetic field has to be divergence free, $$\vec{\nabla}\cdot \vec{B}={1\over r^2}{\partial \over \partial r}\left(r^2B_r\right)=0,$$ $r^2B_r$ must be  constant, i.e. $B_r\propto 1/r^2$. The velocity is $$\vec{v} = v_r(r)\vec{\hat{e}}_r + v_\phi(r)\vec{\hat{e}}_\phi.$$ As in the Parker wind, mass continuity tells us that $r^2\rho v_r = \dot M/4\pi$ is constant. With $\vec{v}$ and $\vec{B}$ being in the equatorial plane, and $\partial/\partial\phi=0$, the only possible non-zero component of the induction equation is
$${\partial B_\phi\over \partial t} = -c(\vec{\nabla}\times\vec{E})_\phi = -{1\over r}{d\over dr}\left[r\left(v_rB_\phi - v_\phi B_r\right)\right].$$ In a steady state, we must therefore have 
$$r\left(v_rB_\phi - v_\phi B_r\right) = {\rm constant}= -R^2\Omega B_r(R) = -r^2\Omega B_r\label{eq:Bconst}$$
where $\Omega$ is the spin of the star. (On the right-hand side of {eq}`eq:Bconst`, we first evaluated the constant at the surface of the star where $v_r=0$ and $v_\phi=\Omega R$, and then we used $B_r\propto 1/r^2$ for the final step).
This tells us that 
\begin{equation}\label{eq:bphibr}
{B_\phi\over B_r} = {v_\phi-\Omega r\over v_r}
\end{equation}
so that the flow is along the magnetic field lines everywhere in the rotating frame. There is a steady pattern in the rotating frame.

To focus on the angular momentum, let's look at the $\phi$ component of the momentum equation. This is
$$\rho v_r{1\over r}{d\over dr}\left(r v_\phi\right) = {1\over c}\left(\vec{J}\times\vec{B}\right)_\phi = {B_r\over 4\pi r}{d\over dr}\left(r B_\phi\right),$$
where we use 
$$\vec{J} = {c\over 4\pi}\vec{\nabla}\times\vec{B} = -{c\over 4\pi} {1\over r}{d\over dr}\left(r B_\phi\right) \vec{\hat{e}}_\theta.$$
But $\rho v_r\propto 1/r^2$ and $B_r\propto 1/r^2$, and so we can integrate this:
\begin{equation}\label{eq:L}
rv_\phi - {B_r\over 4\pi \rho v_r} r B_\phi = {\rm constant} = L.
\end{equation}
We call the constant $L$ because we see that the first term is the angular momentum per unit mass. If the magnetic field was not present, $rv_\phi$ would be constant, but the magnetic torques cause the specific angular momentum to change across the flow. 

The Alfven velocity $v_A^2 = B_r^2/4\pi \rho$ can be used to define a radial Alfven Mach number
$$M_A = {v_r\over v_A} = {\sqrt{4\pi \rho} v_r\over B_r}.$$  Equation {eq}`eq:L` becomes
\begin{equation}
	\label{eq:L2} rv_\phi -  {1\over M_A^2} r v_r {B_\phi\over B_r}  = L.
\end{equation}
We see that since $B_r\propto \rho v_r$, $M_A^2\propto v_r/B_r\propto 1/\rho$, so the Alfven Mach number increases through the flow.

Together, equations {eq}`eq:induction` and {eq}`eq:L2` can be used to solve for $v_\phi$:
$$rv_\phi = {L M_A^2 - r^2\Omega\over M_A^2 - 1}.$$
Close to the star, $M_A\ll 1$, $v_\phi \approx r\Omega$ which corresponds to rigid rotation at the stellar spin frequency. Far from the star, $M_A\gg 1$ and $rv_\phi = L$ , so the flow has constant angular momentum per unit mass. What's happening is that close to the star the magnetic field is strong enough to keep the fluid moving rigidly with the star; far from the star the magnetic torques are no longer important and so the fluid moves outwards with constant angular momentum. The transition occurs at a particular radius, the **Alfven radius** $r_A = (L/\Omega)^{1/2}$ at which $M_A=1$. 

The angular momentum loss in the wind is therefore 
$$\dot M r_A^2 \Omega$$
which can be much greater than $\dot M R_\star^2\Omega$ which would be the angular momentum loss rate for the Parker wind. The magnetic field keeps the plasma rotating rigidly out to $r=r_A$ which gives a larger "lever arm" for the torque.

In their paper, Weber \& Davis go on to look at the radial structure of the wind. As well as the Alfven point (at $\sim 30 R_\odot$ in their model), there is also a sonic point as in the spherical solution (located much closer to the Sun at a few solar radii). (In fact, there are multiple critical points where the flow velocity matches one of the wave speeds as they discuss in detail in the paper). 

The plot below is taken from [Pneuman \& Kopp (1971)](https://ui.adsabs.harvard.edu/abs/1971SoPh...18..258P/abstract) which was an early paper doing a multi-D model of the wind, with the stellar field assumed to be a dipole. We see the same ideas apply: a closed zone close to the star where the magnetic torques dominate, and open field lines further out where the field becomes flow-aligned.

```{figure} wind.png
```

## Jets as nozzles

Next, let's discuss an example which is more one-dimensional: the collimation of a jet. Active galaxies in particular show jets that remain remarkably collimated over huge scales (much larger than the size of the host galaxy). An early idea discussed by [Blandford \& Rees (1974)](https://ui.adsabs.harvard.edu/abs/1974MNRAS.169..395B/abstract) is that the pressure of the gas around the source could act to collimate the jet and achieve a supersonic outflow. 

We showed earlier that for a 1D isentropic flow, the mass flux increases with velocity for subsonic flows (incompressible flow) but decreases with velocity for supersonic flows (compressible flow; see eq. [[16]](week4-reading#eq-river) of the Week 4 notes). One place where this comes up is in designing a nozzle through which gas can flow and become supersonic. If a sonic transition is to occur with a steady flow, the product of area and mass flux must be constant. This means that the nozzle must be designed to have a decreasing area at first while the flow is subsonic, but then increase again later so that the flow can continue to accelerate. This kind of nozzle is known as a [de Laval nozzle](https://en.wikipedia.org/wiki/De_Laval_nozzle).

Blandford \& Rees proposed that a similar effect is happening in radio galaxies, except the area of the nozzle is not specified in advance but rather that the confining pressure from the external gas sets the area of the flow. The figure below from their paper shows the overall idea:

```{figure} blandfordrees.png
```

For a 1D isentropic flow, the momentum equation can be written 
$${d\over dx}\left({1\over 2}v^2 + {c_s^2\over \gamma-1}\right) = 0$$
where $c_s^2 = \gamma P/\rho$ is the adiabatic sound speed and $P\propto \rho^\gamma$. The Bernoulli constant 
$$B = {1\over 2}v^2 + {c_s^2\over \gamma-1}\label{eq:Bjet}$$
is a constant of the flow.
If there is some pressure and density $P_0$ and $\rho_0$ at which $v=0$ (in the nozzle context, this is the pressure and density in the container; for the jet it's the pressure and density at the base of the flow) then keeping $B$ constant implies 
$${v^2\over c_s^2} = {2\over \gamma-1}\left[1-\left({P\over P_0}\right)^{(\gamma-1)/\gamma}\right]\label{eq:stagnationjet}$$
which gives the velocity as a function of pressure. For a large enough pressure drop in the external gas, the flow will make a transition to supersonic flow. Blandford \& Rees made essentially this argument, although they used relativistic equations since the flow speed is a significant fraction of $c$ for the radio jets.

## Accretion disks

In the Bondi accretion flow, the flow is spherically-symmetric and the gas flows exactly radially-inwards onto the central star. In many cases, however, the incoming gas has too much angular momentum to accrete straight onto the star. The accreting gas settles into a rotating flow in which dissipative processes (viscosity, turbulence) act to transport angular momentum outwards, allowing the gas to accrete.

The classic example is the **thin disk** that forms when gas is able to cool efficiently, ie. it can lose energy much faster than angular momentum. The accreting gas then settles into a disk surrounding the central object. The detailed equations that describe the evolution of a thin disk can be found in the review by [Pringle 1981](https://ui.adsabs.harvard.edu/abs/1981ARA%26A..19..137P/abstract). Here I'll summarize the main ideas:

*  **Keplerian orbits**. The main assumption is that particles in the disk are on Keplerian orbits with $\Omega^2 = GM/r^3$, which means that the velocity decreases outwards. Viscosity tries to reduce the differential rotation, transporting angular momentum outwards.
*  **Vertical structure**. For small disk masses, the gravity from the central star dominates. The vertical component is 
$$g_z = {GM\over r^2}{z\over r}\label{eq:gz}$$
where $r$ is the midplane distance from the central star, and $z$ is the vertical distance from the midplane (i.e. cylindrical coordinates). Hydrostatic balance in the vertical direction $\partial P/\partial z=-\rho g_z$ then implies that the midplane pressure is
$$P\approx {GM\over r^2}{H\over r}\Sigma = {GM\over r^3} H^2 \langle\rho\rangle,$$ 
where $H$ is the characteristic disk thickness, $\Sigma$ is the column density (mass per unit area) in the disk, and the mean density is $\langle\rho\rangle\approx \Sigma/H$. Since the sound speed is given by $c_s^2\approx P/\langle\rho\rangle$, we have the result 
$$c_s = \Omega H,$$ which encapsulates the vertical hydrostatic balance. It implies that 
$${c_s\over v_{\rm Kep}} = {c_s\over \Omega r} = {H\over r}< 1$$
(the disk is thin), showing that the Keplerian motion is supersonic.
*  **Surface temperature**. If the disk radiates as a blackbody and is accreting steadily, then we could write an equation for energy conservation at a radius $r$ as
$$2\times \sigma_{SB}T_\mathrm{eff}^4 \times 2\pi r dr = {GM\dot M\over 2r^2} dr,\hspace{2cm}\label{eq:energybalance}$$
where the factor of 2 on the LHS comes from the two sides of the disk, and the RHS is the rate of release of gravitational energy as mass moves from radius $r+dr$ to $r$ (recall that the energy of a Keplerian orbit (gravitational plus kinetic) is $-GM/2r$ per unit mass). In fact, there is also energy released in the form of viscous dissipation[^visc] in the disk, which turns out to be twice as large as the energy from the changing orbit, giving a factor of 3 on the RHS. Inserting the correct prefactor, we get the temperature profile of the disk 
$$T_\mathrm{eff} = \left({3GM\dot M\over 8\pi r^3 \sigma_{SB}}\right)^{1/4}\propto {1\over r^{3/4}}$$

[^visc]: The viscous heating rate per unit volume is $\Sigma\nu(dv_\mathrm{Kep}/dr)^2\sim \Sigma \nu \Omega^2$. In the innermost part of the disk, the profile deviates from Keplerian and the dissipation is actually smaller than the RHS of equation {eq}`eq:energybalance`, as needed so that overall energy is released in the disk at a rate $GM\dot M/2R$.

*  **Viscous time**. In the momentum equation, the viscous term looks like $\nu \nabla^2\vec{u}$, so that the characteristic viscous timescale is given by 
$$t_\mathrm{visc}\approx {r^2\over \nu}$$ (the velocity varies on a lengthscale $\sim r$). The source of viscosity in disks was a puzzle for a long time! Microscopic viscosity is much too small to reproduce observed accretion rates in disks, and now we think that some kind of turbulent transport is responsible, most likely driven by the magnetorotational instability (MRI). As a simple model, Shakura and Sunyaev introduced the famous $\alpha$-prescription for viscosity, writing $$\nu \equiv \alpha c_s H,$$ where the viscosity is written in terms of the sound speed and disk thickness. Since these set the maximal scales for velocity and length in the disk, we expect to have $\alpha<1$. The viscous time is therefore 
$$t_\mathrm{visc}\approx {r^2\over \nu} = {r^2\over \alpha c_s H} = \alpha^{-1} \Omega^{-1} \left({r\over H}\right)^2,$$
much greater than the orbital timescale $\Omega^{-1}$. The radial flow speed is 
$$v_r\approx {r\over t_\mathrm{visc}} \approx \alpha c_s \left({H\over r}\right) \ll c_s.$$ We can use this to estimate the accretion rate by writing $\dot M\approx 2\pi r H \rho v_r \approx 2\pi \Sigma \nu.$ In fact, the real calculation gives $${\dot M\over 3\pi}\left[1-\left({R_\star\over r}\right)^{1/2}\right] = \nu \Sigma,$$ so that in the outer parts of the disk[^accrcorr] where $r\gg R_{\star}$, $\dot M \approx 3\pi \nu \Sigma$.

[^accrcorr]: In the theory, correction terms like the one in square brackets appear in many of the equations -- they are important near the star, where the flow begins to deviate from Keplerian as it joins onto the star. For example, as mentioned in the footnote on the previous page, the local flux near the star is suppressed relative to the outer parts of the disk. For more details see [Pringle (1981)](https://ui.adsabs.harvard.edu/abs/1981ARA\%26A..19..137P/abstract).

## Accretion onto a magnetized star

Just as stellar magnetic fields affect the flow in stellar winds, the accretion flow near a star which is strongly-magnetized can be disrupted by the magnetic field. The flow is then channelled by the magnetic field onto the magnetic polar caps of the star.

To estimate when this happens, we can compare the magnetic pressure $${B^2\over 8\pi} = {B_\star^2\over 8\pi}\left({R_\star\over r}\right)^6\propto {1\over r^6}$$ to the ram pressure in the accretion flow $$\rho v^2\approx {\dot M\over 4\pi r^2 v} v^2 = {\dot M\over 4\pi r^2}\left({2GM\over r}\right)^{1/2}\propto {1\over r^{5/2}}.$$
Here we take the magnetic field of the star to be a dipole, giving $B=B_\star (R_\star/r)^3$ (higher order multipoles fall off more quickly with $r$, so usually the dipole component is the relevant one). We've also used the relation $\dot M = 4\pi r^2 \rho v$ for a steady accretion flow and taken the velocity to be the free-fall velocity, giving $v^2\sim 2GM/r$. 

This shows that magnetic pressure grows more quickly with decreasing $r$ than the ram pressure. At a distance $r < r_M$, the flow becomes magnetically-channelled, where $r_M$ is the radial distance where magnetic and ram pressures are equal, 
$$r_M = \left(B_\star^2R_\star^6\over 2\dot M(2GM)^{1/2}\right)^{2/7} = 5\times 10^8\ {\rm cm}\ \mu_{30}^{4/7}\dot M_{16}^{-2/7}\left({M\over M_\odot}\right)^{-1/7}$$
where $\mu_{30}$ is the dipole moment $B_\star R_\star^3$ in units of $10^{30}\ {\rm G\ cm^3}$, and $\dot M_{16}$ is the accretion rate in units of $10^{16}\ {\rm g\ s^{-1}}$. This value of dipole moment corresponds to a neutron star with a magnetic field of $\sim 10^{12}\ {\rm G}$ or a white dwarf with a magnetic field of $\sim 10^3\ {\rm G}$. 

In fact, we need to balance the magnetic torque with the viscous torque to find $r_M$ for disk accretion, but the answer is about the same (and has the same scalings). For a famous treatment of the disk case, you can look at [Ghosh \& Lamb (1978)](https://ui.adsabs.harvard.edu/abs/1978ApJ...223L..83G/abstract) and their follow up papers. This figure from their paper shows the accretion geometry:

```{figure} GhoshLamb.png
```

The accretion disk is terminated near $r_M$, and the matter funnelled onto the magnetic polar cap. Examples of systems where this happens are *accreting X_ray pulsars* which involve accretion onto magnetized neutron stars, or *Am Her* systems or *intermediate polars* in which the accretion is onto a magnetized white dwarf. In both cases, the emission is modulated by the rotation of the compact object across our line of sight.


## Reading questions

- What is the sonic radius $r_s$? How would equation {eq}`eq:rs` change if the flow was adiabatic instead of isothermal?
- In the Weber-Davis solution the radial magnetic field falls off as $1/r^2$. Comment on whether this surprises you given your knowledge of electromagnetism.
- Explain why equation {eq}`eq:bphibr` shows that the magnetic field is flow-aligned in the frame rotating with the star. Sketch the pattern of the flow lines/field lines in this frame as carefully as you can.
- How do you go from equation {eq}`eq:Bjet` to equation {eq}`eq:stagnationjet`?
- In a thin disk, what is the ordering of the three velocities $v_r$, $v_\phi$ and $c_s$?
- Where does equation {eq}`eq:gz` come from?
- Sketch what you think the figure from Ghosh & Lamb (magnetic accretion) would look like from above. Explain your answer.






