# Week 4: Compressible fluids

This week, we'll look at several aspects of compressible flows: sound waves, how compressible flow differs from incompressible, the phenomenon of steepening, and how to understand what happens at a shock.

## Sound waves

Compressions in a gas propagate as sound waves. The simplest case to consider is a gas at uniform density and at rest. We then make small perturbations to the density, velocity, and pressure 
$$\rho \rightarrow \rho + \delta\rho, \hspace{1cm} \vec{v}\rightarrow \vec{v}+\delta\vec{v}, \hspace{1cm} P\rightarrow P+\delta P.$$ Substituting into the fluid equations and cancelling the zeroth order terms gives 
\begin{equation}\label{eq:sound1}
{\partial\delta \rho\over \partial t}	= -\rho \vec{\nabla}\cdot\delta\vec{v}
\end{equation}
and
\begin{equation}\label{eq:sound2} 
\rho{\partial \delta\vec{v}\over \partial t} = -\vec{\nabla} \delta P,
\end{equation}
where we have kept only terms first order in the perturbations. These equations show the physics of the wave: equation {eq}`eq:sound1` shows that compression leads to a local increase in density and therefore pressure; equation {eq}`eq:sound2` shows that the pressure gradient acts as a restoring force trying to remove the compression.

To see that there is a wave, we assume that the perturbations are rapid enough that there is no time for heat to flow into or out of a fluid element, so that the perturbations are adiabatic, with $${\delta P\over P}=\gamma{\delta\rho\over\rho}.$$ In that case, equations {eq}`eq:sound1` and {eq}`eq:sound2` can be combined into a wave equation
$${\partial^2\delta\vec{v}\over \partial t^2} = {\gamma P\over \rho} \nabla^2\delta\vec{v} = c_s^2 \nabla^2\delta\vec{v},$$
where the *adiabatic sound speed*[^adiabcs] $c_s$ is given by $c_s^2 = \gamma P/\rho$. This is the sound speed that we usually think of — for example looking up values for atmospheric pressure $\approx 10^5\ {\rm Pa}$, density of air at STP $\approx 1.2\ {\rm kg\ m^{-3}}$, and $\gamma=7/5$ for a diatomic gas, I get $340\ {\rm m/s}$.

[^adiabcs]: Note that in general, the sound speed is  
$$c_s^2 = {\partial P\over \partial \rho}$$ with the partial derivative taken under whatever conditions are appropriate for the perturbations.  We considered adiabatic perturbations so the derivative is taken at constant entropy. When heat transfer is rapid compared to the wave period for example, we would keep temperature constant when taking the derivative, giving the isothermal sound speed $c_T^2 = P/\rho$.

Looking for plane wave solutions, ie. perturbations $\propto e^{-i\omega t+\vec{k}\cdot\vec{r}}$, we find a *dispersion relation*
$$\omega^2 = c_s^2 k^2.$$
The linear dispersion relation $\omega\propto k$ means that these waves are non-dispersive. They have frequency-independent and equal phase and group velocities: the phase velocity is $\omega/k = c_s$ and group velocity is $d\omega/d k = c_s$. 

Things get more complicated when the fluid is magnetized. As we discussed in the first week, a magnetized plasma has a magnetic pressure that acts perpendicular to the field lines. Acoustic waves that are travelling across the magnetic field lines experience an extra restoring force and travel more quickly. For the perpendicular case $\vec{k}\perp\vec{B}$, the dispersion relation is
$$\omega^2 = k^2(c_s^2 + v_A^2)$$
where
$$\vec{v}_A = {1\over \sqrt{4\pi \rho}}\vec{B}$$
is the *Alfvèn velocity*. This mode is known as the *fast magnetosonic mode*. An acoustic wave travelling along the field direction $\vec{k}\parallel \vec{B}$ does not feel the magnetic pressure and has the usual dispersion relation $\omega^2 = c_s^2k^2$. These are known as *slow magnetosonic modes*.

