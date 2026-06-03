Image stitching
Local Features
Segmentation
Hough Transform
Stereo
Model based vision
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

# Hough Line Transform

### 1. The Hough Line Transform is typically applied to:

A. Raw colour images  
B. Edge images  
C. Segmented images only  
D. Histograms

**Answer:** B

---

### 2. A common preprocessing pipeline for Hough line detection is:

A. Threshold → Blur  
B. Gaussian smoothing → Edge detection  
C. Edge detection → Gaussian smoothing  
D. Histogram equalisation → Segmentation

**Answer:** B

---

### 3. The goal of the Hough Line Transform is to:

A. Detect circles  
B. Detect corners  
C. Find points that lie on the same line  
D. Compute homographies

**Answer:** C

---

### 4. Why is a threshold needed in the Hough Transform?

A. To remove noise  
B. To determine how many points must support a line  
C. To estimate line slope  
D. To compute gradients

**Answer:** B

---

### 5. If the threshold were set to 2 points, then:

A. No lines would be detected  
B. Only vertical lines would be detected  
C. Any two points could define a line  
D. Only horizontal lines would be detected

**Answer:** C

---

### 6. In the Cartesian Hough Transform, each image point maps to:

A. A point in parameter space  
B. A line in parameter space  
C. A circle in parameter space  
D. A histogram

**Answer:** B

---

### 7. In the slope-intercept formulation, the line equation is rearranged as:

A. y=mx+c
B. m=xy+c
C. c=−xm+y
D. c=mx−y

**Answer:** C

---

### 8. In Hough space, a line in the image becomes:

A. A point  
B. A circle  
C. A curve/line  
D. An edge

**Answer:** C

---

### 9. A strong candidate line is indicated by:

A. A low accumulator value  
B. A maximum where many curves intersect  
C. A minimum SSD  
D. A large image gradient

**Answer:** B

---

### 10. The accumulator array stores:

A. Pixel colours  
B. Edge gradients  
C. Votes for parameter combinations  
D. Image intensities

**Answer:** C

---

# Polar Hough Transform

### 11. The main problem with the slope-intercept representation is:

A. It cannot detect horizontal lines  
B. It cannot detect circles  
C. Vertical lines cause division-by-zero issues  
D. It requires colour images

**Answer:** C

---

### 12. The polar representation describes a line using:

A. (x,y)
B. (m,c)
C. (r,θ) 
D. (a,b)

**Answer:** C

---

### 13. The primary advantage of the polar Hough Transform is:

A. Faster execution  
B. Better colour handling  
C. Correct handling of vertical lines  
D. Scale invariance

**Answer:** C

---

### 14. In polar form, a line is represented by:

A. Distance from origin and angle  
B. Slope and intercept  
C. Centre and radius  
D. Gradient magnitude and orientation

**Answer:** A

---

# Hough Circles

### 15. The equation of a circle with centre (a,b) and radius r is:

A. ax+by=r
B. (x−a)2+(y−b)2=r2
C. y=mx+c
D. x2+y2=r

**Answer:** B

---

### 16. For fixed-radius circle detection, the accumulator space is:

A. 1D  
B. 2D  
C. 3D  
D. 4D

**Answer:** B

---

### 17. For arbitrary-radius circle detection, the accumulator space becomes:

A. 2D  
B. 3D  
C. 4D  
D. 5D

**Answer:** B

---

### 18. In circle detection, accumulator peaks correspond to:

A. Edge orientations  
B. Circle centres  
C. Circle radii only  
D. Gradient magnitudes

**Answer:** B

---

### 19. The parameters of a circle are:

A. m,c
B. r,θ
C. a,b,r
D. x,y,m

**Answer:** C

---

# Generalised Hough Transform

### 20. The Generalised Hough Transform is designed to detect:

A. Lines only  
B. Circles only  
C. Arbitrary shapes  
D. Corners only

**Answer:** C

---

### 21. Unlike line and circle Hough transforms, the Generalised Hough Transform uses:

A. Edge pixels only  
B. Pixel intensity only  
C. Edge pixels and edge directions  
D. Colour histograms

**Answer:** C

---

### 22. The R-table stores:

A. Circle radii  
B. Line slopes  
C. Shape information indexed by edge direction  
D. Pixel intensities

**Answer:** C

---

### 23. For each contour point in the template shape, the algorithm records:

A. RGB colour  
B. Edge direction and (r,α)(r,\alpha)(r,α)  
C. Harris response  
D. Homography parameters

**Answer:** B

