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
- baseline
	- line connecting two camera viewpoints

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
- two corresponding points fall on same line
- don't need to search on y axis, horizontal for simple case
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

**Calibrated cameras (general case)**
- cameras don't necessarily have parallel optical axes
- Only difference is that its no longer a horizontal scan line
	- Epipolar constraint still otherwise holds
	- ie still a single line to scan through
- ![[Pasted image 20260601134915.png|301]]
- Definitions
	- ![[Pasted image 20260601135005.png|379]]
- Example
	- ![[Pasted image 20260601135214.png|357]]
- Generalising stereo geometry
	- Cameras are at arbitrary orientations
		- image planes not necessarily parralel
	- Separation between optical centres not parallel to image planes
	- camera coordinate systems differ from each other and scene
	- coordinate systems related by
		- rotation matrices R1 and Rr giving orientations of each camera relative to scene
		- translation vectors T1 and Tr between camera origins and scene origin
	- Calibration finds these matrices and vectors

**Stereo reconstruction**
![[Pasted image 20260601135634.png|406]]
for every point on the image plane p1
- P is O1 + some multiple of the vector p1
similarly for p2

![[Pasted image 20260601135802.png|458]]
If we know of the calibration data we can recover world coordinates
$P_l'$ is in world coordinates where $P_l$ is in the left cameras coordinate system

In practice
- Measurement inaccuracies mean vectors wont collide
- need to find midpoint of closest points on each line

**General case**
Essential matrix
- relates points on the left to points on the right camera
- With calibrated cameras we only need one R and T
	- To get from camera frame 1 to camera frame 2
	- By placing world coordinate in one camera reference system
- ![[Pasted image 20260601140626.png|359]]
- Right equation comes from cross prod giving a perpendicular vector
	- if axb = c, then c dotted with either a or b is 0
- matrix form of cross product
	- ![[Pasted image 20260601140808.png|375]]
- The essential matrix is called E
	- ![[Pasted image 20260601141022.png|201]]
	- it related corresponding image points between both cameras
	- if we observe a point in one image
		- position in other constrained to lie on line defined by E

**rectification**
- reproject image planes onto a common plane parallel to line between optical centres
- this means our scanlines are now horizontal

**Correspondence problem**
- ![[Pasted image 20260601141442.png|392]]
- assumptions (soft constraints) can help identify pairs
	- similarity
	- uniqueness
	- ordering
- to find matches in the image pair assume
	- most scene points visible in both
	- matches are similar in appearance

**Dense correspondence search**
- For each pixel in first image
	- Find corresponding epipolar line in right image
	- examine all pixels on line and pick best match
		- (e.g. SSD, correlation)
	- Triangulate matches to get depth
- Easier when epipolar lines are scanlines
	- rectify first
- Template methods fragile
	- illumination methods can mess it up
	- we assume cameras are in similar conditions
- Window size
	- need large enough to capture illumination intensity variation
	- small enough to catch only similar disparity pixels

**Sparse correspondence search**
- Restrict search to sparse set of detected features
- use feature descriptors and distances
	- rather than pixel values
- narrow search further by epipolar geometry as before
- Need sufficient number of matches
- More efficient than dense
- Both dense and sparse break down in textureless regions
- Handles occlusions better

**sources of error**
- low contrast / textureless regions
- occlusions
- camera calibration errors
- violations of brightness constancy (e.g. specular reflections)
- large motions

**Applications**
- Segmentation of background/foreground
- view interpolation
	- inserting things into other images
- virtual viewpoint
	- e.g. the matrix

**Camera parameters**
- Extrinsic parameters
	- Rotation matrix
		- 3x3
		- (3 free parameters)
	- Translation vector
		- (Tx,Ty,Tz)
- Intrinsic parameters
	- ![[Pasted image 20260601161223.png|318]]
	- Relate pixel coordinates to image coordinates
	- pixel size (sx,sy)
		- pixels may not be square
	- origin offset (dx,dy)
		- pixel origin may not be on optic axis
	- focal length f
	- these aren't totally independent

**calibration**
- calibrate using calibration targets
- construct real world object with known distances
	- do corner detection
	- work backwards to get camera params
- algorithms
	- tradeoff between
		- accuracy
		- robustness
		- complexity

**uncalibrated stereo**
- calibration necessary to determine absolute 3D positions
- we can determine relative 3D positions without
	- (up to a scale factor)
- If at least 8 correspondences in the scene are known
	- sufficient camera parameters can be estimated
- instead of essential matrix
	- we have fundamental matrix
		- beyond course unit
	- we need to avoid generate features
		- ie not coplanar, on same plane
