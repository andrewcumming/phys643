# Week 1: Introduction

In these notes, we introduce the fluid equations, laying the groundwork for the specific topics in future weeks.

## What is a fluid?

In astrophysics, we are often in a situation where the mean free path of particles $\lambda$ is much smaller than the distances over which bulk properties change. By bulk properties, we mean quantities such as the temperature, density, or mean velocity. Under these conditions, we can treat the matter as a continuum and describe its evolution with a set of conservation equations for mass, momentum and energy. These are the equations of *continuum mechanics* or as we will refer to them, the *fluid equations*.

There is a connection here to statistical mechanics. You may recall the idea from statistical mechanics that in a system that is in or close to equilibrium, we don't have to worry about following the trajectories and interactions of individual particles (like in an $N$-body simulation of a star system for example). Instead, we know that in this situation, the distribution of particle velocities will be a Maxwell-Boltzmann distribution, characterized by just one number: the temperature $T$. If we also know the particle density $n$, then we can calculate the pressure $P=nk_BT$ (assuming an ideal gas). In a system that is not quite in equilibrium, for example a system in which temperature depends on position $T(\vec{r})$ so that there is a temperature gradient, as long as $\lambda$ is small compared to the scale over which temperature varies $L$, we can say to a very good approximation that at any given point, the particles will have a Maxwell-Boltzmann distribution at the local temperature. There will be a small departure from Maxwell-Boltzmann, so that heat can flow from hot to cold, but it will be of order $\lambda/L\ll 1$. We say that the fluid is in *local thermodynamic equilibrium* (LTE) [^boltzmann].

[^boltzmann]: There is a systematic derivation of the fluid equations based on this idea. It starts from Lioville's theorem from statistical mechanics for the phase-space density of particles $f(\vec{r},\vec{v})$ and expands in the small parameter $\lambda/L$. This is covered in the early chapters of Choudhuri and is worth going through if you haven't seen it before. For our purposes though, it is enough to jump straight to the conservation equations.

As an example, let's estimate $\lambda$ in the Sun and check this assumption. At the center of the Sun, the temperature is $T\approx 10^7\ {\rm K}$ and density $\rho\approx 150\ {\rm g\ cm^{-3}}$, so the matter is a completely-ionized plasma of (mostly) protons and electrons. The mean free path is given by $n\sigma\lambda = 1$ where $n$ is the number density of scatterers and $\sigma$ is the scattering cross-section. We can get $n$ from the density, $n\approx \rho/m_p\sim 10^{26}\ {\rm cm^{-3}}$. The Coulomb cross-section for scattering of charged particles is given roughly by finding the impact parameter $b$ for which the Coulomb energy $e^2/b$ is comparable to the particle kinetic energy $k_BT$, and the cross-section can then be estimated as
$$\sigma\sim \pi b^2\sim \pi{e^4\over (k_BT)^2}.$$
Plugging in numbers gives $$\lambda \sim 10^6\ {\rm cm}\ {T^2\over n}\sim 10^{-6}\ {\rm cm}.$$
This is much smaller than the radius of the sun $R_\odot\approx 7\times 10^{10}\ {\rm cm}$, which is the lengthscale across which the temperature varies. This large difference in scales means that at any given position inside the Sun, local thermodynamic equilibrium is a good approximation.

:::{admonition} Exercise
:class: tip
Evaluate $\lambda$ for different astrophysical environments. Are there cases where a fluid description may not be appropriate?
:::

## The continuity equation

We'll go through the conservation laws one by one, starting with mass. This also introduces the advective derivative, Eulerian and Lagrangian approaches, and the idea of an incompressible fluid/flow.

