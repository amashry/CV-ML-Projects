# Visual Odometry Project
This repository contains the implementation of a Visual Odometry project. The project aims to reconstruct the three-dimensional (3D) trajectory of a camera mounted on a vehicle using a sequence of frames captured during a driving sequence. The dataset used is collected by Oxford Robotics Institute. Two distinct approaches are implemented to achieve the objective: one leveraging built-in functions provided by openCV, and the other focusing on custom functions created for this project without using off-the-shelf openCV functions. 

## Table of Contents
- [Dataset](#dataset)
- [Results](#results)
- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Visual Odometry Using OpenCV Built-In Functions](#visual-odometry-using-opencv-built-in-functions)
- [Visual Odometry Using Custom Implementation](#visual-odometry-using-custom-implementation)

## Dataset 
A sequence of 377 images captured during a driving sequence from a car driving around a block in a loop as shown below. Note that the GIF below shows the image sequence after using the camera intrinsic model calibration for image rectification and for removing distortion.  

![oxford_car_dataset_undistorted (1)](https://github.com/amashry/CV-ML-Projects/assets/98168605/ee071929-5e4c-42d0-a655-717d0762cdbd)

## Results

Both the OpenCV and the custom implementations provide a 2D and 3D trajectory of the camera's movement over the driving sequence. These trajectories serve as the camera's visual odometry.

<table>
<tr>
<td>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/51bb8473-e891-42ba-8280-b458566b3e20" alt="Camera 2D Trajectory" width="450"/>
</td>
<td>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/fa220c4f-c582-4bcd-a263-aba2da70a67a" alt="Camera 3D Trajectory" width="450"/>
</td>
</tr>
</table>

## Project Overview
Visual odometry is an important concept in robotic perception, used to estimate the trajectory of a robot (or more precisely, the robot's camera). This project seeks to reconstruct the camera's trajectory, which, by implication, represents the movement path of the vehicle itself. 

The implementation process involves several key steps:
- Identifying shared keypoints across the series of frames.
- Estimating the fundamental and essential matrices between frames.
- Decomposing the essential matrices into translation and rotation parameters.
- Plotting the camera center to visualize the 3D trajectory.

Two routes are implemented to perform these steps. The first approach relies on openCV's built-in functions, while the second uses custom functions created for this project. The motivation behind the second approach is to gain a deeper understanding of the underlying processes and to explore the potential for customization and optimization beyond the capabilities provided by off-the-shelf functions. 

<figure>
    <img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/0e22e2ee-9f3b-4da0-9639-7845685ef465" alt="Key Feature Matching between frames"/>
    <figcaption>Key Feature Matching between consecutive frames in the video sequence.</figcaption>
</figure>

## Getting Started
To get started with the project, clone this repository to your local machine. The project requires Python 3.6 or higher and the following Python packages installed:
- OpenCV
- NumPy
- Matplotlib


## Project Structure
The repository contains the following files:

- `custom_implementation_vio_final_project.py`: Contains the custom implementation of the visual odometry pipeline. This script uses manually coded functions to estimate the fundamental and essential matrices and to estimate the rotation and translation of the camera center.

- `OpenCV_implementation_vio_final_project.py`: Contains the implementation of the visual odometry pipeline using openCV's built-in functions. 

Both scripts produce plots visualizing the 3D trajectory of the camera center over the driving sequence.

## Visual Odometry Using OpenCV Built-In Functions
This approach leverages various built-in functions provided by openCV, an open-source computer vision and machine learning software library. Key steps in this implementation include:

1. Camera calibration: `ReadCameraModel`
2. Loading and undistorting images: `cv2.imread`, `cv2.cvtColor`, `UndistortImage`
3. Identifying keypoints and matches: `cv2.xfeatures2d.SIFT_create`, `cv2.BFMatcher`
4. Estimating the fundamental matrix: `cv2.findFundamentalMat`
5. Estimating the essential matrix: `cv2.findEssentialMat`
6. Estimating camera motion: `cv2.recoverPose`
7. Computing the visual odometry
8. Trajectory visualization: `matplotlib.pyplot.plot`

More detailed information about each step can be found in the full technical report.

## Visual Odometry Using Custom Implementation
This approach employs custom functions created for this project. These functions perform the same steps as in the OpenCV approach but are implemented manually to gain a deeper understanding of the process. The steps include:

1. Reading the Camera Model: `ReadCameraModel`
2. Loading and Undistorting Image: `load_and_undistort_image`
3. Finding Keypoints and Matches: `find_keypoints_and_matches`
4. Generating Zhang's Grid: `generate_zhang_grid`
5. Implementing Eight-Point Algorithm: `eight_point_algorithm`
6. Estimating Essential Matrix: `estimate_essential_matrix`
7. Calculating Camera Pose: `calculate_camera_pose`
8. Implementing Linear Triangulation: `linear_triangulation`
9. Calculating Visual Odometry to Reconstruct the Trajectory: `visual_odometry`

More detailed information about each step can be found in the full technical report.
