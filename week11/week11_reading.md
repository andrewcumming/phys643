# Week 11: Radiation and relativistic flows

There are many examples of flows in astrophysics that involve relativistic motions, e.g. jets from black hole binaries, outflows from active galactic nuclei, or gamma-ray bursts. We therefore need to be able to write the fluid equations in a Lorentz-covariant form, even more so for extreme events like neutron star or black hole mergers which require general relativity. Similarly, many flows involve the interaction between radiation and the fluid. Examples include line-driven stellar winds or neutrino transport in supernovae. We can't go into these topics in a lot of detail, but to finish off the course let's try to get some sense of what the fluid equations look like in relativity and some possible applications, as well as how to include interactions with radiation (so-called radiation hydrodynamics).

## Relativistic hydrodynamics

It helps first to remind ourselves what the non-relativistic momentum and energy equations look like in flux-conservative form. Written with index notation, the momentum equation is
$${\partial\over\partial t}(\rho u_i) + {\partial\over \partial x_j}(\rho u_i u_j) = -{\partial P\over\partial x_i},$$
where we are using the Einstein convention that a repeated index implies a sum over that index. Since we'll soon be going into 4-vector notation, rewrite this as
$$\partial_t(\rho u_i) + \partial_j(\rho u_i u_j) = -\partial_i P,$$
which can be simplified further into the form
$$\partial_t (\rho u_i) = - \partial_j \Pi_{ij}$$
if we define the **momentum flux tensor**, also known as the **stress tensor**,
$$\Pi_{ij} = \rho u_i u_j + P\delta_{ij}.$$
Similarly, the energy equation can be written as
$$\partial_t \left({1\over 2}\rho u^2 + \rho E\right) = -\partial_j \left(u_j\left[{1\over 2}\rho u^2 + \rho E + P\right]\right),$$
where the quantity inside the derivative on the right-hand side is the **energy flux**. Here $E$ is the specific internal energy.

Writing the momentum and energy equations in flux-conservative form like this helps to motivate the form of these equations in relativity. Before we write these down, here is a quick reminder of 4-vectors. We write *contravariant vectors* with index raised, e.g. the position 4-vector $x^\mu = (ct, \vec{x})$. To transform this from frame S to frame S$^\prime$ we use the Lorentz transformation
$$x^{\prime\mu} = \Lambda^\mu_\nu x^\nu$$
where
$$\Lambda_\nu^\mu = \begin{pmatrix} \gamma& -\gamma\beta & 0 & 0 \\ -\gamma\beta & \gamma & 0 & 0 \\ 0 & 0 & 1& 0\\ 0 &0&0&1 \end{pmatrix},$$
$\gamma^2 = 1/(1-\beta^2)$ and $\beta=u/c$.
A *covariant vector* with index down, e.g. $x_\mu$ transforms as
$$x^\prime_\mu = (\Lambda^{-1})^\nu_\mu x_\nu,$$
where note that the components of the inverse matrix $\Lambda^{-1}$ are the same as $\Lambda$ except the off-diagonal components change sign. An important example of a covariant vector is the derivative $\partial/\partial x^\mu = \partial_\mu$. The contravariant and covariant vectors are related by the metric tensor $\eta_{\mu\nu}$, e.g.
$$x_\mu = \eta_{\mu\nu}x^\nu.$$
We will take
$$\eta_{\mu\nu} = \mathrm{diag}(-1,+1,+1,+1).$$
The scalar product of two 4-vectors is then
$$a_\mu b^\mu = \eta_{\mu\nu}a^\mu b^\nu =  -a^0 b^0 + \vec{a}\cdot\vec{b}.$$ Note that this is invariant under a Lorentz transformation. A tensor transforms as
$$T^{\mu\nu} = \Lambda^\mu_\rho \Lambda^\nu_\sigma T^{\rho\sigma},$$
so each index gets its own Lorentz transformation.

Once we introduce relativistic effects we expect some mixing between energy and momentum. Indeed, it turns out that the energy and momentum equations can be written in terms of a single **energy-momentum tensor** $T^{\mu\nu}$ which takes the form
$$
T^{\mu\nu} =
\left(
\begin{array}{c|c}
T^{00} &
\begin{array}{ccc}
 & T^{0i} & 
\end{array}
\\ \hline
\begin{array}{c} 
\\ T^{i0} \\ \\ 
\end{array} &
\begin{array}{ccc}
 & & \\
 & T^{ij} & \\
 & & 
\end{array}
\end{array}
\right)
$$
The top left entry $T^{00}$ is the energy density, the vectors $T^{0i}$ and $T^{i0}$ are the energy flux divided by $c$, written as either row or column vector respectively, and finally the purely spatial part $T^{ij}$ is the momentum flux tensor/stress tensor. Note that $T^{\mu\nu}$ is symmetric. We're also using the convention that greek letters (e.g. $\nu$ in $T^{\mu\nu}$) run over time and space indices, where as roman letters (e.g. $i$ in $T^{ij}$) run over space indices only.

