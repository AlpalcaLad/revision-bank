**Greyscale**
- In normal vision pictures, the greyscale value represents the amount of light reaching the observer.
- Other applications like MRI scans represent different things

**Representations**
- Image function
	- Greyscale images are a function $I(x,y) : R^2 \rightarrow R$ which gives the intensity at position $(x,y)$
	- Digital image is discrete quantized version of this function
- Landscape
	- Smooth representation of image function
	- ![[Pasted image 20260529170236.png|324]]
	- Continuous maps help with certain computations
- Array of pixels
	- Spatial relationship of pixels is important as well as brightness
	- Matrix of intensity values (often 0 to 255)
- Image histogram
	- Frequencies of brightness's
	- Useful for thresholding
	- Spatial information lost

**Resolution**
Spatial resolution
- Level of perceivable detail
- Number of pixels
	- Digital cams ~ 1k x 1k / 2.5k x 2k
	- Medical images ~ 4k x 4k
Grey level resolution
- Word length at each pixel
	- CDD 8-bit (256)
	- Medical images 12-bit (4k)
		- Useful for fine changes in brightness

**Image arithmetic**
g(x,y) = f(x,y) + 20
	brighter image
g(x,y) = f(-x,y) 
	flip image
Addition
	Take average over images in sequence
	reduces noise
subtraction
	Need to scale negatives back to 0:255 range
	or take absolute difference
	static background shows motion

**Noise**
- Stochastic (random) process
- Identical images have varying values
- Small fluctuations
- $SNR = \frac{signal_{max}}{\sigma_{noise}}$
- Temporal averaging
	- average N images
	- $\sigma_N=\frac{\sigma}{\sqrt{N}}$ ie reduction of variation
	- ![[Pasted image 20260529233444.png|386]]
- Spatial averaging
	- Replace centre value with average of 3x3 grid
	- Can carry out convolution to do this
	- Also called local averaging
	- Noise is reduced more using bigger kernels but image blurred

**Image sub-sampling**
- e.g. throw away every other row gives image half the size
- Seems to add noise, loss of information
- If we smooth first, subsampling has less information loss

**Neighbourhood processing**
![[Pasted image 20260530113935.png|419]]
what a pixel represents depends on its neighbours (e.g. 3x3 area)
Two main methods
- rank filtering (e.g. max min median)
- convolution

**Rank filtering
- Take values under filter window and order them
- Output value
	- First: minimum (aka erosion)
		- shrinks features
	- Last: maximum (aka dilation)
		- expands features
	- middle: median filtering
		- similar to average filtering
			- better at some noise than mean 
				- (dark spots/outliers blur area surrounding with mean filtering)
		- Robust to high noise, especially salt and pepper
		- preserves edges
		- ![[Pasted image 20260530114459.png|313]]
		- ![[Pasted image 20260530114649.png|341]]
	- other: e.g. 7th of 9th

**Convolution**
![[Pasted image 20260530115201.png|439]]
Its just a weighted average over an area, we probably dont need to memorise this formula
She does a better explanation here https://canvas.manchester.ac.uk/courses/40962/pages/week-1-self-study-material?module_item_id=3992050
Padding
- Zero
	- Set all pixels outside image to zero
- Constant
	- Set all pixels outside image to specified border val
- Mirror 
	- reflect pixels across image image

**Smoothing kernels**
![[Pasted image 20260530115617.png|407]]

**Thresholding**
Segmentation
- Label each pixel as either object or background
- Greyscale image -> binary label image
- Thresholding
	- Simple high contrast images
	- Can use simple value
		- Pixels higher are white
		- Pixels lower are black
	- Selecting thresh val often uses histogram
	- ![[Pasted image 20260530115835.png|286]]
	- Intermodel minimum
		- Smallest value between two peaks
		- Histogram is derivative of area as function of threshold
		- $H(D)=\frac{dA(D)}{dD}$
		- Threshold placed where rate of change of segmented area is smallest
- Adaptive thresholding
	- Automatic selection can fail
		- Can be more than 2 means
	- Threshold can vary over image rather than global
	- ![[Pasted image 20260530120200.png|260]]
		- Green line is global threshold
		- Red line is adaptive threshold
	- Relies on whether you can estimate background shading