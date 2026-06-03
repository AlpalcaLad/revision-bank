Image stitching
## 1. Which of the following is a common application of image stitching?

A. Image segmentation  
B. Panorama creation  
C. Edge detection  
D. Image compression

**Answer:** B

---

## 2. In feature-based image stitching, images are aligned primarily using:

A. Pixel intensities only  
B. Local features such as SIFT  
C. Histogram equalisation  
D. Convolution filters

**Answer:** B

---

## 3. A common illumination issue in wide-lens cameras is:

A. Motion blur  
B. Barrel distortion  
C. Darker image corners  
D. Chromatic aberration

**Answer:** C

---

## 4. Image alignment can be viewed as:

A. Image filtering  
B. Feature extraction  
C. Model fitting  
D. Edge detection

**Answer:** C

---

## 5. When fitting a transformation model, the objective is typically to:

A. Maximise image brightness  
B. Minimise residual errors between matched points  
C. Increase image resolution  
D. Reduce feature count

**Answer:** B

---

## 6. Which transformation model is typically the goal in image stitching?

A. Translation  
B. Rotation  
C. Affine  
D. Projective

**Answer:** D

---

## 7. Changing pixel locations in an image is known as:

A. Filtering  
B. Thresholding  
C. Warping  
D. Smoothing

**Answer:** C

---

## 8. Changing image intensities without moving pixels is known as:

A. Warping  
B. Filtering  
C. Registration  
D. Projection

**Answer:** B

---

## 9. In global warping, the transformation:

A. Is different for every pixel  
B. Depends on image intensity  
C. Is the same for every point in the image  
D. Only affects edge pixels

**Answer:** C

---

## 10. Which of the following is a linear transformation in 2D?

A. Translation  
B. Scaling  
C. Perspective projection  
D. Homography

**Answer:** B

---

## 11. A 2D rotation matrix represents:

A. Scaling  
B. Translation  
C. Rotation about the origin  
D. Projection

**Answer:** C

---

## 12. The standard rotation matrix shown in the notes performs:

A. Clockwise rotation  
B. Anticlockwise rotation  
C. Reflection  
D. Scaling

**Answer:** B

---

## 13. Why cannot translation be represented by a 2×2 linear transformation matrix?

A. Translation changes dimensionality  
B. Translation is nonlinear on 2D coordinates  
C. Translation requires trigonometric functions  
D. Translation only works in homogeneous coordinates

**Answer:** B

---

## 14. To represent translations using matrix multiplication, coordinates are converted to:

A. Polar coordinates  
B. Cartesian coordinates  
C. Homogeneous coordinates  
D. Cylindrical coordinates

**Answer:** C

---

## 15. The homogeneous representation of point (x, y) is:

A. [x y]ᵀ  
B. [x y 0]ᵀ  
C. [x y 1]ᵀ  
D. [1 x y 1]ᵀ

**Answer:** C

---

## 16. Converting homogeneous coordinates (x, y, w) back to Cartesian coordinates involves:

A. Multiplying by w  
B. Dividing x and y by w  
C. Setting w = 1  
D. Removing w without modification

**Answer:** B

---

## 17. An affine transformation differs from a purely linear transformation because:

A. It allows translation  
B. It preserves perspective effects  
C. It changes image intensity  
D. It requires nonlinear optimisation

**Answer:** A

---

## 18. Which statement about affine transformations is true?

A. Parallel lines remain parallel  
B. Parallel lines may intersect  
C. Ratios are never preserved  
D. They model full perspective effects

**Answer:** A

---

## 19. Another name for a projective transformation is:

A. Similarity transform  
B. Homography  
C. Linear mapping  
D. Convolution

**Answer:** B

---

## 20. Which property is NOT generally preserved by projective transformations?

A. Straight lines remain straight  
B. Parallel lines remain parallel  
C. Planar mappings are possible  
D. Perspective effects can be represented

**Answer:** B

---

## 21. For the homography formulation used in the notes, how many unknown parameters must be solved?

A. 4  
B. 6  
C. 8  
D. 9

**Answer:** C

---

## 22. What is the minimum number of point correspondences required to solve for a homography?

A. 2  
B. 3  
C. 4  
D. 8

**Answer:** C

---

## 23. In robust feature alignment, correct matches are called:

A. Outliers  
B. Inliers  
C. Residuals  
D. Samples

**Answer:** B

---

## 24. Why can ordinary least squares fail when matching image features?

