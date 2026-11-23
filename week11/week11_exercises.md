# Exercises

## 1. Relativistic Euler

Take the spatial component of the relativistic Euler equation {eq}`eq:releuler` and check that it reduces to the correct non-relativistic version. What order of $v/c$ are the correction terms? What extra terms does relativity add, how can we interpret them physically?

## 2. Shock breakout

A supernova launches a shock that travels outwards through the envelope of the massive star. When it reaches the outer layers, radiation is able to escape from the shock and causes a burst of radiation that is known as *shock breakout*.

(a) First show that if the post-shock material is dominated by radiation pressure, then the compression across the shock, assuming the strong shock limit, is $\rho_2 = 7 \rho_1$ and that the post-shock pressure is $P_2=(6/7)\rho_1 v_s^2$ where $v_s$ is the shock speed. Assuming values $\rho_1\approx 10^{-7}\ \mathrm{g\ cm^{-3}}$ and $v_s\approx 10^9\ \mathrm{cm\ s^{-1}}$, check the post shock temperature and show that it was a good assumption that the shock is radiation pressure dominated.

(b) Show that photons diffuse ahead of the shock over a region of optical depth $\tau\approx c/v_s$. [Hint: calculate the size of the region $\ell$ for which the shock crossing time $\ell/v_s$ is the same as the photon diffusion time.] These kinds of shocks are actually radiation-mediated; the radiation streaming ahead of the shock front decelerates the fluid.

(c) Breakout occurs when the shock is close enough to the stellar surface that the optical depth of the material ahead of it becomes less than $c/v_s$. For shock velocity of $10^9\ \mathrm{cm\ s^{-1}}$, what is this optical depth? Use the post shock energy density and the size of the region with optical depth $c/v_s$ to estimate the order of magnitude of the energy in a shock breakout event. You can assume $R\approx 10^{13}\ \mathrm{cm}$.

## 3. Co-moving frame

We mentioned in the notes that the right-hand side of equation {eq}`eq:energywithrad` is missing a term to account for the difference between comoving and inertial frames. In the comoving frame the net heating/cooling from the radiation field is
$$c\rho\kappa(E^\prime_r-aT^4),\label{eq:week11ex1}$$
but for equation {eq}`eq:energywithrad` we need to transform this into the inertial frame. Here the prime on the radiation energy density indicates it is evaluated in the comoving frame; we don't need to do the same for temperature or opacity because these are both defined in the rest frame of the fluid, they are automatically comoving quantities.

To do the transformation, we can use the energy-momentum tensor for radiation, which is
$$
T^{\mu\nu}_\mathrm{rad} =
\left(
\begin{array}{c|c}
E &
\begin{array}{ccc}
 & \vec{F}/c & 
\end{array}
\\ \hline
\begin{array}{c} 
\\ \vec{F}/c \\ \\ 
\end{array} &
\begin{array}{ccc}
 & & \\
 & P_{ij} & \\
 & & 
\end{array}
\end{array}
\right),
$$
where $E$ is the radiation energy density, $\vec{F}$ is the flux, and $P_{ij}$ is the radiation pressure tensor (e.g. for isotropic radiation this would be $P_{ij}={1\over 3}E\delta_{ij}$).

Use the Lorentz transformation to show that the energy density in the comoving frame is 
$$E_r^\prime = E_r - {2\vec{v}\cdot\vec{F}_r\over c^2} + {\mathcal O}\left({v^2\over c^2}\right)$$
and use that to write down the equivalent of equation {eq}`eq:week11ex1` in the inertial frame. What is the physical interpretation of the extra term that appears?

## 4. Frequency-averaged opacities

In the notes, we assumed that the opacity was independent of the photon frequency (grey opacity), which allows us for example to write the radiation force as $\rho\kappa F/c$ where $\kappa$ is the grey opacity and $F$ the total radiative flux (integrated over frequency). In general, opacity will of course depend on the photon frequency so we should really be writing this as $\int d\nu \rho \kappa_\nu F_\nu/c$. We can still write this in the form $\rho\kappa F/c$ as long as we use an appropriate frequency-averaged opacity.

Look up the definitions of the Rosseland mean opacity, Planck mean opacity, and flux mean opacity.

Take a look at equations {eq}`eq:momwithrad`, {eq}`eq:energywithrad` from week 11 and equation {eq}`eq:radiativediffusion` from week 3. Explain which frequency-averaged opacity you would use in each case.

## 5. Stellar winds

In the CAK theory for stellar winds (Castor et al. 1975), the momentum equation is of the form
$$v{dv\over dr} = -{GM\over r^2} + {C\over r^2}\left({1\over \rho}{dv\over dr}\right)^\alpha,$$
where the last term describes the acceleration due to line driving. The parameter $\alpha$ lies between 0 and 1. For simplicity, we've neglected the pressure gradient term.

(a) Show that for given values of $v$, $r$, there are two positive solutions for the velocity gradient $dv/dr$. [Hint: you can do this graphically. Note that specifying $r$ and $v$ also specifies $\rho$ since $\dot M = 4\pi r^2\rho v$ is constant in a steady wind.]

(b) Next, find the condition for the two solutions to merge. This corresponds to a critical point of the wind. Show that at this point, the acceleration is
$$v{dv\over dr} = {\alpha\over 1-\alpha} {GM\over r^2}.$$

In a smooth wind solution, the velocity gradient transitions from one of the branches of the solution to the other at the critical point, where the two branches merge. In the full CAK theory, this adds a constraint that determines the wind mass loss rate.

(c) Show that the velocity profile
$$v = v_\infty\left(1- {R_\star\over r}\right)^{1/2}$$
satisfies the momentum equation, independent of the choice of $\alpha$.

Use the critical point condition from part (b) to show that the terminal velocity is
$$v_\infty^2 = {2\alpha\over 1-\alpha}{GM\over R_\star},$$
and hence obtain an expression for the mass loss rate in terms of $M$, $\alpha$ and $C$.
