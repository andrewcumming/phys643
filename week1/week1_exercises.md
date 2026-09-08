# Exercises

### 1. Bernoulli's principle

Consider a barotropic fluid which has $P\propto \rho^\gamma$ (when might this be true?) Use the vector identity $$(\vec{u}\cdot\vec{\nabla})\vec{u} = \vec{\nabla}\left({1\over 2}u^2\right) - \vec{u}\times (\vec{\nabla}\times \vec{u})$$ and the momentum equation {eq}`eq:simple_momentum` to show that the *Bernoulli constant* $$B = {1\over 2}u^2 + h + \Phi$$ is constant along streamlines in a steady flow (i.e. a flow with $\partial\vec{u}/\partial t=0$). Here $\Phi$ is the gravitational potential, and $$h = {\gamma\over \gamma -1}{P\over \rho}$$ is the enthalpy per unit mass satisfying $dh = dP/\rho$.

Bernoulli's principle explains why pressure drops when a flow speeds up, e.g. when a flow goes through a narrow channel.

[Hint: another way to say "B is constant along streamlines" is $\vec{u}\cdot\vec{\nabla} B = 0$.]

:::{seealso} Solution
:class: dropdown
Dividing by $\rho$, the momentum equation is
$${\partial \vec{u}\over\partial t} + \vec{u}\cdot\vec{\nabla}\vec{u} = -{\vec{\nabla} P\over \rho} + \vec{g}.$$
Using the vector identity given in the question, setting $\partial/\partial t=0$ for a steady flow, and writing $\vec{g} = -\vec{\nabla}\Phi$ gives
$$\vec{\nabla}\left({1\over 2}u^2\right) - \vec{u}\times (\vec{\nabla}\times \vec{u}) = -{\vec{\nabla} P\over \rho} -\vec{\nabla}\Phi.$$
Given the definition of enthalpy per unit mass in the question, we can also rewrite $${\vec{\nabla} P\over \rho} = \vec{\nabla} h.$$ Then doing $\vec{u}\cdot$ the momentum equation gives
$$\vec{u}\cdot\vec{\nabla}\left({1\over 2} u^2 + h + \Phi\right) =0$$ which is the result we are looking for.

Note that a key part of the derivation is being able to write the term $(\vec{\nabla} P)/\rho$ as the gradient $\vec{\nabla} h$. This cannot be done in general, but here we assumed a barotropic fluid for which $$h = e + {P\over\rho} = {P\over (\gamma-1)\rho} + {P\over \rho} = {\gamma\over \gamma-1}{P\over \rho}$$ satisfies $dP/\rho = dh$. An easier example that satisfies Bernoulli's principle is an incompressible fluid such as water where we can easily write $(\vec{\nabla} P)/\rho = \vec{\nabla}(P/\rho)$.
:::


### 2. Vorticity equation

Vorticity is the quantity $\vec{\omega} = \vec{\nabla}\times\vec{u}$ and measures the amount of local rotation in the flow. Use the identity from question 1 and the momentum equation {eq}`eq:simple_momentum` to show that
$${\partial\vec{\omega}\over\partial t} = \vec{\nabla}\times(\vec{u}\times\vec{\omega})$$
for a barotropic fluid [^baro].

Compare with the induction equation for MHD. What conclusion do you come to about lines of vorticity?

[^baro]: If the fluid is not barotropic, there is source term for vorticity on the right hand side, $\vec{\nabla}\rho\times \vec{\nabla}P/\rho^2$, which is known as the *baroclinic vector*. Misaligned density and pressure gradients generate vorticity. This is an important effect in planetary atmospheres.

:::{seealso} Solution
:class: dropdown
After applying the identity we get
$${\partial \vec{u}\over\partial t} + \vec{\nabla}\left({1\over 2}u^2\right) - \vec{u}\times (\vec{\nabla}\times \vec{u}) = -{\vec{\nabla} P\over \rho} -\vec{\nabla}\Phi$$
or since we are assuming a barotropic fluid as in question 1, we can collect the gradient terms
$${\partial \vec{u}\over\partial t} - \vec{u}\times (\vec{\nabla}\times \vec{u}) = -\vec{\nabla}\left({1\over 2}u^2 + h + \Phi \right).$$
If we take the curl of this equation the right hand side will vanish because the curl of a gradient vanishes. On the left hand side, writing $\vec{\nabla}\times\vec{u}$ as the vorticity $\vec{\omega}$ gives the result asked for.

The induction equation for $\vec{B}$ has exactly the same form as long as we can neglect ohmic diffusion. So by analogy with flux-freezing in MHD we can see that vortex lines will move with the fluid. Just as ohmic diffuson breaks flux freezing, if we had included vorticity in the momentum equation we would get an extra term that causes vortex lines to diffuse through the fluid.
:::

### 3. Magnetic field winding

Consider a spherical star which is differentially rotating such that the fluid velocity is $\vec{u}=\hat{\phi}\  R \Omega(R)$, where we use cylindrical coordinates $(R,\phi,z)$ with $z$ along the rotation axis. A poloidal magnetic field $(B_R(R,z), 0, B_z(R,z))$ threads the star initially. For this question, neglect the ohmic diffusion term in the induction equation. Assume that the velocity does not change over time. What does the induction equation imply for the subsequent evolution of the field? Explain your result physically.

Without calculating anything, think about what the back-reaction on
the fluid will look like. How will the system evolve in time?

