# CV-mini-project 4

## Part 1: Epipolar Geometry (30 Points)

In the first part of the homework, we focused on the concept of Epipolar Geometry and the implementation of the Normalized 8-point algorithm with RANSAC to automatically estimate the Fundamental Matrix (F).

![Epipolar Geometry](https://www.cs.umd.edu/class/spring2023/cmsc426-0201/hw_images/epipolar_geometry.jpg)

### Brief Overview

The algorithm began with loading the data provided (`matches.mat`) which included detected Harris corners row-column positions for two images and their corresponding matched pairs. We implemented several helper functions to support the process of estimating the fundamental matrix, which include `ransacF()`, `getInliers()`, `normalize()`, `computeF()`, and `plot_epipolar_lines()`.

In `ransacF()`, we performed RANSAC based 8-point algorithm, where we utilized a normalized random sample of 8 matched points to calculate a candidate fundamental matrix, and then computed the inliers that satisfy the epipolar constraint.

The function `getInliers()` implemented the criteria for checking inliers, which is based on a geometric distance between corresponding points and their corresponding epipolar lines.

The `normalize()` function was used to find the transformation to make the mean zero and variance sqrt(2), preparing the data for further processing.

The `computeF()` function calculated the fundamental matrix from corresponding points using Singular Value Decomposition (SVD), while `plot_epipolar_lines()` function is used for plotting the images with corresponding epipolar lines.

Finally, we estimated the fundamental matrix F, normalized it so the last entry is 1, and visualized the images with corresponding epipolar lines using the `plot_epipolar_lines()` function.

The implementation demonstrated the application of computer vision theory to real-world problem-solving, especially in the case of image alignment and stereoscopic vision.

## Part 2: Image Stitching (30 Points)

In the second part of the homework, we worked on Image Stitching, which is a technique used to combine multiple images with overlapping fields of view to produce a wide-angle panorama.

![Image Stitching](https://www.cs.umd.edu/class/spring2023/cmsc426-0201/hw_images/image_stitching.png)

### Brief Overview

We outlined the image stitching process into the following steps:

1. **Detect keypoints**: Detected the keypoints in the input images using a feature detection algorithm.
2. **Match keypoints**: Matched the keypoints across the two images using a matching algorithm.
3. **Estimate homography with matched keypoints (using RANSAC)**: After getting the matched keypoints, we used these matched points to estimate the homography that aligns one image with the other.
4. **Combine images**: Lastly, we combined the images using the estimated homography.

In the code, the function `drawMatches()` was used to draw matches between two images using the detected keypoints. The `plot_matches()` function was used to plot the matched keypoints across two consecutive images.

The homography between two images was estimated using `est_homography()`. This function used the Singular Value Decomposition (SVD) method to find the homography matrix that best aligns the matched points in the source and destination images.

The `apply_homography()` function was used to apply the estimated homography to the source points and transformed them into the coordinate frame of the destination image.

This section demonstrated the application of keypoint detection, matching, and homography estimation to stitch together multiple images into a single panorama. This is an essential technique in many applications including virtual reality, video stitching, and panoramic photography.
