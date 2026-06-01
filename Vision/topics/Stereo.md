- Goal of stereo
	- Recovery of 3D structure
	- Using multi-view geometry
		- Single image is inherently ambiguous
	- Visual cues
		- Shading
		- Texture
		- Focus
		- Perspective
		- Motion
	- Generic problem formulation
		- Given several images of same object or scene
			- compute a representation of its 3D shape

**Stereo viewing**
- Taking two images of same subject from slightly different viewpoints to create a depth map
- Using triangulation
	- Point corrospondance
		- need confidence two points are the same
	- Camera pose
		- need camera calibration

**Geometry for a simple stereo system**
- Pinhole camera
	- ![[Pasted image 20260601125526.png|304]]
	- big coordinate system is global
	- small letters for local image plane coordinate system
	- ![[Pasted image 20260601125652.png|386]]
	- out goal is to find Z
		- need focal length f to do so
- Perspective projection
	- ![[Pasted image 20260601125721.png|387]]
- Simple system (special setup)
	- ![[Pasted image 20260601125939.png|392]]
		- coordinate system placed between two comparison points
		- focal length assumed to be same for both images
		- image planes placed so they are at same y axis (only x changed)
	- ![[Pasted image 20260601130152.png|395]]
	- ![[Pasted image 20260601130442.png|399]]
		- This is the most important formula to know

**Components of stereo analysis**
- Find correspondences
	- Same points in both images
	- hard problem
- Reconstruction
	- calculate scene coordinates (X,Y,Z)
	- easy with points
- Calibration
	- parameters of cameras
	- e.g. focal length f

**Epipolar constraint**
- two corresponding points fall on same horizontal line
- don't need to search on y axis
- 1D search rather than 2D
- Edges are good places to match
	- significant structure
	- small number of points to match
	- polarity and direction provide cues for matching
	- horizontal edges are hard to match
- Instead of this we can use local feature stuff

**Moravec operator**
- non-linear filter
- over neighbourhood area
- minimum of values
	- $\sum(I_{i,j}-I_{i+1,j})^2$
	- $\sum(I_{i,j}-I_{i-1,j+1})^2$
	- $\sum(I_{i,j}-I_{i+1,j+1})^2$
	- $\sum(I_{i,j}-I_{i,j+1})^2$
- finds points where intensity is varying quickly
- taking minimum eliminates edges as candidates