Just to give a bit of the flavour of the calculation, the magnetic field enters through the $\vec{J}\times\vec{B}$ force. If the background field is uniform with $\vec{J}=0$, the perturbations give a $\vec{J}\times\vec{B}$ force
$${\delta \vec{J}\times\vec{B}\over c} = {(\vec{\nabla}\times \delta \vec{B})\times\vec{B}\over 4\pi} = {i\over 4\pi}(\vec{k}\times\delta\vec{B})\times\vec{B}.$$
We also need the induction equation 
$$i\omega \delta\vec{B} = \vec{\nabla}\times (\delta\vec{v}\times\vec{B}).$$
With these two extra ingredients, you can show that (try it!)
\begin{eqnarray}\delta\vec{v}(\omega^2 - (\vec{k}\cdot\vec{v}_A)^2) - (\vec{k}\cdot\delta \vec{v})\left[\vec{k}(c_s^2+v_A^2)-\vec{v}_A(\vec{k}\cdot\vec{v}_A)\right]\nonumber\\ + \vec{k}(\vec{k}\cdot\vec{v}_A)(\delta \vec{v}\cdot\vec{v}_A)
=0.\label{eq:magneticwavesdispersion}
\end{eqnarray}
This is a complicated dispersion relation, so it helps to think about particular limits. Setting $\vec{k}\cdot\vec{v}_A=0$ (so $\vec{k}$ perpendicular to $\vec{B}$) makes several terms vanish, and you can straightforwardly show that $\omega^2 = k^2(c_s^2 + v_A^2)$, the fast magnetosonic mode mentioned above. If instead we assume $\vec{k}\parallel \vec{v}_A$, then things simplify to
\begin{equation}\label{eq:alfven_disp}\delta\vec{v}(\omega^2-k^2v_A^2) = (\vec{k}\cdot\delta\vec{v})\vec{k}(c_s^2-v_A^2).	
\end{equation}
Dotting this equation with $\vec{k}$ gives $\omega^2=k^2c_s^2$ the slow magnetosonic wave mentioned earlier. 

We should mention that there is also a non-compressive wave in the magnetized case, the *Alfvèn wave*. The tension of magnetic field lines supports a transverse wave similar to a wave on a string. To see this, set $\vec{k}\cdot\delta\vec{v}=0$ (an incompressible perturbation) in equation {eq}`eq:alfven_disp`. There is a solution if  $$\omega^2 = v_A^2k^2$$
which is the dispersion relation for Alfven waves. You can use the induction equation to show that for these waves $\vec{k}\cdot\delta\vec{B}=0$, ie. they are transverse to the magnetic field. They propagate at the Alfven speed $\vec{v}_A$. 


## Compressible vs. incompressible flow

An important point to make is that compressibility is a flow property as well as a material property. Flows that are subsonic, with fluid velocities much smaller than the sound speed, are incompressible with $\vec{\nabla}\cdot\vec{v}\approx 0$, even though the material itself may be compressible. A way to think of this is that there is plenty of time for compressions to be smoothed out by propagation of sound waves if the flow is subsonic. 

A simple illustration is given by a steady 1D isentropic flow. Isentropic means that we can write the pressure gradient term as $\partial P/\partial x = c_s^2 \partial \rho/\partial x$, where $c_s$ is the isentropic sound speed. The momentum equation for a steady 1D flow is then
$$v{dv\over dx} = - {c_s^2\over\rho}{d\rho\over dx}$$
$$\Rightarrow {v\over\rho}{d\rho\over dv} = -{v^2\over c_s^2}$$
\begin{equation}\label{eq:river}\Rightarrow {1\over\rho}{d\over dv}\left(\rho v\right) = 1 -{v^2\over c_s^2}.\end{equation}

Equation {eq}`eq:river` shows that for subsonic flow, the mass flux $\rho v$ increases with velocity. This is what we would expect for an incompressible flow: at constant density, if you move faster the mass flux is larger. But note what happens at speeds faster than the sound speed. Then, the mass flux decreases as the flow speed increases. Despite moving faster, the drop in density dominates, giving a smaller mass flux. 

Real-life examples of these two limits are a river, which flows faster when the river narrows or slower when the river widens, and traffic on the freeway, which behaves oppositely: it flows faster when the road widens and slows when the road narrows. 

## Steepening and formation of a shock

