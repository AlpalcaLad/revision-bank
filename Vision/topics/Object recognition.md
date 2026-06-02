**Applications**
- Image retrieval
	- e.g. here is a picture, find it in these other pictures
	- e.g. find Bernie from the cw

**Indexing local features**
- each patch/region has a descriptor
	- point in high dimensional (e.g. 128D) feature space (e.g. SIFT)
- If two points have similar descriptors 
	- they likely have similar local content
- With potentially thousands of features per image and thousands of images
	- Very inefficient search using brute force
- Inverted file index in books
	- efficient way to find all pages on which a word occurs
	- in our case we want to find all images in which a feature occurs
	- we need to map our features to "visual words"

**Visual Words**
- Extract local features from a number of images
- Similar descriptors have similar content
	- these can be merged, no need to store twice
		- e.g. ![[Pasted image 20260601213745.png|326]]
	- clustering using k-means etc
		- we need to decide vocabulary size

**Inverted file for Images of Visual Words**
- ![[Pasted image 20260601213901.png|256]]
- Where each word number refers to a cluster of descriptors
- When we get a new image
	- We extract the features and assign to a word
		- We can then immediately compare to all of the other images with that feature
- Fail point
	- Images can share many visual words but not be the same
		- we can fix this by checking where features are compared to each other
			- scale
			- location
			- orientation
		- called spatial verification
		- voting mechanism
	- Relies on texture being present

**Sampling strategies**
![[Pasted image 20260601215117.png|456]]

**Object categorisation**
- Tasks
	- Find this particular object
	- Find ANY of an object
		- e.g. any car
- deep neural nets can perform > 99%
	- classical models generally get up to 78%

**Visual Object Categories**
- Basic level categories are defined predominantly visually
- humans usually start with basic level before identification
- 10k to 30k categories for many applications
- We need to robustly identify general traits of object
	- whilst ignoring the differences intra-class
- Generally semi-supervised
	- objects take up most of the image
	- some clutter in background
	- whole image labelled, not segmented

**Bag of words**
- Independent features
- Histogram representation
	- summarise image based on distribution of word occurrences
	- Fixed size representation of an image
		- size of visual vocabulary
		- can directly compare images
	- loss of structural information
- csurka et al
	- works well for image-level classification
- Both presence of visual words and co-occurrence are indicators of a category

**Feature detection**
- regular grid
	- colour histogram approach
	- fixed size grid divides up image
- interest point detection
	- scale invariant
	- descriptors using e.g. sift

**Image classification**
- Given bag of words model
- Generative methods
	- p(image|class)
	- probabilistic ideas
	- e.g. Naive bayes model
		- assume each feature is conditionally independent given class
		- $p(w_1,\dots,w_N|c)=\prod_{i=1}^Np(w_i|c)$
		- ![[Pasted image 20260602115434.png|314]]
		- csurka et al
- Discriminative method
	- Learn decision rules
	- each rule has a boundary
	- e.g. nearest neighbour classification
		- high dimensional space divided into regions
			- each region separated by decision boundaries
		- can do k-Nearest neighbour
			- which category do most nearest neighbours fall into
	- properties
		- simple and flexible
		- handles multi-class
		- large search problem
		- storage of data hard
