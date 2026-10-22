# Week 7: Oscillations and instabilities

We've already seen two examples of waves in a fluid system: [sound waves](week4-reading#sound-waves) in a uniform gas, and [fast and slow magnetosonic waves](week4-reading#fast-and-slow-magnetosonic-waves) and Alfvèn waves in a magnetized plasma. Here I go through two cases of linear stability analysis as examples of more complex situations: first what happens when we include the energy equation explicitly for sound waves, and second how to deal with a background that has a gradient, using a plane-parallel atmosphere as an example. We will see that the plane-parallel atmosphere has a new type of wave (gravity wave) as well as an instability (convection).

## Sound waves with thermal conduction

Earlier, we derived the dispersion relation for sound waves by assuming a relation between the pressure and density perturbations $$\delta P = {\partial P\over \partial \rho} \delta \rho = c_s^2 \delta \rho.$$
The partial derivative can be taken at constant entropy, in which case $c_s^2 = \gamma P/\rho$ is the adiabatic sound speed, or at constant temperature, giving the isothermal sound speed $c_s^2=P/\rho = k_BT/\mu m_p$. These two cases can be understood as limits of either very inefficient heat transfer (adiabatic) or efficient heat transfer (isothermal) on the timescale of the sound wave period ($2\pi/\omega = 2\pi/c_sk = \lambda/c_s$). 

Instead of making one of these assumptions, let's instead include the energy equation in the calculation and see if we can find a relation between $\delta P$ and $\delta \rho$ that is valid inbetween these two limits. We will assume ideal gas, in which case the pressure, density and temperature perturbations are related by 
\begin{equation}\label{eq:idealgas}
{\delta P\over P} = {\delta \rho\over \rho} + {\delta T\over T}	
\end{equation}
(since $P\propto \rho  T$). 
The entropy equation is 
$$T{Ds\over Dt} = -{1\over\rho} \vec{\nabla}\cdot\vec{F} = {1\over \rho} \vec{\nabla}\cdot \left(K\vec{\nabla} T\right),$$ where $K$ is the thermal conductivity (we will assume this is a constant). 

Perturbing the entropy equation with perturbations $\propto e^{i\omega t}e^{-ikx}$ gives
\begin{equation}\label{eq:entropy}
-i\omega T\delta s = - {k^2 K \delta T\over \rho}
\end{equation}
(the background is stationary, so only the time derivative term of $D/Dt$ contributes at linear order). We can use this to eliminate $\delta T$ and derive the relation between $\delta P$ and $\delta \rho$. To do this, write
\begin{equation}
\label{eq:ds1}Tds = T\left.{\partial s\over \partial T}\right|_P dT + T\left.{\partial s\over \partial P}\right|_T dP.
\end{equation}
We then use the fact that $T\left.\partial S/\partial T\right|_P = c_P$ the heat capacity at constant pressure, the identity
$$\left.{\partial s\over \partial P}\right|_T \left.{\partial P\over \partial T}\right|_s \left.{\partial T\over \partial s}\right|_P = -1$$
(which you may remember from your thermodynamics course), and the adiabatic index
$${\gamma-1\over \gamma} = \left.{\partial \ln T\over \partial \ln P}\right|_s$$ to rewrite equation {eq}`eq:ds1` as
\begin{equation}
	T ds = c_p\left( dT - {\gamma-1\over \gamma} {T\over P} dP\right).
\end{equation}
This allows us to write down $\delta s$ in terms of $\delta T$ and $\delta P$. Equation {eq}`eq:entropy` then gives
$$c_PT\left({\delta T\over T}- {\gamma-1\over \gamma} {\delta P\over P}\right) = {k^2 K T\over i\omega\rho}\left({\delta T\over T}\right).$$ 
Using the ideal gas relation from equation {eq}`eq:idealgas` to eliminate $\delta T$ in favour of $\delta P$ and $\delta\rho$, we find
\begin{equation}\label{eq:boxed}
\boxed{{1\over \gamma}{\delta P\over P} - {\delta \rho\over \rho} = {k^2K\over i\omega \rho c_P}\left({\delta P\over P} -{\delta \rho\over \rho}\right)}	
\end{equation}

I've put a box around this result because it is the relation between $\delta P$ and $\delta \rho$ that we've been looking for. The quantity $D = K/\rho c_P$ is the thermal diffusivity (units of ${\rm cm^2/s}$), since we can write
$$T{Ds\over Dt} = c_P{DT\over Dt} = {K\over \rho} \vec{\nabla}^2 T\Rightarrow {DT\over Dt} = {K\over \rho c_P} \vec{\nabla}^2 T = D \vec{\nabla}^2 T$$
(working at constant pressure for simplicity and again assuming constant $K$). The thermal timescale associated with the perturbation is therefore $1/(k^2D)$. When the mode frequency $\omega$ is either large or small compared with $k^2D$, we recover the adiabatic or isothermal limits discussed earlier.  However, in general, we see that the relation between $\delta P$ and $\delta \rho$ has a complex prefactor. The dispersion relation is
$${\omega^2\over k^2} = c_s^2 = {\gamma P\over\rho} \left({i\omega -k^2D\over i\omega -\gamma k^2 D}\right).$$ In general we see that $k^2$ will be complex, so that for a given $\omega$ there will be a propagating wave (real part of $k$) but with a decaying amplitude (imaginary part of $k$). 