---

### 24. The purpose of the R-table is to:

A. Store accumulator votes  
B. Describe the shape template  
C. Compute gradients  
D. Remove noise

**Answer:** B

---

### 25. To detect objects at arbitrary scales and orientations, the Generalised Hough Transform requires:

A. A 2D accumulator  
B. A 3D accumulator  
C. A 4D accumulator including scale and orientation  
D. No accumulator

**Answer:** C

---

# Harder Exam Questions

### 26. Why does the Hough Transform remain effective when some edge pixels are missing?

A. It uses machine learning  
B. Detection is based on voting from many pixels  
C. It computes descriptors  
D. It uses homographies

**Answer:** B

---

### 27. What does a high value in the accumulator array represent?

A. Strong image gradients  
B. Many votes supporting a parameter combination  
C. Large object size  
D. High pixel intensity

**Answer:** B

---

### 28. In the Generalised Hough Transform, each edge pixel votes for:

A. Possible object centres  
B. Possible radii only  
C. Possible line slopes  
D. Possible colours

**Answer:** A

---

### 29. Which Hough variant requires a separate model description for each object type?

A. Standard line Hough  
B. Polar Hough  
C. Circle Hough  
D. Generalised Hough

**Answer:** D

---

### 30. Compared with line and circle Hough transforms, the Generalised Hough Transform is:

A. More flexible but computationally more expensive  
B. Less flexible but faster  
C. Restricted to convex objects  
D. Restricted to circles

**Answer:** A


# Motivation & Fundamentals

### 1. The primary goal of stereo vision is:

A. Image compression  
B. Object classification  
C. Recovery of 3D structure  
D. Edge detection

**Answer:** C

---

### 2. Why is a single image insufficient for reliable 3D reconstruction?

A. Images are noisy  
B. Perspective projection is inherently ambiguous  
C. Cameras have low resolution  
D. Edges are difficult to detect

**Answer:** B

---

### 3. Which of the following is a visual depth cue?

A. Shading  
B. Texture  
C. Perspective  
D. All of the above

**Answer:** D

---

### 4. Stereo viewing estimates depth using:

A. Filtering  
B. Segmentation  
C. Triangulation  
D. Thresholding

**Answer:** C

---

### 5. Triangulation requires:

A. Correspondences and camera pose  
B. Homographies only  
C. Segmentation and filtering  
D. Edge detection only

**Answer:** A

---

# Simple Stereo Geometry

### 6. The line connecting two camera viewpoints is called the:

A. Epipolar line  
B. Optical axis  
C. Baseline  
D. Scanline

**Answer:** C

---

### 7. In a simple stereo setup, both cameras are assumed to have:

A. Different focal lengths  
B. The same focal length  
C. No focal length  
D. Variable focal lengths

**Answer:** B

---

### 8. Increasing the baseline generally makes depth estimation:

A. More accurate  
B. Less accurate  
C. Impossible  
D. Independent of depth

**Answer:** A

---

### 9. Which quantity is ultimately being recovered in simple stereo geometry?

A. Focal length  
B. Disparity  
C. Depth (Z)  
D. Brightness

**Answer:** C

---

### 10. Disparity is:

A. Difference in intensity  
B. Difference in position between corresponding image points  
C. Difference in focal lengths  
D. Difference in camera orientation

**Answer:** B

---

### 11. Depth is inversely proportional to:

A. Focal length  
B. Baseline  
C. Disparity  
D. Brightness

**Answer:** C

---

### 12. If disparity increases, depth:

A. Increases  
B. Decreases  
C. Remains unchanged  
D. Becomes undefined

**Answer:** B

---

# Stereo Pipeline

### 13. Which component of stereo analysis is generally considered the hardest?

A. Reconstruction  
B. Calibration  
C. Correspondence finding  
D. Projection

**Answer:** C

---

### 14. Reconstruction refers to:

A. Finding matching points  
B. Estimating camera parameters  
C. Calculating scene coordinates  
D. Detecting edges

**Answer:** C

---

### 15. Calibration determines:

A. Object identities  
B. Camera parameters  
C. Edge locations  
D. Segmentation masks

**Answer:** B

---

# Epipolar Geometry

### 16. The epipolar constraint states that corresponding points lie on:

A. The same circle  
B. The same line  
C. The same plane only  
D. The same object

**Answer:** B

---

### 17. In the simple stereo setup, the epipolar search is:

A. Vertical only  
B. Diagonal only  
C. Horizontal only  
D. 2D

**Answer:** C