:::{seealso} Solution
:class: dropdown
We need to write out the induction equation
$${\partial \vec{B} \over \partial t} = \vec{\nabla}\times\left(\vec{u}\times\vec{B}\right)$$ in cylindrical coordinates. First
$$\vec{u}\times\vec{B} = R\Omega(R) \hat{\phi} \times \left(B_R(R,z)\hat{R} + B_z(R,z)\hat{z}\right).$$
We can use $\hat{\phi}\times\hat{R} =-\hat{z}$, $\hat{\phi}\times\hat{z} = \hat{R}$ and so
$$\vec{u}\times\vec{B} = -\hat{z} R\Omega(R)B_R(R,z) + \hat{R} R\Omega(R) B_z(R,z).$$
If you look up the cylindrical curl, you'll see that the only component that is non-zero is the $\phi$ component, $$(\vec{\nabla}\times \vec{A})_\phi = {\partial A_R\over \partial z} - {\partial A_z\over \partial R}.$$
Therefore the induction equation gives
$${\partial B_\phi\over \partial t} = R\Omega(R){\partial B_z\over\partial z} + \Omega(R){\partial (R B_R)\over \partial R} + R{\partial \Omega(R)\over \partial R} B_R,$$ with $B_R$ and $B_z$ constant in time.
Rewriting this as
$${\partial B_\phi\over \partial t} = R\Omega(R) \left[{\partial B_z\over\partial z} + {1\over R}{\partial (R B_R)\over \partial R}\right] + R{\partial \Omega(R)\over \partial R} B_R,$$
we see that the square bracket vanishes because $\vec{\nabla}\cdot\vec{B} = 0$. Therefore,
$$\boxed{{\partial B_\phi\over \partial t} = R B_R{\partial \Omega(R)\over \partial R}},$$ showing that differential rotation leads to growth of an azimuthal component of the field. This is known as **winding**. Physically, the magnetic field is tied to the fluid, so radial shear winds the radial field into the azimuthal direction. (Note there is no winding in a rigidly-rotating star, which makes sense because in the rotating frame there is no motion so the field would stay the same.)

For the last part, we would expect that there should be a back-reaction on the flow because the tension of the field lines will resist the winding. The differential rotation will slow down and eventually reverse, undoing the winding and eventually winding up in the opposite direction. This ends up being a *torsional Alfven wave* travelling along the poloidal field.

To see this in more detail, we can look for the azimuthal component of the $\vec{J}\times\vec{B}$ force. The poloidal ($R,z$) part of the current density is
$$\vec{J} = {c\over 4\pi} \left( - \hat{R} {\partial B_\phi\over\partial z}  + \hat{z} {1\over R} {\partial (RB_\phi)\over \partial R}  \right)$$
so
$${(\vec{J}\times\vec{B})_\phi\over c} ={1\over 4\pi} \left( B_z{\partial B_\phi\over \partial z} + {B_R\over R}{\partial (RB_\phi)\over\partial R}   \right).$$
Therefore
$$\rho R{\partial \Omega\over\partial t} = {1\over 4\pi} \left( B_z{\partial B_\phi\over \partial z} + {B_R\over R}{\partial (RB_\phi)\over\partial R} \right).$$
To see what the evolution looks like, we can make the approximation that the largest gradients are those associated with $\Omega(R)$, so we only consider terms that involve differentiating $\Omega$ with respect to $R$ and no other gradients. Then we can differentiate once more with respect to time and get
$$\rho R{\partial^2 \Omega\over\partial t^2} = {1\over 4\pi} R B_R^2 {\partial^2 \Omega\over\partial R^2},$$
which is a wave equation
$$\boxed{
{\partial^2 \Omega\over\partial t^2} = v_A^2 {\partial^2 \Omega\over\partial R^2}
}$$
where $v_A = B_R/(4\pi \rho)^{1/2}$ is known as the Alfvèn speed. This is an example of a torsional Alfvèn wave.
:::

### 4. Electric field in an atmosphere

Consider a plane-parallel atmosphere of fully ionized hydrogen gas in hydrostatic balance. By writing down the momentum equations for the protons and electrons separately, show that (1) the structure of the atmosphere is given by $dP/dz=-\rho g$, where $P$ is the sum of the electron and proton pressures, and (2) there is an electric field in the atmosphere. What is the value of the electric field, and what is its role?

:::{seealso} Solution
:class: dropdown
Since we are in a static atmosphere, we can drop the inertial terms in the momentum equations for  the protons and electrons, but as hinted in the question, we should allow for the possibility of an electric field. By charge neutrality the number densities are equal $n_p=n_e=n$. The momentum equations are therefore
$${dP_e\over dz} = -n m_e g - n e E$$
$${dP_p\over dz} = -n m_p g + n e E.$$
Adding these two equations gives
$${dP\over dz} = -n (m_e + m_p) g \approx -nm_pg= -\rho g,$$
which is the usual hydrostatic balance equation. To get the electric field value, we can subtract the equations:
$$2neE = n (m_p-m_e) g + {d\over dz}(P_p-P_e).$$
For an ideal gas, $P_e=P_p=nk_BT=P/2$ and $m_e\ll m_p$, so this simplfies to
$$eE = {m_p g\over 2}.$$
The electron force balance is dominated by the electric field. Without it, the electrons would float up out of the atmosphere. 
:::