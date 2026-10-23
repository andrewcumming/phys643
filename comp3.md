
# Computational Exercise 3: Oscillation modes of the Sun

:::{note}
The due date for this assignment is **Thursday November 12th before 1pm**. Your solution should be written up in a Jupyter notebook and submitted to myCourses. Before you submit, please clear the notebook and rerun it to make sure it runs with no errors. You should use markdown cells and latex to add explanations and discussion to your solution.
:::

**Overview**. The goal of this exercise is to compute the oscillation frequencies and eigenmodes of the Sun. You will be able to identify the p-modes and g-modes and study their frequencies, and their eigenfunctions and how they relate to the internal structure.

**Perturbation equations**. The equations describing adiabatic perturbations of a spherically-symmetric star are derived in the [Extra material](week7-extras) for Week 7 — see equations (13) and (14) of those notes, as well as equations (15) and (18) which give the boundary conditions at the centre and surface of the star.  

The perturbation equations consist of two ODEs for the radial displacement $\xi_r$ and the pressure perturbation $\delta P$ in the mode. They form an eigenvalue problem in that the boundary conditions at the centre and surface of the star can only be satisfied for a discrete set of mode frequencies (the eigenvalues). 
The idea here is to integrate these equations using background quantities ($N^2$, $g$, $c_s$, $\rho$) from a model of the Sun, and to find the eigenvalues and corresponding eigenfunctions.

**Solar model**. You can find a model of a 1 solar mass star here: [solar_model.dat](http://www.physics.mcgill.ca/~cumming/teaching/643/code/solar_model.dat). This file is a `profile` file from the `1M_pre_ms_to_wd` test suite in the MESA stellar evolution code. I ran this with the `max_age` parameter set to 5 Gyr to make this model, so it should be a reasonable approximation to the Sun.

The first few lines of the file give some parameters of the model, and then you will see the radial profile of various quantities in the star. Here are descriptions of the different columns taken from MESA (the `profile_columns.list` file in MESA):

```
   zone       ! numbers start with 1 at the surface
   mass       ! m/Msun. mass coordinate of outer boundary of cell.
   logR       ! log10(radius/Rsun) at outer boundary of zone
   logT       ! log10(temperature) at center of zone
   logRho     ! log10(density) at center of zone
   logP       ! log10(pressure) at center of zone
   x_mass_fraction_H
   y_mass_fraction_He
   z_mass_fraction_metals
   log_g      ! log10 gravitational acceleration (cm sec^2)
   pressure_scale_height ! in Rsun units
   gamma1     ! dlnP_dlnRho at constant S
   csound     ! sound speed
   brunt_N2   ! brunt-vaisala frequency squared
```

It is a good idea to make some plots of these  different quantities (for example against $r$). Do they match what you would expect for the Sun?

**Shooting method**. One way to solve the equations for the eigenvalues and eigenmodes is to start at the centre of the star, make a guess for the frequency $\omega$, integrate out to the surface and check whether the boundary condition is satisfied there. If not, modify the guess for $\omega$ and integrate again, repeating until the outer boundary is satisfied. This method is known as a *shooting method*. 

When integrating the ODEs, you will need to evaluate the background quantities such as $N^2$ at different locations $r$. To do this, you can interpolate between the values of $r$ given in the model file. A useful routine for this is [`scipy.interpolate.interp1d`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.interpolate.interp1d.html).

By writing a function that calculates how well the outer boundary condition is satisfied as a function of $\omega$, ie. it calculates $\delta P/P - \xi_r/H$ at $r=R$ for any given value of $\omega$, you can find the modes using a root finder such as [`scipy.optimize.brentq`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.brentq.html).

**Exploring the mode spectrum**. Once you have your code working, explore the spectrum of modes. One way to begin is to first fix $\ell=1$ and try to find the modes with a small number of radial nodes $n$ (the nodes are places where $\xi_r$ crosses zero — you will see this if you plot the eigenfunction, but you can also get your code to calculate that for you). Typical frequencies for these should be of order $\sim 100\ \mu{\rm Hz}$. Then work your way up and down in frequency from there. 

**Questions**

1. What do the eigenfunctions look like for the different modes? Can you separate the $g$ and $p$ modes? 

2. How do the frequencies of the $g$ and $p$ modes scale with the number of radial nodes? Does this scaling match what you would expect from the dispersion relation?

3. Do you see trapping of the modes in particular regions of the star? To help with this, you can plot $N^2$ and $\ell(\ell+1) c_s^2/r^2$ on the same plot as your eigenfunction. A guide to where the modes should propagate is where $k^2$ from the analytic dispersion relation is positive. 

4. We mentioned that $g$ modes are incompressible modes. Check this using your solutions. 

There is a nice set of [lecture notes on stellar oscillations](http://www.physics.mcgill.ca/~cumming/teaching/643/Lecture_Notes_Stellar_Oscillations_Christensen-Dalsgaard.pdf) by Jørgen Christensen-Dalsgaard. Chapter 5 shows some results for the Sun that you can compare against (in particular Figs. 5.2, 5.6, 5.8, and 5.10).


