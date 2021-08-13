---

title: "DL应用"
date: 2021-08-05T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
math: true
menu:
  sidebar:
    name: DL应用
    identifier: DL应用
    parent: ML
    weight: 10
---

# DL 应用

---

## 1 Setting up ML application

### 1.1 Train/dev/test set

* **Training set**
* **Validation/Development set**: used for selecting model.
* **Test set**: used for assessment of the generalization error of the final chosen model.

> In previous era, we with limited data, we use <u>60/20/20</u> for tain/dev/test.
>
> In Big data era, we use <u>99%</u> of data as training set.

> Make sure dev and test set come from same distribution.

### 1.2 Bias(偏差)/Variance(方差)

| Test set error | Dev set error | Evaluation                |
| -------------- | ------------- | ------------------------- |
| 1%             | 11%           | high variance (过拟合)    |
| 15%            | 16%           | high bias (欠拟合)        |
| 15%            | 30%           | high bias & high variance |
| 0.5%           | 1%            | low bias & low variance   |

.

> If the <u>output(base) error</u> is high, 15% for example, then the above is not high bias.

### 1.3 Regularization(正则化)

> Regularization helps to prevent overfitting, or reduce the errors in NN.

#### In *Logistic Regression*

$$
J(w,b)=\frac{1}{m}\sum^{m}_{i=1}L(\hat{y}^{(i)},y^{(i)})+\frac{\lambda}{2m}||w||_2^2
$$

* $\lambda$: regularization parameter
* L2 regularization: $||w||_2^2$
  * $\sum_{j=1}^{n_x}w_j^2=w^Tw$
  * used most often.
* L1 regularization: $||w||_1$
  * $\sum_{j=1}^{n_x}|w_j|$​
  * `w` will be sparse (the vector `w` will have a lot of zeros in it)

#### In *Neural Network*

$$
J(w,b)=\frac{1}{m}\sum^{m}_{i=1}L(\hat{y}^{(1)},y^{(1)},...,\hat{y}^{(L)},y^{(L)})+\frac{\lambda}{2m}\sum^L_{l=1}||w^{[l]}||_F^2
$$

* $||w^{[l]}||=\sum_{i=1}^{n[l-1]}\sum_{j=1}^n(w_{ij}^{[l]})^2$​​ (Forbenius norm)

