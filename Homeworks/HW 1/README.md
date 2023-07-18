# Homework 1 - Readme

This homework is divided into two parts: Hybrid Image and Pyramid Image. Each part has a specific purpose and uses a different image processing approach. The homework was implemented using Python in a Google Colab notebook. 

## Part A: Hybrid Image 

The purpose of this part is to create a hybrid image, which is the sum of a low-pass filtered version of one image and a high-pass filtered version of a second image. The filtering is controlled by a parameter called the "cutoff-frequency", which decides the amount of high frequency to remove from the first image and the amount of low frequency to leave in the second image. The implementation is divided into helper functions to read, filter, and perform Fourier Transform on the image. The notebook includes instructions on how to choose appropriate images and tune the cutoff frequency for the best results.

In the end, three hybrid image results are required. One of them is then selected to answer four sub-parts related to the original and filtered images, the hybrid image and its scale, and the log magnitude of the Fourier transform of these images. A brief explanation of how the implementation works, using the selected result as an illustration, is also provided.

The code makes use of several Python libraries including cv2, numpy, pandas, skimage, PIL, matplotlib, and scipy.

## Part B: Pyramid Image

In this part, an image with a diverse range of textures is selected and converted to grayscale. The goal is to create a Gaussian and Laplacian pyramid of a certain level (N) from this image. In each level, the resolution is reduced by a factor of 2. Helper functions are provided to downsample, upsample, and filter the image. Gaussian and Laplacian pyramids are then constructed using these helper functions. 

Finally, the pyramids are visualized in terms of both intensity images and log magnitude of their Fast Fourier Transform (FFT). An explanation of how the Gaussian and Laplacian pyramids are built and what they represent is provided.

## Dependencies

To run this notebook, you'll need the following Python libraries:

- cv2
- numpy
- pandas
- google.colab
- skimage
- PIL
- matplotlib
- scipy

You can install any missing libraries using pip:

```bash
pip install opencv-python numpy pandas google-colab scikit-image pillow matplotlib scipy
```

## Usage

To run the notebook:

1. Open Google Colab in your browser.
2. Upload the notebook file.
3. Run the cells in order from top to bottom.

Note: You'll need to upload your own images or use the predefined images in the notebook.

Please make sure to read the comments and follow the instructions in each cell. They guide you through the process and explain what each part of the code does. Also, remember to adjust the "cutoff-frequency" and select appropriate images for the best results.