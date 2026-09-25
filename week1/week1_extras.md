# Extra material

## Two fluid equations

Another way to approach the MHD equations is to consider the electron and ions separately. Coupled by a collisional term, the momentum equations for each species are
\begin{equation}\label{eq:mom}
 n_e m_e {D\vec{v_e}\over Dt} =  - {n_em_e(\vec{v_e}-\vec{v_i})\over \tau_{e}} - n_e e \left(\vec{E} + {\vec{v_e}\times\vec{B}\over c}\right) - \vec{\nabla} P_e
\end{equation}
\begin{equation}\label{eq:mom2}
 n_i m_i {D\vec{v_i}\over Dt} =  - {n_im_i(\vec{v_i}-\vec{v_e})\over \tau_{i}} + n_i Ze \left(\vec{E} + {\vec{v_i}\times\vec{B}\over c}\right) - \vec{\nabla} P_i
\end{equation}
where $n_e$, $n_i$, $P_e$ and $P_i$ are the electron and ion densities and pressures, $m_e$ and $m_i$ are the electron and ion masses, and $\tau_e$ and $\tau_i$ are the timescales on which the electron or ion velocity $\vec{v_e}$ or $\vec{v_i}$ relaxes due to collisions with the other species. 

Charge neutrality implies that $n_e = Zn_i$. Momentum conservation also tells us that the collisional terms must cancel, i.e. $n_em_e/\tau_e = n_im_i/\tau_i$ or $\tau_e = (Zm_e/m_i)\tau_i$. This means that the electron velocity changes on a much faster timescale due to collisions with protons than vice versa. This makes sense if we consider two body collisions between particles with very different masses: the heavy particle undergoes a smaller velocity change by roughly the ratio of the particle masses.

The electrons and ions satisfy the continuity equations
$${\partial n_e\over \partial t} + \nabla\cdot (n_e\vec{v_e}) = 0$$
$${\partial n_i\over \partial t} + \nabla\cdot (n_i\vec{v_i}) = 0.$$
Multiplying by the particle masses and adding, we find
$${\partial \over \partial t}(n_em_e + n_im_i) + \nabla\cdot (n_em_e\vec{v_e} + n_im_i\vec{v_i}) = 0$$
or
$${\partial \rho\over \partial t} + \nabla\cdot (\rho\vec{u}) = 0,$$
where $\rho = n_em_e + n_im_i$ is the mass density and we define the fluid velocity $\vec{u}$ such that $$\rho\vec{u} = n_e m_e\vec{v_e}+ n_i m_i \vec{v_i}.$$ Note that since $m_e\ll m_i$, the fluid velocity is close to the ion velocity $\vec{u}\approx \vec{v_i}$. Subtracting the continuity equations and assuming charge neutrality gives $\nabla\cdot\vec{J}=0$ as required for charge conservation.

Now add the two momentum equations [](#eq:mom) and [](#eq:mom2). On the left hand side this gives 
$$n_e m_e {D\vec{v_e}\over Dt} + n_i m_i {D\vec{v_i}\over Dt} = \rho {D\vec{u}\over Dt}.$$
On the right hand side, the pressure gradient terms add $\vec{\nabla} P_i + \vec{\nabla} P_e = \vec{\nabla} P$, where $P$ is the total pressure, and the Lorentz force terms are 
$$- n_e e \left(\vec{E} + {\vec{v_e}\times\vec{B}\over c}\right)+ n_i Ze \left(\vec{E} + {\vec{v_i}\times\vec{B}\over c}\right)= n_e e {(\vec{v_i}-\vec{v_e})\times\vec{B}\over c} = {\vec{J}\times\vec{B}\over c}.$$ The final result is $$\rho {D\vec{u}\over Dt} = - \vec{\nabla} P + {\vec{J}\times\vec{B}\over c} ,$$ which is the familiar momentum equation for the fluid.

Ohm's law can be obtained from the electron equation of motion. We neglect the acceleration term on the left hand side, assuming that the electron velocity quickly adjusts to changes in Lorentz forces since the electrons are much less massive than the ions. Therefore 
$$ 0 =  - {n_em_e(\vec{v_e}-\vec{v_i})\over \tau_{e}} - n_e e \left(\vec{E} + {\vec{v_e}\times\vec{B}\over c}\right) - \vec{\nabla} P_e$$
or
$$\vec{E} = {m_e\vec{J}\over n_ee^2\tau_e} - {(\vec{v_e}-\vec{v_i})\times\vec{B}\over c}  -{\vec{v_i}\times\vec{B}\over c} - {\vec{\nabla} P_e\over n_e e}.$$
The electrical conductivity is $\sigma = n_ee^2\tau/m_e$, and since $\vec{u}\approx \vec{v_i}$, we have 
\begin{equation}\label{eq:ohm}
\vec{E} = {\vec{J}\over \sigma} -{\vec{u}\times\vec{B}\over c} + {\vec{J}\times\vec{B}\over n_e e c}- {\vec{\nabla} P_e\over n_ee}.
\end{equation}
Equation [](#eq:ohm) is the same as the Ohm's law we wrote down earlier, except for two additional terms: the *Hall term* and *battery term*. The first of these is the Hall electric field that you may have come across before that arises when a current flows perpendicular to a magnetic field. The Lorentz force deflects the current-carrying charges until the Hall electric field grows to balance it. The battery term enters the induction equation as the cross product of the electron pressure and density gradients $\vec{\nabla} P_e\times \vec{\nabla} n_e$ (after taking the curl of $\vec{E}$) so that misalignment of the surfaces of constant electron density and constant electron pressure leads to magnetic field growth (the ``battery effect''). This can happen with differential heating for example, leading to growth of magnetic field.
