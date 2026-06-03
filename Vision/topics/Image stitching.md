We can be asked about how ORB is used in the coursework
but not inner workings of it

Applications of image stitching
- Panorama stitching
	- ![[Pasted image 20260601182835.png|273]]
- A look into the past
	- ![[Pasted image 20260601182819.png|360]]
- 

**image stitching**
- simple method
	- feature based image stitching
	- local features ie SIFT
	- illumination issues
		- wide lensed cameras often have darker corners

**Alignment as fitting**
- fitting a model to features in one image
	- find model M that minimises $\sum_i residual(x_i,M)$
		- ie minimise distances between points
	- find transformation T that minimised $\sum_i residual(T(x_i),x_i')$
		- ![[Pasted image 20260601183107.png|318]]

**Transformation models**
![[Pasted image 20260601183152.png|352]]
we aim for projective
examples
	![[Pasted image 20260601183509.png|370]]

**Image function transformations**
- we can
	- change intensities - filtering
	- change pixel locations - warping
- Global warping
	- p=(x,y) -> T -> p'=(x',y')
	- transformation T is a coordinate changing machine
	- T is global
		- same for any point p
		- described by few parameters

**linear transformations**
- ie can be represented by 2x2 matrix
- scaling
	- $\begin{bmatrix}S_x &0\\0 & S_y \end{bmatrix}$
	- if uniform Sx = Sy
- rotation
	- $\begin{bmatrix}cos\theta &-sin\theta\\ sin\theta & cos\theta \end{bmatrix}$
	- above is anticlockwise
- Translation not possible
	- not linear operation on 2D coordinates
- ![[Pasted image 20260601184046.png|384]]
- Trick to add translations
	- add extra coordinate w
	- convert to homogeneous
		- $(x,y)$ => $\begin{bmatrix}x \\ y \\ 1 \end{bmatrix}$
	- convert back to normal coordinates
		- $\begin{bmatrix}x \\ y \\ 1 \end{bmatrix}$ => $(\frac{x}{w}, \frac{y}{w})$ 
	- gives translations
		- ![[Pasted image 20260601184415.png|325]]
		- This is an affine transformation
	- other transformations
		- ![[Pasted image 20260601184514.png|373]]
	- same properties as before
		- except origin doesn't map to origin necessarily

**Affine transformations**
- Messing with that bottom line
- Projective transformations aka homographies
	- ![[Pasted image 20260601184734.png|191]]
- This is the mapping of one plane to another via a point
	- ![[Pasted image 20260601184911.png|229]]
	- e.g.
	- ![[Pasted image 20260601184942.png|367]]
		- we get black area where no pixels are available
- properties
	- parallel lines don't necessarily stay parallel
	- origin doesn't map to origin necessarily
	- ratios are not preserved
- alternate form of homographies
	- ![[Pasted image 20260601185148.png|312]]
- we know (x,y), (x',y') matches
	- we want to know transformation matrix values from that
	- using form where bottom right is 1
		- only 8 unknowns
		- even value means 4 matches is enough to solve
	- we don't need to know how to solve for this course
		- ![[Pasted image 20260601185610.png|331]]
		- We do need to know
			- normalise homography matrix A
			- target vector h is unit vector
			- only 8 unknowns need solving
			- least of square problem to solve

**Robust feature alignment**
- Least squares works where matches are correct
- Practically we don't always have all correct matches
	- call right matches inliers
	- wrong matches outliers
- given a hypothesised line
	- count number of points that agree with line
		- "agree" -> within small distance
	- For all lines select one with most inliers

**RANSAC (Random Sample Consensus)**
- Concept
	- Inliers will agree with each other
	- Outliers will often disagree with each other
	- RANSAC works if there are <50% outliers
- Algorithm
	- Randomly sample s sample matches
		- s = minimum sample size to fit a transformation model
	- Compute transformation from sample group
	- Find inliers to transformation
	- If inliers is large enough
		- re-compute least squares estimate on all inliers
	- repeat N times
	- keep transformation with largest number of inliers

NB: video suspiciously ended - there may be more content not visible on canvas 