A. It cannot handle translations  
B. It requires homogeneous coordinates  
C. It is sensitive to outliers  
D. It only works for affine transformations

**Answer:** C

---

## 25. What is the main idea behind RANSAC?

A. All points contribute equally to model estimation  
B. Random subsets are used to find a model supported by the most inliers  
C. The transformation is computed only once  
D. It assumes all matches are correct

**Answer:** B

---

## Harder Exam Questions

### 26. According to the notes, RANSAC is most effective when:

A. More than 90% of matches are outliers  
B. Exactly 50% of matches are outliers  
C. Fewer than 50% of matches are outliers  
D. There are no outliers

**Answer:** C

---

### 27. In RANSAC, the sample size _s_ should be:

A. Equal to the number of image pixels  
B. The minimum number of matches needed to fit the transformation model  
C. Half the number of matches  
D. Equal to the number of outliers

**Answer:** B

---

### 28. After a good set of inliers is found in RANSAC, the algorithm typically:

A. Stops immediately  
B. Discards the model  
C. Recomputes a least-squares estimate using all inliers  
D. Converts the model to affine form

**Answer:** C

---

### 29. Which statement about projective transformations is correct?

A. The origin must map to the origin  
B. Ratios are always preserved  
C. Parallel lines may cease to be parallel  
D. Translation is impossible

**Answer:** C

---

### 30. Which stage of a feature-based stitching pipeline is most closely associated with RANSAC?

A. Feature detection  
B. Feature matching  
C. Robust transformation estimation  
D. Image filtering

**Answer:** C

# Feature Detection & Motivation

### 1. What is a major limitation of global image representations?

A. They require local descriptors  
B. They struggle with occlusions  
C. They cannot represent colours  
D. They only work on grayscale images

**Answer:** B

---

### 2. Which of the following is NOT a desired property of an image feature?

A. Detectable  
B. Meaningful  
C. Global in nature  
D. Invariant to illumination changes

**Answer:** C

---

### 3. Why are local features often preferred over global representations?

A. They always contain more information  
B. They are robust to occlusion and clutter  
C. They eliminate noise completely  
D. They require no matching

**Answer:** B

---

### 4. Which application commonly relies on local image features?

A. Image compression  
B. SLAM  
C. Histogram equalisation  
D. Thresholding

**Answer:** B

---

# Image Stitching

### 5. Which step comes first in a feature-based image stitching pipeline?

A. Align images  
B. Blend images  
C. Detect feature points  
D. Estimate homography

**Answer:** C

---

### 6. Corresponding feature pairs are primarily used to:

A. Increase image resolution  
B. Align images  
C. Remove noise  
D. Detect edges

**Answer:** B

---

# Feature Finding

### 7. A feature descriptor is computed from:

A. The entire image  
B. A local region around a keypoint  
C. Only image edges  
D. Histogram equalisation

**Answer:** B

---

### 8. Repeatability means:

A. Features are detected quickly  
B. The same points are found reliably across runs/images  
C. Features are scale invariant  
D. Features are unique

**Answer:** B

---

### 9. Which transformation should a good feature detector ideally be invariant to?

A. Translation  
B. Rotation  
C. Scale  
D. All of the above

**Answer:** D

---

### 10. Why is locality important for image features?

A. Reduces memory requirements  
B. Makes them robust to occlusion  
C. Eliminates lighting changes  
D. Allows larger descriptors

**Answer:** B

---

# Corners and Harris Detector

### 11. Why are edges generally poor feature points?

A. They contain too much information  
B. They localise poorly in one direction  
C. They are scale invariant  
D. They cannot be detected

**Answer:** B

---

### 12. Corners are preferred because they exhibit:

A. Constant intensity  
B. Significant change in all directions  
C. No gradients  
D. Only horizontal gradients

**Answer:** B

---

### 13. In the Harris detector, the matrix M is also known as the:

A. Covariance matrix  
B. Hessian matrix  
C. Second moment matrix  
D. Rotation matrix

**Answer:** C

---

### 14. The purpose of the window function w(x,y) is to:

A. Increase image size  
B. Restrict calculations to a local region  
C. Remove corners  
D. Estimate scale

**Answer:** B

---

# SVD and Eigenvalues

### 15. Singular Value Decomposition decomposes a matrix into:

A. A + B + C  
B. UDVᵀ  
C. QR  
D. LDLᵀ

**Answer:** B

---

