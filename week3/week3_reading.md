# Week 3: Hot Stars

This week we are going to  move onto "hot stars" for which $k_BT\gg E_F$ and temperature matters in describing their structure. We therefore need to understand the energy sources and energy sinks within the star and how energy is transported around.

## Radiative diffusion, opacity, and the luminosity of stars

The main energy transport mechanism in stars is diffusion of photons. The mean free path of a photon is $\lambda = 1/n\sigma$ where $n$ is the number density of scatterers or absorbers and $\sigma$ is the cross-section. In astrophysics, we usually write everything per gram, so that $\lambda = 1/\rho\kappa$ where $\kappa$ is the cross-section per gram, or the *opacity*. For example, free electrons scatter photons with the Thomson cross-section $$\sigma_T = {8\pi\over 3}\left({e^2\over m_e c^2}\right)^2 = 6.67\times 10^{-25}\ {\rm cm^2}.$$ For pure hydrogen, the opacity is $\kappa = n_e\sigma_T / \rho = \sigma_T/m_p =  0.40\ {\rm cm^2\ g^{-1}}$.

Using this Thomson scattering opacity gives the photon mean free path in the center of the Sun as $\lambda\approx 10^{-2}\ {\rm cm}$ (taking $\rho=150\ {\rm g\ cm^{-3}}$). This is obviously much less than the solar radius, so photons are scattered or absorbed many times on traversing the Sun, but it is also much longer than the particle mean free path ($\sim 10^{-6}\ {\rm cm}$; as we discussed in Week 1), so that photons carry information about the temperature at their origin to the location where they are absorbed, thereby transporting heat.

Other important opacity sources in stars are *free-free absorption* and *bound-free absorption*, associated with an electron absorbing a photon in the presence of a nucleus. The words 'free' and 'bound' refer to whether the electron doing the absorbing starts or ends in a bound state or unbound state. Unlike electron scattering, the bound-free and free-free opacities depend on density and temperature, with the *Kramer's law* scaling $\kappa\propto \rho T^{-7/2}$.

The heat flux carried by the diffusing photons is 
$$F = -{1\over 3}\, c\,\lambda\, {d\over dr}\left({aT^4}\right) = -{4acT^3\over 3\kappa\rho}{dT\over dr}.\label{eq:radiativediffusion}$$ The outwards luminosity at radius $r$ is then $L = 4\pi r^2 F$. Note that in general the opacity depends on the local density, temperature and composition so we can write $\kappa(\rho,T,X_i)$ where $X_i$ is a set of mass fractions describing the composition. The heat flux is of the form we discussed in Week 1, $F=-K\vec{\nabla}T$ where $K\propto T^3/\kappa\rho$ is the thermal conductivity.

Let's use the radiative diffusion equation to estimate the luminosity of a star. We mentioned last time that hydrostatic balance is enough to estimate the central temperature of a star if we know its mass and radius, $$k_B T_c\approx {GM m_p\over R} \Rightarrow T_c\approx 2\times 10^7\ {\rm K}\ \left({M\over M_\odot}\right)\left({R\over R_\odot}\right)^{-1}.$$ The hot interior implies a luminosity
$$L\sim 4\pi R^2 {4 ac T^4\over 3\kappa R} {4\pi R^3\over 3 M}\sim {64\pi^2\over 9}{acT^4 R^4\over \kappa M},$$
where we write $r\approx R$, $\rho \approx (3/4\pi)(M/R^3)$, and $dT/dr\approx T/R$. Now putting in $T_c$ for the temperature,
$$L\sim {64\pi^2\over 9}{ac\over\kappa}\left({Gm_p\over k_B}\right)^4 M^3 \left({T\over T_c}\right)^4$$
$$\sim 2\times 10^{35}\ {\rm erg\ s^{-1}}\ \left({M\over M_\odot}\right)^3\left({\kappa\over 0.4\ {\rm cm^2\ g^{-1}}}\right)^{-1}$$
for a temperature $T=0.2T_c$ which is the temperature at $\approx 0.5R$ in the Sun. This estimate is quite a bit larger than the actual solar luminosity, $L_\odot\approx 4\times 10^{33}\ {\rm erg\ s^{-1}}$, but this is just a rough estimate. The important thing is the scaling $L\propto M^3$ which is seen in models for stars with mass $M\gtrsim M_\odot$ for which the central temperature is large enough that electron scattering dominates the opacity. For $M\lesssim 1 M_\odot$, free-free opacity dominates instead, introducing a temperature and density scaling into $\kappa$. These low mass main-sequence stars have a steeper dependence $L\propto M^{5.5}$. 