We can recover the energy equation as
$$\partial_t(T^{00}) = -\partial_i T^{i0}$$
and momentum as
$$\partial_t(T^{i0}) = -\partial_j T^{ij}.$$
They can be combined as
$$\boxed{\partial_\mu T^{\mu\nu} = 0}$$
which is the relativistic statement of **energy and momentum conservation**. The $\nu=0$ component gives energy conservation, and the $\nu=i$ component gives momentum conservation.

In terms of the 4-velocity of the fluid, $u^\mu = \gamma(c,\vec{u})$,
$$\boxed{T^{\mu\nu} = (e+P){u^\mu u^\nu\over c^2}+P\eta^{\mu\nu}}\label{eq:Tmunu}$$
where $e$ is the internal energy density of the fluid including the rest mass energy, $P$ is the pressure and $\boxed{w=P+e}$ is the enthalpy density, all of which are evaluated in the proper frame of the fluid.
With our sign convention for the metric, $u^\mu u_\mu = \eta_{\mu\nu}u^\nu u^\mu=-c^2$.
The components of $T^{\mu\nu}$ are
$$T^{ij} = {wu^iu^j\over c^2(1-u^2/c^2)} + P\delta^{ij}$$
$$T^{00} = {w\over 1-u^2/c^2} - P = {e+P u^2/c^2\over 1-u^2/c^2}$$
$$T^{i0} = {wu^i\over c(1-u^2/c^2)}.$$
Note that these have the expected non-relativistic limits, with $e\rightarrow {1\over 2}\rho u^2 + \rho c^2 + \rho E$.

The continuity equation can also be written in covariant form. If the number density in the rest frame of a fluid element is $n$, the number density measured for a moving fluid element by a stationary observer is $n^\prime = \gamma n$ because the volume is Lorentz contracted in the direction of motion. Similarly the number flux is $\gamma n\vec{u}$. The number flux 4-vector is
$$n^\mu = n u^\mu = \gamma n(c,\vec{u}).$$
The **continuity equation** is then
$$\boxed{\partial_\mu n^\mu = \partial_\mu (n u^\mu) = 0.}$$

Using this covariant form of the fluid equations we can recover many of the results that we've derived already for non-relativistic flow. First writing out $\partial_\mu T^{\mu\nu}=0$ using equation {eq}`eq:Tmunu` and simplifying with the continuity equation gives
$$nu^\mu \partial_\mu\left({w\over n}{u^\nu\over c}\right) +c \eta^{\mu\nu}\partial_\mu P = 0.\label{eq:rel1}$$
Multiplying equation {eq}`eq:rel1` with $u_\nu$ and simplifying gives
$$nu^\nu\left[{\partial_\nu P\over n} - \partial_\nu\left({w\over n}\right) \right]=0.$$
From the first law of thermodynamics,
$$d\left({w\over n}\right) -{dP\over n} = T d\left({s\over n}\right)$$
where $s$ is the entropy density. Therefore we have
$$\boxed{n u^\nu T\partial_\nu \left({s\over n}\right) = 0}$$
which says that the entropy per particle $s/n$ is constant along particle trajectories, i.e. **adiabatic flow**. This makes sense because we didn't include any source terms in the energy equation.

Next, we can apply the projection operator
$$P^{\mu\nu} = \eta^{\mu\nu} + {u^\mu u^\nu\over c^2}$$ to equation {eq}`eq:rel1`. In the rest frame, this operator isolates the spatial component, i.e. the momentum equation, and so is way to isolate the momentum part of $\partial_\mu T^{\mu\nu}=0$ in any frame. After applying this operator and simplifying, we get
$${w\over c^2} u^\mu \partial_\mu u^\nu  = - \eta^{\mu\nu}\partial_\mu P - {u^\nu u^\mu\over c^2} \partial_\mu P,$$
which is the **relativistic Euler equation**.

## Applications of the relativistic fluid equations

