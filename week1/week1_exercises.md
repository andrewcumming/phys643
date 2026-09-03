# Exercises

Here are some example problems to work on that will give you a chance to play around with the fluid and MHD equations:

### 1. Bernoulli's principle

Consider a barotropic fluid which has $P\propto \rho^\gamma$ (when might this be true?) Use the vector identity $$(\vec{u}\cdot\vec{\nabla})\vec{u} = \vec{\nabla}\left({1\over 2}u^2\right) - \vec{u}\times (\vec{\nabla}\times \vec{u})$$ and the momentum equation {eq}`eq:simple_momentum` to show that the *Bernoulli constant* $$B = {1\over 2}u^2 + h + \Phi$$ is constant along streamlines in a steady flow (i.e. a flow with $\partial\vec{u}/\partial t=0$). Here $\Phi$ is the gravitational potential, and $$h = {\gamma\over \gamma -1}{P\over \rho}$$ is the enthalpy per unit mass satisfying $dh = dP/\rho$.

Bernoulli's principle explains why pressure drops when a flow speeds up, e.g. when a flow goes through a narrow channel.

[Hint: another way to say "B is constant along streamlines" is $\vec{u}\cdot\vec{\nabla} B = 0$.]

### 2. Vorticity equation

Vorticity is the quantity $\vec{\omega} = \vec{\nabla}\times\vec{u}$ and measures the amount of local rotation in the flow. Use the identity from question 1 and the momentum equation {eq}`eq:simple_momentum` to show that
$${\partial\vec{\omega}\over\partial t} = \vec{\nabla}\times(\vec{u}\times\vec{\omega})$$
for a barotropic fluid [^baro].

Compare with the induction equation for MHD. What conclusion do you come to about lines of vorticity?

[^baro]: If the fluid is not barotropic, there is source term for vorticity on the right hand side, $\vec{\nabla}\rho\times \vec{\nabla}P/\rho^2$, which is known as the *baroclinic vector*. Misaligned density and pressure gradients generate vorticity. This is an important effect in planetary atmospheres.

### 3. Magnetic field winding

Consider a spherical star which is differentially rotating such that the fluid velocity is $\vec{u}=\hat{\phi}\  R \Omega(R)$, where we use cylindrical coordinates $(R,\phi,z)$ with $z$ along the rotation axis. A poloidal magnetic field $(B_R(R,z), 0, B_z(R,z))$ threads the star initially.

(a) First assume that the velocity does not change over time. What does the induction equation imply for the subsequent evolution of the field? Explain your result physically.

(b) Now write down the momentum equation for the fluid and include the back reaction of the field on the fluid. What is the evolution in time?

### 4. Electric field in an atmosphere

Consider a plane-parallel atmosphere of fully ionized hydrogen gas. By writing down the momentum equations for the protons and electrons separately, show that (1) the structure of the atmosphere is given by $dP/dz=-\rho g$, where $P$ is the sum of the electron and proton pressures, and (2) there is an electric field in the atmosphere. What is the value of the electric field, and what is its role?
