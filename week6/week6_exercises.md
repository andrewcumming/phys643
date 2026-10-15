# Exercises

## 1. Adiabatic accretion

Show that the Bondi accretion rate for an adiabatic flow is
$$\dot M = {\pi (GM)^2\rho_\infty\over c_\infty^3} \left({2\over 5-3\gamma}\right)^{(5-3\gamma)/2(\gamma-1)}.$$

(Hint: first show that $\dot M = \pi (GM)^2 \rho_s/c_s^3$, where $c_s$ and $\rho_s$ are the sound speed and density at the sonic point. Then relate the conditions at the sonic point to those at infinity using the Bernoulli constant.)

Check that in the isothermal limit this reduces to the expression given in the notes.



## 2. Thermal equilibria of a thin disk

Write a short python code to calculate the thermal equilibria of a thin disk. To do this, you can balance the viscous heating rate $Q_+=\nu \Omega^2 \Sigma$ per unit area with the cooling rate $Q_-=\sigma_{SB} T_\mathrm{eff}^4$. Make a plot of the column depth $\Sigma_\mathrm{eq}(T)$ for which the disk is in thermal equilibrium at each temperature $T$. (Put the temperature on the $y$-axis and column depth on the $x$-axis.)

For the effective temperature, you can take $T_\mathrm{eff}^4 = T^4/\tau$ with optical depth $\tau\approx \kappa(\rho,T)\Sigma$ and density $\rho\approx \Sigma/H$. For the opacity, you can use the interpolation formula
$${1\over \kappa^2} = {1\over \kappa_{ff}^2} + {1\over (\kappa_{H^-}+\kappa_d)^2},$$
where the free-free opacity is $\kappa_{ff}=6.6\times 10^{22}\ \mathrm{cm^2\ g^{-1}}\ \rho T^{-7/2}$, appropriate for $T\gtrsim 10^4\ \mathrm{K}$ when hydrogen is ionized, and $\kappa_{H^-}= 2.5\times 10^{-31}\ \mathrm{cm^2\ g^{-1}}\ \rho^{1/2} T^9$ is the H$^-$ opacity that sets in at $T\lesssim 10^4\ \mathrm{K}$ when H$^{-}$ opacity dominates. To model the transition to dust opacity at low temperatures, we've added a contribution $\kappa_d = 0.1\ \mathrm{cm^2\ g^{-1}}$.

Consider a temperature range from $2000\ \mathrm{K}$ to $30,000\ \mathrm{K}$. You should be able to calculate the curve $\Sigma_\mathrm{eq}(T)$ using only the parameters $\Omega$ (angular velocity of the disk at the location you are considering), $\alpha$ (viscosity) and $\mu$ (mean molecular weight). Good values to try would be $\Omega = 2\pi/(1\ \mathrm{day})$, $\mu=0.6$, and $\alpha=0.1$.

You can use a root finder to solve for the $\Sigma$ where $Q_+-Q_-=0$ at each $T$. For example:
``` python
from scipy.optimize import brentq
def f(sigma, T):
    Q_plus = ...
    Q_minus = ...
    return Q_plus - Q_minus

def find_sigma(T):
    return brentq(f,1,1e4,args=(T,))
```


Questions to consider:
- what is the shape of the curve?
- on which side of the curve is $Q_+>Q_-$ and which side $Q_+<Q_-$? What would happen if a disk started off the curve somewhere, how would it evolve in time?

## 3. Magnetized accretion

(a) What strength magnetic field $B_\star$ would the central object need for accretion to be magnetically-controlled in the following cases:
- a neutron star accreting at the Eddington rate $\sim 10^{-8}\ M_\odot\ \mathrm{yr^{-1}}$ in a low mass X-ray binary,
- a white dwarf accreting at $\dot M\sim 10^{-10}\ M_\odot\ \mathrm{yr^{-1}}$ in a cataclysmic variable (CV),
- a young newly-forming gas giant planet accreting mass at $10^{-3}\ M_\oplus\ \mathrm{yr^{-1}}$,
- a young solar mass star accreting from a disk at $\sim 10^{-8}\ M_\odot\ \mathrm{yr^{-1}}$.

What do you conclude from your results?

(b) Calculate the orbital period of a Keplerian orbit at $r=r_M$ as a function of $B_\star$, $\dot M$, $M$, and the radius of the star $R_\star$. This is a lower limit to the spin period of the accreting star because if the star (and its magnetosphere) rotate faster than the Keplerian frequency at $r_M$, the accreting matter does not have enough angular momentum to attach to the magnetic field. (In this case, the matter is flung away in what is known as the "propeller" regime).

Do you think it likely that the objects you consider in part (a) would be formed spinning significantly below their breakup frequencies?

## 4. Two-temperature accretion

A black hole accretes from surrounding gas with density $\rho_\infty$ and sound speed $c_\infty$ at a rate given by the Bondi rate $\dot M = \pi (GM)^2 \rho_\infty/c_\infty^3$. Assume the flow is adiabatic ($T\propto \rho^{2/3}$). Investigate whether Coulomb collisions can effectively couple electrons and protons in the flow.

Hints:
* The collision rate between electrons and protons is $n\sigma v_e=1/t_\mathrm{coll}$, where $n$ is the proton density, $v_e$ is the electron velocity, and $\sigma$ is the Coulomb cross-section, roughly [given by](week1-reading)
$$\sigma\approx \pi {e^4\over (k_BT)^2}.$$
* You can get the density as a function of radius by using $\dot M = 4\pi r^2\rho v_{ff}=$ constant, where $v_{ff}\approx (2GM/r)^{1/2}$ is the free-fall velocity.
* The timescale to transfer energy from protons to electrons is 
$$t_E\approx \left({m_p\over m_e}\right)t_\mathrm{coll}$$ 
(can you see why this is true?)
* To assess whether electrons and protons couple to each other, you could compare the timescale $t_E$ with the free-fall timescale $t_{ff} = r/v_{ff}$.

## 5. Parker's argument for a wind

Here we'll work through Parker's argument that there must be a solar wind. He did this by showing that it is not possible to find a solution for the solar corona that is in hydrostatic balance.

(a) If the thermal conductivity $\kappa\propto T^n$, first argue that the temperature profile in the corona must be 
$$T(r) = T_0 \left({a\over r}\right)^{1/(1+n)}$$
if there are no energy sources in the corona beyond some radius $r=a$. (Hint: the heat flux is $-\kappa\vec{\nabla}T$.)

(b) Now assume hydrostatic balance with gravity $g=GM_\star/r^2$. Calculate the density and pressure profiles. A useful parameter is $\lambda=GM_\star/2k_BTa$.

(c) What happens to the pressure at large distances from the star? Do you agree with Parker that the hydrostatic solution doesn't work and there must be a wind?

## 6. The solar wind

Parker (1958) modelled the solar wind as an isothermal wind.

(a) Show that the velocity in the isothermal wind is given by
$$\left({v\over c_s}\right)^2 - \ln \left({v\over c_s}\right)^2 = 4\ln \left({r\over r_s}\right) + {4r_s\over r} -3.$$
(Hint: see equation [(6)](week6-reading#eq-isowind) in the notes).

(b) Considering temperatures from $0.5$ to $4$ million K, plot the wind velocity as a function of distance from the Sun. How far away from the Sun is the sonic point, and what is the solar wind speed you predict at Earth as a function of the wind temperature?