When deriving the sound speed, we considered linear waves, ie. small perturbations to a background state. However, we know that the fluid equations have a non-linear term $(\vec{v}.\vec{\nabla})\vec{v}$, so that for large amplitudes it is not very useful to write the flow as a sum of plane waves. Whereas in a linear problem the plane waves evolve independently, and so it makes sense to use a Fourier decomposition, the non-linear terms couple the amplitudes of the different modes.

An important effect of the non-linear terms is that they lead to steepening of the velocity profile. We can see this by looking at the equation 
\begin{equation}\label{eq:simpleadvect}
	{\partial v\over\partial t} + v{\partial v\over \partial x}=0.
\end{equation}
The general solution to this equation is 
$$v = f(x-vt) = f(\xi),$$ where $f(\xi)$ is some arbitrary function of $\xi=x-vt$. To see this, change variables
$${\partial v\over\partial t} = {df\over d\xi} {\partial\xi\over\partial t}= f^\prime \left(-v-t{\partial v\over\partial t}\right)$$
$$\Rightarrow {\partial v\over\partial t}={-vf^\prime\over 1+f^\prime t}.$$
Similarly,
\begin{equation}\label{eq:dvdx}
{\partial v\over\partial x}={f^\prime\over 1+f^\prime t}.
\end{equation}
Combining these derivatives, we see that equation {eq}`eq:simpleadvect` is indeed satisfied.

More importantly, we see an interesting behaviour in the spatial derivative given by equation {eq}`eq:dvdx`. An initial profile with $\left.\partial v/\partial x\right|_{t=0}=f^\prime<0$ will reach $\partial v/\partial x\rightarrow \infty$ after a time
$$t=\left|-{1\over f^\prime}\right| = \left|-{1\over \left.\partial v/\partial x\right|_{t=0}}\right|$$
which we can think of as a local "turnover time" for the fluid. 

The profile *steepens* as illustrated in the sketch below.

```{figure} steepening.png
```

A *shock* forms in which the velocity $v$ changes its value on a very short lengthscale. The thickness of the shock is set by the viscous term in the momentum equation which becomes important as $dv/dx$ becomes large. Viscous stresses act to smooth out the velocity gradient and eventually will balance the steepening from the non-linear term. The lengthscale on which this happens is very short, of order the microscopic mean free path. 

The sketch below shows some different scenarios where shocks can arise:

```{figure} shockexamples.png
```

The first example is the *shock tube* in which a piston moves into a cylinder. A shock propagates ahead of the piston, accelerating the fluid from rest to the speed of the piston, and at the same time compressing the gas. The second example is supersonic flow around an object. A shock forms which acts to slow the fluid from supersonic to subsonic. The fact that the flow is subsonic near the object means that the sound crossing time can be shorter than the flow time, and in this way the fluid can divert and flow around the obstacle.

## Shock jump conditions

In practise, we don't need to understand the details of what happens inside the shock, we can instead treat the shock as a discontinuity and relate the fluid velocity, density and temperature on each side using conservation of mass, momentum and energy. These relations are known as the *shock jump conditions*, also known as the Rankine-Hugoniot relations. To derive them, we first move into the frame of the shock as illustrated below. On the left, you see the shock moving to the right at speed $v_s$; on the right in the shock frame the unshocked fluid is moving to the left at speed $v_s$. Across the shock, the fluid changes velocity from $v_1=-v_s$ to $v_2$, and density and pressure change from values $\rho_1$ and $P_1$ to $\rho_2$ and $P_2$.

```{figure} shockframe.png
```

