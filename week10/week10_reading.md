# Week 10: Astrophysical plasmas

So far in the course we have focused on using the fluid equations, including the MHD equations, to model astrophysical plamas. As discussed in [week 1](week1-reading#what-is-a-fluid), the idea is that we can think of the fluid as a continuum when the mean free path of particles is smaller than the size of the system. However, we have seen examples already where this idea breaks down. One example is astrophysical shocks, which are often *collisionless*, with shock thickess much smaller than the mean free path. Another was the solar wind where the mean free path for Coulomb collisions can be as large as the scale of the wind itself. Plasma physics is a big subject, easily worth a course by itself. Here, we'll focus on some of the main ideas that it is good to know about.

## Debye length and screening

Much of the interesting behaviour of plasmas comes about from the interaction of the charged particles with electromagnetic fields, which enables **collective behavior** of the plasma. Rather than two-body collisions, particles mainly interact with the electromagnetic fields produced by the collection of particles.

In a plasma electrostatic fields are screened on a lengthscale known as the **Debye length**. To derive an expression for the Debye length, we can think about putting a point charge $Q$ into a plasma. The extra charge will polarize the ions and electrons, with electrons being attracted towards the charge and ions being repelled. The net effect of this will be to **screen** the charge from the surrounding plasma. In thermal equilibrium, we can write the number densities as
$$n_i = n \exp\left(-{Ze\phi\over k_BT}\right)$$
$$n_e = Zn \exp\left({e\phi\over k_BT}\right),$$
where $Z$ is the ion charge and $n$ is the number density of ions at large distance (where the plasma will be charge neutral, with electron density $Z$ times larger than the ion number density). The electrostatic potential $\phi(r)$, where $r$ is the distance from the charge $Q$, is given by Poisson's equation
$$\nabla^2 \phi = -4\pi(Zn_i-n_e)e - 4\pi Q\delta(r),$$
or
$$\nabla^2 \phi = -4\pi Zne\left[ \exp\left(-{Ze\phi\over k_BT}\right)-\exp\left({e\phi\over k_BT}\right) \right] - 4\pi Q\delta(r).$$
The second term with the delta function accounts for the point charge $Q$; the first term is the contribution from the screening cloud of electrons and ions.

When $Ze|\phi|\ll k_BT$, we can expand the exponentials to get
$$\nabla^2 \phi - {4\pi n Z(Z+1)e^2 \phi\over k_BT} = \nabla^2\phi - {\phi\over\lambda_D^2} = - 4\pi Q\delta(r),$$
where the Debye length[^debyelength] is
$$\lambda_D = \left({k_BT\over 4\pi nZ(Z+1)e^2}\right)^{1/2}.$$
The solution for the potential is
$$\phi(r) = Q {e^{-r/\lambda_D}\over r}$$
which is known as a **screened Coulomb potential** or Yukawa potential. It falls off as the usual $1/r$ Coulomb potential close to the charge, but is exponentially suppressed for $r>\lambda_D$. This means that the effect of the charge $Q$ is confined to a volume $\sim \lambda_D^3$.

[^debyelength]: One additional assumption we've made here is that the electrons and ions have the same temperature. If not, the Debye length can be written more generally as $${1\over \lambda_D^2} = {4\pi n_e e^2\over k_BT_e} + {4\pi n_i Z^2e^2\over kBT_i}.$$

The number of ions in a Debye sphere with radius $\lambda_D$ gives a measure of how many particles can participate in collective interactions. This is known as the **plasma parameter**
$$\Lambda = {4\pi \over 3} n\lambda_D^3 = {4\pi \over 3}  \left({k_BT \over 4\pi Z(Z+1)e^2}\right)^{3/2}n^{-1/2} = 1376\, {T^{3/2}\over n^{1/2}}\,[Z(Z+1)]^{-3/2},$$
where in the last expression temperature is in K and $n$ is in $\mathrm{cm}^{-3}$. A related parameter is the **Coulomb coupling parameter**
$$\Gamma = {Z^2e^2\over a k_BT} = 2.7\times 10^{-3} {Z^2 n^{1/3}\over T},$$
where $a$ is the interion spacing given by $(4\pi/3)a^3n=1$. This measures the ratio of the typical Coulomb energy between ions to the thermal energy, and is related to the plasma parameter by
$$\Lambda = \left({\lambda_D\over a}\right)^3 = \left[{Z\over 3(Z+1)\Gamma}\right]^{3/2}.$$ Large $\Lambda$ or small $\Gamma$ is the limit of a **weakly-coupled plasma**. In that case, there are many particles within a Debye sphere and so collective interactions are more important than individual two-body interactions.

Screening is very important to take into account when calculating nuclear reaction rates. It reduces the Coulomb barrier for two nuclei that are approaching each other, exponentially enhancing the nuclear burning rate. This correction is discussed in one of the [papers](week10-papers) for this week.


## Plasma waves and particle-wave interactions

At low frequencies, where the ions and electrons can move together, a plasma supports the same set of modes that we have seen before based on the MHD equations: fast and slow magnetosonic waves and Alfvèn waves. Plasmas also have ion-acoustic waves, compressive waves with restoring force from electron pressure and the ions supplying the inertia. At high frequencies, where the ions are not able to respond due to their large mass, the electron motion relative to the ions modifies the dispersion relation for transverse electromagnetic waves and introduces a new longitudinal mode, the Langmuir wave.

### Cold plasma waves

To see what the high frequency modes look like, we can perturb a plasma assuming that the ions remain at rest and only the electrons respond to the perturbations. The background state is at rest and has $E=0$ and $B=0$. In the limit of a **cold plasma** we can neglect the electron pressure. The linear perturbation equations are then
$$-m_e n i\omega\delta \vec{u} = -e n \delta \vec{E}$$
$$\vec{\nabla}\times\delta\vec{B} = -{4\pi\over c}ne\delta\vec{u} + {1\over c}(-i\omega)\delta\vec{E}$$
$$\vec{\nabla}\times\delta\vec{E} = -{1\over c}(-i\omega) \delta\vec{B},$$
which are the electron momentum equation, Ampère's law and Faraday's law. Using the momentum equation to substitute for $\delta\vec{u}$ in Ampère's law gives
$$\vec{\nabla}\times \delta\vec{B} = - {i\omega\over c}\delta\vec{E} \left(1-{\omega_P^2\over \omega^2}\right) = -{i\omega\over c} \epsilon \delta\vec{E},$$
where the **plasma frequency** $\omega_P$ is given by
$$\boxed{\omega_P^2 = {4\pi ne^2\over m_e}},$$
and we define the **dielectric constant** of the plasma
$$\boxed{\epsilon = 1 - {\omega_P^2\over \omega^2}}.$$
Plugging numbers into the expression for plasma frequency gives $f_P = \omega_P/2\pi \approx 10\ \mathrm{kHz}\ n^{1/2}$.

To see the waves, we can look for solutions $\propto e^{i\vec{k}\cdot\vec{r}}$. The perturbation equations are then
$$-i m_e \omega n \delta \vec{u} = -e n \delta \vec{E}\label{eq:pert1}$$
$$i\vec{k}\times\delta\vec{B} = - {i\omega\over c}\epsilon\delta\vec{E}\label{eq:pert2}$$
$$i\vec{k}\times\delta\vec{E} = {i\omega\over c} \delta\vec{B}.\label{eq:pert3}$$
These equations can be used to obtain a dispersion relation for the waves. We can use the identity
$$\vec{k}\times(\vec{k}\times\delta\vec{E}) = -k^2\delta\vec{E} + \vec{k}(\vec{k}\cdot\vec{E}).$$
Taking $\vec{k}\times$ equation {eq}`eq:pert3`, using this identity and then substituting equation {eq}`eq:pert2` gives
$$-k^2\delta\vec{E} + \vec{k}(\vec{k}\cdot\delta\vec{E}) = -{\omega^2\over c^2}\epsilon\delta\vec{E}.\label{eq:dispcold}$$

If $\boxed{\vec{k}\cdot\delta\vec{E}=0}$, i.e. the electric field perturbations are perpendicular to the wave direction (transverse wave), we get the dispersion relation
$$\boxed{\omega^2 = {c^2k^2\over \epsilon} = {c^2k^2\over n^2}},$$
where $n = \sqrt{\epsilon}$ is the refractive index. For $\omega>\omega_P$, $\epsilon$ is real and less than 1, so we have a **propagating transverse wave** with phase and group velocities
$$v_p = {\omega\over k} = {c\over n}; \hspace{1cm} v_g = {\partial \omega\over \partial k} = nc.$$
This is the usual electromagnetic wave but modified by the plasma currents.
Note that since $n<1$ the phase velocity is larger than the speed of light $c$, but the group velocity (the speed of information propagation) is smaller than $c$.

For low frequencies $\omega<\omega_P$, $\epsilon$ is negative, giving $k^2<0$ or in other words an evanescent wave ($k$ is imaginary). Only waves with $\omega>\omega_P$ can propagate through a plasma. A way to think about this physically is that when the frequency is smaller than the plasma frequency, there is plenty of time for the electrons to move, shorting out the electric field of the wave. At high frequencies on the other hand, the electrons do not have time to respond.

Looking at equation {eq}`eq:dispcold` we can see that there is another possibility: a **longitudinal wave** with $\vec{k}\parallel\delta\vec{E}$. In that case, the left-hand side cancels and for a non-trivial solution we need $\epsilon=0$ or $\boxed{\omega = \omega_P}$. This is known as a **Langmuir oscillation**. It has $v_g=0$, so is non-propagating. It corresponds physically to a longitudinal oscillation of the electrons relative to the ions, but with no propagation of the disturbance.

### Warm plasma waves and Landau damping

A full analysis of the effect of temperature on the wave spectrum requires perturbing the Vlasov equation, which is the equation for the evolution of the distribution functions of the electrons and ions in the presence of the electric and magnetic fields. However, we can get a sense of what happens by using a fluid prescription for the electrons. Adding the pressure gradient terms back into the momentum equation for the electrons gives
$$-i\omega m_e n \delta \vec{u} = -e n \delta \vec{E} - {3 P\over n}\vec{\nabla}\delta n,\label{eq:pert4}$$
where we've assumed a relation $\delta P = (3 P/n) \delta n$ which comes from the full calculation and depends on the electron distribution function (e.g. Maxwellian at temperature $T$). As before, we are looking at high frequency waves where ion motion is not important. Unlike in the cold plasma, the electron density perturbation $\delta n$ now appears in the equations. We then need to also include the continuity and Poisson equations:
$$-i\omega\delta n + n\vec{\nabla}\cdot\delta\vec{u} = 0\label{eq:pert5}$$
$$\vec{\nabla}\cdot\delta\vec{E} = -4\pi e \delta n.\label{eq:pert6}$$
Again assuming perturbations $\propto e^{i\vec{k}\cdot\vec{r}}$ and taking $\vec{k}\parallel \delta\vec{E}$ for the longitudinal wave, equations {eq}`eq:pert4` to {eq}`eq:pert6` give the dispersion relation
$$\boxed{\omega^2 = \omega_P^2 + k^2 {3 P\over m_en}= \omega_P^2 + k^2 {3 k_BT\over m_e} }.\label{eq:warmdispersion}$$
We see that the effect of non-zero temperature is to add a wavelength-dependent term to the dispersion relation. This is the same longitudinal mode that we found for cold plasmas, but now with a non-zero group velocity. This is known as a **Langmuir wave**. Equation {eq}`eq:warmdispersion` is valid in the long-wavelength limit; the kinetic approach (perturbing the Vlasov equation) is needed when $k\lambda_D$ is no longer small.

Including the particle distribution functions in the analysis also reveals an important new effect: **Landau damping**. Resonant particle-wave interactions occur for particles moving with velocities close to the phase velocity of the wave (more precisely particles with the component of velocity in the direction of the wave close to the wave phase velocity). If the particles are moving faster than the wave, particles lose energy, whereas if the particles are moving slower than the wave, they gain energy. The net transfer of energy therefore depends on the slope of the particle distribution function with velocity. For a Maxwellian distribution, $f(v_\parallel)$ decreases with increasing particle velocity, so that there are more particles on the slower side of the resonance than on the faster side of the resonance. The net effect is therefore for the wave to lose energy. In the full calculation, this appears as an imaginary part of the wave frequency.





### Whistler waves and the Hall effect


## Anisotropic conductivity


## Reading questions

1. Show that the dispersion relation for electromagnetic waves in a plasma can be written as $\omega^2 = \omega_P^2 + c^2k^2$. Why does this expression show that $\omega$ has to be $>\omega_P$ for a propagating wave?


