# Extra material

## TOV equations

When calculating the structure of a neutron star, general relativistic corrections are important, since 
$${GM\over Rc^2} = 0.15\ \left({M\over M_\odot}\right)\left({R\over 10\ {\rm km}}\right)^{-1}.$$ The GR version of the stellar structure equations are known as the Tolman-Oppenheimer-Volkoff (TOV) equations. They are
\begin{eqnarray}
{dm\over dr} &=& 4\pi r^2\rho\\
{dP\over dr} &=& -\rho {Gm\over r^2}\left(1+{P\over\rho c^2}\right)\left(1+{4\pi r^3P\over Gm}\right)\left(1-{2Gm\over rc^2}\right)^{-1}\\
{d\Phi\over dr} &=& -{1\over\rho c^2}{dP\over dr} \left(1+{P\over\rho c^2}\right)^{-1}.
\end{eqnarray}
As well as the continuity and momentum equations, there is an additional equation for the metric function $\Phi$, which is defined such that the metric is
$$ds^2 = -e^{2\Phi}dt^2 + e^{2\lambda}dr^2 + r^2 d\Omega,$$
with
$$e^{2\lambda(r)} = \left(1-{2Gm\over r}\right)^{-1}.$$ To match onto the exterior Schwarzschild metric, $\Phi(R) = (1/2) \ln (1-2GM/Rc^2)$ at the surface of the star. Note that $r$ is defined such that it corresponds to the sphere with surface area $4\pi r^2$ (or circumference $2\pi r$). The proper distance between two shells is $dr (1-2Gm/rc^2)^{-1/2}$, giving a volume element
$$\left(1-{2Gm\over rc^2}\right)^{-1/2}4\pi r^2 dr.$$
The quantity $m(r)$ is the gravitational mass interior to coordinate $r$, equal to $M$ at the surface.






