To relate the quantities on either side of the shock, we can integrate the fluid equations across the shock. For a steady 1D flow, continuity is
$${\partial\over\partial x}(\rho v)=0.$$
We integrating from one side of the shock ($x=-\epsilon$) to the other ($x=+\epsilon$) and take $\epsilon$ to zero. This gives
$$\int^\epsilon_{-\epsilon}dx {\partial\over\partial x}(\rho v) = \left[\rho v\right]^\epsilon_{-\epsilon} = 0$$
\begin{equation}\label{eq:jump1}
\Rightarrow \rho_1 v_1 = \rho_2 v_2.	
\end{equation}
Momentum is 
$$\rho v {dv\over dx} = {d\over dx}(\rho v^2) = -{dP\over dx},$$
which when integrated gives 
\begin{equation}\label{eq:jump2}
P_1+\rho v_1^2 = P_2 + \rho v_2^2.
\end{equation}
The total energy equation is 
$${d\over dx}\left[ v \left({1\over 2}\rho v^2 + \rho e + P\right)\right]= 0$$
$$\Rightarrow {1\over 2}v_1^2 + e_1 + {P_1\over \rho_1} = {1\over 2}v_2^2 + e_2 + {P_2\over \rho_2}.$$
For an ideal gas, $P=(\gamma-1)\rho e$, so we can rewrite this as
\begin{equation}\label{eq:jump3}
	{1\over 2}v_1^2 + {\gamma\over\gamma-1}{P_1\over \rho_1} = {1\over 2}v_2^2 + {\gamma\over\gamma-1}{P_2\over \rho_2}.
\end{equation}
Equations {eq}`eq:jump1`, {eq}`eq:jump2`, and {eq}`eq:jump3` are the shock jump conditions, relating the *upstream* conditions ($v_1, \rho_1, P_1$, in the undisturbed gas) to the *downstream* ones ($v_2, \rho_2, P_2$, in the shocked gas).

The jump conditions can be combined to derive a number of useful results. One of them is 
$${\rho_2\over \rho_1} = {v_1\over v_2} = {(\gamma+1)M_1^2\over 2 + (\gamma-1)M_1^2}$$ where $M_1 = u_1/c_1$ is the upstream Mach number, the shock velocity divided by the upstream sound speed. This shows that there is a maximum compression which occurs for a strong shock ($M_1\gg 1$), $\rho_2/\rho_1=(\gamma+1)/(\gamma-1)$. This compression factor is 4 for a monatomic gas ($\gamma=5/3$). 

While the compression is limited, note that the pressure and therefore temperature jump can be large. The pressure jump is
$${P_2\over P_1} = {2\gamma M_1^2 -(\gamma-1)\over \gamma+1}$$
which is $\propto M_1^2$ for a strong shock and keeps growing as Mach number grows.

The $P_2$-$\rho_2$ relation is known as the shock adiabat or the Hugoniot curve. But note that the flow across the shock is definitely not adiabatic! There is a large jump in entropy as the ordered kinetic energy of the rapid upstream flow is converted into heat in the compressed slow-moving gas downstream. For example, for a strong shock with $\gamma=5/3$ you should be able to show that the downstream temperature is $${k_BT_2\over \mu_1 m_p} = {3\over 16}v_s^2.\label{eq:strongshockT}$$

Jump conditions can be derived also for more complicated cases:
- an *oblique shock*, in which the flow direction is not perpendicular to the shock. These occur in flow around an object, where the shocks help to redirect the fluid.
- a *magnetized shock*. As you might expect from our discussion of fast and slow magnetosonic waves, the direction of the magnetic field relative to the shock front makes a difference. A magnetic field perpendicular to the flow and parallel to the shock is compressed and gives an extra pressure that must be included in the jump conditions. There is also a jump condition on $B$ coming from integrating the induction equation across the shock. For example, you can show that the ratio $B/\rho$ is the same on both sides when  the magnetic field is parallel to the shock. Compression of the fluid also implies a larger field strength because of magnetic flux conservation. 
- a *radiative shock*. Shocks in astrophysics are often very radiative: the temperature immediately after the shock is so great that it leads to rapid cooling of the shocked gas. The net result can be much larger compression factors than in the strong shock case. A limit to consider is the *isothermal shock* in which the cooling is strong enough to equalize the temperature of the pre-shock and post-shock gas. In terms of the isothermal sound speed $c_T$, the compression ratio is $\rho_2/\rho_1 = u_1^2/c_T^2$ which can be very large.

## Reading questions

- Calculate the value of the adiabatic sound speed in atomic hydrogen as a function of temperature in Kelvin.

- Explain why sound waves travel faster when moving across magnetic field lines compared to moving along magnetic field lines.

- An astrophysical jet has a steady flow along it that starts subsonic but transitions to supersonic. If you can approximate the flow as 1D, explain how you would expect the cross-sectional area of the jet to change along its length.

- Derive equation {eq}`eq:strongshockT`. Give a physical interpretation.
