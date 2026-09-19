# Exercises

## 1. Photon diffusion

Estimate the timescale for a photon to diffuse from the centre of the Sun to the surface.

Can you use this timescale to estimate the luminosity of the Sun?

:::{seealso} Solution
:class: dropdown

In a random walk, the distance travelled is $\sqrt{N}$ times the step size. The time taken is therefore
$$t_\mathrm{diff} = {N\ell\over c} ={R^2\over \ell c},$$ where $\ell$ is the mean free path of the photon. From the notes, we had $\ell\approx 0.01\ \mathrm{cm}$ near the centre of the Sun. This gives
$$t_\mathrm{diff} \approx 10^{13}\ \mathrm{s}\approx 3\times 10^5\ \mathrm{yr}$$
(using $1\ \mathrm{yr}\approx 3.14\times 10^7\ \mathrm{s}$).

We saw in last week's exercises that the radiation pressure is about $10^{-3}$ of the gas pressure at the centre of the Sun. This implies that the energy in the photons in the Sun is $\approx 2\times 10^{-3}GM^2/R\sim 10^{46}\ \mathrm{erg}$. If we release this in $10^{13}\ \mathrm{s}$, this would give a luminosity of $\approx 10^{33}\ \mathrm{erg\ s^{-1}}$.
Not too far away from the actual value $L_\odot\approx 4\times 10^{33}\ \mathrm{erg\ s^{-1}}$.
:::




## 2. Opacities

