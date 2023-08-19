# CV-mini-project 1

This homework is divided into two parts: Hybrid Image and Pyramid Image. Each part has a specific purpose and uses a different image processing approach. The homework was implemented using Python in a Google Colab notebook. 

## Part A: Hybrid Image 

The purpose of this part is to create a hybrid image, which is the sum of a low-pass filtered version of one image and a high-pass filtered version of a second image. The filtering is controlled by a parameter called the "cutoff-frequency", which decides the amount of high frequency to remove from the first image and the amount of low frequency to leave in the second image. The implementation is divided into helper functions to read, filter, and perform Fourier Transform on the image. The notebook includes instructions on how to choose appropriate images and tune the cutoff frequency for the best results.

In the end, three hybrid image results are required. One of them is then selected to answer four sub-parts related to the original and filtered images, the hybrid image and its scale, and the log magnitude of the Fourier transform of these images. A brief explanation of how the implementation works, using the selected result as an illustration, is also provided.

![download (1)](https://github.com/amashry/CV-ML-Projects/assets/98168605/ebaecd59-b48b-4945-bea4-2779a6ff450c)

## Part B: Pyramid Image

In this part, an image with a diverse range of textures is selected and converted to grayscale. The goal is to create a Gaussian and Laplacian pyramid of a certain level (N) from this image. In each level, the resolution is reduced by a factor of 2. Helper functions are provided to downsample, upsample, and filter the image. Gaussian and Laplacian pyramids are then constructed using these helper functions. 

Finally, the pyramids are visualized in terms of both intensity images and log magnitude of their Fast Fourier Transform (FFT). An explanation of how the Gaussian and Laplacian pyramids are built and what they represent is provided.


Note: You'll need to upload your own images or use the predefined images in the notebook.
