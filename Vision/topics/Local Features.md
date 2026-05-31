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

