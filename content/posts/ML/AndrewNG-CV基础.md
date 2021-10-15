---

title: "AndrewNG-CV基础"
date: 2021-08-05T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
math: true
menu:
  sidebar:
    name: AndrewNG-CV基础
    identifier: AndrewNG-CV基础
    parent: ML
    weight: 10
---

# AndrewNG-CV 基础

---

## 1 The Basics of Convolutional Neural Networks

### 1.1 Edge detection

Use <u>filter</u> to do the <u>convolution</u> operation

#### One Example

![image-20210811183228302](/images/posts/ML/image-20210811183228302.png)

![image-20210811183734299](/images/posts/ML/image-20210811183734299.png)

Convolution function in tensorflow: `tf.nn.conv2d`

#### Other Examples

![image-20210812114628935](/images/posts/ML/image-20210812114628935.png)

* 1->-1: light->dark
* -1->1: dark->light

![image-20210812114940924](/images/posts/ML/image-20210812114940924.png)

> Furthermore, treat the 9 numbers as parameters, and use backward propagation to improve them.

### 1.2 Padding(填充)

> To preserve the information on the edges and corners.

* **Valid convolutions**:
  * No padding
  *  $n\times n$ * $f\times f$​ ——> $(n-f+1)\times(n-f+1)$
* **Same convolutions**: 
  * Pad so that output size is the same as the input size.
  * $n+2p-f+1=n$  ==> $p=\frac{f-1}{2}$​
  * f 通常是奇数

### 1.3 Strided Convolutions

* with $n\times n$​ image, $f\times f$​​ filter, padding p, stride s, the ouput size is:

$$
\bigg\lfloor\frac{n+2p-f}{s}+1\bigg\rfloor\times\bigg\lfloor\frac{n+2p-f}{s}+1\bigg\rfloor
$$

### 1.4 Convolutions over volumes

channels（depths, 第三个维度）相等

![image-20210812233547145](/images/posts/ML/image-20210812233547145.png)

multiple filters：

![image-20210812233900130](/images/posts/ML/image-20210812233900130.png)

### 1.5 One Layer of a CNN

If layer **`l`** is a convolution layer:

* $f^{[l]}=$filter size
* $p^{[l]}=$​padding
* $s^{[l]}=$​stride
* $n_C^{[l]}=$​number of filters
* Each filter is: $f^{[l]}\times f^{[l]}\times n_C^{[l-1]}$​
* Weights: $f^{[l]}\times f^{[l]}\times n_C^{[l-1]}\times n_C^{[l]}$​
* bias: $n_C{[l]}$ — (1,1,1,$n_C{[l]}$)
* Input: $n^{[l-1]}_H\times n^{[l-1]}_W\times n^{[l-1]}_C$​​
* Output: $a^{[l]}=n^{[l]}_H\times n^{[l]}_W\times n^{[l]}_C$​​​

$$
n^{[l]}=\bigg\lfloor\frac{n^{[l-1]}+2p^{[l]}-f^{[l]}}{s^{[l]}}+1\bigg\rfloor
$$

### 1.6 Example ConvNet

![image-20210818172112985](/images/posts/ML/image-20210818172112985.png)

> Height and Width stay the same for a while, and gradually trend down as you go deeper in the neural network.

> The number of channels gradually increase.

**Types of layer in a convolutional network:**

* Convolution (CONV)
* Pooling (POOL)
* Fully connected (FC) 

### 1.7 Pooling layers

* Max pooling

> only has hyperparameters(fixed), doesn't has parameters.

  ![image-20210819122112750](/images/posts/ML/image-20210819122112750.png)
$$
n^{[l]}=\bigg\lfloor\frac{n^{[l-1]}+2p^{[l]}-f^{[l]}}{s^{[l]}}+1\bigg\rfloor
$$

### 1.8 Neural network example

![image-20210828223356588](/images/posts/ML/image-20210828223356588.png)

## 2 Deep Convolutional Models: Case Study

### 2.1 Classic Networks

#### LeNet-5

* trained on grayscale images(灰度图片)

![image-20210829201819663](/images/posts/ML/image-20210829201819663.png)

#### AlexNet

*  Similar to LeNet, but much bigger.
* $\approx60M$ parameters.
* Use ReLU

![image-20210829202734063](/images/posts/ML/image-20210829202734063.png)

#### VGG-16

* 共16个layer
* CONV层的卷积核和POOLING层的格式都是固定的
* $\approx138M$ parameters.
* 核VGG-19的表现不相上下

![image-20210829203437393](/images/posts/ML/image-20210829203437393.png)

### 3 Residual Networks (ResNets 残差网络)

#### Residual block

* Add "short cut" (skip connection)

![image-20210829205525706](/images/posts/ML/image-20210829205525706.png)