### 16. In SVD, the columns of U and V are:

A. Random vectors  
B. Orthogonal unit vectors  
C. Eigenvalues  
D. Image gradients

**Answer:** B

---

### 17. Why is SVD useful in Harris corner analysis?

A. It provides a new coordinate system for measuring variance  
B. It removes image noise  
C. It estimates scale  
D. It computes gradients directly

**Answer:** A

---

# Harris Corner Response

### 18. The Harris corner response is:

R=det⁡(M)−k(trace⁡(M))2R = \det(M) - k(\operatorname{trace}(M))^2R=det(M)−k(trace(M))2

What is a typical value of k?

A. 0.0001  
B. 0.04–0.06  
C. 0.5–1.0  
D. 2–5

**Answer:** B

---

### 19. A large positive Harris response indicates:

A. Edge  
B. Flat region  
C. Corner  
D. Noise

**Answer:** C

---

### 20. A large negative Harris response indicates:

A. Corner  
B. Edge  
C. Blob  
D. Flat region

**Answer:** B

### 21. A small Harris response indicates:

A. Flat region  
B. Strong corner  
C. Strong edge  
D. Scale change

**Answer:** A

---

### 22. The Harris response depends directly on:

A. Eigenvalues of M  
B. Image size  
C. Pixel coordinates  
D. Descriptor length

**Answer:** A

---

# Window Functions

### 23. Why is a Gaussian window preferred over a uniform window?

A. Faster computation  
B. Rotation invariance  
C. Better colour representation  
D. Lower memory use

**Answer:** B

---

# Scale Selection

### 24. A key limitation of the Harris detector is that it is:

A. Not rotation invariant  
B. Not scale invariant  
C. Not translation invariant  
D. Not local

**Answer:** B

---

### 25. The Laplacian of Gaussian (LoG) is commonly used for:

A. Feature matching  
B. Scale selection  
C. Histogram equalisation  
D. Edge suppression

**Answer:** B

---

### 26. The Laplacian operator is:

A. First derivative  
B. Product of derivatives  
C. Sum of second derivatives  
D. Integral of gradients

**Answer:** C

---

### 27. Why is smoothing applied before the Laplacian?

A. To increase contrast  
B. To reduce noise sensitivity  
C. To improve colour balance  
D. To detect corners

**Answer:** B

---

# Harris-Laplace and DoG

### 28. Harris-Laplace combines:

A. Harris corners and LoG scale selection  
B. Harris corners and SSD matching  
C. DoG and homographies  
D. SIFT and RANSAC

**Answer:** A

---

### 29. Difference of Gaussians (DoG) is primarily used because it:

A. Is more accurate than LoG  
B. Approximates LoG efficiently  
C. Computes exact second derivatives  
D. Produces scale-invariant descriptors

**Answer:** B

---

### 30. Which feature detector uses DoG for feature detection?

A. Harris  
B. FAST  
C. SIFT  
D. ORB

**Answer:** C

---

# SIFT

### 31. SIFT achieves invariance to:

A. Translation only  
B. Translation and rotation only  
C. Translation, rotation, and scale  
D. Illumination only

**Answer:** C

---

### 32. In SIFT, candidate feature locations are initially detected using:

A. Harris corners  
B. DoG extrema  
C. SSD matching  
D. Homographies

**Answer:** B

---

### 33. Features with strong edge responses are rejected because:

A. They are computationally expensive  
B. They are poorly localised  
C. They lack gradients  
D. They are not scale invariant

**Answer:** B

---

### 34. The dominant orientation in SIFT is determined from:

A. Pixel intensities  
B. Homography matrices  
C. Gradient orientation histograms  
D. Laplacian values

**Answer:** C

---

### 35. The standard SIFT descriptor has:

A. 16 dimensions  
B. 32 dimensions  
C. 64 dimensions  
D. 128 dimensions

**Answer:** D

---

### 36. For each detected SIFT feature, the algorithm stores:

A. Position only  
B. Position and scale only  
C. Position, scale, orientation, and descriptor  
D. Descriptor only

**Answer:** C

---

# Matching Features

### 37. The simplest descriptor matching method uses:

A. Determinant comparison  
B. SSD distance  
C. LoG response  
D. Trace comparison

**Answer:** B

---

### 38. Why can SSD alone produce incorrect matches?

A. It ignores gradients  
B. Multiple descriptors may have similarly small distances  
C. It requires homographies  
D. It is not invariant to translation

