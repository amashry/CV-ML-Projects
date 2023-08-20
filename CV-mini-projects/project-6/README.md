# CV-mini-project 6 - Part 1

## Overview

In the first part of project 6, we worked on training an image classifier utilizing the PyTorch library. From loading the data, building a model, setting up an optimizer, choosing a loss function, to finally training the model through gradient descent optimization. 

## Dataset and Task

We used the CIFAR-10 dataset, a classic within the machine learning community, primarily used for image classification tasks. This dataset consists of 60,000 32x32 color images in 10 classes, with 6000 images per class. There are 50,000 training images and 10,000 testing images.

The task was to train an image classifier that could correctly identify these classes.

![CIFAR10](https://miro.medium.com/max/578/1*BCsHErqOJxmKDLQXYJR_ow.png)

## Methodology

### Data Preprocessing
We used PyTorch's built-in functionality to load and normalize the CIFAR10 training and test datasets using torchvision. To improve model generalization, the images were normalized to Tensors with a range [-1, 1].

**Random sample images from the dataset:**

![download (11)](https://github.com/amashry/CV-ML-Projects/assets/98168605/03fa01b3-923d-47de-8dec-b23e5e188198)

### Model Architecture
We constructed a Convolutional Neural Network (CNN) with the following structure: `Conv2d --> ReLU --> MaxPool2d --> Conv2d --> ReLU --> MaxPool2d --> Flatten --> Linear --> ReLU --> Linear --> ReLU --> Linear`. The model architecture was designed to capture the hierarchical pattern in data by applying reusable weights to different spatial locations.

### Training
To train our CNN, we used a Classification Cross-Entropy loss and SGD with momentum. We trained the model for four epochs, iteratively optimizing the model parameters to minimize the loss. The model's performance was evaluated on the test dataset after each epoch, and we observed improvements over time.

### Evaluation
We evaluated our trained network on the test data, predicting the class labels outputted by our network and checking them against the ground truth. We also calculated accuracy per class to understand how well our model is performing across different categories. 

![download (12)](https://github.com/amashry/CV-ML-Projects/assets/98168605/4ae64a2b-e690-4082-a1bb-1baffb6f75a8)

### Confusion Matrix
To further analyze our model's performance, we plotted a confusion matrix. This matrix provided insights into the specific classes our model excelled at predicting, as well as classes where it struggled.

![download (13)](https://github.com/amashry/CV-ML-Projects/assets/98168605/39ebebeb-f6d2-458d-80d4-2b75b767ee55)

---

# CV-mini-project 6 - Part 2 - Semantic Segmentation

## Introduction
In the second part of the project 6, the task involved implementing a semantic segmentation model and running it on a dataset. Semantic segmentation is an image analysis task where every pixel in an image is classified into a class. As such, given an image, the goal was to generate a semantically segmented version of it where each pixel was assigned a class.

![download (14)](https://github.com/amashry/CV-ML-Projects/assets/98168605/5acb8010-5468-4e62-b9f6-af92e3f2107f)

The classes for the segmentation were defined as follows:

```python
VOC_CLASSES = [
    "background",
    "aeroplane",
    "bicycle",
    "bird",
    "boat",
    "bottle",
    "bus",
    "car",
    "cat",
    "chair",
    "cow",
    "diningtable",
    "dog",
    "horse",
    "motorbike",
    "person",
    "potted plant",
    "sheep",
    "sofa",
    "train",
    "tv/monitor",
]
```

## Implementation

The task was divided into two main parts:

### 1. Data Loader for Training and Validation

This involved implementing a custom `VocDataset` class that would serve as the dataloader for the training and validation data. This dataloader takes in the images, applies necessary transformations, and converts the mask image into a segmentation mask where each pixel corresponds to the class index.

The image transformations applied included resizing to a common size, converting to a tensor, and normalizing the pixel values.

### 2. Model Definition and Training Code

The next task was to implement a Fully Convolutional Network (FCN) model and the associated training code.

The initial model architecture based on the VGG16 model didn't produce the desired results. It involved creating a modified version of VGG16 where the last classification layer was replaced with a convolutional layer, followed by an upsampling layer. However, this implementation didn't yield satisfactory results.

The revised model architecture leveraged the VGG16 model as a pretrained feature extractor and added a series of upsampling layers to achieve the final segmentation. This modification worked, and the model was able to generate meaningful segmentation maps. The implemented model was then trained for 10 epochs with a batch size of 4.

## Results

After training, the model was able to segment the input images with reasonable accuracy. This shows that the FCN-32 model was a good choice for the task.

<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/9d673958-621d-4c79-b17e-0dae19b6ff50">
<img src="https://github.com/amashry/CV-ML-Projects/assets/98168605/ec2b980e-18d7-4736-88fc-731885e26125">
