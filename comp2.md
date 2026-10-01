# Computational Exercise 2: Steepening

:::{note}
The due date for this assignment is **Thursday October 22nd before 1pm**. Your solution should be written up in a Jupyter notebook and submitted to myCourses. Before you submit, please clear the notebook and rerun it to make sure it runs with no errors. You should use markdown cells and latex to add explanations and discussion to your solution.
:::

**Overview.** The goal of this exercise is to write a 1D hydro code and use it to demonstrate the steepening of a sound wave.

**Algorithm**. The [lecture notes on hydrodynamics](https://www.ita.uni-heidelberg.de/~dullemond/lectures/num_fluid_2011/index.shtml) from the University of Heidelberg give a simple algorithm that you can use to solve the 1D hydro equations (in Chapter 5). First, the fluid equations are written in flux-conservative form, with conserved quantities 
$$f_1 = \rho$$
$$f_2 = \rho v$$
(the mass and momentum densities)
and it is assumed that $P=c_s^2 \rho$ with constant sound speed $c_s$. The equations to solve are then
$${\partial f_1\over\partial t} + {\partial\over \partial x}\left(v f_1\right) = 0$$
$${\partial f_2\over\partial t} + {\partial\over \partial x}\left(v f_2\right) = -{\partial P\over\partial x}.$$
These are in flux-conservative form with the pressure gradient acting as a source term for the momentum density $f_2$. Note that given $f_2$ and $f_1$, the velocity at the grid centre can be obtained from the ratio $f_2/f_1$.

The algorithm has two steps:
- Use donor-cell advection to update $f_1$ and $f_2$. To calculate the velocity at the cell boundaries, you can take an average of the velocity at the cell centres $$v_{j+\frac{1}{2}} = {1\over 2}\left(v_j + v_{j+1}\right).$$
- Add an additional update to the value of $f_2$ from step 1 to take into account the source term. You can do this by writing $${\partial P\over \partial x} = c_s^2 {\partial\rho\over\partial x}$$ and using a first order difference to calculate the density gradient in terms of the new values of $f_1$ you found in step 1. 

**Questions**

1. Choose an initial condition that has a sinusoidal variation in density and/or velocity. Check that for small amplitudes, the wave propagates as expected. Then check that you see steepening at larger wave amplitudes.
2. How large a timestep can you take and still be numerically stable?
3. Do you form a shock in your simulation? What sets its thickness? 
4. Now add the energy equation to your code. You will need to follow a third quantity 
$$f_3 = \rho e_{\rm tot}$$
where $e$ is the specific total energy (sum of kinetic and internal energy). The energy equation is 
$${\partial f_3\over\partial t} + {\partial\over \partial x}\left(v f_3\right) = -{\partial \over\partial x}\left(vP\right).$$
In a similar way to momentum, we can solve this by advecting $f_3$ in step 1 and then updating $f_3$ using the source term on the right hand side in step 2. The pressure is $$P = (\gamma-1)\rho e$$ where $$e = e_{\rm tot} - {v^2\over 2}$$ is the thermal energy. 
Use the code to validate the shock jump conditions, e.g. check that the compression factor is $(\gamma+1)/(\gamma-1)$ for a strong shock.

If you have time, other possible extensions are:

- Modify your code to work in spherical symmetry (adding appropriate $r^2$ factors), and then model the Sedov-Taylor blast wave, comparing with the analytic scaling for the shock radius as a function of time.

- Use a higher order approximation for the advection step (section 4.3 in the Heidelberg notes) and see how it improves the results.
