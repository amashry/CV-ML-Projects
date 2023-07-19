# HW6 Part1 

## Overview

In the first part of HW6, we engaged with the exciting task of training an image classifier utilizing the PyTorch library. This assignment allowed us to understand the essence of machine learning model development: from loading the data, building a model, setting up an optimizer, choosing a loss function, to finally training the model through gradient descent optimization. We were able to take advantage of Google Colab's GPU for efficient training.

## Dataset and Task

We used the CIFAR-10 dataset, a classic within the machine learning community, primarily used for image classification tasks. This dataset consists of 60,000 32x32 color images in 10 classes, with 6000 images per class. There are 50,000 training images and 10,000 testing images.

The task was to train an image classifier that could correctly identify these classes.

**Classes in the CIFAR-10:**
![CIFAR10](https://miro.medium.com/max/578/1*BCsHErqOJxmKDLQXYJR_ow.png)
*(Image placeholder: CIFAR-10 class examples)*

## Methodology

### Data Preprocessing
We used PyTorch's built-in functionality to load and normalize the CIFAR10 training and test datasets using torchvision. To improve model generalization, the images were normalized to Tensors with a range [-1, 1].

**Sample images from the dataset:**
```md
<Sample Images from Dataset>
```
*(Image placeholder: Sample images from the CIFAR-10 dataset)*

### Model Architecture
We constructed a Convolutional Neural Network (CNN) with the following structure: Conv2d --> ReLU --> MaxPool2d --> Conv2d --> ReLU --> MaxPool2d --> Flatten --> Linear --> ReLU --> Linear --> ReLU --> Linear. The model architecture was designed to capture the hierarchical pattern in data by applying reusable weights to different spatial locations.

### Training
To train our CNN, we used a Classification Cross-Entropy loss and SGD with momentum. We trained the model for four epochs, iteratively optimizing the model parameters to minimize the loss. The model's performance was evaluated on the test dataset after each epoch, and we observed improvements over time.

### Evaluation
We evaluated our trained network on the test data, predicting the class labels outputted by our network and checking them against the ground truth. We also calculated accuracy per class to understand how well our model is performing across different categories. 

**Loss Over Time:**
```md
<Loss Over Time Plot>
```
*(Image placeholder: Loss over epochs)*

**Test Accuracy Over Time:**
```md
<Test Accuracy Over Time Plot>
```
*(Image placeholder: Accuracy over epochs)*

### Confusion Matrix
To further analyze our model's performance, we plotted a confusion matrix. This matrix provided insights into the specific classes our model excelled at predicting, as well as classes where it struggled.

```md
<Confusion Matrix>
```
*(Image placeholder: Confusion Matrix)*

## Extra Credit

For extra credit, we compared our model's performance with the VGG model that was pretrained on the ImageNet dataset. We tested both models on two images containing objects from the CIFAR-10 classes and compared the accuracy. Surprisingly, our custom model outperformed the VGG model in this case. 

**My Model vs. VGG Performance:**
```md
<My Model vs. VGG Performance>
```
*(Image placeholder: My Model vs. VGG Performance)*

## Conclusion
Overall, this assignment solidified our understanding of building and training a convolutional neural network using PyTorch. We learned how to preprocess data, define a neural network architecture, set up a loss function and optimizer, and train the network. We also learned how to evaluate the network's performance and gained practical experience in working with a well-known dataset in the machine learning community. While our model outperformed the pretrained VGG model on the CIFAR-10 dataset, we realize that more complex models might perform better on larger, more diverse datasets. 

## References
- [PyTorch Tutorials](https://pytorch.org/tutorials/beginner/introyt/trainingyt.html)
- [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html)
