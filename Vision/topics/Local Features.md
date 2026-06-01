**motivation**
- global representations have limitations
	- occlusions 
		- (i.e. objects blocking parts of objects)
		- global can only handle partial
	- intra-category variations 

**Image features**
- Feature
	- Local, meaningful, detectable part of the image
	- Location of a sudden change
	- Invariant to change of view point, illumination
	- Lower computational burden than global
	- Information content high
- applications
	- SLAM (cognitive robotics)
	- Image matching
	- Mars Rover images
	- Motion tracking

**Image stitching**
- Detect feature points in both images
- Find corresponding pairs
- e.g. matching Bernie in cw2
- Use pairs to align images
- ![[Pasted image 20260531155711.png|365]]

**Feature finding**
- Procedure
	- Find a set of distinctive keypoints (x,y)
	- Define region around each keypoint (e.g. 3x3 area)
	- extract and normalise region content
	- compute local descriptor from region
	- match local descriptors
		- using similarity measure e.g $d(f_A,f_B)<T$
- Predictability
	- Same points need to be found reliably
		- ie same points found on same image when rerun
	- Same descriptors need to be generated for points
- Requirements
	- Repeatable region extraction
		- invariant to translation, rotation, scale
		- robust or covariant to out of plane (affine) transformations
		- robust to lighting variations, noise, blur, quantisation
	- Locality
		- Features are local
			- robust to occlusion and clutter
	- Quantity
		- sufficient number of regions to cover object
	- Distinctive
		- regions contain interesting structure
	- Efficiency
		- close to real time performance

**Keypoint detection**
- Edges only localise in one direction
	- no change along edge direction
- Corners are better for matching
	- (corners are points where two edges meet)
	- These have a significant change in all directions

**Harris detector formulation**
- Change in intensity for shift \[u, v\]
- $E(u,v) = \sum_{x,y} w(x,y)[I(x+u,y+V)-I(x,y)]^2$
	- approximation below, don't use above formula
- w is the window function
	- 1 if in window, 0 outside
	- makes sure only relevant region considered
- $E(u,v) \approx [u,v]M[^u_v]$
- Where M is a 2x2 matrix computed from image derivatives
	- ![[Pasted image 20260531161055.png|326]]
		- sum over the image area we're checking for corner
	- M is also called second moment matrix or autocorrelation matrix
- ![[Pasted image 20260531234101.png|293]]
- we can't measure variance of full covariances as they aren't parallel to our coordinate axis

**singular value decomposition**
- SVD is general methodology
- Any nxn matrix can be written as product of 3 matrices
	- $U \cdot D \cdot V^T$ 
	- $U\cdot U^T = V \cdot V^T=1$
	- where U,V are unitary matrices
		- columns are orthogonal vectors and have unit length vectors
	- D is a diagonal matrix with non negative values
- For 2x2 square matrix
	- $A=U\cdot D \cdot U^T$
	- ![[Pasted image 20260601000036.png|412]]
- SVD gives us a new coordinate system, allowing us to measure variance

**Harris detector: mathematics**
![[Pasted image 20260601000228.png|378]]
- Corner response measure
	- $R=det M - k (trace M) ^2$
		- $detM=\lambda_1 \lambda_2$
		- $traceM = \lambda_1+\lambda_2$
		- k is a small constant (0.04 to 0.06)
		- for 2x2 matrix
			- tr(A)=a11+a22
			- det(A)=a11a22-a12a21
	- R depends only on eigenvalues of M
	- R is large for a corner
	- R is negative with large magnitude for an edge
	- R is small for a flat region

**Window function**
- Option 1: uniform window
	- ![[Pasted image 20260601000843.png|226]]
	- Rotation sensitive
- Option 2: Smooth with gaussian
	- ![[Pasted image 20260601000804.png|287]]
	- Rotation invariant

**Fast approximation**
- Don't need to compute eigenvalues
	- Square matrix, det and trace have well defined immediate formula
- Compute second moment matrix
	- Blur and compute image derivatives
	- Square of derivatives
	- Gaussian filter of each
	- compute M

