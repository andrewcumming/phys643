# Exercises

## 1. Sound speed

Derive a formula giving the sound speed in km/s as a function of temperature in K. You can use the adiabatic sound speed with $\gamma=5/3$ and assume pure atomic hydrogen. Make a table of the sound speed in different astrophysical environments. 

Considering the typical flow speeds you might expect in each environment, comment on the likelihood of achieving supersonic flows.

:::{seealso} Solution
:class: dropdown
Using $c_s^2 = \gamma k_BT/\mu m_p$ with $\gamma=5/3$ and $\mu=1$ gives  

$$c_s = 0.12\ \mathrm{km\ s^{-1}} \ \left({T\over \mathrm{K}}\right)^{1/2}.$$

In terms of temperature, you could go from $\sim 10\ \mathrm{K}$ in a dense molecular cloud to $\sim 10^8\ \mathrm{K}$ for gas in a galaxy cluster (or even hotter in stellar interiors or an explosive situation). 

:::

## 2. Magnetoacoustic waves

Consider a wave propagating in the $z$-direction, so $\mathbf{k} = k \hat{\mathbf{z}}$, across a magnetic field that lies at an angle $\theta$ to $\mathbf{k}$ in the $x$-$z$ plane, $\mathbf{v}_A = v_A(\sin\theta \hat{\mathbf{x}} + \cos\theta \hat{\mathbf{z}})$.

Take the $x$- and $z$-components of equation {eq}`eq:magneticwavesdispersion` and eliminate $\delta v_x$ and $\delta v_z$ to show that the dispersion relation for magnetoacoustic waves travelling at an angle $\theta$ to the magnetic field is
$$\omega^2 = {k^2\over 2}\left[c_s^2+v_A^2\pm \sqrt{(c_s^2+v_A^2)^2-4c_s^2v_A^2\cos^2\theta}\right].$$

Check the limits $\theta\rightarrow 0$ and $\theta\rightarrow\pi/2$ make sense.

:::{seealso} Solution
:class: dropdown

With the definitions of $\mathbf{k}$ and $\mathbf{v}_A$ given, we have $\mathbf{k}\cdot\mathbf{v}_A = kv_A \cos \theta$. Then the $x$- and $z$- components of equation  {eq}`eq:magneticwavesdispersion` give

$$\delta v_x (\omega^2-v_A^2k^2\cos^2\theta) =  -\delta v_z k^2v_A^2\sin\theta\cos\theta$$
$$\delta v_z (\omega^2- k^2(c_s^2+v_A^2) + k^2v_A^2\cos^2\theta) = -\delta v_x k^2v_A^2\cos\theta\sin\theta$$

Cross-multiplying (or equivalently setting the determinant of the linear system to zero) gives
\begin{eqnarray}
(\omega^2-v_A^2k^2\cos^2\theta)(\omega^2- k^2(c_s^2+v_A^2) + k^2v_A^2\cos^2\theta)\nonumber\\
-k^4v_A^4 \cos^2\theta\sin^2\theta = 0
\end{eqnarray}
or
$$(\omega^2-v_A^2k^2\cos^2\theta)(\omega^2- k^2c_s^2 -k^2v_A^2\sin^2\theta) -k^4v_A^4 \cos^2\theta\sin^2\theta = 0$$
$$\Rightarrow \omega^4 - \omega^2k^2\left(c_s^2+v_A^2\right) +k^4c_s^2v_A^2\cos^2\theta = 0.$$
Solving the quadratic for $\omega^2$ gives the dispersion relation in the question.

When $\theta$ goes to $\pi/2$, so that the wave is moving perpendicular to the field lines, we get $\omega^2 = k^2(c_s^2+ v_A^2)$ which is the fast mode (there is also another solution with $\omega^2=0$ which corresponds to the slow mode that goes to zero frequency in this limit). When $\theta\rightarrow 0$, meaning the wave is moving along the field, then the two solutions to the quadratic are $\omega^2=k^2 v_A^2$ and $\omega^2=k^2 c_s^2$. The first corresponds to the transverse Alfven wave with polarization in this plane, and the other corresponds to the slow mode. 
:::

## 3. Supersonic to subsonic transition