An alternative energy transport mechanism in stars is *convection*, in which fluid motions transport heat. We'll look more into this when we talk about instabilities, but the basic idea is that if the temperature gradient is steep enough, the entropy gradient in the star can become negative (entropy decreases outwards). High entropy material underneath low entropy material is unstable to mixing and results in convection. Stars can be fully-convective (low mass stars $\lesssim 0.3 M_\odot$), have a surface convection zone ($M\sim M_\odot$), or a convective core ($M\gtrsim M_\odot$). 

## Thermonuclear reactions

We've seen that a star must be hot to hold itself up against gravity $T_c\propto M/R$, and that implies a certain luminosity ($L\propto M^3$ for electron scattering). The luminosity is supplied by nuclear burning — at each stage of a star's life, the radius of the star adjusts to give the right central temperature at which nuclear burning can balance the luminosity. 

For two nuclei to fuse, they must approach to a distance $\sim 10^{-13}\ {\rm cm}$ (about the size of a nucleus) at which strong forces operate. In practise, this is not possible because of Coulomb repulsion between nuclei. For example, at the Sun's central temperature, the average energy of protons is $\approx 1\ {\rm keV}$. We know that the binding energy of hydrogen $e^2/a_0$ is about 10 eV for $a_0\sim 10^{-8}\ {\rm cm}$ (the Bohr radius), so at $1\ {\rm keV}$, the closest approach distance must be $\sim 10^{-10}\ {\rm cm}$. This is a factor of 1000 too large for fusion to occur. How then do nuclear reactions happen? The answer is that the protons tunnel through the Coulomb barrier.

We can estimate the probability for quantum tunnelling using basic ideas from quantum mechanics. You might recall that when a particle tunnels through a potential barrier, the wavefunction decreases by a factor $e^{-kx}$, where $x$ is the barrier width, and $k\approx \sqrt{2m V_0}/\hbar$ is the wavevector of the evanescing wavefunction. Now for two protons at their closest approach distance $r_c$, the potential barrier height is $V_0\sim e^2/r_c$ and the width of the barrier is $r_c\approx e^2/E$ where $E$ is the center of mass energy of the two protons. Therefore $$kx\sim {e\over \hbar}\sqrt{2m r_c}\sim \sqrt{2m c^2\over E} {e^2\over \hbar c} = \sqrt{2\alpha^2m c^2\over E},$$
where $\alpha = e^2/\hbar c = 1/137$ is the fine-structure constant. A more detailed treatment which integrates through the barrier gives a similar result but with an extra factor of $\pi$ in the prefactor. Allowing for nuclei other than hydrogen by including the charges of the fusing nuclei $Z_1$ and $Z_2$, the final tunnelling probability is
$${\rm Prob} \propto \exp\left({-\sqrt{E_G\over E}}\right)\label{eq:tunnellingprob}$$
where $$E_G=2\pi^2\alpha^2mc^2(Z_1Z_2)^2\approx 1\ {\rm MeV}\ Z_1^2Z_2^2\left({m\over m_p}\right)$$ is the *Gamow energy* and $m$ is the reduced mass of the two nuclei $m=m_1m_2/(m_1+m_2)$.

Equation {eq}`eq:tunnellingprob` shows that tunnelling is most likely for high energy particles. However, the particle energies are determined by the Maxwell-Boltzmann distribution, which falls off steeply at high energy, $\propto e^{-E/k_BT}$. The tunnelling rate is therefore a convolution between the tunnelling probability and Maxwell-Boltzmann distribution. The tunnelling is most likely for energy $E_0$ where $\exp(-E_0/k_BT-\sqrt{E_G/E_0})$ has a maximum, or $E_0=(k_BT)^{2/3}(E_G/2)^{1/3}$. For $k_BT\approx 1\ {\rm keV}$ and $E_G\approx 1\ {\rm MeV}$, this is $E_0\approx 6\ {\rm keV}$. The energies around $E_0$ where the reaction is most likely to occur is called the *Gamow window*. For many reactions, the energy-dependence of the cross-section must also be taken into account, particularly when there is a resonance which boosts the cross-section at the resonant energy. 

