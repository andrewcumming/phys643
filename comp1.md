# Computational Exercise 1: The white dwarf mass-radius relation

:::{note}
The due date for this assignment is **Thursday October 1st before 1pm**. Your solution should be written up in a Jupyter notebook and submitted to myCourses. Before you submit, please clear the notebook and rerun it to make sure it runs with no errors. You should use markdown cells and latex to add explanations and discussion to your solution.
:::

**Overview**. The goal of this exercise is to calculate the mass-radius relation for $T=0$ white dwarfs. This requires numerically integrating the equation of hydrostatic balance. You can do this using whatever method you wish, but to help you I describe a possible procedure below.

**Equations and boundary conditions**. The structure of the white dwarf is given by the equations of hydrostatic balance $${dP\over dr}=-{Gm\rho\over r^2}\hspace{1cm}{dm\over dr}=4\pi r^2\rho.$$ The boundary conditions are $m=0$ at $r=0$ and $P=\rho=0$ at $r=R$.

**Equation of state**. The integration variables are $m$ and $P$, so at each step you will need to compute the density from the pressure using the equation of state. Usually the equation of state is given the other way round, as a function $P(\rho)$, often as a numerical table for complex equations of state. Given $P(\rho)$, you can find the density $\rho_0$ corresponding to a particular pressure $P_0$ by solving the equation $P(\rho_0)=P_0$ numerically using a root-finding algorithm. 

You can use this root-finding technique in your code, but there is also another option since we have an analytic expression for the equation of state. In this case, we can change integration variables from $P\rightarrow \rho$, ie. use the analytic equation of state to write $dP/dr$ in terms of $d\rho/dr$. As the white dwarf mass increases, the electrons go from being non-relativistic ($P\propto \rho^{5/3}$) to relativistic ($P\propto\rho^{4/3}$). To take this into account, we can use the analytic fitting formula for the equation of state derived by Paczynksi (1983) that I mentioned in the notes: $$P^{-2}=P_{nr}^{-2}+P_{r}^{-2},\label{eq:Pe}$$ where $P_{nr}=K_{nr}\rho^{5/3}$ is the non-relativistic degenerate electron pressure and $P_{r}=K_r\rho^{4/3}$ is the relativistic degenerate electron pressure. It is then straightforward to show that $${d\ln P\over dr}={d\ln\rho\over dr}\left[{5\over 3}\left({P\over P_{nr}}\right)^2+{4\over 3}\left({P\over P_r}\right)^2\right].\label{eq:dlnPdr}$$ Use the class notes to determine the constants $K_{nr}$ and $K_r$. Assume  a carbon/oxygen white dwarf which has $Y_e=0.5$.

**Integration**. Now the idea is to integrate outwards from the center of the star to the surface. At the center, there is a problem at $r=0$ since the equation for $dP/dr$ has an $r$ in the denominator and we can't divide by zero! To avoid this, start the integration at a small distance $r=\epsilon$ from the center, where $\rho\approx \rho_c$ and $m\approx 4\pi\rho_c\epsilon^3/3$. Here I've written the central density as $\rho_c$.

Integrate outwards until the density falls to zero. The radius at which $\rho=0$ is the radius of the star $r=R$, and the value of $m$ at this point is the mass $M$ of the star. How you do this step in practice depends on your integrator. Most likely you will have to tell your integration routine to integrate from $r=r_1=0$ to $r=r_2$. In that case, try different values of $r_2$ until you find the one that gives $\rho=0$ at the edge.

Repeat this integration for several different choices for central density $\rho_c$ logarithmically spaced from about $10^6\ {\rm g\ cm^{-3}}$ to $10^9\ {\rm g\ cm^{-3}}$. You'll have to experiment to get the correct range in central density that covers a mass range up to the Chandrasekhar mass at $\approx 1.4\ M_\odot$. 

**Questions**

1. *Mass-radius relation*. Plot the curve of radius against mass. For low masses, when the central density is small and $\gamma=5/3$, you should find $R\propto M^{-1/3}$, but you'll see the slope changes at large masses. How does your answer compare with the analytic approximation from the class notes, $$R=8.7\times 10^8\ {\rm cm}\ \left({M\over M_\odot}\right)^{-1/3}\left[1-\left({M\over M_\mathrm{Ch}}\right)^{4/3}\right]^{1/2},$$ and what do you determine to be the Chandrasekhar mass?
2. *Investigate the density profile.* Plot the density profile as a function of radius for different mass white dwarfs. How does the density profile change as you change the white dwarf mass?
3. *The extent to which the electrons are relativistic.* Plot the value of $\gamma = d\ln P/d\ln\rho$ and $E_F/m_ec^2$ at the center of the white dwarf as a function of mass. Comment on your results.
4. *Add the Coulomb pressure of the ions $P_C$ to the electron pressure*, i.e. write $P=P_e + P_C$ where $P_e$ is given by equation {eq}`eq:Pe` and $P_C$ is given by equation {eq}`eq:PC` of the notes. You can then derive the extra term that needs to be added to equation {eq}`eq:dlnPdr`. Calculate the new models — what changes? At what masses does the Coulomb energy become important?
