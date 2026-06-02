![[Pasted image 20260602134542.png]]
> [!question]- Describe an algorithm for the above task
> my answer:
> The student could use a bag of visual words model to classify leaves. They could do this with a discriminative model for example nearest neighbour classification. 
> The implementation of this algorithm would start with image pre-processing in which the image might be thresholded to reduce the number of possible image patches in each image.
> From here, keypoints and their descriptors would be generated using a method like SIFT
> Similar descriptors would be grouped into visual words to create a smaller size of vocabulary for our BoW model. 
> One potential limitation of using a BoW model is that it might be sensitive to rotation and scale, however SIFT improves upon other image patch descriptors by rotating patches to have a standard direction, allowing it to work regardless of the orientation of the leaves. Furthermore SIFT is scale invariant using Difference of Gaussians to detect keypoints across multiple scales.
> The parameter of vocabulary size would need to be determined. Many similar applications use a size of 100 visual words, but a selection (e.g. 50, 100, 200) could be used and validation accuracy compared to determine the best for the Leaf categorisation use case.
> Histograms of the visual words would be plot into high dimensional space, with new leaves being checked for which group they fall closest to, to categorise them.
> 




![[Pasted image 20260602134607.png]]
> [!question]- Describe an algorithm for the above task
> my answer:
> We could use probabilistic clustering to segment the image, in which each pixel has a defined probability of falling into each cluster, compared to k-means which assigns a single cluster to each pixel at each stage. This has the advantage of k-means that it can handle non spherical groupings, which would be necessary to better group points on the coloured cones in the sample image. 
> Our feature space would include the r,g,b pixel values along with x,y. It's important to include positions as otherwise similar colours will be considered the same cluster even if theyre part of separate objects. In the case of Figure 2, this would lead to the green cones being clustered with the green background pattern
> This would work by using taking an initial number of random clusters. At each stage, given our current clusters the ownership of each pixel is calculated and then the clusters are updated with these ownership probabilities. Repeating these two steps iteratively moves closer to the best cluster locations.

> [!question]- For the same two images as above, describe an algorithm to calculate depth into the scene
> First the images would need to be rectified using camera calibration data to ensure points lie on the same horizontal scanline. From here point matches would be made across the image with depth calculated according to the formula Z = b * f / (xl - xr). This takes f as the camera focal length, b as the baseline (physical distance between cameras), xl as the coordinate of the point in the left image and xr the coordinate in the right. 
> One limitation of this method is that it will struggle with occluded areas, for example the bottom left of the face is hidden by the green cone in the left image but less covered in the right. The pixels on that portion of the face won't be able to be matched so can't have an accurate estimation for depth.



> [!question]- Describe in detail the Hough Lines transform
> 


> [!question]- Describe the Generalised Hough Transform
> TODO


> [!question]- Give all the differentiation kernels and name them
> TODO


> [!question]- Explain the Marr-Hildreth algorithm
> TODO

![[Pasted image 20260602135018.png|139]]
> [!question]- Find the covariance matrix of the above data
> TODO

$A = \begin{bmatrix} 4 & 2 \\ 1 & 3 \end{bmatrix}$
> [!question]- Find eigenvectors and eigenvalues for the above matrix
> TODO

$A = \begin{bmatrix} 12 & 1 \\ 4 & 3 \end{bmatrix}$
> [!question]- Find eigenvectors and eigenvalues for the above matrix
> TODO


> [!question]- Explain the PCA algorithm
> Assemble data into matrix of samples vs variables size
> apply PCA to the deviation vectors, giving covariance matrix -> eigenvectors
> e.g. $x=\hat{x} + b_1p_1+b_2p_2+b_3p_3$
> changing b1 might make the shape wider or longer etc


> [!question]- Explain how Active Shape Models work
> first calculate mean of all training shape data
> store all variations from this mean
> the ASM equation is $x=\hat{x} + Pb$ where b is the shape parameters and P is the matrix of PCA eigenvectors


> [!question]- Explain the Harris Keypoint Detector algorithm
> TODO


> [!question]- Explain how SVD works
> TODO


> [!question]- How does Harris corner detection handle scale
> TODO


> [!question]- Explain the Harris-Laplace method
> TODO


> [!question]- Explain the SIFT algorithm
> TODO


> [!question]- Describe and Explain the Depth formula for Stereo
> TODO


> [!question]- Explain the Epipolar constraint
> TODO


> [!question]- Describe the Moravec operator
> TODO


> [!question]- Describe the Essential matrix and how its found
> TODO


> [!question]- Explain both Dense and Sparse correspondence searching and compare
> TODO


> [!question]- How many correspondences do we need in a scene for uncalibrated cameras
> 8


> [!question]- What are examples of extrinsic and intrinsic camera parameters
> TODO


> [!question]- Explain the K-means algorithm
> TODO


> [!question]- What is GrabCut, how does it work?
> TODO


> [!question]- What is mean shift, how does it work?
> TODO


> [!question]- What is RANSAC, how does it work?
> TODO


