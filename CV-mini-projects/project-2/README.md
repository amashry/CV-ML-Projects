# CV-mini-project 2

In this homework assignment, I implemented a feature tracker that can track features from an image sequence. The assignment was broken into two main parts: Keypoint Selection and Feature Tracking. 

![Image](https://www.cs.umd.edu/class/spring2023/cmsc426-0201/hw_images/1_overview.png)

### Part 1: Keypoint Selection

The purpose of the keypoint selection was to identify potential features that can be tracked throughout the image sequence. To achieve this, I employed the Harris corner detection algorithm. The `getKeypoints()` function, which I implemented, takes an image and a threshold as input. It then follows the following steps to identify keypoints:

1. The function first converts the image to grayscale and applies a Gaussian filter to smooth the image.
2. The Sobel operator is used to compute the x and y gradients of the smoothed image.
3. The second moment matrix components are computed from these gradients and another Gaussian filter is applied to reduce noise.
4. The Harris corner response is then computed from the second moment matrix components.
5. Non-maximum suppression is applied over a 5x5 window to identify local maxima.
6. Finally, keypoints are identified as pixels that are above a certain threshold and are local maxima.

I used `tau = 0.06` as the threshold and computed keypoints for the first frame of the image sequence.

<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/2a17692d-60c1-4cb7-acdd-fa7abd3eda89" width=40%> 

Above is the first frame of the sequence overlaid with the detected keypoints. 

### Part 2: Feature Tracking

In the second part of the homework, I applied the Kanade-Lucas-Tomasi (KLT) tracking algorithm to track the keypoints found in Part 1 throughout the image sequence. I implemented the `getNextPoints()` function which performs the Iterative Lucas-Kanade feature tracking. 

The keypoints from the first frame are used as initial points for the tracking. For each point, a 15x15 window is used. The function follows these steps:

1. Convert the images to grayscale.
2. Initialize the displacement vector.
3. Compute the image gradients.
4. Compute the template from the first image for the patch to be tracked.
5. For each keypoint, compute the Sobel operator, calculate the image intensity difference and the sum of the square difference matrix.
6. Solve the linear system to obtain the displacement vector.
7. Update the keypoint positions based on the displacement vector and continue the iterations until convergence or until a maximum number of iterations is reached.

Keypoints are tracked throughout the image sequence and any track where the predicted translation falls outside the image frame is discarded.

<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/e645395c-8148-4cf1-af83-1085ba91640b" width=33%>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/cc6d0470-790f-425b-a42e-fc4e9486b374" width=33%>
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/285e1dd5-e3c7-4b2f-a5f4-a9c81d82e8f9" width=33%>

Above are three plots: The first one shows the keypoints overlaid in the first sequence, and the second one shows the keypoints at the first frame (green) and the tracked keypoints at the second frame (red) on the first frame of the sequence. Additionally, I also plotted the 2D path of 20 random keypoints over the sequence of frames. The path is overlaid on the first frame of the sequence as shown below:
