# Exercises

### 1. Fermi energy at the centre of a white dwarf

Calculate as accurately as you can the electron Fermi energy at the centre of a 0.6 solar mass white dwarf. Give your answer in keV. How does your answer compare with the electron rest mass?

:::{seealso} Solution
:class: dropdown
From the reading, we know that the ratio of the central density to mean density is $\beta = 5.99$ for a $\gamma=5/3$ polytrope. We can check at the end that the Fermi energy we obtain is small enough that approximating the electrons as non-relativistic is appropriate at this mass. The mass-radius relation is given in equation {eq}`eq:WD53MR` gives a radius of $R=1.0\times 10^9\ \mathrm{cm}$ for $0.6\ M_\odot$, or a mean density
$$\langle\rho\rangle = {3M\over 4\pi R^3} = 2.5\times 10^5\ \mathrm{g\ cm^{-3}}.$$

The number density of electrons is $n_e = \rho Y_e/m_p$, and we can safely assume $Y_e=0.5$ for a CO or ONe white dwarf.

The Fermi energy for non-relativistic electrons is then
$$E_F = {\hbar^2 k_F^2\over 2m_e} = {\hbar^2\over 2m_e}(3\pi^2n_e)^{2/3} = {\hbar^2\over 2m_e}(3\pi^2)^{2/3}\left({\beta\langle\rho\rangle Y_e\over m_p}\right)^{2/3}.$$

Putting in numbers gives $E_F = 3.4\times 10^{-7}\ \mathrm{erg}$ or using $1\ \mathrm{keV} = 1.6\times 10^{-19}\ \mathrm{J} = 1.6\times 10^{-12} \ \mathrm{erg}$,
$$E_F = 212\ \mathrm{keV}.$$

This is smaller than  the electron rest mass $m_e c^2=511\ \mathrm{keV}$ so this should be reasonably accurate. If we want the most accurate answer we could compute the correction from special relativity by writing the relativistic expression for kinetic energy
$$E_F = \left[(p_Fc)^2+(m_ec^2)^2\right]^{1/2} - m_e c^2,$$
which in terms of the non-relativistic $E_{F,\mathrm{NR}} = p_F^2/2m_e$ is
$$E_F = E_{F,\mathrm{NR}} {m_ec^2\over E_{F,\mathrm{NR}}}\left[\sqrt{1+ {2E_{F,\mathrm{NR}}\over m_ec^2}}-1\right].$$ For our value of $E_{F,\mathrm{NR}}/m_ec^2=212/511=0.42$, this gives a correction factor of 0.85, or $E_F=180\ \mathrm{keV}$.

:::

### 2. Equation of state at the centre of the Sun

At the centre of the Sun, the density and temperature are $\rho\approx 150\ \mathrm{g\ cm^{-3}}$ and $1.5\times 10^7\ \mathrm{K}$ respectively. The composition is approximately 35% H and 65% He by mass. Discuss whether it is a good approximation to use the ideal gas equation of state under these conditions.

:::{seealso} Solution
:class: dropdown
Possible corrections to the ideal gas equation of state could come from degeneracy, Coulomb effects, or radiation pressure:

1. **Degeneracy**. We can check the value of
$${E_F\over k_BT} = {p_F^2\over 2m_e k_BT} = {\hbar^2\over 2m_ek_BT}\left({3\pi^2 Y_e\rho\over m_p}\right)^{2/3}.$$ Since helium dominates the composition, we'll take $Y_e=0.5$ as an approximate value. With the temperature and density given in the question, I get $E_F/k_BT = 0.35$. So the gas is non-degenerate ($k_BT>E_F$), but degeneracy effects are starting to become important at these densities.

2. **Coulomb effects**. We can use the expression from the notes for Coulomb pressure. With $Y_e=0.5$, $Z=2$ and the density given, equation {eq}`eq:PC` gives $P_C = - 3\times 10^{15}\ \mathrm{erg\ cm^{-3}}$. The ideal gas pressure is $\rho k_BT/\mu m_p\approx 1.4\times 10^{17}\ \mathrm{erg\ cm^{-3}}$ where again for simplicity take the pure He value $\mu=4/3$. So the Coulomb pressure is about a 2\% correction to the ideal gas pressure. Coulomb interactions between ions are very important to consider when calculating nuclear reaction rates because small differences in separation between nuclei significantly change the tunnelling probability for nuclei to fuse.

3. **Radiation pressure**. The radiation pressure is $(1/3)aT^4=1.3\times 10^{14}\ \mathrm{erg\ cm^{-3}}$, so only about 0.1% of the ideal gas pressure. Radiation pressure makes only a small contribution for the Sun. It does however play a role in very massive stars.


:::



### 3. Pressure ionization in a neutron star

*Pressure ionization* occurs when the spacing between atoms becomes comparable to their size. Then it no longer makes sense to think of electrons being in bound states of individual atoms. At high enough densities the atoms become fully-ionized and all of the electrons can be considered free electrons.

Consider a neutron star with a surface temperature $10^6\ \mathrm{K}$, mass $1.4\ M_\odot$, and radius $12\ \mathrm{km}$. Estimate how deep into the atmosphere you have to go (in cm) before the plasma is pressure ionized.

:::{seealso} Solution
:class: dropdown

The density at which atoms start to overlap can be estimated from $(4\pi/3)a^3 \rho = m_p$, where $a$ is the typical size of an atom. For hydrogen atoms, $a$ is the Bohr radius $\approx 5\times 10^{-9}\ \mathrm{cm}$. This gives a critical density $\rho\approx 3.2\ \mathrm{g\ cm^{-3}}$.

Now consider the thin atmosphere of a neutron star. Assume we're low enough density near the surface that we have an ideal gas. The pressure where the atoms start to overlap is therefore $P=\rho k_BT/m_p \approx 2.6\times 10^{14}\ \mathrm{g\ cm^{-3}}$.

Knowing the pressure, we can find out how much mass is in the thin layer using hydrostatic balance. The gravity is $g=GM/R^2\approx 1.3\times 10^{14}\ \mathrm{cm\ s^{-2}}$. The mass of the layer is given by
$$P \approx g {\Delta M\over 4\pi R^2},$$
which gives a mass $$\Delta M\approx 2\times 10^{-20}\ M_\odot.$$
The thickness would be
$$H\approx {\Delta M\over 4\pi R^2\rho}\approx 0.7\ \mathrm{cm}.$$
A very thin layer.
:::





### 4. Metallic hydrogen in Jupiter

(a) In the inner part of Jupiter, hydrogen molecules are compressed so close together that their electron orbitals begin to overlap and form a conduction band: the hydrogen becomes metallic.
You can roughly estimate the transition density for this to occur by asking when the distance between two $H_2$ molecules becomes comparable to their size. Estimate the density $\rho$ where this occurs.

(b) Jupiter can be modelled as an $n=1$ polytrope. Why? Use the analytic result for an $n=1$ polytrope $$\rho(r) = \rho_c {\sin(\pi r/R)\over \pi r/R}$$ to estimate the radius at which the metallic transition occurs inside Jupiter.


:::{seealso} Solution
:class: dropdown

(a) This part is very similar to the previous question, but instead of H atoms touching we have $H_2$ molecules. For a simple estimate, we could double the size which would decrease the density by almost an order of magnitude, so let's use $\rho\approx 0.3\ \mathrm{g\ cm^{-3}}$ as our critical density.

(b) The reason we can use an $n=1$ polytrope is that this is the polytrope which has radius independent of mass (we used this for neutron stars). Looking up the central density of Jupiter, we have $\rho_c\approx 30\ \mathrm{g\ cm^{-3}}$. So then we would say that the onset of metallic hydrogen happens at radius $\pi r/R = x$ given by $\mathrm{sinc} (x) = \rho/\rho_c\approx 0.01$. Trial and error gives $x\approx 0.99$, so we have then the transition radius
$$r\approx 0.32\ R_J.$$
In real models of Jupiter, the metallic hydrogen starts at about $20,000\ \mathrm{km}$ from the surface, about $r/R\approx 0.7$. The difference is probably telling us that the polytropic density profile is not quite right for Jupiter's interior.
:::



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

:::{seealso} Solution
:class: dropdown
(a) Use the equations of stellar structure to first replace $dm$ with $4\pi r^2\rho dr$ and then $(Gm\rho/r^2) dr$ with $-dP$. This gives
$$\Omega = -\int {Gm\over r} dm = -\int 4\pi r^3 {Gm\rho\over r^2} dr =  \int 4\pi r^3 dP.$$
If we integrate by parts, the derivative is transferred from the $P$ to the $4\pi r^3$ term, giving
$$\Omega = \int P d(4\pi r^3) = -3 \int P 4\pi r^2 dr = -3 \int P dV.$$
The integration by parts also has a surface term, but it vanishes at the surface where $P=0$ and at the centre where $r=0$. 

(b) Again the strategy here is to arrange terms so that when we integrate by parts and transfer the derivative it gives the answer we're looking for:
$$\int P dV = \int {P\over \rho} 4\pi r^2\rho dr = \int {P\over \rho} dm = -\int m\, d\left({P\over \rho}\right).$$
Again the surface term vanishes in the integration by parts because $m=0$ at the centre and $P=0$ at the surface. The polytropic relation $P\propto \rho^\gamma$ or $dP/P = \gamma d\rho/\rho$ then gives the final answer
$$\int P dV = -\left({\gamma-1\over\gamma}\right) \int m {dP\over \rho}.$$

(c) Use hydrostatic balance to change $dP$ to a $dr$:
$$\int P dV = - \left({\gamma-1\over\gamma}\right) \int m {dP\over \rho} = \left({\gamma-1\over\gamma}\right) \int m {Gm\over r^2} dr.$$
Now the trick is to rewrite this as
$$\int P dV = -\left({\gamma-1\over\gamma}\right) \int Gm^2 d\left({1\over r}\right).$$
Then integrate by parts:
$$\int P dV = -\left({\gamma-1\over\gamma}\right)\left[{GM^2\over R} -2\int {Gm\over r}dm\right],$$
where this time the surface term did not vanish.

Therefore we have
$$-{\Omega\over 3} = -\left({\gamma-1\over\gamma}\right)\left[{GM^2\over R} + 2\Omega\right].$$

Simplifying terms gives the answer in the question.
:::







### 6. Solid white dwarf

A dense plasma will solidify when the Coulomb energy associated with Coulomb repulsion between ions in the plasma, $Z^2e^2/a$ becomes large enough compared to the thermal energy $k_BT$. Here $a$ is the mean spacing between the ions. A plasma becomes solid when
$$\Gamma = {Z^2e^2\over ak_BT} \gtrsim 175.$$

Consider a 0.6 solar mass white dwarf. What is the central density? As the white dwarf cools, at what temperature will it start to solidify?

:::{seealso} Solution
:class: dropdown
From question 1, the central density is $\rho_c\approx 1.5\times 10^6\ \mathrm{g\ cm^{-3}}$. Assuming carbon composition, the number density of nuclei is $n\approx \rho/(12 m_p) \approx 7.5\times 10^{28}\ \mathrm{cm^{-3}}$. The mean spacing between ions can be esimated by writing $(4\pi/3)a^3 n =1$ which gives $a\approx 1.5\times 10^{-10}\ \mathrm{cm}$. Then using $e=4.8032\times 10^{-10}$ in cgs units, and taking $Z=6$ for carbon, we get
$$\Gamma = {Z^2e^2\over ak_BT} = {409\over T_6}$$ where $T_6 = T/10^6\ \mathrm{K}$. This shows that $\Gamma$ will cross the crystallization point when $T_6\lesssim 2$. At this point the centre of the white dwarf will begin to freeze.
:::