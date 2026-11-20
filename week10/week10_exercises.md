# Exercises

## 1. Anisotropic currents

Consider a plasma with a constant magnetic field in the vertical direction, $\vec{B} = B_z \hat{z}$. An electric field is applied in the $x$-direction, $\vec{E}= E_x\hat{x}$. Calculate the current $\vec{J}$ that flows in response to the applied electric field.

What happens in the limits of small and large magnetic field?

We saw in Week 1 that the rate at which magnetic energy is dissipated is $\vec{J}\cdot\vec{E}$. Calculate the dissipation rate in this case at small and large magnetic field strength. Which component of the current dominates the dissipation in each case?

## 2. Dispersion measure

Consider a pulse of radio emission that travels from a neutron star at distance $d$ to Earth. Show that the intervening plasma causes a delay in the arrival of the pulse of
$$\Delta t\approx 3\ \mathrm{ms}\ \left({\mathrm{DM}\over \mathrm{pc\ cm^{-3}}}\right)\left({1\ \mathrm{GHz}\over \nu}\right)$$
where the **dispersion measure** is
$$\mathrm{DM} = \int_0^d d\ell\ n_e,$$
the electron density integrated along the line of sight.

Hint: use the group velocity from the cold plasma dispersion relation {eq}`eq:colddispersion`, neglect magnetic fields, and take the limit where $\omega\gg\omega_p$ (you can check whether this is a good approximation for the interstellar medium).






## 3. Rotation measure

Consider the propagation of radio waves in the magnetized interstellar medium, assuming $\omega\gg\omega_p$ and $\omega\gg \Omega_c$. Use the cold plasma dispersion relation {eq}`eq:dispersionb` to show that left-handed and right-handed waves travelling along the magnetic field have a difference in refractive index
$$\Delta n = n_+-n_-\approx  {\omega_P^2 \Omega_c\over \omega^3},$$
and therefore travel at different speeds.

Use this to show that a linearly-polarized wave that travels a distance $d$  will rotate its angle of polarization by an amount
$$\Delta \theta = {1\over 2}\int_0^d {d\ell\over c}{\Omega_c\omega_p^2\over \omega^2} = \mathrm{RM} \lambda^2,$$
where the quantity $\mathrm{RM}$ is known as the **rotation measure**, and $\Omega_c$ is the cyclotron frequency based on the line-of-sight magentic field.


## 4. Estimate $\Omega\tau$ in astrophysical environments

Estimate $\Omega\tau$ for some different astrophysical environments, e.g. the solar wind, centre of the Sun, hot gas in a cluster of galaxies, interstellar medium. If you are not sure what magnetic field strength to take, you could calculate instead what magnetic field strength would be required for $\Omega\tau$ to exceed 1.