The equation for mass conservation is known as the *continuity equation*,
$${\partial\rho\over\partial t} = -\vec{\nabla}\cdot\left(\rho\vec{u}\right).\label{eq:continuity1}$$
This equation is written in what is known as *flux-conservative form*: the rate of change of a density of some quantity (here the mass density) on the left hand side is given by minus the divergence of the flux[^fluxfootnote] of that quantity (here the mass flux $\rho\vec{u}$, with units: ${\rm g\ cm^{-2}\ s^{-1}}$) on the right hand side. You can see where this comes from by integrating over a volume and applying the divergence theorem. The left hand side gives the rate of change of mass in the volume,
$$\int dV {\partial \rho\over \partial t} = {\partial\over \partial t}\int \rho dV;$$
the right hand side is the surface integral of the mass flux over the boundaries of the volume:
$$-\int dV \vec{\nabla}\cdot\left(\rho\vec{u}\right) = - \int d\vec{S}\cdot \rho\vec{u}.$$
If there is a net mass flux across the surface, the mass contained within the volume must change. Shrinking the volume smaller and smaller, we see that equation [](#eq:continuity1) is a local version of mass conservation. We'll write similar equations below for momentum and energy conservation as well.

[^fluxfootnote]: In general, we can construct a flux of a quantity by multiplying its volume density by velocity.

An important operator is the *advective derivative*, also known as the Lagrangian derivative. It represents the rate of change of a quantity following along with the fluid element (Lagrangian approach) rather than asking what is the rate of change of the quantity at a fixed point in space (Eulerian approach).
We will write it as
$${D\over Dt} = {\partial \over\partial t} + \vec{u}\cdot\vec{\nabla}.$$
Using the advective derivative, equation [](#eq:continuity1) can be rewritten
$${D\rho\over Dt} = -\rho\vec{\nabla}\cdot\vec{u}\label{eq:continuity},$$
which shows explicitly that fluid elements will change their density whenever there is a divergence of the flow.

An incompressible fluid (e.g. water) has a constant density, so that $D\rho/Dt=0$ and $\vec{\nabla}\cdot\vec{u}=0$. A consequence of this that you will be familiar with is the increase in the speed of the flow in a river when the river narrows. The water has to flow faster to achieve the same flow rate when the river narrows. We can also think of incompressibility as being a property of a fluid flow: if a flow is subsonic $\left|u\right|\ll c_s$, density variations will be rapidly smoothed out by sound waves much faster than the fluid motion. This means that a flow can be incompressible ($\vec{\nabla}\cdot\vec{u}=0$) even if the fluid itself is not (e.g. subsonic flow of air).


## Momentum equation

Next, we turn to the conservation of momentum. Important concepts here are body and surface forces, viscosity, and equation of state.

The momentum equation in flux conservative form is
$${\partial \over \partial t} \left(\rho u_i\right) +{\partial\over \partial x_j}\left(\rho u_i u_j\right) = f_i + {\partial \over \partial x_j} T_{ij}.\label{eq:fluxconsmom}$$
This describes conservation of the $i$th component of the momentum density $\rho \vec{u}$ (momentum per unit volume). The flux of the $i$th component of momentum in the $j$-direction is $\rho u_i u_j$. Note that whereas with mass we had a scalar density and vector flux, now we have a vector density (we are conserving a vector quantity, momentum), and so the flux is a tensor.

On the right hand side of equation {eq}`eq:fluxconsmom`, forces act to change the momentum. They are of two types. The first term represents *body forces* that act on each particle in the fluid element. The body force per unit volume in the $i$-direction is $f_i$. Examples are gravity, $\vec{f}=\rho\vec{g}=-\rho\vec{\nabla}\Phi$, where $\Phi$ is the gravitational potential, and magnetic force, $\vec{f}=\vec{J}\times\vec{B}/c$, where $\vec{J}$ is the current density and $\vec{B}$ the magnetic field.

The second term on the right hand side of equation {eq}`eq:fluxconsmom` represents *surface forces*. The quantity $T_{ij}$ is the stress tensor. The diagonal elements of the stress tensor are forces that push inwards or outwards on the surface of a fluid element (direction along the normal to the surface). An example is pressure, described by 
$$T_{ij} = -P\delta_{ij}$$
which gives 
$${\partial\over \partial x_j} T_{ij} = -{\partial \over \partial x_i}P = -\left(\vec{\nabla}P\right)_i$$
the $i$th component of the pressure gradient. Fluid elements feel a force down the pressure gradient. Physically, when there is non-zero pressure gradient, it means that the pressure force on one side of the fluid element outbalances the pressure force on the other, giving a net acceleration.

With pressure and gravity forces only, and using the continuity equation to simplify the left hand side, a common form of the momentum equation is
$$\rho{D\vec{u}\over Dt} = -\vec{\nabla}P +\rho \vec{g}.\label{eq:simple_momentum}$$ (Think of this as $F=ma$ for a fluid element). In a static situation where the left hand side vanishes, this is the equation of hydrostatic balance. We'll use this when we look at the structure of stars and planets.

Another important surface force is *viscosity*, which is a force that resists shear in the flow. It arises because random motions of particles within the fluid transfer momentum between parts of the fluid moving with different velocities. It gives off-diagonal contributions to $T_{ij}$, i.e. the viscous force mostly acts in a direction parallel to the surface of a fluid element rather than normal to it. In general, the viscous stress can be written
$$\sigma_{ij} = \mu\left({\partial u_i\over\partial x_j}+{\partial u_j\over \partial x_i}-{2\over 3}\delta_{ij}\vec{\nabla}\cdot\vec{u}\right) + \xi \delta_{ij}\vec{\nabla}\cdot\vec{u},$$ where $\mu$ is the *shear viscosity* and $\xi$ is the *bulk viscosity* (units of viscosity: ${\rm g\ cm^{-1}\ s^{-1}}$). The velocity derivatives in the first term describe shearing motions of the fluid[^vort], and is usually the most important viscous force. The bulk viscosity describes irreversible processes that occur when a fluid element is compressed. It can often be ignored, but not always.

Often we'll work with the quantity $\nu = \mu/\rho$, which is known as the *kinematic viscosity* (units: ${\rm cm^2\ s^{-1}}$). For an ideal gas this is roughly $\nu\sim \lambda^2/t_c\sim \lambda v_\mathrm{th}$, where $t_c$ is the collision time and $v_\mathrm{th}$ is the thermal velocity of the particles in the gas. If the fluid motions have $\vec{\nabla}\cdot\vec{u}\approx 0$, the viscous term in the momentum equation simplifies to
$${\partial\over \partial x_j} T_{ij} \approx {\partial\over \partial x_j}\left(\mu {\partial u_i\over\partial x_j}\right)$$
or for constant $\mu$,
$$\approx \mu \nabla^2\vec{u}.$$ Adding this last form to equation [](#eq:simple_momentum) shows that *viscosity leads to diffusion of momentum*.

[^vort]: As opposed to rotation of a fluid element which would have a minus sign between the two velocity derivatives. You'll see this when you look at vorticity in the exercises.

The momentum and continuity equations describe the fluid motion completely if we know how to relate $P$ and $\rho$, which depends on the *equation of state* of the fluid. For example, if the fluid flow is rapid enough that there is no time for heat flow between fluid elements, the motion is adiabatic and we can write $P\propto \rho^\gamma$, where $\gamma$ is the adiabatic index. The opposite limit is extremely rapid heat transport so that the gas remains isothermal, $P\propto \rho$. In both of these limits, pressure $P$ depends only on $\rho$. In intermediate cases, pressure depends on both $\rho$ and $T$, so we need an extra equaiton, the energy equation. We'll come to that soon.

## Magnetic fields: the MHD equations

Astrophysical plasmas are often magnetized. In this case, as mentioned already, there is a $\vec{J}\times\vec{B}$ force in the momentum equation[^rhoe]. We also need to discuss how the magnetic field evolves. The electric field is given by Ohm's law[^ohm], $$\vec{E}=-{\vec{u}\times \vec{B}\over c}+{\vec{J}\over \sigma}.$$ The first term on the right hand side comes from the relativistic transformation from the fluid rest frame (where the usual form of Ohm's law $\vec{J}=\sigma\vec{E}$ applies) to the frame in which the fluid is moving with velocity $\vec{u}$. Inserting our expression for the electric field into Faraday's law then gives the time-dependence of $\vec{B}$, 
\begin{eqnarray}
{\partial\vec{B}\over \partial t}  &=& -c\vec{\nabla}\times \vec{E}\nonumber\\
&=&\vec{\nabla}\times\left(\vec{u}\times\vec{B}\right)-c\vec{\nabla}\times\left({\vec{J}\over \sigma}\right).\label{eq:induction}
\end{eqnarray}

[^rhoe]: If there is a non-zero charge density $\rho_e$, there will also be an electric force $\rho_e\vec{E}$, but usually in astrophysical situations the plasma is electrically neutral $\rho_e=0$ to a good approximation.

[^ohm]: In fact, there are other terms that can appear in Ohm's law: you can look at the "Extra material" for a more general derivation of Ohm's law using the two fluid equations that shows the extra terms that can arise in some situations.

Equation {eq}`eq:induction` is known as the *induction equation*. The first term on the right hand side describes *flux freezing*. This refers to the fact that, in the absence of ohmic dissipation (*ideal MHD*), magnetic field lines move with the fluid. A good way to see this is to derive an equation for the separation $d\vec{\ell}$ between two fluid elements in a fluid. We won't do this here, but it turns out to be of the same form as the induction equation (without the ohmic term) but with $\vec{B}\rightarrow d\vec{\ell}$. So if you take two fluid elements and follow them as they move through the flow, their separation vector and the local magnetic field vector evolve in the same way. That tells you that magnetic field lines are tied into the fluid: if the magnetic field vector initially points from one fluid element to another neighbouring fluid element, it will keep doing so as those fluid elements move around.

To see the effect of the ohmic term, we can use Ampère's law[^ampere], which gives the current density in terms of the magentic field as $$\vec{J}={c\over 4\pi}\vec{\nabla}\times\vec{B}.$$
The induction equation is then
$${\partial\vec{B}\over \partial t}  = -c\vec{\nabla}\times \vec{E} = \vec{\nabla}\times\left(\vec{u}\times\vec{B}\right)-\vec{\nabla}\times\left(\eta\vec{\nabla}\times \vec{B}\right),$$
where we introduce the *magnetic diffusivity* $\eta = c^2/(4\pi \sigma)$. Since $\vec{\nabla}\cdot\vec{B}=0$, $\vec{\nabla}\times\vec{\nabla}\times\vec{B}=-\nabla^2\vec{B}$ and so for constant $\eta$ the ohmic term in the induction equation is 
$${\partial\vec{B}\over \partial t}  = \eta\nabla^2\vec{B},$$
a diffusion equation for $\vec{B}$. We see that ohmic dissipation gives rise to *ohmic diffusion* of the magnetic field. It breaks flux freezing, and leads to diffusion of the field lines within the fluid rest frame. 

[^ampere]: The term $\partial\vec{E}/\partial t$ in Ampère's law can be dropped as long as the timescale on which $\vec{B}$ is evolving is much longer than a light crossing time (this assumption has to be revisited for extremely relativistic flow). Note that we then have $\vec{\nabla}\cdot\vec{J}=0$, consistent with charge conservation.

The fluid equations with the $\vec{J}\times\vec{B}$ force added to the momentum equation, the induction equation, and Ampère's law together form the equations of magnetohydrodynamics (MHD).

One more thing we can do is to look in more detail at the $\vec{J}\times\vec{B}$ force using Ampere's law to write $\vec{J}$ in terms of $\vec{B}$. Then
$${\vec{J}\times \vec{B}\over c} = {1\over 4\pi}\left(\vec{\nabla}\times\vec{B}\right)\times\vec{B}=-\vec{\nabla}\left({B^2\over 8\pi}\right) + {(\vec{B}\cdot\vec{\nabla})\vec{B}\over 4\pi},$$
where in the second step we've used a vector identity.
The first term is the gradient of the magnetic pressure $B^2/8\pi$. The second term has two pieces. One piece has a direction along the field, and cancels the gradient along the field from the first term. The net effect is that the magnetic pressure acts only perpendicular to the field (as it must since the force is $\vec{J}\times\vec{B}$). So if you grab a flux tube and squeeze it, you will feel the magnetic pressure pushing back. The other piece of the $\vec{B}\cdot\vec{\nabla}\vec{B}$ term acts perpendicular to the field: it represents *magnetic tension*. The magnetic tension force tries to make the fields lines straighten (like an elastic string). The magnitude of the tension force per unit volume is $B^2/4\pi R_c$, where $R_c$ is the radius of curvature of the field line. We'll see later that this force supports a transverse wave known as an Alfvèn wave (analagous to a wave on a string).

## Energy equation

The final conservation law is for energy. It helps to consider the bulk kinetic energy, internal energy, and magnetic energy separately.

An equation for the kinetic energy density $(1/2)\rho u^2$ comes from carrying out the dot product
$$\vec{u}\cdot(\mathrm{momentum\ equation})$$
which gives
$${\partial\over \partial t}\left({1\over 2}\rho u^2\right) + {\partial\over \partial x_j}\left({1\over 2}\rho u^2 u_j\right) =\vec{u}\cdot\vec{f}+u_i{\partial T_{ij}\over \partial x_j}.$$
Again this is in flux-conservative form and says that the kinetic energy density changes if there is mechanical work $\vec{u}\cdot\vec{f}$ on the fluid element, either from body or surface forces.

For internal energy, we can start with the 1st law of thermodynamics $dE=TdS-PdV$ which we write per unit mass as 
\begin{equation}\label{eq:1stlaw}
de = T ds + {Pd\rho\over \rho^2},
\end{equation}
where $e$ is the internal energy per unit mass and $s$ is the entropy per unit mass.
For a given fluid element, the rate of change of entropy, 
\begin{equation}
\label{eq:Tdsdt}
T{Ds\over Dt} = {De\over Dt} - {P\over \rho^2}{D\rho\over Dt},
\end{equation}
is the rate of change of heat content of the fluid element. It can come from internal heating or cooling (e.g. nuclear or chemical reactions that deposit energy in the gas or neutrinos that leave the volume and act as a volumetric cooling source), or from a heat flux at the surface of the fluid element. The heat flux $\vec{F}$ can often be written $\vec{F}=-K\vec{\nabla}T$ where $K$ is the thermal conductivity (heat flows down the temperature gradient). Including both contributions gives
$$T{Ds\over Dt} = \epsilon - {1\over \rho}\vec{\nabla}\cdot\vec{F},$$
*the entropy equation*.

If the flow is rapid and there is no time for heat flow, we can write $Ds/Dt=0$. For an ideal gas, $P=(\gamma-1)\rho e$, where $\gamma=c_P/c_V$ is the ratio of specific heats. Substituting for $e$ in equation {eq}`eq:Tdsdt` gives
$${Ds\over Dt}={D\over Dt}\left({P\over\rho^\gamma}\right)=0.$$
As expected, $P\propto \rho^\gamma$ for each fluid element in an adiabatic flow.

Adding the kinetic energy to the internal energy we get an equation for the total energy (neglecting magnetic energy)
$${\partial\over \partial t}\left({1\over 2}\rho u^2+\rho e\right) + {\partial\over\partial x_j}\left(u_j\left[{1\over 2}\rho u^2 + \rho e+ P\right]\right) = \left(\epsilon -{\vec{\nabla}\cdot\vec{F}\over \rho}\right) + \vec{u}\cdot\vec{f}.\label{eq:total_energy}$$
(We write only the body force piece of the mechanical work for simplicity). Note that the *enthalpy* $h = e +P/\rho$ appears in the flux term. The enthalpy is often a more useful quantity than internal energy in flows at constant pressure, since it takes into account the $PdV$ work done as the fluid moves around. It often comes up in chemistry, for example.

To include magnetic energy, we can dot $\vec{B}$ into Faraday's law. This gives an equation for the magnetic energy density $B^2/8\pi$,  
$${\partial\over\partial t}\left({B^2\over 8\pi}\right) = -\vec{\nabla}\cdot \left({c\vec{E}\times\vec{B}\over 4\pi}\right) - \vec{E}\cdot\vec{J}$$
which you may have seen before in electromagnetism. The first term on the right hand side is the divergence of the Poynting flux; the second is Ohmic dissipation. 

Using Ohm's law, the $\vec{J}\cdot\vec{E}$ term can be written as two terms
$$-\vec{E}\cdot\vec{J} = -{J^2\over \sigma} - \vec{u}\cdot{\vec{J}\times\vec{B}\over c}.$$
The first is the energy dissipation rate from ohmic heating. This converts magnetic energy into internal energy: $J^2/\sigma$ is the heating rate per unit volume. The second term has the same form as the mechanical work term $\vec{u}\cdot\vec{f}$ in the kinetic energy equation, but with opposite sign. This shows that the work done on the fluid by the $\vec{J}\times\vec{B}$ force takes energy from (or puts energy into) the magnetic field.

## Reading questions

- What is meant by *advective derivative*?

- What is the distinction between incompressible fluid and incompressible flow?

- In equation {eq}`eq:simple_momentum`, there are two forces on the right hand side. Which of these are body forces and which are surface forces. How can you tell?

- Explain what is meant by *flux freezing*.

- Write out the equations of magnetohydrodynamics.

- Describe physically the different components of the magnetic force in MHD.

- In the internal energy equation {eq}`eq:total_energy`, the flux term (second term on the left hand side) has a factor of $P$ in it. Follow through the derivation of this equation: how does that factor of $P$ get there? What is its physical significance?

- In the text it is mentioned that neutrinos can be considered a volumetric cooling source. Why is that the case? Are there situations where that might not be appropriate?