---
title: "GAN基础"
date: 2021-08-5T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: GAN基础
    identifier: GAN基础
    parent: ML
    weight: 10
---

# GAN

---

## Course 1 —— Build Basic GANs

### 1.1 Introduction

<img src="/images/posts/GAN/image-20210327230913987.png" alt="image-20210327230913987" style="zoom:67%;" /> 

#### **Generative Models:**

* Variational Autoencoders(VAE):

  <img src="/images/posts/GAN/image-20210327231211755.png" alt="image-20210327231211755" style="zoom:67%;" /> 

* GANS: 

  <img src="/images/posts/GAN/image-20210327231532258.png" alt="image-20210327231532258" style="zoom:67%;" /> 

#### **GAN in Real Life**

* **GAN的创始人**：Ian Goodfellow
* **GAN的应用领域：**
  * Image Generation, Deep fake
  * Text Generation
  * Data Augmentaion
  * Image Filters

### 1.2 Basic Components

#### Discriminator

* Use Neural Networks, input: features(image), output: probability

  <img src="/images/posts/GAN/image-20210328103833111.png" alt="image-20210328103833111" style="zoom:67%;" /> 

  <img src="/images/posts/GAN/image-20210327233724319.png" alt="image-20210327233724319" style="zoom:50%;" /> 

* 0.85这个概率也会交给Generator

* Input features e.g.: RGB pixel values for images

#### Generator

* Use Neural Networks, input: class+nose vector, output: features(image)

  <img src="/images/posts/GAN/image-20210328104045156.png" alt="image-20210328104045156" style="zoom:67%;" />   

* Generator目标是让Fake Example的Y^尽量接近1，而Discriminator目标是让其尽量接近0

* 当训练的足够好时，Save Generator（θ）, use random noise to sample more images. 

* The generator learns the probability of features X.

####  BCE Cost Function

* <img src="/images/posts/GAN/image-20210328101716372.png" alt="image-20210328101716372" style="zoom:67%;" /> 
* 前一半：当label y 为0时，为0；当label y 为1时，若Prediction接近1则为0，若Prediction接近0则为负无穷。<img src="/images/posts/GAN/image-20210328101920175.png" alt="image-20210328101920175" style="zoom:67%;" /> 
* 后一半：当label y 为1时，为0；当label y 为0时，若Prediction接近0则为1，若Prediction接近1则为负无穷。<img src="/images/posts/GAN/image-20210328102207241.png" alt="image-20210328102207241" style="zoom:67%;" /> 
* 综合起来，如果Prediction与label相比非常不准确，则最终的值很大。

#### Putting it Together

* 最开始，Discriminator和Generator的水平应该相近。
* Discriminator的任务难度比Generator更简单。
* 若Discriminator过于强大，Generator生成的假图片都被判别为100%fake，100%fake对于Generator没有意义，因为其不知道向哪个方向改进。

#### Coding

* PyTorch vs TensorFlow

<img src="/images/posts/GAN/image-20210328105037161.png" alt="image-20210328105037161" style="zoom:80%;" /> 

* <img src="/images/posts/GAN/image-20210328110647182.png" alt="image-20210328110647182" style="zoom:77%;" />  

* Initialization of the model

  ![image-20210328111958874](/images/posts/GAN/image-20210328111958874.png) 

* Cost function

  ![image-20210328112034910](/images/posts/GAN/image-20210328112034910.png) 

* Optimizer: stochastic gradient descent (随机梯度下降)，lr为learning rate

  ![image-20210328112129298](/images/posts/GAN/image-20210328112129298.png) 

* Training loop for number of epochs

  <img src="/images/posts/GAN/image-20210328112648135.png" alt="image-20210328112648135" style="zoom:80%;" /> 

### 1.3 More Components

#### Activations

* Activation functions are non-linear (to approximate complex functions) and differentiable (for back propagation)

  * **ReLU (Rectified Linear Unit)**

    * Problem: Dying ReLU problem

  * **Leaky ReLU: **<img src="/images/posts/GAN/image-20210328221554677.png" alt="image-20210328221554677" style="zoom:45%;" /> 

  * **Sigmoid: **<img src="/images/posts/GAN/image-20210328221950385.png" alt="image-20210328221950385" style="zoom:60%;" />

    * often used for the last layer
    * Problem: vanishing gradient in saturation problems

     

  * **Tanh (Hyperbolic Tangent): **<img src="/images/posts/GAN/image-20210328222228586.png" alt="image-20210328222228586" style="zoom:60%;" />

    * between -1 and 1

     

#### Batch Normalization

applied on training data and test data.

<img src="/images/posts/GAN/image-20210328223933028.png" alt="image-20210328223933028" style="zoom:70%;" /> 

* Batch normalization smooths the cost function
* Batch normalization reduces the internal covariance shift
* Batch normalization speeds up learning

#### Convolution

* scan the image to detect useful features
* Just element-wise products and sums

#### Stride&Padding

* **Stride**: determines how the filter scans the image

* **Padding: **gives similar importance to the edges and the center

  <img src="/images/posts/GAN/image-20210331164954722.png" alt="image-20210331164954722" style="zoom:67%;" /> 

#### Pooling&Upsampling

* **Pooling: **reduces the size of the input

* **Upsampling: **increases the size of the input

* Difference with convolution: Pooling and Upsampling **have no learnable parameters**, so they involve no learning.

  <img src="/images/posts/GAN/image-20210331170057623.png" alt="image-20210331170057623" style="zoom:57%;" /> 

#### Transposed Convolution

<img src="/images/posts/GAN/image-20210331170744678.png" alt="image-20210331170744678" style="zoom:57%;" /> 

* have learnable parameters
* Problem: results have a checkerboard pattern

### 1.4 Some Problems of Traditional GANs

#### Mode Collapse

* Mode Collapse happens when the generator gets stuck in one mode.

#### Problems with BCE loss

* Flat regions on the cost function = vanishing gradients



### 1.5 Conditional Generation