Consider a shock in an ideal gas with $\gamma=5/3$. If the shock compresses the gas (so $\rho_2>\rho_1$), show that the incoming gas is supersonic, and that the outflowing gas is subsonic, i.e. that the shock takes a supersonic flow and makes it subsonic.

:::{seealso} Solution
:class: dropdown

The compression factor for $\gamma=5/3$ is given by
$${\rho_2\over \rho_1} = {4\mathcal{M}_1^2\over 3 + \mathcal{M}_1^2}$$
$$\Rightarrow \mathcal{M}_1^2 = {3\rho_2/\rho_1 \over 4 - \rho_2/\rho_1 }.$$
This is larger than 1 for $\rho_2>\rho_1$, so compression implies $\mathcal{M}_1>1$. 

The ratio of Mach numbers downstream to upstream of the shock is given by
$$\left({\mathcal{M}_2\over \mathcal{M}_1}\right)^2 = \left({u_2\over u_1}\right)^2 {P_1\rho_2\over P_2\rho_1}$$

We can use the relations
$${P_2\over P_1} = {1\over 4}(5\mathcal{M}_1^2-1)$$ (for $\gamma=5/3$) and $u_2/u_1 = \rho_1/\rho_2$ to rewrite this as

$$\left({\mathcal{M}_2\over \mathcal{M}_1}\right)^2 = {P_1\rho_1\over P_2\rho_2} = {4\over 5\mathcal{M}_1^2-1}{3+\mathcal{M}_1^2\over 4\mathcal{M}_1^2} = {3+\mathcal{M}_1^2\over \mathcal{M}_1^2 (5\mathcal{M}_1^2-1)}.$$
or
$$\mathcal{M}_2^2 -1= {3+\mathcal{M}_1^2\over 5\mathcal{M}_1^2-1}-1={4(1-\mathcal{M}_1^2)\over 5\mathcal{M}_1^2-1}.$$


For $\mathcal{M}_1>1$, the right hand side is always negative, implying $\mathcal{M}_2<1$. The shock always involves a transition from supersonic to subsonic flow, compressing the gas.



:::




## 4. Accretion shock

A white dwarf is accreting matter from a companion. If the matter free-falls onto the surface of the star and is stopped by a strong shock, estimate the temperature of the post-shock gas.

If the shock is optically-thin, where in the electromagnetic spectrum would you look to find this kind of system?

Repeat for a neutron star and discuss your answer.


:::{seealso} Solution
:class: dropdown

From the notes, a strong shock with $\gamma=5/3$ has a post-shock temperature given by
$${k_BT_2\over\mu m_p} = {3\over 16} v_s^2.$$
If we imagine the flow coming in onto a stationary shock at the surface of the star, we are in the shock frame and so the relevant velocity here is $v_s=v_1$ the velocity of the incoming gas. We can use the free-fall velocity $v_{ff} = (2GM/R)^{1/2}$ for this, giving
$$T_2 = {3\over 16}{\mu m_p\over k_B}{GM\over R}$$
$$ \approx 3\times 10^8\ \mathrm{K} \left({M\over M_\odot}\right)\left({R\over 10^9\ \mathrm{cm}}\right)^{-1}.$$

A blackbody with this temperature would emit in X-rays ($k_BT\approx 8.6\ \mathrm{keV}\ T_8$).
There are indeed accreting white dwarfs that are hard X-ray sources for this reason.

A neutron star is about 1000 times smaller, so the predicted temperature is about $10^{11}\ \mathrm{K}$ which would imply gamma rays. However, with such high temperatures we should think about other physics that could be important. One thing that is also relevant for white dwarfs is that the post shock material can be optically thick, for example, if the accretion stream penetrates into the stellar atmosphere, then the photons will thermalize with the surrounding plasma and the spectrum will be softer as the radiation reradiates as a blackbody. Other physics includes how quickly the protons (which carry most of the infall energy) can transfer energy to the electrons (which radiate the photons) and the effects of radiation pressure.

:::


## 5. Isothermal shock

Consider a radiative shock where the cooling is efficient so that the temperature is the same on both sides of the shock. Use the jump conditions to show that the gas is compressed by a factor $(u_1/c_T)^2$ on crossing the shock, where $c_T^2=k_BT/\mu m_p$ is the isothermal sound speed.


