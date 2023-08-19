# computer-vision-machine-learning-projects

This repository is a robust showcase of applications and projects in Computer Vision and Machine Learning, which have been part of ML/CV graduate courses that I took at University of Maryland (UMD).  

# Repository Overview 

This repository documents a series of image processing, computer vision and machine learning tasks, encapsulated within mini-projects and final projects. Projects implemented within the computer vision class has been labeled with `CV` in the title. Projects that has been implemented while taking the graduate Machine Learning class has been also labeled with `ML` in the title. 

The following summarizes the content of this repository:

# Computer Vision Projects 
## 1. CV Mini Projects 

### Project 1 - Hybrid and Pyramid Images 

The first homework introduces two image processing techniques: Hybrid Image creation and Pyramid Image construction. 

- **Hybrid Image**: Combines two images by applying low-pass filtering to one and high-pass filtering to the other. The hybrid image appears to be one picture when viewed up close and another when viewed from afar. This task leverages several Python libraries such as cv2, numpy, pandas, skimage, PIL, matplotlib, and scipy.
- **Pyramid Image**: Constructs Gaussian and Laplacian pyramids from an image. Each level of the pyramid has half the resolution of its predecessor. The pyramids are then visualized both as intensity images and as the log magnitude of their Fast Fourier Transform (FFT).

![download (1)](https://github.com/amashry/CV-ML-Projects/assets/98168605/ebaecd59-b48b-4945-bea4-2779a6ff450c)

### Project 2: Keypoint Selection and Feature Tracking 

The second homework deals with tracking features in an image sequence using Harris corner detection for keypoint selection and the Kanade-Lucas-Tomasi (KLT) algorithm for feature tracking.

### Project 3: Shape Alignment and Object Instance Recognition 

The third homework assignment focuses on the alignment of two sets of points using the Iterative Closest Point (ICP) algorithm and object instance recognition using the Lowe's Scale Invariant Feature Transform (SIFT) algorithm.

### Project 4: Epipolar Geometry and Image Stitching 

In this assignment, the focus is on epipolar geometry and the application of the Normalized 8-point algorithm with RANSAC to estimate the Fundamental Matrix. It also involves image stitching, a technique to combine multiple images with overlapping fields of view to create a wide-angle panorama.

### Project 5: Affine Structure from Motion 

The fifth homework explores the topic of Structure from Motion (SfM), a technique for estimating 3D structures from 2D image sequences. The task was to recover a 3D point cloud from an image sequence using the Affine Structure from Motion algorithm.

### Project 6: Image Classification and Semantic Segmentation 

The sixth homework is divided into two parts:
- **Part 1**: Involves training an image classifier using the CIFAR-10 dataset and the PyTorch library. The classifier is trained to correctly identify images across 10 different classes.
- **Part 2**: Implements a semantic segmentation model that assigns a class to each pixel in an image. This part introduces the concepts of semantic segmentation in computer vision.

## 2. CV Final Project: Visual Odometry 

The final project focuses on implementing visual odometry to reconstruct the 3D trajectory of a camera mounted on a vehicle. The project employs various computer vision techniques, such as keypoint detection, fundamental and essential matrix estimation, and decomposition into translation and rotation parameters. Two distinct approaches are implemented: one that leverages built-in functions provided by OpenCV and a custom approach not relying on openCV built-in functions. The final product is a 3D plot visualizing the trajectory of the camera.

<table>
<tr>
<td>
<figcaption>
  Undistorted Sequence GIF
</figcaption>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/ee071929-5e4c-42d0-a655-717d0762cdbd" alt="Undistorted Sequence GIF" width="450"/>
</td>
<td>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/51bb8473-e891-42ba-8280-b458566b3e20" alt="Camera 2D Trajectory" width="450"/>
</td>
<td>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/fa220c4f-c582-4bcd-a263-aba2da70a67a" alt="Camera 3D Trajectory" width="450"/>
</td>
</tr>
</table>


## TODO's
1. Add images to the hws that don't have images to describe
2. Add images to the project readme
3. Add images to the main readme to visualize different hws and show results of each one.