**Harris corner properties**
- Rotation invariant
- Not invariant to image scale
	- ![[Pasted image 20260601001307.png|315]]

**Descriptors**
Naive approach
- Exhaustive search
- Compare descriptors whilst varying patch size
	- handles different sized patches
	- very inefficient

Automatic scale selection
- Function on the region that is scale invariant
	- Same value for corresponding regions even at different scales
	- take local maximum of function
	- ![[Pasted image 20260601104843.png|399]]
	- invariant region size found independently in each image
- Laplacian-of-Gaussian achieves this (LOG)
	- aka blob detector
	- Laplacian of an image
		- Sum of the second partial deriv respect to x and the one for y
		- ![[Pasted image 20260601113306.png|357]]
		- Can run Laplacian kernel over image to achieve
		- Scalar value
			- found using a single mask
			- orientation information is lost
		- second order derivative
			- taking derivatives increases noise
			- noise sensitive
	- Always combine Laplacian with smoothing operation
		- smooth -> Laplacian
	- This locates blobs and gets maximum response when it fits the blob perfectly
		- characteristic scale: scale that gets peak response of LOG
	- Can also find interest points
		- Local maxima in scale space of LOG
		- Convolve with multiple scales of sigma
		- compare if maxima exists across scales

**Harris-Laplace**
- Initialisation
	- Multiscale Harris corner detection
	- $\sigma, \sigma^2, \sigma^3, \sigma^4$
- scale selection
	- based on LOG
	- only choose points that are also maxima in LOG
- Motivation
	- Harris detects corners
	- using both can detect more variety of features
		- might also detect blob like features

**Approximating LOG with DOG (difference of gaussians)**
- $DOG=G(x,y,k\sigma)-G(x,y,\sigma)$
- Cheaper than 2nd derivatives
	- we often already need to compute Gaussians
		- we can reuse these
		- aka Gaussian scale pyramid
- Used in Lowe's SIFT pipeline for feature detection
- Convolving multiple times with a gaussian adds powers of sigma
- Typically subsample every 2nd pixel etc
	- given we've lost detail from blur anyway
- Method
	- Detect maxima in DOG in scale space
	- Reject low contrast points
	- Eliminate edge responses

**Local feature descriptor**
- Simplest method
	- Square window of surrounding pixels
		- Write regions as vectors
		- compute distance between vectors
		- not invariant to even small changes
- More robust
	- Surrounding image gradients
	- ignore magnitude to make lighting invariant
	- Find dominant direction of gradient for image patch
	- Rotate patch according to this angle
		- Canonical orientation
		- makes system rotation invariant

**SIFT**
- Used for matching local features
- Requirements
	- Feature invariance
		- invariant to translation, rotation and scale
		- invariant feature descriptor
- Method
	- Find candidate locations using DOG
		- note scale they're found in
		- reject features along edges
			- Discard with strong edge response (R using det M and trace M)
	- Carries out gradient orientation over 16x16 pixel region
		- compute histogram of this
			- Quantise directions into eight bins
		- Select dominant orientation of histogram
		- Concatenated into vector
		- Descriptor 128 dimension vector
- Result
	- one image yields
		- n 128-dimensional descriptors
		- n scale parameters (size for each patch)
		- n orientation parameters (angle for each patch)
		- n 2D points (position for each patch)
- Performance
	- Handle up to 60* out of plane rotation
	- significant illumination change handling
	- real time performance
- Finding matches
	- Distance function for two descriptors
		- simplest
			- SSD (Sum squared distance)
				- If many good possible options, ambiguous
				- can give good scores to bad matches
		- more robust
			- ratio distance SSD(f1,f2)/SSD(f1,f2')
				- where f1 is the feature in image 1
				- f2 is the best match in image 2
				- f2' is the second best match
			- only consider ones with big enough ratio
	- For each feature in image 1
		- Test all features in image 2 
			- find one with min distance
			- throw out features with distance > threshold
				- picking threshold hard task, balancing act

**Evaluation**
ROC curve
- true positive rate
	- num matched true positives / num true positives
- false positive rate
	- num matches false positives / num true negatives
- maximise true positive -> 1
- minimise false positive -> 0

