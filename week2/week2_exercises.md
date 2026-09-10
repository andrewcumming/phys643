# Exercises

### 1. Fermi energy at the centre of a white dwarf

Calculate as accurately as you can the electron Fermi energy at the centre of a 0.6 solar mass white dwarf. Give your answer in keV. How does your answer compare with the electron rest mass?

### 2. Equation of state at the centre of the Sun

At the centre of the Sun, the density and temperature are $\rho\approx 150\ \mathrm{g\ cm^{-3}}$ and $1.5\times 10^7\ \mathrm{K}$ respectively. The composition is approximately 35% H and 65% He by mass. Discuss whether it is a good approximation to use the ideal gas equation of state under these conditions.

### 3. Pressure ionization in a neutron star

*Pressure ionization* occurs when the spacing between atoms becomes comparable to their size. Then it no longer makes sense to think of electrons being in bound states of individual atoms. At high enough densities the atoms become fully-ionized and all of the electrons can be considered free electrons.

Consider a neutron star with a surface temperature $10^6\ \mathrm{K}$, mass $1.4\ M_\odot$, and radius $12\ \mathrm{km}$. Estimate how deep into the atmosphere you have to go (in cm) before the plasma is pressure ionized.

### 4. Metallic hydrogen in Jupiter

(a) In the inner part of Jupiter, hydrogen molecules are compressed so close together that their electron orbitals begin to overlap and form a conduction band: the hydrogen becomes metallic.
You can roughly estimate the transition density for this to occur by asking when the distance between two $H_2$ molecules becomes comparable to their size. Estimate the density $\rho$ where this occurs.

(b) Jupiter can be modelled as an $n=1$ polytrope. Why? Use the analytic result for an $n=1$ polytrope $$\rho(r) = \rho_c {\sin(\pi r/R)\over \pi r/R}$$ to estimate the radius at which the metallic transition occurs inside Jupiter.

### 5. Gravitational energy of a polytrope

Here is a more classical kind of question involving analytic manipulation of the stellar structure equations. It has links to the Virial theorem and gives a useful result at the end for the gravitational energy of a polytrope.

(a) Even without any knowledge of the equation of state, there are certain integral relations that can be derived using only the fact that a star is in hydrostatic balance. Here is an example. The gravitational binding energy of a star is 
$$\Omega = -\int {Gm\over r} dm.$$
Using equations [](#eq:cold1) and [](#eq:cold2) and an integration by parts, show that 
$$\Omega = -3\int P dV,$$ where $dV=4\pi r^2 dr$ is the volume element.

(b) Now consider a polytrope which has $P\propto\rho^\gamma$. Show by integrating by parts that $$\int P dV = \int m\ d\left({P\over \rho}\right)=\left({\gamma-1\over \gamma}\right)\int m{dP\over \rho}.$$

(c) Next, use equation {eq}`eq:cold1` to change integration variables to $r$ and integrate by parts to find
$$\int P dV =\left({\gamma-1\over \gamma}\right)\left[{GM^2\over R} + 2\Omega\right].$$

(d) Now apply the result from part (a) to show that
$$-\Omega = {3(\gamma-1)\over 5\gamma - 6}{GM^2\over R} = {3\over 5-n}{GM^2\over R}.$$
As a check, what is the answer for an incompressible equation of state? Does it look familiar?

### 6. Solid white dwarf

A dense plasma will solidify when the Coulomb energy associated with Coulomb repulsion between ions in the plasma, $Z^2e^2/a$ becomes large enough compared to the thermal energy $k_BT$. Here $a$ is the mean spacing between the ions. A plasma becomes solid when
$$\Gamma = {Z^2e^2\over ak_BT} \gtrsim 175.$$

Consider a 0.6 solar mass white dwarf. What is the central density? As the white dwarf cools, at what temperature will it start to solidify?
