# CV-mini-project 3 

## Introduction
This README aims to document the methods and procedures involved in HW3, which focused on two major tasks: Shape Alignment and Object Instance Recognition. The goal of the project was to apply methods like Iterative Closest Point (ICP) and SIFT (Scale Invariant Feature Transform) to solve these real-world problems. 

## Part 1: Shape Alignment
In this task, we built a function to align two sets of points using the ICP algorithm. Our function computes an affine image transformation that maps non-zero points in one image to the corresponding points in another image.

### Method Overview:
Our main function, `align_shape()`, takes in two images and returns an aligned version of the first image that matches the shape of the second one. 

The process begins by padding the input images to accommodate transformations without cropping essential parts of the image. Then, a transformation matrix `T` is initialized based on the means and standard deviations of the images, allowing for the alignment of the centers of mass and scaling the shapes. 

After the initial setup, the algorithm enters a loop where it applies the ICP algorithm. In each iteration, the first image is transformed using the current transformation matrix `T`, and the closest points between this transformed image and the second image are found using a nearest neighbors search. The transformation matrix is then updated by solving a linear system to align the corresponding points in both images. The iterations continue until either the maximum number of iterations is reached or the error between successive iterations falls below a threshold.

The final result is achieved by applying the refined affine transformation matrix to the first image and cropping the padded regions.

### Implementation:
The implementation includes several helper functions for error calculation (`evalAlignment()`) and visualization (`displayAlignment()`). They serve to compute the alignment error and display the alignment result, respectively. The main `align_shape()` function makes extensive use of libraries like `numpy` for array and matrix operations, `sklearn` for nearest neighbors search, and `skimage` for image transformations.

Finally, we tested our alignment function on ten pairs of images, recording the alignment error and the runtime for each pair. The results demonstrate the function's effectiveness and efficiency.

## Part 2: Object Instance Recognition
The second task involved implementing an object instance recognition system based on the Lowe's SIFT algorithm. 

### Method Overview:
For object recognition, we used two methods. One was based on the built-in SIFT feature extractor and feature matching capabilities of OpenCV. The other was an implementation of Lowe's method, where we computed SIFT descriptors for the keypoints in two images and matched the descriptors based on a nearest-neighbor distance ratio test or a distance threshold test. 

### Implementation:
Our implementation in this part made extensive use of libraries like `cv2` for SIFT feature extraction and feature matching, and `numpy` for array operations.

In the OpenCV-based method, we first detected keypoints and computed their SIFT descriptors using OpenCV's `SIFT_create().detectAndCompute()`. We then matched the descriptors using a brute-force matcher and displayed the top 30 matches.

In the Lowe-style method, we defined two main functions: `find_matches()` and `plot_matches()`. `find_matches()` matches descriptors from two images based on either the ratio of distances to the two nearest neighbors (ratio test) or a distance threshold (distance test). `plot_matches()` displays the matched keypoints in two images and draws lines connecting corresponding keypoints.

As in the first part, we tested our functions on several pairs of images and visually examined the quality of matches. 

---

By accomplishing these tasks, we gained valuable experience in shape alignment and object instance recognition, developing robust functions and systems that handle real-world images effectively and efficiently.