:::{seealso} Solution
:class: dropdown

From the notes, the momentum jump condition is $P_1 + \rho_1 u_1^2 =P_2 + \rho_2 u_2^2$. In this isothermal case, we can write $P = \rho c_T^2$ so the momentum jump condition becomes $$\rho_1(u_1^2+c_T^2) = \rho_2(u_2^2+c_T^2).$$
Now using the mass jump condition, $u_2 = u_1 (\rho_1/\rho_2)$ gives
$$\rho_1(u_1^2+c_T^2) = {\rho_1^2 u_1^2\over \rho_2} + \rho_2 c_T^2$$
or
$$c_T^2 \left({\rho_2\over \rho_1}\right)^2 - (u_1^2+c_T^2) \left({\rho_2\over \rho_1}\right) + u_1^2 = 0.$$
Solving the quadratic gives
$${\rho_2\over \rho_1} = {1\over 2c_T^2} \left[u_1^2 + c_T^2 \pm \sqrt{ (u_1^2+c_T^2)^2-4u_1^2c_T^2  } \right]$$
$$ =  {1\over 2c_T^2} \left[u_1^2 + c_T^2 \pm (u_1^2-c_T^2)  \right].$$
The minus sign gives $\rho_2=\rho_1$ which is a trivial solution where the gas is not compressed or slowed, i.e. there is no shock. We need the plus sign which gives
$${\rho_2\over\rho_1} = {u_1^2\over c_T^2} = \mathcal{M}_1^2.$$

The interesting thing is that this can be a large number! Radiative shocks can significantly compress the gas, whereas adiabatic ones are limited to a factor of $(\gamma+1)/(\gamma-1)$.

:::





## 6. Entropy generation

Investigate the change in entropy ($S\propto \ln (P/\rho^\gamma)$) across a shock. You can assume $\gamma=5/3$. 

In particular, what does this look like for a weak shock $\mathcal{M}_1^2 = 1+\epsilon$ and a strong shock $\mathcal{M}_1\gg 1$?

:::{seealso} Solution
:class: dropdown

The entropy change across the shock is
$$\Delta S\propto \ln\left[{P_2/P_1\over (\rho_2/\rho_1)^\gamma}\right].$$

From the notes, we have (with $\gamma=5/3$)
$${\rho_2\over \rho_1} = {(\gamma+1)\mathcal{M}_1^2\over 2 + (\gamma-1)\mathcal{M}_1^2}  ={4\mathcal{M}_1^2\over 3 + \mathcal{M}_1^2}$$
$${P_2\over P_1} = {2\gamma\mathcal{M}_1^2 - (\gamma-1)\over \gamma+1}= {5\mathcal{M}_1^2 - 1\over 4}.$$

Therefore
$$\Delta S\propto \ln \left[ {5\mathcal{M}_1^2 - 1\over 4} \left( {4\mathcal{M}_1^2\over 3 + \mathcal{M}_1^2} \right)^{-5/3} \right].$$

We know that $\mathcal{M}_1>1$, so the entropy always increases across the shock.
For a strong shock,
$$\Delta S\propto \ln\left[{5\mathcal{M}_1^2\over 4^{8/3}} \right].$$

For a weak shock
$$\Delta S\propto \ln\left[ {5(1+\epsilon)-1\over 4} \left( {4(1+\epsilon)\over 3 + (1+\epsilon)} \right)^{-5/3}  \right]$$
$$= \ln\left[ \left(1 + {5\epsilon\over 4}\right)  \left( {1+\epsilon/4\over 1+\epsilon} \right)^{5/3}  \right]$$
$$ = \ln\left(1 + {5\epsilon\over 4}\right) + {5\over 3}\ln\left(1+{\epsilon\over 4}\right) -{5\over 3}\ln \left(1+\epsilon\right).$$

Now Taylor expand these logs: `sympy.series('ln(1+5*x/4) + (5/3)*ln(1+x/4) - (5/3)*ln(1+x)',x)` gives me a result
$$\Delta S\propto {5\over 48}\epsilon^3.$$

So the weak shock entropy generation is only at third order in the strength of the shock (whereas other quantities change to first order across the shock).


:::