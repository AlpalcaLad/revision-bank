Iterative process of placing a model onto an image
e.g. ![[Pasted image 20260531132257.png|418]]

**Principle Component Analysis (PCA)**
Suppose two sets of variables
	e.g. x-axis maths score, y-axis English score
When on a graph
- ![[Pasted image 20260531132431.png|325]]
- ![[Pasted image 20260531132444.png|362]]
- ![[Pasted image 20260531132543.png|364]]
- Each point being approximately mapped onto best fit line is called dimensionality reduction
	- This can be used to 3D visualise data in 2D etc

PCA algorithm
- Assemble data into matrix 
	- size: number of samples x number of variables
	- e.g. in above example 24x2 (24 points and 2 variables)
- Compute covariance matrix (C)
- Find eigenvalues ($\lambda_i$) and Eigenvectors ($v_i$) of C
	- $\lambda_i$ is variance in direction $v_i$
	- Total variance $T=\sum_{i=1}^N \lambda_i$
- Choose K largest eigenvalues to account for p% of T
	- For example p might be 95%

PCA example
![[Pasted image 20260531133135.png|404]]
cov(x,x) = var(x)
cov(x,y) = cov(y,x)
cov(y,y) = var(y)
ie the matrix is symmetrical
![[Pasted image 20260531133308.png|412]]
![[Pasted image 20260531133349.png|416]]

**Eigenvalues and Eigenvectors**
For a square matrix A
Av = $\lambda v$
to find eigenvalues we solve
$|A-\lambda I| = 0$
where I is an identity matrix and | | is the determinant
The eigenvalues show the variance in the directions

To find eigenvectors you then solve $(\lambda I - A)V = 0$, subbing in eigenvalues for $\lambda$ and solving for V

---------------Example from google AI for eigenvalues-----------------
Let's find the eigenvalues for matrix \(A\):  
$A = \begin{bmatrix} 4 & 2 \\ 1 & 3 \end{bmatrix}$

**Step 1: Subtract \(\lambda \) from the diagonals**  
$A-\lambda I=\left[\begin{matrix}4-\lambda &2\\ 1&3-\lambda \end{matrix}\right]$

**Step 2: Find the determinant**  
For a $2 \times 2$ matrix $\left[\begin{matrix}a&b\\ c&d\end{matrix}\right]$, the determinant is $(ad - bc)$.  
$\det (A-\lambda I)=(4-\lambda )(3-\lambda )-(2)(1)$ 
$\det (A-\lambda I)=(\lambda ^{2}-7\lambda +12)-2$
$\det (A-\lambda I)=\lambda ^{2}-7\lambda +10$

**Step 3: Solve the characteristic equation**  
Set the polynomial to zero:  
$\lambda ^{2}-7\lambda +10=0$
Factor the quadratic equation:  
$(\lambda -5)(\lambda -2)=0$

The solutions are $\lambda_1 = 5$ and $\lambda_2 = 2$. Your eigenvalues are $5$ and $2$.
-----------------End of example--------------

![[Pasted image 20260531135604.png|423]]
![[Pasted image 20260531135615.png|423]]

**Active Shape Models (ASM)**
- Non-rigid shape matching
- Images can be scaled, rotated, translated and parts of the shape can move independently
- You need large amounts of annotated data for a real model
- example dataset
	- ![[Pasted image 20260531143517.png|364]]
	- 20 datapoints, x and y for each point
		- 40 variables
	- Practically more datapoints should be used
	- Carrying out PCA
		- data matrix D
			- 40 rows (20 lots of (x,y))
			- 6 columns (6 images)
		- covariance matrix C
		- eigenvalues and eigenvectors
		- k largest eigenvalues
			- For ASM, we use shape parameter vector b
				- setting to 0 gets rid of that vector
			- In the faces example first 9 of 40 eigenvalues were around
				- 69k, 29k, 7k, 5k, 1k, 11k, 800, 700, 500
				- ie they decreased over time
	- From data matrix we can calculate mean shape
		- for each variable average values of samples
	- Different shapes can be generated from model
		- change values in shape parameter b using
			- $x=\hat{x} + Vb$ where x is the new model, $\hat{x}$ is the average model, eigenvectors vi are column vectors of V
			- example:
				- ![[Pasted image 20260531144202.png|387]]
			- b values
				- b1 changes vertical position
				- b2 varies skinny/fat
				- b4 varies looking left/right
				- PCA auto generates these
				- If parameters are too extreme, invalid models are made

**Shape fitting**
Active shape models allow a shape to be found in an unseen image
- Place shape into image
- Search in neighbourhood of current feature points for better locations
	- we allow changed shape parameters b
	- also allow scaling, rotation and translation
		- aka pose parameters
- Fit model to new suggested shape (make proper face shape)
- Repeat until convergence
- ![[Pasted image 20260531144735.png|469]]
- ![[Pasted image 20260531144806.png|473]]

**Applications**
Medical application
- Used frequently in medical field
	- e.g. Positioning an artificial hip

**Alternatives**
Active appearance model
- Face is split into triangles
- Texture in triangle warped to fit model
