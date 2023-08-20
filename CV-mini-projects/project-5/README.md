## CV-mini-project 5 - Affine Structure from Motion

This project is about Structure from Motion (SfM), a photogrammetric range imaging technique for estimating three-dimensional structures from two-dimensional image sequences that may be coupled with local motion signals. The main task was to recover a 3D point cloud from the image sequence `hotel.seq0.png` … `hotel.seq50.png`.

![download (9)](https://github.com/amashry/CV-ML-Projects/assets/98168605/a595165b-dce6-4655-9eb8-7bbab7c5b169)


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

![download (10)](https://github.com/amashry/CV-ML-Projects/assets/98168605/5a64c32f-0ef1-4bb5-8b7a-15d528de454b)

The work is built upon the method proposed by Tomasi and Kanade in their 1992 paper titled "Shape and Motion from Image Streams under Orthography: a Factorization Method".

