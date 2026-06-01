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