The fact that nuclear fusion happens only for particles in the tail of the Maxwell-Boltzmann distribution means that thermonuclear reaction rates are extremely temperature sensitive. This is particularly true for reactions involving heavier nuclei. These nuclei have larger $Z$'s and so a larger Coulomb barrier, and require higher temperatures to fuse. The larger $Z$ nuclei have a larger factor in the exponent and so have reaction rates that are more temperature sensitive than lower $Z$ nuclei. One impact of this for main sequence stars is that massive main sequence stars $M\gtrsim M_\odot$ which burn hydrogen via the CNO cycle have $T_c$ roughly independent of mass and so $R\propto M$. (It's actually a bit shallower because $T_c$ increases a little bit with $M$.)

## Stellar evolution

The full set of equations that are needed to follow the evolution of a hot star are
$${\partial m\over \partial r} = 4\pi r^2\rho$$
$${\partial P\over \partial r} = -{\rho Gm\over r^2}$$
$$T{\partial S\over \partial t} = \epsilon_{\rm nuc}-\epsilon_\nu-{1\over 4\pi r^2\rho}{\partial L\over \partial r}$$
$${\partial T\over\partial r} = {\partial P\over \partial r}{T\over P}\nabla\label{eq:stardTdr}$$
$${\partial X_i\over\partial t} = {m_i\over \rho}\sum_j \left(r_{ji} - r_{ij}\right) + D {\partial^2X_i\over \partial r^2}$$
where the temperature gradient $\nabla\equiv \partial \ln T/\partial\ln P$ in equation {eq}`eq:stardTdr` is determined by the energy transport process. If radiation is transporting energy, $$\nabla = \nabla_{\rm rad} = {3\kappa P L\over 16\pi ac Gm T^4},$$
from the radiative diffusion equation. When convection operates, the temperature gradient is usually close to the adiabatic gradient $\nabla=\nabla_{\rm ad}$ (because this is the entropy-neutral gradient that marks the onset of convection). The nuclear energy generation rate per gram is written as $\epsilon_{\rm nuc}$ (units are ${\rm erg\ g^{-1}\ s^{-1}}$). In massive stars in late burning stages the temperature and density can be large enough that neutrinos become an effective cooling source. The  local neutrino cooling rate is written as $\epsilon_\nu$. The last equation is actually a set of equations, one for each species, which follow the change in composition as nuclear reactions occur and as diffusion, convection or other processes mix composition in the star (for simplicity, I just put a diffusion term here).

