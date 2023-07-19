## Homework 5: Affine Structure from Motion

This homework dives into the exciting topic of Structure from Motion (SfM), a photogrammetric range imaging technique for estimating three-dimensional structures from two-dimensional image sequences that may be coupled with local motion signals. The main task was to recover a 3D point cloud from the image sequence `hotel.seq0.png` … `hotel.seq50.png`.

This homework consists of two primary sections:

### 1. Affine Structure from Motion Implementation

In this section, the first approach to implementing the Affine Structure from Motion algorithm is described.

#### Implementation Details

The main function `affineSFM()` follows the outlined algorithm in the problem statement. 

1. It begins by centering the feature coordinates, subtracting the corresponding centroids. 
2. Then, it constructs the measurement matrix `D`.
3. Following this, it factorizes `D` using Singular Value Decomposition (SVD) and enforces a rank constraint to prepare for motion and structure matrix construction.
4. The motion (affine) and structure (3D shape) matrices are created.
5. Lastly, the matrix `L` is solved using the three orthonormality conditions to eliminate affine ambiguity.

This implementation also makes use of two helper functions: 

- `remove_nan()`: To handle the 'nan' values in the input data, ensuring the preservation of rows where all values are not 'nan'.
- `orthonormality_residuals()`: To calculate the deviation of the solution from the constraints, which helps in finding the `L` matrix.

#### Visualization

The 3D point cloud and the path of the camera frame motion were successfully recovered and visualized using Matplotlib. The function `plot_3D_points()` was used to create a 3D scatter plot of the recovered structure from different viewpoints. The function `plot_camera_path()` plotted the path of the camera in 3D space for each frame.

### 2. Different Way for Solving L using Orthographic constraints

This section offers an alternative approach to solve for the matrix `L` using Orthographic constraints. The difference lies in the way we solve for `L`, but the rest of the method is very similar to the first part.

#### Implementation Details

The primary difference in this implementation is in the fifth step of the `affineSFM()` function where we solve for `L`. Rather than solving for `L` using a least-squares approach with initial guess as in the first implementation, this alternative approach averages the sum of outer products of motion vectors `a_i1` and `a_i2` for all frames. 

The Cholesky decomposition of this average is then used to update the matrices `A` (motion) and `S` (shape), as in the first implementation.

#### Visualization

As in the first part, 3D plots of the tracked points and the camera path are displayed to visualize the results. The same set of helper functions `plot_3D_points()` and `plot_camera_path()` are used for this purpose.

The primary takeaway from this second part of the homework is that a different approach for solving `L` can produce similar results. This further enhances the understanding and reinforces the principles of the Affine Structure from Motion algorithm.

Note: It's important to be aware that these implementations are not based on any pre-existing Structure from Motion code, such as those found in OpenCV. The work is built upon the method proposed by Tomasi and Kanade in their 1992 paper titled "Shape and Motion from Image Streams under Orthography: a Factorization Method".
