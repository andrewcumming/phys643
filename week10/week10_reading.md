# Week 10: Astrophysical plasmas

So far in the course we have focused on using the fluid equations, including the MHD equations, to model astrophysical plamas. As discussed in [week 1](week1-reading#what-is-a-fluid), the idea is that we can think of the fluid as a continuum when the mean free path of particles is smaller than the size of the system. However, we have seen examples already where this idea breaks down. One example is astrophysical shocks, which are often *collisionless*, with shock thickess much smaller than the mean free path. Another was the solar wind where the mean free path for Coulomb collisions can be as large as the scale of the wind itself. Plasma physics is a big subject, easily worth a course by itself. Here, we'll focus on some of the main ideas that it is good to know about.

## Debye length and screening

Much of the interesting behaviour of plasmas comes about from the interaction of the charged particles with electromagnetic fields, which enables **collective behavior** of the plasma. Rather than two-body collisions, particles mainly interact with the electromagnetic fields produced by the collection of particles. The scale on which this can happen is known as the **Debye length**.

To derive an expression for the Debye length, we can think about putting a point charge $Q$ into a plasma. The extra charge will polarize the ions and electrons, with electrons being attracted towards the charge and ions being repelled. The net effect of this will be to **screen** the charge from the surrounding plasma. In thermal equilibrium, we can write the number densities as
$$n_i = n \exp\left(-{e\phi\over k_BT}\right)$$
$$n_e = n \exp\left({e\phi\over k_BT}\right),$$
where $n$ is the number density of ions or electrons at large distance (where the plasma will be charge neutral, with equal electron and ion number densities). The electrostatic potential $\phi(r)$, where $r$ is the distance from the charge $Q$, is given by Poisson's equation
$$\nabla^2 \phi = -4\pi(n_i-n_e)e - 4\pi Q\delta(r),$$
or
$$\nabla^2 \phi = -4\pi ne\left[ \exp\left(-{e\phi\over k_BT}\right)-\exp\left({e\phi\over k_BT}\right) \right] - 4\pi Q\delta(r).$$
The second term with the delta function accounts for the point charge $Q$; the second term is the contribution from the screening cloud of electrons and ions.

When $e\phi\ll k_BT$, we can expand the exponentials to get
$$\nabla^2 \phi - {8\pi n e^2 \phi\over k_BT} = \nabla^2\phi - {\phi\over\lambda_D^2} = - 4\pi Q\delta(r),$$
where the Debye length is
$$\lambda_D = \left({k_BT\over 8\pi ne^2}\right)^{1/2}.$$
The solution for the potential is
$$\phi(r) = Q {e^{-r/\lambda_D}\over r}$$
which is known as a **screened Coulomb potential** or Yukawa potential. It falls off as the usual $1/r$ Coulomb potential close to the charge, but is exponentially suppressed for $r>\lambda_D$. This means that the effect of the charge $Q$ is confined to a volume $\sim \lambda_D^3$.

The number of particles in a Debye sphere with radius $\lambda_D$ gives a measure of how many particles can interact collectively. This is known as the **plasma parameter**
$$\Lambda = {4\pi \over 3} n\lambda_D^3 = {4\pi \over 3}  \left({k_BT \over 8\pi e^2}\right)^{3/2}n^{-1/2} = 486 {T^{3/2}\over n^{1/2}},$$
where in the last expression temperature is in K and $n$ is in $\mathrm{cm}^{-3}$. A related parameter is the **Coulomb coupling parameter**
$$\Gamma = {Ze^2\over a k_BT} = 2.7\times 10^{-3} {n^{1/3}\over T},$$
where $a$ is the interion spacing given by $(4\pi/3)a^3n=1$. This measures the ratio of the typical Coulomb energy between ions to the thermal energy, and is related to the plasma parameter by $\Lambda = (Z/6\Gamma)^{3/2}= (\lambda_D/a)^3$. Large $\Lambda$ or small $\Gamma$ is the limit of a **weakly-coupled plasma**. In that case, the Debye length is large and collective interactions are important.

Screening is very important to take into account when calculating nuclear reaction rates. It reduces the Coulomb barrier for two nuclei that are approaching each other, exponentially enhancing the nuclear burning rate. This correction is discussed in one of the [papers](week10-papers) for this week.


## Plasma waves and particle-wave interactions

At low frequencies, where the ions and electrons can move together, a plasma supports the same set of modes that we have seen before: MHD fast and slow acoustic modes (these are called ion-acoustic modes in this context), and Alfvèn waves. At high frequencies, however, where the ions are not able to respond due to their large mass, the electron motion relative to the ions supports new kinds of waves.

### Cold plasma waves

To see what waves these high frequency modes look like, we can perturb a plasma assuming that the ions remain at rest and only the electrons respond to the perturbations. The background state is at rest and has $E=0$ and $B=0$. In the limit of a **cold plasma** we can neglect the electron pressure. The linear perturbation equations are then
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

For low frequencies $\omega<\omega_P$, $\epsilon$ is negative, giving an imaginary $k$ or in other words an evanescent wave. Only waves with $\omega>\omega_P$ can propagate through a plasma. A way to think about this physically is that when the frequency is smaller than the plasma frequency, there is plenty of time for the electrons to move, shorting out the electric field of the wave. At high frequencies on the other hand, the electrons do not have time to respond.

Looking at equation {eq}`eq:dispcold` we can see that there is another possibility: a **longitudinal wave** with $\vec{k}\parallel\delta\vec{E}$. In that case, the left-hand side cancels and for a non-trivial solution we need $\epsilon=0$ or $\boxed{\omega = \omega_P}$. This is known as a **Langmuir oscillation**. It has $v_g=0$, so is non-propagating. It corresponds physically to a standing longitudinal oscillation of the plasma.

### Warm plasma waves

In a warm plasma, we need to add pressure gradient terms back into the momentum equation:
$$-i\omega m_e n \delta \vec{u} = -e n \delta \vec{E} - {\gamma P\over n}\vec{\nabla}\delta n,\label{eq:pert4}$$
where we've assumed a relation $\delta P = (\gamma P/n) \delta n$. Unlike in the cold plasma, the density perturbation $\delta n$ now appears in the equations. We then need to also include the continuity and Poisson equations:
$$-i\omega\delta n + n\vec{\nabla}\cdot\delta\vec{u} = 0\label{eq:pert5}$$
$$\vec{\nabla}\cdot\delta\vec{E} = -4\pi e \delta n.\label{eq:pert6}$$
Again assuming perturbations $\propto e^{i\vec{k}\cdot\vec{r}}$ and taking $\vec{k}\parallel \delta\vec{E}$ for the longitudinal wave, equations {eq}`eq:pert4` to {eq}`eq:pert6` give the dispersion relation
$$\boxed{\omega^2 = \omega_P^2 + k^2 {3 P\over m_en}= \omega_P^2 + k^2 {3 k_BT\over m_e} }.$$
We have set $\gamma=3$ which is the appropriate value for 1-dimensional (longitudinal) adiabatic perturbation. We see that the effect of non-zero temperature is to turn the longitudinal mode into a propagating wave, known as a **Langmuir wave**.


To be continued ...


### Whistler waves and the Hall effect

### Landau damping

## Anisotropic conductivity