There are a few interesting applications of the relativistic fluid equations using concepts that we've already seen for the non-relativistic case:

- **AGN jets** (see [week 6 notes](week6-reading/#jets-as-nozzles)). Blandford & Rees (1974) used the relativistic version of Bernoulli's constant in their models of AGN jets as nozzles. To derive this we can use the relation $d(w/n) = dP/n$ which applies for adiabatic flow and can be used to rewrite the Euler equation as
$$u^\mu\partial_\mu\left({w u^\nu\over n}\right) + c^2 \partial^\nu \left({w\over n}\right) =0.$$
For a steady flow this reduces to
$$\boxed{\vec{u}\cdot\vec{\nabla}\left({\gamma w\over n}\right) =0}.$$
The quantity $\gamma w/n$ is the **relativistic Bernoulli constant**, constant along streamlines. So as an example, if the plasma in the jet is ultrarelativistic so that $P=(1/3)e$ and $w=e+P=4P$, and adiabatic $P\propto n^{4/3}$ (these are general results for a gas of ultrarelativistic particles), then in order for $\gamma w/n$ to be constant, the flow along the jet should follow $\gamma\propto n^{-1/3}\propto P^{-1/4}$ (see Appendix of Blandford & Rees 1974 for more details). As the gas expands and drops in pressure and density, internal energy is converted into bulk motion. More generally, simulations of AGN jets require relativistic hydrodynamics, and this is included in many codes.

- **Relativistic shocks** ([Blandford & McKee 1976](https://ui.adsabs.harvard.edu/abs/1976PhFl...19.1130B/abstract)). For a shock with flow normal to the shock front, the jump conditions for mass, momentum and energy can be obtained from the continuity equation for mass and from the energy-momentum tensor for the momentum and energy fluxes. This gives
$$[\gamma\beta n]=0\label{eq:relshock1}$$
$$[(e+P)\gamma^2\beta]=0\label{eq:relshock2}$$
$$[(e+P)\gamma^2\beta^2+P]=0.\label{eq:relshock3}$$
As an example, consider a strong shock in the ultrarelativistic limit. One one side of the shock we then have $P_1=0$, $e_1=n_1mc^2$ and on the other $P_2=e_2/3\Rightarrow w_2=4P_2$. In the frame of the shock, the upstream fluid has $\beta_1\approx 1$, $\gamma_1\gg 1$. The shock jump conditions then give
$$\gamma_2 \beta_2 n_2 = \gamma_1n_1$$
$$4P_2\gamma_2^2\beta_2 = n_1 mc^2 \gamma_1^2$$
$$4P_2\gamma_2^2\beta_2^2 + P_2=\gamma_1^2 n_1 mc^2.$$
These equations can be solved to give
$$\beta_2 = 1/3; \hspace{1cm}\gamma_2 = {3\over \sqrt{8}}$$
$$n_2 = \sqrt{8} \gamma_1 n_1; \hspace{1cm} P_2={2\over 3}\gamma_1^2e_1.$$
We can see that the gas is compressed by a factor of $\sqrt{8}\gamma_1$, and the energy density or pressure by a factor of $2\gamma_1^2$. This is quite different from the non-relativistic case which has a maximum compression. The gas flowing downstream of the shock moves with velocity $v_2=c/3$, independent of the upstream Lorentz factor $\gamma_1$.

- **Relativistic blast wave**. Blandford & McKee apply their results for relativistic shocks to do a relativistic version of the Sedov-Taylor blast wave. They find an approximately self-similar solution in which the shocked fluid lies in a shell of thickness $R/\gamma_1^2$ (because of the large compression factor in the shock). Unlike the non-relativistic case, the energy is stored close to the shock front in the shocked material rather than distributed throughout the interior.

- **GRMHD**. 

## Radiation hydrodynamics


To be continued .. 



## Reading questions

- Show that for a fluid at rest the energy-momentum tensor is $T^{\mu\nu} = \mathrm{diag}(e,P,P,P)$.
- In relativity the Bernoulli constant is $\gamma w/n$. Check that this reduces to the usual Bernoulli constant when $u\ll c$.
- Use equation {eq}`eq:tmunu` for $T^{\mu\nu}$ to derive the relativistic shock jump conditions given in equations {eq}`eq:relshock1`-{eq}`eq:relshock3`. Use these jump conditions to show that the velocity downstream from an ultrarelativistic shock is $v_2=c/3$ in the frame of the shock. 