# Exercises

## 1. Models vs reality

(a) In the movie on turbulence, we saw two jets with Reynolds numbers different by a factor of 50. They look the same on the large scale, but one has finer structures than the other on small scales. Explain this observation in terms of the energy spectrum of the turbulence (sketch it for each case on the same plot). How much finer is the small scale structure in the larger Re number jet?

(b) Also discussed in the film was the use of models in simulating exploding ships or erupting volcanoes for movies. Consider a real volcano eruption and a model volcano eruption. Assuming the microscopic properties of the fluid is the same in each, sketch the energy spectrum of the turbulence on the same plot. Estimate the outer and inner scales and the number of order of magnitudes in scale covered by the inertial range.

## 2. Decaying turbulence

A fluid is stirred, generating a turbulent cascade. At time t = 0 the stirring is stopped, and the turbulence begins to decay. Sketch the energy spectrum E(k) against k that you expect at different times. In particular, how does the smallest lengthscale scale with time?

## 3. Turbulence in a cloud

Estimate the energy dissipation in a cumulus cloud on Earth, both per unit mass and for the entire cloud. You’ll need to estimate or look up typical lengthscales and velocities for the fluid motion. Also estimate the inner scale of the turbulence.

## 4. Energy in the cascade

Explain why energy can be transported through the inertial range without being dissipated there.

In the Kolmogorov cascade, is the energy located mostly at large scales or at small scales? If we had two flows with the same outer scale but different Reynolds numbers, how would their total energy differ?

## 5. Convective turnover time

If the internal luminosity of Jupiter is $10^{-10}\ L_\odot$, estimate the convective turnover time.

In a turbulent convection zone, turbulent transport can be modelled with a turbulent diffusivity $\sim v_c H$ where $v_c$ is the convective speed and $H$ the pressure scale height (towards the center of the planet $H$ is some reasonable fraction of $R$). Look up microscopic diffusion coefficients inside Jupiter. How much larger is the turbulent diffusion coefficient?

## 6. Simulating solar convection

The microscopic viscosity of a plasma is given roughly by (from Spitzer's book Physics of Fully-Ionized Gases)
$$\mu \approx 2.21\times 10^{-15}\ \mathrm{g\ cm^{-1}\ s^{-1}}\ T^{5/2}.$$

Consider convection in the Sun. What is the Reynolds number? What range of scales would you have to follow numerically to be able to resolve the full inertial range?

What happens in a simulation where the number of grid points in each direction is limited to say 1024 grid points? Could it still give an accurate representation of the turbulent fluid flow?



