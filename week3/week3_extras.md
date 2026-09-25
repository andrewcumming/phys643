# Extra material

## Gravothermal heat capacity

An interesting aspect of stars and gravitationally-bound systems in general is that they have a negative heat capacity: the temperature decreases in response to energy input. Here's how this works, following a similar argument to the one in Kippenhahn and Wiegert's book on stellar structure. We can ask: what is the response of the gas to entropy changes? 

First, write the entropy change in terms of temperature and pressure:
$$dS = \left.{\partial S\over \partial T}\right|_P dT + \left.{\partial S\over \partial P}\right|_T dP.$$ 
Using the fact that the heat capacity at constant pressure is $c_P = T\left.\partial S/\partial T\right|_P$, 
and the identity
$$ \left.{\partial S\over \partial T}\right|_P  \left.{\partial T\over \partial P}\right|_S \left.{\partial P\over \partial S}\right|_T = -1 ,$$
we can write this as
\begin{equation}\label{eq:ds}
TdS = c_P\left(dT - {T\over P}\nabla_{\rm ad} dP\right),
\end{equation}
where $\nabla_{\rm ad} = \left.\partial\ln T/\partial \ln P\right|_S$.

So far, this is just thermodynamics, but now we put in the fact that the star is in hydrostatic balance, so that $P\propto 1/R^4$ and $\rho\propto 1/R^3$. This means that we must have
\begin{equation}\label{eq:hydrostatic}
{dP\over P} = {4\over 3}{d\rho\over \rho}.	
\end{equation}
But the equation of state relates density to pressure and temperature changes through
$$d\ln P = \chi_T d\ln T + \chi_\rho d\ln \rho$$
where $\chi_X \equiv (\partial \ln P/\partial \ln X)$ with other variables held constant. 
Equation {eq}`eq:hydrostatic` becomes 
\begin{equation}
{\delta P\over P} = {4\chi_T\over 4-3\chi_\rho}{\delta T\over T}.
\end{equation}
Combining equations {eq}`eq:ds` and {eq}`eq:hydrostatic` gives
$$T{dS\over dT} = c_P\left(1 - {4\chi_T \nabla_{\rm ad}\over 4-3\chi_\rho}\right) = c_\star,$$
where $c_\star$ is the effective heat capacity.

Now look at different limits:

- For an ideal gas, $\chi_T=1$, $\chi_\rho=1$, and for a monatomic gas $\nabla_{\rm ad}=2/5$, so that $c_\star = -(3/5)c_P < 0$. (The Sun is stable).
- For a degenerate gas, $\chi_T\sim k_BT/E_F\rightarrow 0$ so that the correction term becomes small and $c_\star\rightarrow c_P>0$. (Helium core flash).
- If the burning is in a thin shell, equation {eq}`eq:hydrostatic` is no longer correct. To see this, consider a shell that has mass $\Delta M$, thickness $H$ and is located at radius $r$. If the shell changes its thickness by $\delta H$, the pressure change is of order $\delta H/r$, since pressure is $\sim GM\Delta M/4\pi r^4$. On the other hand the change in density is of order $\delta H/H$ (since mass conservation $\Rightarrow r^2\rho H=$constant). Therefore for a thin shell, $${\delta P\over P}\sim {H\over R} {\delta\rho\over\rho},$$ which means that $c_\star\approx c_P$ to first order in $H/r$. Burning in a thin shell is therefore unstable. This is the origin of the term *thin shell flash*.















 
