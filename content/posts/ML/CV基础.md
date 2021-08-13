---

title: "CV基础"
date: 2021-08-05T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
math: true
menu:
  sidebar:
    name: CV基础
    identifier: CV基础
    parent: ML
    weight: 10
---

# CV 基础

---

## 1 Convolutional Neural Networks

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
\bigg\lfloor\frac{n+ap-f}{s}+1\bigg\rfloor\times\bigg\lfloor\frac{n+ap-f}{s}+1\bigg\rfloor
$$

### 1.4 Convolutions over volumes

![image-20210812233547145](/images/posts/ML/image-20210812233547145.png)

![image-20210812233900130](/images/posts/ML/image-20210812233900130.png)

### 1.5 One Layer of a CNN