**Answer:** B

---

### 39. Lowe's ratio test compares:

A. Best and worst matches  
B. First image and second image  
C. Best and second-best descriptor matches  
D. Harris and SIFT scores

**Answer:** C

---

### 40. A descriptor match is generally considered reliable when:

A. Best and second-best matches are very similar  
B. Best match is significantly better than second-best match  
C. SSD is maximised  
D. Harris response is negative

**Answer:** B

# Segmentation Fundamentals

### 1. The primary goal of image segmentation is to:

A. Detect edges only  
B. Gather features that belong together  
C. Compress images  
D. Increase image resolution

**Answer:** B

---

### 2. Which of the following is an example of segmentation?

A. Thresholding  
B. Histogram equalisation  
C. Convolution  
D. Fourier transform

**Answer:** A

---

### 3. Which application commonly relies on segmentation?

A. Snapchat stickers  
B. JPEG compression  
C. Sobel filtering  
D. Demosaicing

**Answer:** A

---

### 4. Figure-ground separation refers to:

A. Feature detection  
B. Distinguishing objects from background  
C. Edge enhancement  
D. Colour correction

**Answer:** B

---

# Gestalt Theory

### 5. The Gestalt school is primarily associated with:

A. Computer graphics  
B. Psychology  
C. Statistics  
D. Robotics

**Answer:** B

---

### 6. The Gestalt principle "The whole is greater than the sum of its parts" means:

A. Objects are always larger than their components  
B. Relationships between parts can create additional meaning  
C. Segmentation should use larger images  
D. All features must be grouped

**Answer:** B

---

### 7. Which concept is commonly used as an example of Gestalt perception?

A. Gaussian filtering  
B. Negative space  
C. SSD matching  
D. Homographies

**Answer:** B

---

# Grouping in Vision

### 8. In a top-down approach, pixels belong together because:

A. They have similar colours  
B. They have similar textures  
C. They originate from the same object  
D. They are adjacent

**Answer:** C

---

### 9. In a bottom-up approach, pixels belong together because they:

A. Are manually labelled  
B. Come from the same object  
C. Look similar  
D. Have the same coordinates

**Answer:** C

---

### 10. Why is segmentation difficult to evaluate objectively?

A. Computers cannot segment images  
B. Humans do not always agree on correct segmentation  
C. Images are always noisy  
D. Ground truth is easy to define

**Answer:** B

---

### 11. Superpixels are primarily used to:

A. Increase image resolution  
B. Identify likely uniform regions  
C. Remove noise  
D. Detect corners

**Answer:** B

---

### 12. A common issue with superpixels is:

A. Under-segmentation  
B. Over-segmentation  
C. Aliasing  
D. Scale invariance

**Answer:** B

---

# k-Means Clustering

### 13. k-Means clustering is an example of:

A. Supervised learning  
B. Unsupervised learning  
C. Reinforcement learning  
D. Feature detection

**Answer:** B

---

### 14. The objective of k-Means is to minimise:

A. Cross entropy  
B. SSD to nearest cluster centre  
C. Image variance  
D. Covariance

**Answer:** B

---

### 15. In k-Means, after assigning points to clusters, cluster centres are updated by:

A. Choosing random points  
B. Taking the mean of assigned points  
C. Computing covariance  
D. Taking the median

**Answer:** B

---

### 16. Which step occurs first in k-Means?

A. Assign points to clusters  
B. Compute SSD  
C. Initialise cluster centres  
D. Compute covariance matrices

**Answer:** C

---

### 17. Which property of k-Means is true?

A. Always finds the global optimum  
B. Converges to some solution  
C. Does not require k  
D. Handles arbitrary cluster shapes well

**Answer:** B

---

### 18. k-Means is particularly sensitive to:

A. Rotation  
B. Scale  
C. Outliers  
D. Translation

**Answer:** C

---

### 19. k-Means naturally works best when clusters are:

A. Ring-shaped  
B. Arbitrary  
C. Spherical  
D. Hierarchical

**Answer:** C

---

### 20. Which is a disadvantage of k-Means?

A. Computationally expensive  
B. Requires the number of clusters k  
C. Requires labelled training data  
D. Cannot process images

**Answer:** B

---

# Feature Spaces

### 21. Using (r,g,b) values gives a:

A. 1D feature space  
B. 2D feature space  
C. 3D feature space  
D. 5D feature space

**Answer:** C

---

