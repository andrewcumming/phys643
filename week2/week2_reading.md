# Week 2: Cold stars

We're going to  start the course by discussing objects in hydrostatic balance such as stars and planets. This week we will first focus on "cold stars", which encompasses white dwarfs, neutron stars, and planets. These are objects with barotropic equations of state, ie. pressure only depends on density $P(\rho)$. This allows us to solve for the hydrostatic structure by solving only the mass and momentum conservation equations, without having to worry about energy transport and the temperature profile inside the star. (We'll move onto "hot stars" next week).

Before we get to these cold objects specifically, we'll first discuss some general properties of objects in hydrostatic balance and equations of state.

## Hydrostatic balance

Stars and planets are in *hydrostatic balance* in which the pressure gradient from their interior to the surface balances their self-gravity. To see that must be the case, look at the momentum equation
$${D\vec{u}\over D t} = {-\vec{\nabla} P\over\rho}+\vec{g},$$
and imagine turning off the pressure gradients. The fluid would then accelerate in response to gravity. The time to collapse would be $\sim \sqrt{R/g}\sim \sqrt{R^3/GM}$, or about 30 minutes for the Sun, much less than its 5 billion year age. This implies the pressure gradient must balance gravity to a high degree of accuracy!

Assuming spherical symmetry, the momentum equation in this situation is
\begin{equation}\label{eq:cold1}
{dP\over dr} = -{Gm\rho\over r^2}
\end{equation}
where 
\begin{equation}\label{eq:cold2}
{dm\over dr} = 4\pi r^2\rho
\end{equation}
and $m(r)$ is the mass contained within radius $r$. The boundary conditions are $m=0$ at $r=0$ and $P=0$ at $r=R$.

To solve the equations, we need a relation between $P$ and $\rho$ — the equation of state. Under the assumption $P\propto \rho^\gamma$, the solutions are known as *polytropes*. A polytrope of index $n$ has $\gamma = 1 + {1\over n}$. 

## Back of the envelope stars and planets

We can make an estimate of the structure to get the scalings by writing $${dP\over dr}\approx {P_c\over R}$$ and $$\rho g\approx {M\over R^3}{GM\over R^2},$$ where $P_c$ is the central pressure and $R$ is the radius. This gives a formula for the central pressure in terms of the mass and radius of the object $$P_c\approx {GM^2\over R^4}.$$ Note that we've dropped prefactors of order unity here so this is just a rough estimate (we'll see later that polytropes have exactly this scaling but with a numerical prefactor that depends on $n$).

For an ideal gas of hydrogen, we can write the pressure as $P=\rho k_BT/m_p$. Using the formula for $P_c$ and again writing $\rho\approx M/R^3$ gives the central temperature $$T_c\approx {GMm_p\over k_BR}.$$ For the Sun, this gives $T_c\approx 2\times 10^7\ \mathrm{K}$ which is close to the actual value $\approx 1.5\times 10^7\ \mathrm{K}$.

For a polytropic scaling $P\propto\rho^\gamma$, we can get the mass-radius scaling since
\begin{eqnarray}
P_c\approx {GM^2\over R^4}\propto \rho^\gamma\propto \left({M\over R^3}\right)^\gamma\\\Rightarrow M^{\gamma-2}\propto R^{3\gamma-4}.\label{eq:MRscaling}
\end{eqnarray}

There are several interesting cases that we'll discuss in more detail later:

- *White dwarf mass-radius relation*. For non-relativistic degenerate electrons, $P\propto \rho^{5/3}\Rightarrow \gamma=5/3\Rightarrow R\propto M^{-1/3}$. White dwarfs have the interesting property that their radius decreases with increasing mass (the opposite is true of main sequence stars for example).
- *Chandrasekhar mass*. At large enough masses, the electrons become relativistic and $\gamma\rightarrow 4/3$. In that case, equation {eq}`eq:MRscaling` gives the result that $M$ is independent of $R$! The corresponding mass is the Chandrasekhar mass $M_\mathrm{Ch}\approx 1.4\ M_\odot$, a maximum mass for white dwarfs.
- *Neutron stars*. A neutron star is held up by degenerate neutrons, but interactions between neutrons stiffen the EOS (i.e. steepen the pressure-density relation), giving $\gamma\approx 2$. For this value of $\gamma$, equation {eq}`eq:MRscaling` gives $R$ independent of $M$. This is indeed seen in realistic calculations of neutron stars, which have very similar radii across a wide range of mass.
- *Incompressible material.* In the incompressible limit, $\gamma\rightarrow\infty$ and equation {eq}`eq:MRscaling` gives $M\propto R^3$, which is what we would expect for a constant density. This kind of scaling should hold for small "rocky" bodies such as moons or rocky planets.  (We'll see later that gas giant planets like Jupiter lie between the $M\propto R^3$ and $M\propto R^{-3}$ limits.)
- *Isothermal sphere*. Another limit that is often used to model stellar systems such as globular clusters is the isothermal case $P\propto\rho$ or $\gamma=1$ in which case $M\propto R$. 

## Equation of state of a Fermi gas

We now turn to the equation of state, and in particular consider an ideal gas of fermions. This section will mostly be a review of things you have probably seen in statistical mechanics, although we do have to be careful because we need to consider the possibility that particle velocities can become relativistic.

The starting point is the density of states. Quantum mechanics tells us that the density of states in the six-dimensional phase space of position and momentum is $$dn = {d^3\vec{x} d^3\vec{p}\over h^3}.$$ The number of states with energy between $E$ and $E+dE$ is therefore
$$g(E)dE = {2\over h^3} {4\pi p^2} {dp\over dE} dE$$
per unit spatial volume. The factor of 2 in the first term is to account for the two spin states (we assume spin 1/2 particles such as electrons). We also have assumed the gas is isotropic, so that $d^3\vec{p}$ can be written as $4\pi p^2 dp$. We need to consider arbitrary relativity, ie. particle velocities ranging from $v\ll c$ to $v\sim c$, so to evaluate $dE/dp$ we should use the relativistic relation $E^2 = (pc)^2 + (mc^2)^2$. This gives $${dE\over dp} = {pc^2\over E} = {\gamma m v c^2\over \gamma mc^2} = v.$$

Putting this all together gives the density of states $$g(E) = {8\pi p^2\over h^3v}.$$ For a Fermi gas, the occupation number of the state with energy $E$ is $$f(E) = {1\over 1+e^{(E-\mu)/k_B T}},$$
where $\mu$ is the chemical potential.
We can then calculate properties of the gas by summing over the different states. For example, the number density of particles is
$$n = \int f(E) g(E) dE\label{eq:nintegral}$$
or the internal energy density is
$$U = \int E f(E) g(E) dE.\label{eq:Uintegral}$$
The pressure is
$$P = \int f(E) g(E) dE {1\over 4\pi}\int_{-1}^1 d(\cos\theta) (p\cos\theta)(v\cos\theta)$$
(ie. averaging the momentum flux across a unit area) or
$$P = {1\over 3} \int p v f(E) g(E) dE.\label{eq:Pintegral}$$

With these results in hand we can now look at the equation of state in different limits.

### Non-degenerate gas of non-relativistic particles

For a non-degenerate gas, the chemical potential is large and negative. The exponential term in the denominator of $f(E)$ dominates, simplifying the integral for $n$ to 
$$n = \int {8\pi p^2\over h^3 v} e^{\mu/k_BT} e^{-E/k_BT} dE$$
which corresponds to a Maxwell-Boltzmann distribution of particle energies, $f(E)\propto \exp(-E/k_BT)$. Doing the integral then gives an expression for the chemical potential in terms of the number density $$\mu = k_BT \ln\left({n\over 2n_Q}\right)$$ where "n-quantum" is $$n_Q = \left({2\pi mk_BT\over h^2}\right)^{3/2}.$$
The non-degenerate limit applies when $n\ll n_Q$, giving $\mu/k_BT\ll -1$.

It is straightforward to show that equations {eq}`eq:Pintegral` and {eq}`eq:Uintegral` give the usual results for an ideal gas $$P=nk_BT \hspace{1cm} U = {3\over 2}nk_BT.$$
Pressure and internal energy density are related by $P=(2/3)U$, a consequence of the fact that we've assumed the particles are non-relativistic. Writing $U = nm\langle v^2\rangle/2$ gives $\langle v^2\rangle = 3k_BT/m$. The mean speed is $\langle v\rangle = (8k_BT/\pi m)^{1/2}$.

### Completely-degenerate gas

For a degeneratue gas, the chemical potential is large and positive, $\mu \gg k_BT$. The occupation number $f(E)$ becomes a step function: $f(E) = 1$ for $E<\mu$ and $f(E)=0$ for $E>\mu$, i.e. only the states with energy below the chemical potential are occupied. In this limit, $\mu$ is referred to as the *Fermi energy* $E_F$. 

In this case, it is simplest to write equation {eq}`eq:nintegral` as an integral over momentum rather than energy, giving
$$n = \int_0^{p_F} {8\pi p^2 dp\over h^3} = {1\over 3\pi^2}\left({p_F\over \hbar}\right)^3.$$
Here $p_F$ is the Fermi momentum. The Fermi wavevector $k_F = p_F/\hbar$ is $$k_F = (3\pi^2 n)^{1/3}$$ (this is a useful result to remember!).

The Fermi energy can then be calculated from the Fermi momentum using $E^2 = (pc)^2 + (mc^2)^2$. In the non-relativistic limit, $$E_F = {p_F^2\over 2m}\propto n^{2/3}.$$ In the relativistic limit, $$E_F = p_Fc\propto n^{1/3}.$$

The pressure is $P=(2/5) nE_F\propto n^{5/3}$ in the non-relativistic limit; $P=(1/4)nE_F\propto n^{4/3}$ in the relativistic limit. The internal energy density is $U = (3/5)nE_F = (3/2)P$ in the non-relativistic limit; $U = (3/4)nE_F = 3P$ in the relativistic limit. Notice that these expressions are similar to those for an ideal gas, but with $E_F$ replacing $k_BT$. For a degenerate gas, the Fermi energy $E_F$ sets the scale of particle energies, not $k_BT$.

### Partially-degenerate gas

Inside compact objects, there is a transition from non-degenerate matter in the low density regions at the surface to degenerate matter at high densities. Calculating this transition requires evaluating the integrals for $n$, $P$, and $U$ directly including the full form of $f(E)$ without approximations. For non-relativistic particles, the integrals can be written in terms of the *Fermi integrals* $F_n(\mu/k_BT)$ where $$F_n(x) = \int_0^\infty {t^n dt\over 1+e^{t-x}},$$ giving
$$n = {\sqrt{2}(mk_BT)^{3/2}\over \hbar^3\pi^2} F_{1/2}(\mu/k_BT)$$
$$U = {\sqrt{2}(mk_BT)^{3/2}\over \hbar^3\pi^2} F_{3/2}(\mu/k_BT)$$
and $P=(2/3)U$. [Antia (1993)](https://ui.adsabs.harvard.edu/abs/1993ApJS...84..101A/abstract) provides some useful fitting formulae for the Fermi integrals in case you ever find yourself in the partially-degeneragte limit. There is also a useful interpolation formula by [Paczynski (1983)](https://ui.adsabs.harvard.edu/abs/1983ApJ...267..315P/abstract) that we will use later.

In the non-degenerate or degenerate limits these reduce to the expressions we found earlier. If we also want to include arbitrary degrees of relativistic motion, the Fermi integrals then depend on an additional parameter $k_BT/mc^2$ (you can find more details in [Chabrier \& Potekhin (1998)](https://ui.adsabs.harvard.edu/abs/1998PhRvE..58.4941C/abstract)).

## A mixture of ions, electrons and radiation

In the last section we looked at a Fermi gas and the non-degenerate and degenerate limits. In general in an astrophysical plasma we will have a mixture of electrons, ions of different species, and radiation. Each of these provides a contribution to the pressure, so we would write the total pressure as $$P = P_\mathrm{ions} + P_e + P_\mathrm{rad}.$$ The radiation pressure is given by $P_\mathrm{rad} = (1/3)aT^4$ with the radiation constant $a=7.5657\times 10^{-15}\ \mathrm{cgs}$. The corresponding radiation energy density is $U_\mathrm{rad} = 3P = aT^4$. To calculate the ion and electron contributions to the pressure, we just need a way to work out the number density of the different species.

To keep track of the number densities of different species, we define mean molecular weights ($\mu$'s) and number fractions ($Y$'s) as follows. The mean molecular weight per electron $\mu_e$ relates the mass density and the number density of electrons: $$\rho = \mu_e n_e m_p$$ (you can think of $\mu_e$ as the effective mass measured in proton masses that each electron would have to have to make up the entire mass density). The corresponding number fraction is $Y_e = 1/\mu_e$, i.e. $$\rho Y_e = n_e m_p.$$
In a similar way, we can define a mean molecular weight and number fraction for each ion species $i$: $$\rho = \mu_i n_i m_p; \hspace{1cm} \rho Y_i = n_i m_p; \hspace{1cm} Y_i = 1/\mu_i.$$ Another useful quantity is the mass fraction of species $i$ defined by
$$\rho X_i = n_i A_i m_p,$$ where $A_i$ is the mass of species $i$ measured in proton masses (e.g. carbon $^{12}C$ would have $A=12$). The number fraction and mass fraction are related by $Y_i = X_i/A_i$.

As an example, consider a fully-ionized solar composition gas with hydrogen mass fraction $X_H=0.7$ and helium mass fraction $X_{He}=0.3$. The ion pressure is 
$$P_{\rm ion} = n_H k_BT + n_{He} k_BT = {\rho k_B T\over m_p}\left(X_H+{X_{He}\over 4}\right)={\rho k_B T\over \mu_\mathrm{ion} m_p},$$
which defines $\mu_{\rm ion} = (X_H + X_{He}/4)^{-1}\approx 1.3$. For a general mixture of ions, $$Y_{\rm ion}={1\over \mu_{\rm ion}} = \sum Y_i = \sum {X_i\over A_i}.$$
The electrons contribute $P_e=n_ek_BT$ to the pressure if they are non-degenerate. From charge neutrality, $n_e = \sum n_iZ_i$ and so $$P_e = {\rho k_B T\over m_p}\sum Y_i Z_i = {\rho k_B T\over m_p}\sum {X_iZ_i\over A_i} = {\rho k_B T\over \mu_e m_p}.$$ For the H/He mixture, we infer $\mu_e=(X_H+X_{He}/2)^{-1}\approx 1.2$. The total pressure is $$P = (n_e+n_H+n_{He})k_BT = {\rho k_B T\over m_p}\left({1\over \mu_{\rm ion}}+{1\over \mu_e}\right)={\rho k_B T\over \mu m_p}.$$
This defines the mean molecular weight $\mu^{-1}=\mu_e^{-1}+\mu_{\rm ion}^{-1}$. For the solar mixture, $\mu^{-1}=2X_H+3X_{He}/4$ giving $\mu\approx 0.6$. 

Pure H has $\mu_e=\mu_i=1$ and $\mu=1/2$. Pure He has $\mu_e=2$, $\mu_i=4$, and $\mu=4/3$. Heavier elements than helium also have $\mu_e\approx 2$ since $A\approx 2Z$ for all nuclei except hydrogen.

**To summarize**, the mean molecular weights allow you to compute the number density of a particular species from the mass density: $n_i = \rho / (\mu_i m_p)$. If you know the mass fractions of the different ion species $X_i$ (which all add up to 1), the nuclear masses and charges $A_i$ and $Z_i$, then the mean molecular weight for species $i$ is given by 
$${1\over \mu_i} = {X_i\over A_i}$$ and the mean molecular weight per electron is 
$${1\over \mu_e} = \sum_i {Z_i X_i\over A_i}.$$

## The $\rho$-$T$ plane

To give you a feeling for some numbers, the following figure maps out where in the $\rho$--$T$ plane matter is non-degenerate, degenerate, non-relativistic or relativistic, or (at high temperatures) where radiation pressure dominates:

```{figure} rhoT.pdf
```

(the composition here is assumed to be pure helium).

Electrons become degenerate when $E_F\approx k_BT$, shown as the dashed line in the plot. For non-relativistic electrons, this is given by $${\hbar^2\over 2m_e}\left(3\pi^2n_e\right)^{2/3}\approx k_BT\Rightarrow T_{d,nr} \approx 3\times 10^5\ {\rm K}\ (\rho Y_e)^{2/3},$$ using $n_e=\rho Y_e/m_p$. Degenerate electrons become relativistic when $$p_F=\hbar(3\pi^2n_e)^{1/3}\approx m_e c\Rightarrow \rho Y_e \approx 10^6\ {\rm g\ cm^{-3}},$$ which is the vertical dotted line in the plot. The dashed line shown in the plot takes relativity into account by writing  
$$E_F=m_ec^2\left(\sqrt{1+x^2}-1\right)\approx k_BT$$ where $x=p_F/m_ec\approx (\rho Y_e/10^6\ {\rm g\ cm^{-3}})^{1/3}$; notice it changes slope at $\rho\gtrsim 10^6\ {\rm g\ cm^{-3}}$ once the electrons become relativistic.

The solid curve shows the boundary between radiation pressure $(1/3)aT^4$ and gas pressure, assuming the gas pressure is ideal:
$${1\over 3}aT^4 = {\rho k_BT\over \mu m_p}\Rightarrow T_{\rm rad} = \left({3\rho k_B\over \mu m_p a}\right)^{1/3}\approx 3\times 10^7\ {\rm K}\ \left({\rho\over \mu}\right)^{1/3}.$$\
At high temperatures $T>T_\mathrm{rad}$, radiation pressure dominates over gas pressure.


## White dwarf mass-radius relation

White dwarfs are stars held up by degenerate electron pressure [^ionpressure]. For low masses, the electrons are non-relativistic so that $P\propto \rho^{5/3}$, but as the mass approaches the Chandrasekhar mass the electrons become more and more relativistic and $\gamma\rightarrow 4/3$.

[^ionpressure]: The ions also have a pressure, but it is much smaller than the electron pressure. That is because the ions are non-degenerate, so their pressure is a factor $\sim k_BT/E_F$ times smaller.

As we mentioned earlier, the solutions of the stellar structure equations {eq}`eq:cold1` and {eq}`eq:cold2` for $P\propto\rho^\gamma\propto \rho^{1 + 1/n}$ are known as polytropes. You can look up the properties of polytropes for different values of polytropic index $n$, in particular the numerical solutions give the values of $$\alpha_n = {P_c\over GM^2/R^4}\hspace{1cm}\beta_n = {\rho_c\over \langle \rho\rangle},$$ where $\langle\rho\rangle = 3M/4\pi R^3$ is the mean density. For $\gamma=5/3$, $n=3/2$, $\alpha=0.77$ and $\beta=5.99$. For $\gamma=4/3$, $n=3$, $\alpha = 11.1$ and $\beta = 54.2$.

To get the white dwarf mass--radius relation, we write  the equation of state at the center as $P_c=K_{nr}\rho_c^{5/3}$,
where
\begin{eqnarray}
K_{nr}&=&{P\over \rho^{5/3}} = {2\over 5}{n E_F\over \rho^{5/3}} = {2\over 5}{n\over \rho^{5/3}}{p_F^2\over 2m}={2\over 5}{\hbar^2(3\pi^2)^{2/3}\over 2m}\left({n\over \rho}\right)^{5/3}\nonumber\\ &=& 9.9\times 10^{12}\ {\rm cgs}\ Y_e^{5/3}.
\end{eqnarray}
Then using the $n=3/2$ polytrope results for $\alpha$ and $\beta$ gives the white dwarf mass-radius relation at low masses
\begin{eqnarray}
R_{5/3} &=& M^{-1/3} \left({K_{nr}\over \alpha_{3/2} G}\right)\left({3\beta_{3/2}\over 4\pi}\right)^{5/3}\nonumber\\
&\approx 9\times 10^8\ {\rm cm}\ \left({M\over M_\odot}\right)^{-1/3}\left({Y_e\over 0.5}\right)^{5/3}.
\end{eqnarray}
(We write $R_{5/3}$ to indicate that this is the white dwarf radius assuming $\gamma=5/3$). As the star gets more massive, the radius shrinks. The central density increases rapidly with mass, $\rho_c\propto M/R^3\propto M^2$.

Doing the same thing for the equation of state $P_c=K_r\rho_c^{4/3}$, the radius drops out and we get an expression for the Chandrasekhar mass
$$M_\mathrm{Ch} = \left({K_r\over \alpha_3 G}\right)^{3/2}\left({3\beta_3\over 4\pi}\right)^2 = 1.45\ M_\odot\ \left({Y_e\over 0.5}\right)^2.$$
We can interpolate between the two limits by using the fitting formula obtained by [Paczynski (1983)](https://ui.adsabs.harvard.edu/abs/1983ApJ...267..315P/abstract) for the pressure of degenerate electrons 
\begin{equation}
P_e^{-2}\approx P_{e,nr}^{-2}+P_{e,r}^{-2},
\end{equation}
which interpolates between non-relativistic and relativistic electrons (and Pacynski found was accurate to a few percent). If you use this formula for the central pressure, you will find 
$$R\approx R_{5/3}\left[1-\left({M\over M_\mathrm{Ch}}\right)^{4/3}\right]^{1/2}.$$
Here is a plot of this $M(R)$ relation:

```{figure} wd.pdf
```

As the mass approaches the Chandrasekhar mass, the central density increases dramatically (because of decreasing radius but also the increasing value of $\beta_n$ as $\gamma\rightarrow 4/3$, see above). Once it gets to $\rho_c\sim 10^9\ {\rm g\ cm^{-3}}$, interesting things can happen. One possibility is carbon fusion leading to a Type Ia supernova. The other is that electrons can capture into the nuclei, removing pressure support and leading to collapse to a neutron star. White dwarfs can reach these large masses either through merging or accretion, or through stellar evolution, e.g. the iron core of a massive star.


## Neutron stars

We saw that the radius of a $\gamma=5/3$ star is $R\propto M^{-1/3} K_{nr}$. The key point for neutron stars is that $K_{nr}\propto 1/m$ where $m$ is the mass of the degenerate particle. For white dwarfs this is the electron mass; for neutron stars, the star is held up by degenerate neutron pressure and we should take $m=m_n$ the neutron mass. We therefore expect the radius of a neutron star to be smaller than a white dwarf by a factor of $m_n/m_e\approx 2000$, or $R_{NS}\sim 10^9 {\rm cm}/2000\approx 5\ {\rm km}$. This is about right. Detailed models give neutron star radii $\approx 10$-$13\ {\rm km}$. They are a little larger because the neutrons repel each other when they are very close, so that the equation of state is stiffer than $\gamma=5/3$, in fact closer to $\gamma\approx 2$. As we argued in the beginning, this gives radius almost independent of mass, which is seen in detailed calculations of mass-radius relations.

## Coulomb pressure and planets

If you plug in Jupiter's mass $M_J\approx 10^{-3}M_\odot$ into the white dwarf mass-radius relation $R\propto M^{-1/3}$, you'll get a radius $\approx 10^{10}\ {\rm cm}$ which is not too far off Jupiter's radius ($1\ R_J\approx 0.1\ R_\odot\approx 7\times 10^9\ {\rm cm}$). But clearly, as we reduce mass further something else must happen: planets less massive than Jupiter have smaller radii than Jupiter not larger radii! What if instead of scaling down in mass, we scale up in mass? If we scale up from the Earth assuming the same density ($M\propto R^3$) then that is also not so far off — Jupiter is about 10 times the radius of Earth and about 300 times the mass [^earthscale]. This tells us that somehow the mass-radius relation must turnover and change from $M\propto R^{-3}$ to $M\propto R^3$ at approximately Jupiter's mass. 

[^earthscale]: I'm ignoring factors from composition differences here. Earth is about 4 times denser than Jupiter, and the $Y_e$ in a white dwarf is $\approx 0.5$ whereas Jupiter is mostly hydrogen so will have $Y_e$ closer to 1.

What happens is that the Coulomb attraction of the positive ions and electrons in the plasma becomes important, leading to a negative contribution to the pressure, the *Couloumb pressure*. To calculate the size of this effect, first note that it is a good approximation to assume the electrons in the plasma are uniformly distributed in space because $E_F\gg Ze^2/a$ where $a$ is the interion spacing, so the electrons barely notice the ions. Then we can use the Wigner-Seitz approximation to calculate the energy associated with each ion. In this approximation, we consider an electrically-neutral sphere of radius $R_Z$ around each ion that contains $Z$ electrons, ie. $(4\pi R_Z^3/3)n_e=Z$. The electrostatic energy of the sphere can then be calculated using simple electrostatics (e.g. you might remember calculating the energy of a  uniformly-charged sphere in your E&M class). There are two contributions:
$$U_{ee}={3\over 5}{(Ze)^2\over R_Z}\hspace{1cm}\mathrm{electron-electron\ repulsion}$$
$$U_{ei}=-{3\over 2}{(Ze)^2\over R_Z}\hspace{1cm}\mathrm{electron-ion\ attraction}.$$
Adding these gives the total energy per unit volume
$$U_C = -n_e {9\over 10}{Ze^2\over R_Z} = -{9\over 10}\left({4\pi\over 3}\right)^{1/3}Z^{2/3}e^2n_e^{4/3}$$
(where I used $n_i = n_e/Z$).
Notice that $U_C$ becomes more negative as density increases, giving a negative pressure! The pressure is $-\partial (U_CV)/\partial V$ for volume $V$, giving $P_C = (1/3)U_C$ or $$P_C \approx - 6\times 10^{12}\ {\rm erg\ cm^{-3}}\ (\rho Y_e)^{4/3} Z^{2/3}.\label{eq:PC}$$
This pressure needs to be added to the electron pressure to compute the total pressure of the gas.

The fact that $P_C$ is negative has the interesting consequence that the density does not go to zero as we take the pressure to zero: there is a *zero pressure solid*. The total pressure from electrons and Coulomb is
\begin{equation}
P_{\rm tot} = K_e \rho^{5/3} - K_C\rho^{4/3}.
\end{equation}
There is a zero-pressure solution  with density
$$\rho_0 = \left({K_C\over K_e}\right)^3 \approx 0.2\ {\rm g\ cm^{-3}}\ ZA.$$ This overpredicts the density of terrestrial metals: for example, copper has $A\approx 64$ and $Z=29$, giving $\rho_0\sim 300\ {\rm g\ cm^{-3}}$ (actual density is $9\ {\rm g\ cm^{-3}}$), but the electronic configuration is much more complex than we have assumed in our simple model.  The important point is that we have found a self-bound state which exists without any confining pressure. This suggests that at low masses we should see $M\sim\rho_0 R^3$.

We can use the extra contribution to the pressure to derive a modified mass-radius relation. 
Follow the approach we used earlier to derive a "back of the envelope" mass-radius relation, but now include a third term representing Coulomb pressure:
$${GM^2\over R^4} \approx K_e\left({M\over R^3}\right)^{5/3} - K_C\left({M\over R^3}\right)^{4/3}.$$
Solving for $R$, we get
$$R = {K_e\over GM^{1/3}+K_CM^{-1/3}}.$$
The two limits are $R=(K_e/G) M^{-1/3}$ "white dwarf" and $R=(K_e/K_C)M^{1/3}$ "rock". The maximum radius is where $M=(K_C/G)^{3/2}\approx 0.4\ M_J$. 

The interplay between degeneracy pressure and Coulomb pressure, leading to the turnover of the $R(M)$ relation, is the reason why the radii of brown dwarfs are about the same as Jupiter, despite being $30$-$100$ times more massive!