---

### 18. The epipolar constraint reduces matching from:

A. 1D to 0D  
B. 2D to 1D  
C. 3D to 2D  
D. 2D to 3D

**Answer:** B

---

### 19. Why are horizontal edges difficult to match?

A. They are too bright  
B. They provide poor localisation along the epipolar line  
C. They violate epipolar geometry  
D. They cannot be detected

**Answer:** B

---

### 20. Which alternative is often used instead of edge matching?

A. Thresholding  
B. Local features/descriptors  
C. Histograms  
D. Gaussian filtering

**Answer:** B

---

# Moravec Operator

### 21. The Moravec operator is designed to find:

A. Lines  
B. Blobs  
C. Interest points  
D. Circles

**Answer:** C

---

### 22. The Moravec operator computes:

A. Maximum directional change  
B. Average intensity  
C. Minimum directional intensity variation  
D. Correlation only

**Answer:** C

---

### 23. Taking the minimum response helps reject:

A. Corners  
B. Noise  
C. Edges  
D. Features

**Answer:** C

---

# General Stereo Geometry

### 24. In the general stereo case, cameras:

A. Must have parallel optical axes  
B. May have arbitrary orientations  
C. Must have equal baselines  
D. Must be rectified

**Answer:** B

---

### 25. Calibration estimates:

A. Rotation and translation relationships  
B. Descriptor vectors  
C. Image gradients  
D. Segmentation labels

**Answer:** A

---

### 26. The coordinate systems of cameras are related by:

A. Histograms  
B. Rotation matrices and translation vectors  
C. SSD distances  
D. Gaussian models

**Answer:** B

---

# Stereo Reconstruction

### 27. In ideal stereo reconstruction, rays from corresponding points:

A. Are parallel  
B. Intersect at the 3D point  
C. Form circles  
D. Remain in image coordinates

**Answer:** B

---

### 28. In practice, rays often fail to intersect due to:

A. Noise and measurement errors  
B. Perspective projection  
C. Rotation matrices  
D. Rectification

**Answer:** A

---

### 29. A common solution when rays do not intersect exactly is to use:

A. Mean shift  
B. Graph cuts  
C. Midpoint of the closest points  
D. Thresholding

**Answer:** C

---

# Essential Matrix

### 30. The Essential Matrix relates:

A. Camera parameters only  
B. Corresponding image points between calibrated cameras  
C. Intensities between images  
D. Edge responses

**Answer:** B

---

### 31. The Essential Matrix requires:

A. Uncalibrated cameras  
B. Calibrated cameras  
C. Parallel cameras only  
D. Rectified images only

**Answer:** B

---

### 32. The Essential Matrix is commonly denoted by:

A. H  
B. F  
C. E  
D. M

**Answer:** C

---

### 33. The Essential Matrix constrains a corresponding point to lie on:

A. A circle  
B. A line  
C. A sphere  
D. A corner

**Answer:** B

---

# Rectification

### 34. Stereo rectification aims to:

A. Remove distortion  
B. Make epipolar lines horizontal  
C. Detect edges  
D. Compute homographies

**Answer:** B

---

### 35. Why is rectification useful?

A. Simplifies correspondence search  
B. Increases image resolution  
C. Removes noise  
D. Estimates focal length

**Answer:** A

---

# Correspondence Search

### 36. Dense correspondence search attempts to find matches for:

A. Selected features only  
B. Every pixel  
C. Corners only  
D. Edges only

**Answer:** B

---

### 37. Sparse correspondence search uses:

A. Every image pixel  
B. Feature descriptors  
C. Histograms only  
D. Segmentation masks

**Answer:** B

---

### 38. Compared with dense matching, sparse matching is generally:

A. More expensive  
B. Less efficient  
C. More efficient  
D. Impossible to rectify

**Answer:** C

---

### 39. Both dense and sparse matching struggle in:

A. High-texture regions  
B. Textureless regions  
C. Rectified images  
D. Calibrated cameras

**Answer:** B

---

### 40. Sparse matching typically handles ______ better than dense matching.

A. Occlusions  
B. Calibration  
C. Projection  
D. Focal length estimation

**Answer:** A

---

# Camera Parameters

### 41. Which is an extrinsic camera parameter?

A. Focal length  
B. Pixel size  
C. Rotation matrix  
D. Principal point offset

**Answer:** C

---

### 42. Which is an intrinsic camera parameter?

A. Translation vector  
B. Rotation matrix  
C. Focal length  
D. Baseline

**Answer:** C