Overall, the life of a star involves moving to higher central temperatures and densities, stopping at various nuclear burning stages, until the core becomes degenerate. This is illustrated in the figure below, taken from [Iben (1985)](http://adsabs.harvard.edu/abs/1985QJRAS..26....1I}) (see also the movies linked below). The solid curves with arrows show the paths taken by the central density/temperature of stars of different mass. Without an internal energy source, the star contracts and moves up and to the right in the diagram. When the centre hits one of the dashed lines, nuclear burning ignites and can support the star as long as the fuel lasts. When the fuel runs out, the star starts to contract again and moves up to the next dashed line. In this way, stars burn H first, then He, if massive enough they burn carbon next and so on up to the most massive stars that burn all the way to iron. The end of the stars life happens when the central conditions become dense enough that the equation of state becomes degenerate. Then cooling no longer causes contraction and the star just cools off as a white dwarf. 

```{figure} iben.png
```

Several codes to follow stellar evolution are available. An interesting one to try is [MESA](http://mesastar.org) (Modules for Experiments in Stellar Astrophysics). Here are two movies made using this code that show the evolution of main sequence stars:

- [1 solar mass](https://www.youtube.com/watch?v=oZY3TtA63sE)
- [3 solar masses](https://www.youtube.com/watch?v=C4tucmhAaSk)

These movies show the temperature profiles (as a function of density) and how they evolve over time. Red regions show nuclear burning. Watching these movies you'll see that the nuclear burning is often unstable, leading to a rapid local rise in temperature within the star. This happens either when the nuclear burning is in a degenerate region (e.g. when helium ignites in the core of the solar mass star) or when the burning is in a thin shell (He burning or H burning shells in giants). In either of these situations, the star is not able to lower the pressure by expansion in response to nuclear energy release. The temperature rises and the nuclear burning runs away.

## Cores and envelopes

In stellar evolution, there is an interesting interplay between cores and envelopes. In a main sequence star like the Sun, the star is relatively compact, with a smooth change in density, temperature and composition from the center to the surface. However, once hydrogen runs out in the core and the main sequence lifetime ends, the star adopts a very different structure. The star contracts and heats up until the hydrogen at the edge of the helium core is hot enough to ignite. The non-burning helium core now has a hydrogen-burning shell on top of it.

The ignition of a shell source has a dramatic effect on the hydrostatic structure of the star, which becomes a red giant, with a large, low density, extended hydrogen envelope sitting on top of a compact helium core in the center. This is a general feature: *if the nuclear burning is central, the star will be compact; if burning is in a shell source, the star adopts a giant structure.*
 
In a red giant, the helium core is isothermal at a temperature that is regulated by the shell H burning. An interesting aspect of an isothermal non-degenerate core is that there is a maximum mass envelope that it can support. The way to see this is to write an equation for the pressure at the surface of the core $P_s$. Integrating the hydrostatic balance equation from the center to the surface of the core gives 
\begin{equation}\label{eq:Ps}
P_s = A {T_c M_c\over R_c^3} - B {GM_c^2\over R_c^4}
\end{equation}
for constants $A$ and $B$ that depend on the internal density profile (the core has mass $M_c$ and radius $R_c$). Think of this as saying that the surface pressure is the mean pressure in the core reduced by the weight of the core. For zero pressure at the surface, the radius is $R_0 = BGM_c/AT_c$ (which shows the $T\propto M/R$ scaling we've seen before).

Equation {eq}`eq:Ps` has the interesting feature that, varying the core radius, there is a maximum pressure. At large core radius, both terms go to zero, so the surface pressure becomes small. At small core radius, the gravitational term increases faster than the mean pressure term, also reducing the pressure. The maximum surface pressure is
$$P_{s,{\rm max}}={27\over 256}B{GM_c^2\over R_0^4}\propto {T_c^4\over M_c^2}$$ 
at a radius $R=(4/3)R_0\propto M_c/T_c$.

The maximum surface pressure means that there is a maximum mass envelope that the core can support hydrostatically. This is known as the *Schönberg-Chandrasekhar limit*, and can be written as a ratio of core mass to total mass. This is because most of the mass of the star is contained in the envelope, so the pressure at the base of the envelope is $P_b\approx GM^2/R^4\propto T_c^4/M^2$ since the (base of the) envelope is at the same temperature as the core and $T\propto M/R$. This means that $P_b/P_{s,{\rm max}}\propto (M_c/M)^2$. Typically the limit is found to be $M_c/M\lesssim 0.1$ for stability. 

For red giants, this can lead to collapse of the helium core: as the hydrogen shell adds more and more helium to the core, it grows in mass. Once it reaches the Schönberg-Chandrasekhar mass, it collapses, initiating helium burning in the core. This ends the giant phase, and the star evolves into a compact, helium burning configuration. In practise, this happens only in a limited range of stellar masses, because massive stars leave the main sequence with a helium core that already exceeds the Schönberg-Chandrasekhar limit.

Note that the surface pressure does not have this behaviour for a degenerate core: then the pressure $\propto 1/R^5$ rather than $1/R^3$ and the radius can always adjust to supply any surface pressure needed. In that case, the helium burning starts in an unstable way once the core temperature reaches a critical value. The helium burning is unstable because burning starts to heat up the core. A non-degenerate star would expand to accomodate the extra energy, but a degenerate core barely changes its pressure ($E_F\gg k_BT$) and so doesn't expand. Instead it gets hotter which causes the nuclear burning to go faster, which makes the core even hotter ... the core unstably ignites, giving a core helium flash.

This difference between degenerate or non-degenerate cores means that there is a separation in stellar evolution between stars that develop a degenerate helium core and undergo a helium core flash ($\lesssim 2\ M_\odot$) and those that have a non-degenerate helium core and do not undergo a core flash ($\gtrsim 2\ M_\odot$).

## Reading questions

- Explain physically why the flux of diffusing photons has the form given in equation {eq}`eq:radiativediffusion`.
- Write down some differences between low mass stars (less massive than the Sun) and high mass stars (more massive than the Sun).
- Watch the movie showing the evolution of a solar mass star. Make a list of events you can see in the movie and how they are reflected in temperature profile.
- Explain the difference in how stars larger and smaller than 2 $M_\odot$ end their red giant phase.
