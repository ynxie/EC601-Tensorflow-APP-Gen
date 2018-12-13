# EC601-Tensorflow-APP-Gen
# Dataset
Stanford prepared the [Tiny ImageNet dataset](https://tiny-imagenet.herokuapp.com/). The dataset spans 200 image classes with 500 training examples per class. The dataset also has 50 validation and 50 test examples per class.

The images are down-sampled to 64x64 pixels vs. 256x256 for the original ImageNet. The full ImageNet dataset also has 1000 classes.

Tiny ImageNet is large enough to be a challenging and realistic problem. But not so big as to require days of training before you see results.

# Quick Tour of Repository
## Python Files
### vgg_16.py

[This paper](https://arxiv.org/pdf/1409.1556.pdf) by Karen Simonyan and Andrew Zisserman introduced the VGG-16 architecture. The authors reached state-of-the-art performance using only a deep stack of 3x3xC filters and max-pooling layers. Because Tiny ImageNet has much lower resolution than the original ImageNet data, I removed the last max-pool layer and the last three convolution layers. With a little tuning, this model reaches 52% top-1 accuracy and 77% top-5 accuracy.

To keep it fair, I didn't use any pre-trained VGG-16 layers and only trained using the Tiny ImageNet examples.

### input_pipe.py

Load JPEGs (using Tiny ImageNet directory structure)
Load labels and build label integer-to-text dictionary
QueueRunner to feed GPU
including data augmentation (i.e. various image distortions)
### train.py

Trains models and monitors validation accuracy. The training loop has learning rate control and terminates training when progress stops. I take full advantage of TensorBoard by saving histograms of all weights, activations, and also learning curves.

Training is built to run fast on GPU by running the data pipeline on the CPU and model training on the GPU. It is straightforward to train a different model by changing 'model_name' in TrainConfig class.

### losses.py

Contains three loss functions:

Cross-entropy loss
Smoothed cross-entropy loss (add small, non-zero, probability to all classes)
SVM (works, but never got great performance)
### metrics.py

Measures % accuracy.

## Notebooks
### train.ipynb

This is an example to show the progress during the training.<br>

# APK_Build_Folder
This is the step that build the APK file.<br>
This module is generally base on Google Tensorflow Open Source [TensorFlow for Poets 2](https://github.com/googlecodelabs/tensorflow-for-poets-2) <br>