---

### 43. Extrinsic parameters describe:

A. Camera internals  
B. Relationship of camera to the world  
C. Pixel intensities  
D. Descriptor values

**Answer:** B

---

### 44. Intrinsic parameters relate:

A. World coordinates to scene coordinates  
B. Pixel coordinates to image coordinates  
C. Features to descriptors  
D. Images to depth maps

**Answer:** B

---

# Calibration & Uncalibrated Stereo

### 45. Camera calibration is commonly performed using:

A. Random images  
B. Calibration targets with known geometry  
C. Feature descriptors  
D. SSD matching

**Answer:** B

---

### 46. Without calibration, stereo reconstruction can recover:

A. Exact depth  
B. Absolute world coordinates  
C. Relative structure up to scale  
D. Nothing useful

**Answer:** C

---

### 47. The matrix used in uncalibrated stereo is the:

A. Homography matrix  
B. Essential matrix  
C. Fundamental matrix  
D. Covariance matrix

**Answer:** C

---

### 48. According to your notes, how many correspondences are sufficient to estimate the required parameters in uncalibrated stereo?

A. 4  
B. 6  
C. 8  
D. 12

**Answer:** C

### 1. What is the main purpose of Principal Component Analysis (PCA)?

A. Increase the number of variables  
B. Reduce dimensionality while preserving variation  
C. Improve image resolution  
D. Remove all noise from data

**Answer:** B

---

### 2. In the example using Maths and English scores, each point being approximately mapped onto a best-fit line is known as:

A. Clustering  
B. Classification  
C. Dimensionality reduction  
D. Segmentation

**Answer:** C

---

### 3. The first step in PCA is to:

A. Compute eigenvalues  
B. Compute covariance matrix  
C. Assemble data into a matrix  
D. Find the mean shape

**Answer:** C

---

### 4. If there are 24 samples and 2 variables, the data matrix size is:

A. 2 × 24  
B. 24 × 24  
C. 24 × 2  
D. 2 × 2

**Answer:** C

---

### 5. In PCA, the covariance matrix CCC is used to calculate:

A. Shape parameters only  
B. Eigenvalues and eigenvectors  
C. Pose parameters  
D. Texture information

**Answer:** B

---

### 6. What does an eigenvalue λi\lambda_iλi​ represent in PCA?

A. The mean of the data  
B. The number of samples  
C. The variance along eigenvector viv_ivi​  
D. The dimensionality of the data

**Answer:** C

---

### 7. The total variance TTT in PCA is:

A. The largest eigenvalue  
B. The sum of all eigenvalues  
C. The product of all eigenvalues  
D. The determinant of the covariance matrix

**Answer:** B

---

### 8. Why are only the largest KKK eigenvalues typically retained in PCA?

A. To reduce memory requirements while preserving most variance  
B. Because small eigenvalues are always incorrect  
C. To increase dimensionality  
D. To improve image brightness

**Answer:** A

---

### 9. Which of the following is always true for a covariance matrix?

A. It is diagonal  
B. It is triangular  
C. It is symmetric  
D. It is singular

**Answer:** C

---

### 10. Which covariance term is equal to cov(y,x)\text{cov}(y,x)cov(y,x)?

A. var(x)\text{var}(x)var(x)  
B. cov(x,y)\text{cov}(x,y)cov(x,y)  
C. var(y)\text{var}(y)var(y)  
D. None of the above

**Answer:** B

---

### 11. For a square matrix AAA, the eigenvector equation is:

A. Av=vAv=vAv=v  
B. Av=λvAv=\lambda vAv=λv  
C. A+λ=vA+\lambda=vA+λ=v  
D. A=λIA=\lambda IA=λI

**Answer:** B

---

### 12. To find eigenvalues, which equation must be solved?

A. (λI−A)V=0(\lambda I-A)V=0(λI−A)V=0  
B. AV=λAV=\lambdaAV=λ  
C. ∣A−λI∣=0|A-\lambda I|=0∣A−λI∣=0  
D. A−1=0A^{-1}=0A−1=0

**Answer:** C

---

### 13. For the matrix

A=[4213]A=\begin{bmatrix} 4 & 2\\ 1 & 3 \end{bmatrix}A=[41​23​]

what are the eigenvalues?

A. 1 and 3  
B. 4 and 2  
C. 5 and 2  
D. 5 and 3

**Answer:** C

---

### 14. After finding eigenvalues, eigenvectors are found by solving:

A. A−1V=0A^{-1}V=0A−1V=0  
B. (λI−A)V=0(\lambda I-A)V=0(λI−A)V=0  
C. AV=0AV=0AV=0  
D. A+λ=0A+\lambda=0A+λ=0

**Answer:** B

---

### 15. Active Shape Models (ASM) are primarily used for:

A. Rigid object matching only  
B. Non-rigid shape matching  
C. Texture compression  
D. Image enhancement

**Answer:** B

---

### 16. Which transformations are typically allowed in ASM?

A. Scaling only  
B. Rotation only  
C. Translation only  
D. Scaling, rotation, translation, and local shape changes

**Answer:** D

---

### 17. A practical ASM generally requires:

A. One training image  
B. Large amounts of annotated data  
C. No training data  
D. Only synthetic data

**Answer:** B

---

### 18. In the example dataset with 20 landmark points, how many variables are present?

A. 20  
B. 40  
C. 60  
D. 80

**Answer:** B

---

### 19. For 20 points represented by (x,y)(x,y)(x,y) coordinates and 6 training images, the data matrix DDD has dimensions:

A. 6 × 40  
B. 20 × 6  
C. 40 × 6  
D. 40 × 40

**Answer:** C

---

### 20. In ASM, the shape parameter vector is denoted by:

A. xxx  
B. VVV  
C. CCC  
D. bbb

**Answer:** D

---

### 21. Setting all shape parameters bbb to zero produces:

A. A random shape  
B. The mean shape  
C. The largest shape variation  
D. An invalid shape

**Answer:** B

---

### 22. The ASM shape generation equation is:

A. x=V+bx = V + bx=V+b  
B. x=x^+Vbx = \hat{x} + Vbx=x^+Vb  
C. x=CVx = CVx=CV  
D. x=x^bx = \hat{x}bx=x^b

**Answer:** B

---

### 23. In the ASM equation x=x^+Vbx=\hat{x}+Vbx=x^+Vb, x^\hat{x}x^ represents:

A. Covariance matrix  
B. Eigenvector matrix  
C. Mean shape  
D. Shape parameter vector

**Answer:** C

---

### 24. The eigenvectors used in ASM are stored as:

A. Rows of VVV  
B. Columns of VVV  
C. Diagonal entries of VVV  
D. Elements of bbb

**Answer:** B

---

### 25. Why should shape parameters not be set to extreme values?

A. They increase training speed  
B. They produce invalid shapes  
C. They remove eigenvectors  
D. They eliminate variance

**Answer:** B

---

### 26. Which shape variation was associated with b2b_2b2​ in the notes?

A. Looking left/right  
B. Vertical position  
C. Skinny/fat variation  
D. Rotation

**Answer:** C

---

### 27. Which shape variation was associated with b4b_4b4​?

A. Looking left/right  
B. Vertical position  
C. Smile intensity  
D. Face size

**Answer:** A

---

### 28. During ASM fitting, after searching for better feature locations, the next step is to:

A. Recompute covariance matrix  
B. Fit the model to the suggested shape  
C. Delete eigenvectors  
D. Increase image resolution

**Answer:** B

---

### 29. Pose parameters in ASM refer to:

A. Shape deformation only  
B. Texture information  
C. Scaling, rotation, and translation  
D. Eigenvalues and eigenvectors

**Answer:** C

---

### 30. The ASM fitting process repeats until:

A. Maximum variance is reached  
B. Covariance becomes zero  
C. Convergence occurs  
D. Eigenvalues are equal

**Answer:** C

---

### 31. Which medical application was mentioned for Active Shape Models?

A. Detecting tumours only  
B. MRI reconstruction  
C. Positioning an artificial hip  
D. Blood pressure monitoring

**Answer:** C

---

### 32. How does an Active Appearance Model differ from ASM?

A. It uses no landmarks  
B. It only uses texture  
C. It splits the face into triangles and warps texture  
D. It does not use PCA

**Answer:** C

---

### 33. Which statement about PCA and ASM is correct?

A. PCA is used within ASM to model shape variation.  
B. ASM does not use eigenvectors.  
C. PCA requires texture information.  
D. ASM only works on rigid objects.

**Answer:** A

---

### 34. What percentage of total variance is commonly retained in PCA?

A. 25%  
B. 50%  
C. 75%  
D. Around 95%

**Answer:** D

---

### 35. The iterative process of placing a model onto an image and repeatedly improving the fit is known as:

A. Thresholding  
B. Shape fitting  
C. Histogram equalisation  
D. Convolution

**Answer:** B