I will leave this as an exercise, but for example one limit to consider is when the wave is *almost* adiabatic, so that $k=k_R + i k_I$ with $k_I\ll k_R$. In this limit, $\omega^2\approx k_R^2 c_{\rm ad}^2$, where $c_{\rm ad}$ is the adiabatic sound speed, and $${k_I\over k_R} \approx {\gamma-1\over 2}{k_R^2D\over \omega} \approx {\gamma-1\over 2}{\omega D\over c_{\rm ad}^2}.\label{eq:kIkR}$$
For air, $c_s\approx 330\ {\rm m\ s^{-1}}$ and $D\approx 2\times 10^{-5}\ {\rm m^2/s}$, giving a decay length of about $10^6$ wavelengths.

## Gravity waves and convection in an atmosphere

As a second example, let's look at the waves in a plane-parallel atmosphere. The additional ingredient here is gravity, since the atmosphere is in hydrostatic balance $${dP\over dz} = - \rho g$$ so that there are background pressure, density and temperature gradients.

When dealing with problems with background gradients, it can be useful to write things in terms of Lagrangian perturbations. The perturbations we have been writing down so far are Eulerian, since at any given time $t$ they give the difference between the perturbed and unperturbed flows at the same point in space, e.g.
$$\delta \rho\left(\vec{r}, t\right) = \rho\left(\vec{r}, t\right) - \rho_0\left(\vec{r}, t\right),$$
where $\rho$ is the perturbed density and $\rho_0$ is the unperturbed density. Instead we could define the Lagrangian perturbation 
$$\Delta \rho\left(\vec{x_0}, t\right) = \rho\left(\vec{r}(\vec{x_0},t), t\right) - \rho_0\left(\vec{r_0}(\vec{x_0},t), t\right),$$
where $\vec{x_0}$ is a Lagrangian label that identifies the fluid element, for example a good choice would be the initial location of the fluid element. The difference in the positions of the fluid element in the unperturbed flow $\vec{r_0}(\vec{x_0},t)$ and perturbed flows $\vec{r}(\vec{x_0},t)$ is the Lagrangian displacement 
$$\xi = \vec{r}(\vec{x_0},t)-\vec{r_0}(\vec{x_0},t).$$ The Eulerian and Lagrangian perturbations at a particular spatial location $\vec{r}$ are related by
$$\Delta \rho\left(\vec{r}(\vec{x_0},t), t\right) - \delta \rho\left(\vec{r}, t\right) = -\rho_0\left(\vec{r_0}(\vec{x_0},t), t\right)+\rho_0\left(\vec{r}, t\right)\approx \xi\cdot \vec{\nabla} \rho_0(\vec{r}),$$
or 
$$\boxed{\Delta\rho = \delta \rho + \xi\cdot \vec{\nabla} \rho}$$
As an application, consider the perturbed continuity equation
$$-i\omega\delta\rho = -\vec{\nabla}\cdot\left(\rho \delta \vec{v}\right).$$
We assume $\vec{v}=0$ in the background, in which case we can also write
$$\delta \vec{v}  = {\partial \xi\over\partial t} = -i\omega \xi$$
and so
$$\delta\rho = -\vec{\nabla}\cdot\left(\rho\xi\right) = -\rho \vec{\nabla}\cdot \xi - \xi\cdot\vec{\nabla}\rho$$
\begin{equation}\label{eq:continuitypert}\Rightarrow \boxed{ {\Delta\rho\over\rho} = -\vec{\nabla}\cdot\xi}\end{equation}
If the Lagrangrian displacements have a non-zero divergence, it implies a Lagrangian density change. Note that if the background is moving then $\delta v$ and $\xi$ have a more complex relation.

