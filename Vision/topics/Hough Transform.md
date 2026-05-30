**Hough line Transform**
- Works on edge image
	- Gaussian -> Edge kernel
- Takes a set of points and wants to find those on the same line
- Must decide threshold of how many points define a line 
	- (if 2 then any two points have a line)
- rearrange line equation
	- c=-xm+y
	- e.g. if (x=-10, y=10) c=10m+10
	- do this for all points
	- ![[Pasted image 20260530143603.png|281]]
	- plot of m vs c
	- Where many lines meet, many points would be in the line with that m and c
- To achieve programatically
	- Create 2D array with columns for m and values for c
	- Might need large range and small gaps in practice
	- Plot lines into array
		- ![[Pasted image 20260530144441.png|261]]
		- ![[Pasted image 20260530144520.png|262]]
		- We can then choose elements with highest values
			- (over threshold)
- Problem with cartesian
	- Division by 0 for vertical lines
	- Polar coordinates can handle this
		- Distance and angle $(r,\theta)$ rather than $(x,y)$
		- $r = x cos(\theta) = y sin(\theta)$
		- ![[Pasted image 20260530144813.png|260]]
		- 

**Hough circles**
Special case of circles in an image (fixed radius)
- circle equation: $(x-a)^2+(y-b)^2=r^2$
	- where (a,b) is circle center, r is radius
- parameter space
	- $(a-x)^2+(b-y)^2=r^2$
	- use 2D array for a,b with a fixed radius
	- Where many circles intersect, this is the centre of the best circle
	- For arbitrary radius circles
		- 3D accumulator array for a,b,r

**Generalised Hough transform**
Detecting general shapes in an image
edge pixels used on a feature for lines and circles
same used for contours in generalised but also uses edge directions
Method
- Previously a description of the shape was needed
- For Hough, 
	- user provides a shape image 
	- description performed by algorithm
- Special case
	- fixed orientation and size
		- ![[Pasted image 20260530145942.png|455]]
		- ![[Pasted image 20260530150013.png|459]]
	- We use an R table
		- Range of possible edge directions at some resolution (e.g. 1*)
		- For every contour pixel in shape
			- edge gradient found
			- $(r,\alpha)$ calculated and appended to R table for that $\theta$
	- Create accumulator array
		- Using $(r,\alpha)$ pairs a potential shape centre can be calculated
			- $x_c=x+rcos(\alpha)$
			- $y_c=y+rsin(\alpha)$
		- Pick shapes that have a greater than threshold value in array
	- Need separate R table for each shape
		- Each table can detect template multiple times

In real world we want to find objects at any angle
For this a 4D accumulator array including an orientation parameter is used
- $x_c=x-(acos(\theta)-bsin(\theta))s$
- $y_c=y-(asin(\theta)+bcost(\theta))s$
- where s and $\theta$ are varying scale and orientation