### 22. Using (r,g,b,x,y) encourages:

A. Scale invariance  
B. Spatial coherence  
C. Rotation invariance  
D. Edge detection

**Answer:** B

---

### 23. Intensity-only clustering corresponds to:

A. 1D feature space  
B. 2D feature space  
C. 3D feature space  
D. 5D feature space

**Answer:** A

---

# Gaussian Mixture Models

### 24. A Gaussian Mixture Model represents clusters using:

A. Means only  
B. Histograms  
C. Gaussian distributions  
D. Thresholds

**Answer:** C

---

### 25. A multivariate Gaussian is defined by:

A. Mean only  
B. Mean and covariance  
C. Variance only  
D. SSD and covariance

**Answer:** B

---

### 26. The covariance matrix of a Gaussian describes its:

A. Mean position  
B. Size only  
C. Shape and orientation  
D. Number of points

**Answer:** C

---

### 27. Which advantage do GMMs have over k-Means?

A. Faster computation  
B. No parameters required  
C. Can model non-spherical clusters  
D. No iteration required

**Answer:** C

---

### 28. Data points more than approximately three standard deviations from the mean are often considered:

A. Cluster centres  
B. Inliers  
C. Outliers  
D. Superpixels

**Answer:** C

---

# Mixture of Gaussians

### 29. In a Mixture of Gaussians model, each Gaussian component is selected with probability:

A. σ  
B. μ  
C. α (or π)  
D. SSD

**Answer:** C

---

### 30. The likelihood of observing a point x in a MoG is:

A. Product of all Gaussian densities  
B. Weighted sum of Gaussian densities  
C. Maximum Gaussian density only  
D. Mean Gaussian density

**Answer:** B

---

# Expectation Maximisation

### 31. The goal of Expectation Maximisation (EM) is to:

A. Maximise likelihood  
B. Minimise image intensity  
C. Detect corners  
D. Compute homographies

**Answer:** A

---

### 32. In the E-step of EM:

A. Cluster parameters are updated  
B. Ownership probabilities are estimated  
C. Features are detected  
D. SSD is minimised directly

**Answer:** B

---

### 33. In the M-step of EM:

A. Ownership probabilities are updated  
B. Features are matched  
C. Model parameters are updated  
D. Outliers are removed

**Answer:** C

---

### 34. EM alternates between:

A. Detection and matching  
B. E-step and M-step  
C. Thresholding and smoothing  
D. Segmentation and stitching

**Answer:** B

---

# Mean Shift

### 35. Mean Shift works by repeatedly moving a window toward:

A. The nearest edge  
B. The image centre  
C. The mean of points inside the window  
D. The largest cluster

**Answer:** C

---

### 36. Mean Shift requires selecting:

A. Number of clusters k  
B. Covariance matrix Σ  
C. Window size h  
D. Learning rate

**Answer:** C

---

### 37. A major advantage of Mean Shift is that it:

A. Requires knowing k beforehand  
B. Assumes spherical clusters  
C. Is model-free  
D. Requires labelled data

**Answer:** C

---

### 38. Mean Shift is generally:

A. Sensitive to outliers  
B. Robust to outliers  
C. Unable to find clusters  
D. Supervised

**Answer:** B

---

# GrabCut

### 39. GrabCut requires the user to initially provide:

A. Feature descriptors  
B. A bounding box around the object  
C. Cluster centres  
D. Edge maps

**Answer:** B

---

### 40. Initially, GrabCut assumes:

A. Everything is background  
B. Everything is foreground  
C. Inside box = foreground, outside = background  
D. Inside box = background, outside = foreground

**Answer:** C

---

### 41. GrabCut alternates between:

A. Thresholding and smoothing  
B. Graph-cut segmentation and foreground/background modelling  
C. SIFT and RANSAC  
D. EM and k-Means

**Answer:** B

---

### 42. GrabCut models foreground and background using:

A. Harris corners  
B. Homographies  
C. Gaussian Mixture Models  
D. Mean Shift

**Answer:** C

---

### 43. Superpixels improve GrabCut primarily by:

A. Increasing accuracy of colour values  
B. Improving computational performance  
C. Reducing image size  
D. Increasing contrast

**Answer:** B

---

### 44. Which metrics were specifically mentioned for evaluating segmentation performance?

A. Precision and Recall  
B. SSD and MSE  
C. TPR and FPR  
D. Accuracy and Entropy

**Answer:** A