Equation {eq}`eq:continuitypert` is the first perturbation equation for our example of the plane-parallel atmosphere. If we consider adiabatic perturbations, then we can immediately write a second equation by taking advantage of the Lagrangian formalism. Since $P\propto\rho^\gamma$ for any given fluid element, we must have
$${\Delta P\over P} = \gamma {\Delta\rho\over \rho}.$$
This can be rewritten as
$${\delta P\over P} = \gamma{\delta \rho\over \rho}  -  \xi_z  \left[{d\ln P\over dz}-\gamma{d\ln \rho\over dz} \right]$$
or
\begin{equation}\label{eq:adiabatic}{\delta P\over \rho c_s^2} = {\delta \rho\over \rho} - {N^2\xi_z\over g},\end{equation}
where we define the *Brunt-Väisälä frequency* $N$ and *convective discriminant* $\mathcal{A}$ according to
$$N^2 = - g{\mathcal A} = -g\left[{d\ln \rho\over dz} - {1\over \gamma}{d\ln P\over dz}\right].$$
In addition, we also need the momentum equations 
\begin{eqnarray}\label{eq:mom1}
-\rho\omega^2 \xi_z &=& -{d\delta P\over dz} - g\delta\rho\\
-\rho\omega^2 \xi_x &=& -ik_x\delta P.	\label{eq:mom2}
\end{eqnarray}
Note that whereas we have assumed an $x$-dependence for the perturbations of $e^{ik_xx}$, we do not specify a functional form for the $z$-dependence; it will be determined by how the background changes with height. To solve the equations in a realistic atmosphere or star requires integration of the equations over height $z$. The equations form an eigenvalue problem: in general, only a certain set of frequencies $\{\omega_n\}$ give solutions that satisfy the boundary conditions at $z=0$ or $z=\infty$ ($r=0$ and $r=R$ in the case of a star).

A useful limit to consider is when the vertical wavelength of the waves is much smaller than the pressure or density scale heights. Then the coefficients in the equations can be considered constants on the scale of a wavelength, and we can write a local WKB solution with $z$-dependence $\propto e^{ik_zz}$. Substituting this into the continuity equation, momentum equations and adiabatic condition (eqs. {eq}`eq:continuitypert`, {eq}`eq:adiabatic`, {eq}`eq:mom1`) gives the dispersion relation
$$c_s^2 k_z^2 = \left(\omega^2-N^2\right)\left(1-{k_x^2c_s^2\over\omega^2}\right).\label{eq:atmosdispersion}$$
A vertically-propagating wave requires $k_z^2>0$ so that $k_z$ is real. This can happen in two ways. The first is $\omega^2\gg N^2$, when $\omega^2 = c_s^2(k_z^2 + k_x^2) = c_s^2 k^2$. These are the sound waves or acoustic waves we have encountered before. They appear again in the plane-parallel atmosphere. 

The second solution for propagating waves is when $\omega^2<N^2$ and $\omega^2<c_s^2 k^2$. Then both terms on the right hand side of the dispersion relation are negative and so $k_z^2>0$. The dispersion relation  when $\omega^2\ll N^2$ is
$$\omega^2 = N^2 \left({k_x\over k}\right)^2.$$
These waves are **internal gravity waves**. They are incompressible waves, ie. they satisfy $\vec{\nabla}\cdot\xi\approx 0$ (if you repeat the calculation setting $\vec{\nabla}\cdot\xi=0$ exactly, you'll find that the sound waves go away but the gravity waves survive). The restoring force for the wave is from horizontal pressure gradients caused by horizontal variations in the hydrostatic column that arise as the fluid moves. One interesting fact about gravity waves is that the phase and group velocities of a wavepacket are orthogonal (try proving this using the dispersion relation). In the context of stars, standing gravity waves or acoustic waves can exist that occupy the entire stellar volume in some cases or may propagate in only a limited region of the stellar interior (where $k^2>0$). In this context, gravity waves are referred to as **g-modes** and the acoustic waves as **p-modes** (g for gravity and p for pressure).

This example also includes an instability: **convection**. The convective discriminant $\mathcal{A}$ is so-named because it indicates whether the atmosphere is unstable to convection. In a situation in which ${\mathcal A}>0$, $N^2<0$ and $\omega^2<0$ indicating instability. The way to understand this is to consider moving a fluid element upwards slowly enough that it stays in pressure equilibrium with its surroundings, but quickly enough that the motion is adiabatic. The density contrast between the fluid element and its surroundings after moving a vertical distance $\Delta z$ is
$$ \Delta z\left.{\partial\rho\over \partial P}\right|_S{dP\over dz}  - \Delta z {d\rho\over dz} = -\rho\Delta z \left[{d\ln\rho\over dz}-{1\over\gamma}{d\ln P\over dz}\right] = -\rho \Delta z {\mathcal A}.$$
If ${\mathcal A}>0$, we see that the fluid element will be less dense than its surroundings and so will buoyantly rise further: the atmosphere is unstable to vertical perturbations. The criterion ${\mathcal A}>0$ is the **Schwarzschild criterion** for convection.

## Reading questions

- What is the difference between an Eulerian and Lagrangian perturbation? How are they related?
- Derive equation {eq}`eq:kIkR`.
- Write out the equations you would have to integrate to find the eigenmodes of an atmosphere, $\delta P(z)$ and $\xi_z(z)$ in the form:
$${d\delta P\over dz} = f(\delta P, \xi_z)$$
$${d\xi_z\over dz} = g(\delta P, \xi_z),$$
where $f$ and $g$ are functions of $\delta P$ and $\xi_z$. Why do we need only these two equations?
- Derive equation {eq}`eq:atmosdispersion`.
- Why does $\omega^2<0$ imply instability?







