# Extra material

## Perturbation equations in spherical geometry

In the notes, we looked at gravity waves and acoustic waves in a plane-parallel atmosphere. If we want to study stellar or planetary oscillations, we need to write the perturbation equations in spherical geometry instead.

We assume the background is spherically-symmetric, so pressure or density depend only on $r$. We take density perturbations of the form 
$$\delta\rho = \delta\rho(r) e^{im\phi} P^m_\ell(\cos\theta)e^{-i\omega t}$$
and similarly for the pressure perturbation $\delta P$ and radial displacement $\xi_r$. The non-radial displacements have a different angular dependence: 
$$\xi_\theta = \xi_\theta(r) e^{im\phi} {dP^m_\ell(\cos\theta)\over d\theta} e^{-i\omega t}$$
$$\xi_\phi = \xi_\phi(r) e^{im\phi} {im  P^m_\ell(\cos\theta)\over\sin\theta} e^{-i\omega t}$$
With these choices for the angular dependences, the perturbation equations then depend only on $r$, as follows:

Adiabatic perturbations
$${\Delta\rho\over\rho} = {1\over \gamma}{\Delta P\over P}$$

$$\Rightarrow {\delta\rho\over\rho} = {1\over \gamma}{\delta P\over P} + {N^2\xi_r\over g}$$
(using the definition of $N^2$ from the text; $g(r) = Gm(r)/r^2$).

Continuity
$${\Delta\rho\over\rho} = -\vec{\nabla}\cdot\xi$$

$${1\over \gamma}{\delta P\over P} + {\xi_r\over \gamma}{d\ln P\over dr} = -{1\over r^2}{d(r^2\xi_r)\over dr} -{\xi_\theta\over r\sin\theta P^m_\ell}{\partial\over\partial\theta}(\sin\theta {\partial P^m_\ell\over \partial \theta}) + {m^2\xi_\phi\over r\sin^2\theta}$$
$$\Rightarrow {1\over \gamma}{\delta P\over P} + {\xi_r\over \gamma}{d\ln P\over dr} = -{1\over r^2}{d(r^2\xi_r)\over dr} +\ell(\ell+1){\xi_\theta\over r},$$
where we use
$${1\over \sin\theta}{\partial\over\partial\theta}\left(\sin\theta {\partial P^m_\ell\over\partial\theta}\right) =-\left[\ell(\ell+1)-{m^2\over\sin^2\theta}\right]P_\ell^m$$
and the fact that $\xi_\phi=\xi_\theta$ (see momentum below).

Momentum
$$-\rho \omega^2 \xi_r = -{d\delta P\over dr} - g\delta \rho$$
$$-\rho \omega^2 \xi_\perp = - {\delta P\over r}$$
$$\xi_\phi = \xi_\theta = \xi_\perp$$

We have made the approximation that the perturbations do not change the gravitational potential, so $\delta g = 0$; this is known as the Cowling approximation.

These simplify to give two ODEs to integrate:

$$\label{eq:app1}
{1\over r^2}{d(r^2\xi_r)\over dr}  &=& {g\over c_s^2}\xi_r - {\delta P\over \rho}\left[{1\over c_s^2}  -{\ell(\ell+1)\over \omega^2r^2}\right]$$
$${d\delta P\over dr} &=&  - {g\over c_s^2}\delta P + \rho (\omega^2-N^2) \xi_r	.\label{eq:app2}$$
We have used the fact that $\gamma H = \gamma P/\rho g = c_s^2/g$, where $c_s^2$ is the adiabatic sound speed and $H = -dz/d\ln P$ is the pressure scale height.

The boundary condition at the stellar surface is that the Lagrangian pressure perturbation should vanish there
\begin{equation}\label{eq:bc1}
{\Delta P\over P} = 0\Rightarrow {\delta P\over P} = {\xi_r\over H}\hspace{1cm} {\rm at\ } r=R.	
\end{equation}
At the center $r=0$, we see that there are terms that diverge, so we need to step away from the origin and begin our integration at a small non-zero value of $r$. The boundary conditions for $\ell>0$ (non-radial oscillations) are
$${d\delta P\over dr} = {\ell\over r}\delta P\hspace{1cm} {d\xi_r\over dr} = {\ell-1\over r}\xi_r,$$
or for $\ell=0$ (radial oscillations)
$${d\delta P\over dr} = 0\hspace{1cm} {d\xi_r\over dr} = {\xi_r\over r}.$$
An equivalent way to write the first $\ell>0$ boundary condition is 
\begin{equation}\label{eq:bc2}
\xi_r = \ell \xi_\perp, 
\end{equation}
where $\xi_\perp$ can be expressed in terms of $\delta P$ using the horizontal momentum equation.

Equations {eq}`eq:app1` and {eq}`eq:app2` and the boundary conditions of equations {eq}`eq:bc1` and {eq}`eq:bc2` define an eigenvalue problem for the mode frequency $\omega$.

There are three "quantum numbers" that label the modes: $\ell$, $m$, and the number of radial nodes $n$. However note that the azimuthal wavenumber $m$ doesn't enter into the equations, so the frequency of the mode depends on the number of radial nodes $n$ and the angular quantum number $\ell$, but not $m$. This changes if spherically symmetry is broken, eg. a rotating or magnetized star.



