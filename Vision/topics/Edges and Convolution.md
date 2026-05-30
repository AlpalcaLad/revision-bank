**Causes of edges**
- ![[Pasted image 20260530120422.png|350]]
In images we look at discontinuities in intensity values
ie a rapid change in the image intensity function
Edges in the first derivative have a polarity based on what direction we change in.
Due to this we normally call it extrema rather than maxima/minima
![[Pasted image 20260530121545.png|422]]

**Image filtering: Differentiation**
We can differentiate with the convolution kernel $[0,\dots,0,-1,1,0,\dots,0]$
The second derivative uses the kernel $[0,\dots,0,1,-2,1,0,\dots,0]$
![[Pasted image 20260530121837.png|416]]
Noise amplifies edges and makes it hard to localise
Better to smooth first then differentiate
You can convolve the smoothing with the edge kernel before applying, saving an operation

**Kernels**
Prewritt Kernel
- ![[Pasted image 20260530122159.png|222]]

Sobel kernel
- ![[Pasted image 20260530122224.png|227]]

**Sobel edge detector**
- Two derivative images $I_x', I_y'$
- Edge magnitude $|I'|=\sqrt{I_x'^2 + I_y'^2}$
- Gradient direction $\phi=tan^{-1} \frac{I_y'}{I_x'}$
- Kernels are decomposable, we can do vertical followed by horizontal to save operations
- ![[Pasted image 20260530122605.png|405]]
- 1 nxn                        vs                    2 1xn then nx1
- cheaper than $n^2$
- important for larger kernels, not useful dramatically for 3x3

**Smoothing**
- Weighted average gives improved smoothing
- Gaussian (normal distribution) commonly used
	- Hyperparameters of sigma and kernel size
- Scale selection
	- Small edges may just be noise
	- Direction of larger edges more reliable
	- Location of large edges can direct search for small edges
	- Sigma determines the scale

**Laplacian**
Best position for edges on local maxima of derivative
Can be hard to find best position for wide peak
We can use second derivative to get exact value
	![[Pasted image 20260530123218.png|382]]
Laplacian kernel
- Second derivative
- Negative centre, positive surrounding
- ![[Pasted image 20260530123311.png|111]]
- ![[Pasted image 20260530123325.png|115]]
- 2 versions are approximations of second deriv kernel
	- Either work
- Sum of all values should be zero
- Isotropic
	- Same for any edge direction 
	- No horizontal vertical split

**Marr-Hildreth edge detector**
- uses Laplacian kernel on Gaussian
- Scale selection still relevant