An approximate formula for free-free opacity is $\kappa_{ff} \approx 10^{23}\ \rho T^{-7/2} Y_e {Z^2\over A}$. Derive a formula for the density-temperature curve along which $\kappa_{ff}=\kappa_{es}$. Compare with Figure 3 in [Paxton et al. 2011](https://ui.adsabs.harvard.edu/abs/2011ApJS..192....3P/abstract) that shows the opacities used in the MESA code. Does your formula help to understand the plot? Where is the centre of the Sun in the plot?

:::{seealso} Solution
:class: dropdown

Setting the free-free opacity $\kappa_{ff}$ equal to the electron scattering opacity $\kappa_{es}$ gives
$$10^{23}\ \rho T^{-7/2}Y_e{Z^2\over A} = 0.4 Y_e$$
and therefore
$$\rho  = 4\times 10^{-3}\ \mathrm{g\ cm^{-3}}\ \left({T\over 10^6\ \mathrm{K}}\right)^{7/2}.$$
Here I've set $Z^2/A = 1$ which works for either H or He so should be good for solar composition.

Here is the plot from Paxton et al.:

```{figure} mesa_opacities.jpg
```
The top left area where the opacity has a constant value (light blue) is electron scattering. The transition to the red triangle (free-free and bound-free) roughly matches our equation. For example, at a density of $10^{-3}\ \mathrm{g\ cm^{-3}}$, the transition occurs around $10^6\ \mathrm{K}$ as expected. At $10^7\ \mathrm{K}$, the density is more like $1\ \mathrm{g\ cm^{-3}}$ which is about right.

The cyan/green colored curves in the plot are profiles of stars labelled by the mass. We see that the solar mass model does extend into the electron scattering region at the centre, but only just. This is consistent with the idea that the Sun is at the transition between free-free (lower mass stars) and electron scattering (more massive stars).

:::

## 3. Massive stars

Near the surface of a star, the photons are mostly travelling outwards. As they scatter, they push on the plasma with a force density $n_e \sigma_T F/c$, where $F=L/4\pi r^2$ is the radiation flux at radius $r$, and $n_e$ is the electron density.

Derive a formula for the luminosity at which this outwards force could overcome gravity (this is known as the Eddington luminosity). What is this value for the Sun? How massive does a main sequence star have to be to approach the Eddington luminosity?

:::{seealso} Solution
:class: dropdown

Balancing the force densities gives 
$${n_e\sigma_T F_\mathrm{Edd}\over c} = \rho {GM\over r^2}.$$
The Thomson scattering opacity is $\kappa_T = n_e\sigma_T/\rho$, so we can use that to simplify, giving a luminosity
$$L_\mathrm{Edd} = {4\pi GMc\over \kappa}.$$
Putting in $\kappa_{es} = 0.4 Y_e\ \mathrm{cm^2\ g^{-1}}$ gives
$$L_\mathrm{Edd} = 1.25\times 10^{38}\ \mathrm{erg\ s^{-1}} \ Y_e^{-1} \left({M\over M_\odot}\right).$$

For the Sun, $L_\odot/L_\mathrm{Edd}$ is therefore $\approx 4\times 10^{33}/1.25\times 10^{38}\approx 3\times 10^{-5}$. In the notes we saw that we can use $L\propto M^3$ for massive stars, so $L/L_\mathrm{Edd}\propto M^2$. If we increase mass by a factor of $\sqrt{3\times 10^4}$ or just over a 100 then the stellar luminosity would approach Eddington. This is one of the reasons that main sequence stars have an upper mass limit around 100 $M_\odot$.

:::




## 4. Giant stars

Estimate the temperature in the hydrogen burning shell of a red giant star. How does it compare with the central temperature in the Sun?


:::{seealso} Solution
:class: dropdown

The gravity at the base of the envelope is dominated by the gravity there $GM_c/R_c^2$, where $M_c$ and $R_c$ are the mass and radius of the core. Hydrostatic balance then gives
$$P\approx {\rho k_B T\over m_p}\approx {M_\mathrm{env}\over 4\pi r^2} {GM_c\over R_c^2}$$
(the pressure is given by the mass per unit area times the gravity, ie. the pressure force per unit area supports the weight of the column of mass per unit area).

The density in the envelope should be roughly $\rho\sim M_\mathrm{env}/r^3$ so for $r\approx R_c$, we get 

$$k_BT\approx {GM_cm_p\over R_c}.$$

We've dropped prefactors here for a rough estimate, but this should capture the correct scaling. The point is that the core properties determine the temperature at the base of the envelope, because the core dominates the gravity there.

Putting in $M_c \approx 0.5 M_\odot$ and $R_c\approx 10^9\ \mathrm{cm}$ (typical white dwarf radius) gives

$$T\approx 8\times 10^8\ \mathrm{K}.$$

In a red giant, the core can be more extended, so this is probably an overestimate. But it shows that the temperature can easily reach what is needed to burn H in a shell ($\sim 10^7\ \mathrm{K}$ in RGB stars or He ($\sim 10^8\ \mathrm{K}$) in AGB stars.
:::





## 5. Virial theorem

The thermal energy $E_T$ and gravitational energy $E_G$ of a star are related by 
$$2E_T = -E_G$$
(this is an example of the Virial theorem). Use this to argue that the Sun has a negative heat capacity.

Discuss the implications of this result for the stability of the Sun.


:::{seealso} Solution
:class: dropdown

This is a neat result if you haven't thought about it before. Imagine that we heat the plasma inside the Sun, so we add an amount of energy $\Delta E$. The star will adjust to a new Virial equilibrium, maintaining the relationship $2E_T=-E_G$. A larger overall energy means $E_G$ becomes less negative, and therefore $E_T$ is smaller. We deposited energy, but the thermal energy and therefore temperature dropped.

This corresponds to a negative heat capacity: $dE/dT$ is negative.

The negative heat capacity has an important consequence: the Sun is thermally stable. If some energy is deposited, say by nuclear burning, the star will expand to cool down again, reducing the nuclear burning rate. In this way it can find an equilibrium state.

In the core of a giant star or in shell burning in a giant star, the opposite happens. In the first case, the star is degenerate, so doesn't respond to a change in temperature; in the second, the gravity in the shell is set by the core (see question 4), so even if the shell expands, it does so at constant pressure. In both cases, the effective heat capacity is positive. So a fluctuation in thermal energy raises the temperature, increasing nuclear burning rates, depositing more energy and so on leading to a thermal runaway (the helium core flash or thin shell flash respectively).
:::



## 6. Proton tunnelling

Without evaluating the tunnelling probability, estimate the fraction of proton collisions at the centre of the Sun that result in a fusion reaction.

Discuss whether the tunnelling probability would give the same answer or not.

:::{seealso} Solution
:class: dropdown

This question is a bit of a puzzle: how can we estimate the fraction of collisions that lead to fusion without looking at the tunnelling probability? The answer is that we know the lifetime of a proton in the Sun: the time a proton waits before it fuses with another proton is about $10\ \mathrm{Gyr}$ (the lifetime of the Sun), or $\sim 3\times 10^{17}\ \mathrm{s}$.

The time between collisions on the other hand is given by
$$t_\mathrm{coll} = {\ell\over v},$$ where $\ell\approx 10^{-6}\ \mathrm{cm}$ is the proton mean free path we estimated in week 1, and the thermal velocity of protons is $v\approx (k_BT/m_p)^{1/2}\approx 300\ \mathrm{km\ s^{-1}}$ at $T\sim 10^7\ \mathrm{K}$. So we find $t_\mathrm{coll}\sim 3\times 10^{-14}\ \mathrm{s}.$

Taking the ratio of collision time to lifetime gives the probability of fusion
$$\sim {10^{-14}\over 3\times 10^{17}}\sim 10^{-30}.$$

If we had instead calculated the tunnelling probability, would we get the same answer? There is an extra piece of physics that enters H fusion which is that it is not enough for the two protons to penetrate the Coulomb barrier, we also need a weak reaction to occur to convert one of the protons into a neutron (the reaction overall is $p+p\rightarrow d+\gamma$). Because we are dealing with the weak nuclear force, this adds another small probability to the rate.


:::