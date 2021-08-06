---

title: "DL基础"
date: 2021-08-5T06:00:20+06:00
hero: ../../../static/images/posts/writing-posts/hugo-logo.svg
math: true
menu:
  sidebar:
    name: DL基础
    identifier: DL基础
    parent: ML
    weight: 10
---

# Deep Learning 基础

---

## 1 Logistic Regression Model

### 1.1 Binary Classification

> To learn a classifier that can input an image represented by the feature vector `x`, and predict the corresponding label `y`.
>

**Notation——n training examples**: ($ n_x $为向量维数，$X$为$ n_x\times m $矩阵)
$$
(x^{(1)},y^{(1)}),(x^{(2)},y^{(2)}), ..., (x^{(m)},y^{(m)}),x\in R^{n_x}, y\in \{0,1\}
$$

$$
  X=[x^{(1)},x^{(2)},...,x^{(m)}], X\in R^{n\times m}
$$

$$
  Y=[y^{(1)},y^{(2)},...,y^{(m)}], Y\in R^{1\times m}
$$


### 1.2 Logistic Regression

> An algorithm for *binary classification* problems.

Given `x`, we want $\hat{y}=P(y=1|x)$​

**Way**:

* Parameters: $w\in R^{nx},b\in R$

* Output: （$\sigma$为sigmoid函数，$\sigma(z)=\frac{1}{1+e^{-z}}$）

  $$
  \hat{y}=\sigma(w^Tx+b), (z = w^Tx+b)
  $$

### 1.3 Cost Function

we want $\hat{y(i)}\approx y(i)$

**Loss(error) function**: $L(\hat{y},y)=-(y·log\hat{y}+(1-y)log(1-\hat{y}))$​

* $\hat{y(i)}$与$y(i)$越接近，$L(\hat{y},y)$越小
* If $y=1$: $L(\hat{y},y)=-log\hat{y}$
* If $y=0$: $L(\hat{y},y)=-log(1-\hat{y})$

> It measures how well you're doing <u>on a single training example</u>.

**Cost function**:$J(w,b)=\frac{1}{m}\sum_{i = 1}^{m}L(\hat{y},y)$​

> It measures how well you're doing <u>on the entire training set</u>.

### 1.4 Gradient Descent

> An algorithm to learn the parameteres `w` and `b` on your training set.

$$
w := w-\alpha\frac{\partial J(w,b)}{\partial w}, b:=b-\alpha\frac{\partial J(w,b)}{\partial b}
$$

$\alpha$​​​​ is the <u>learning rate</u>.

#### Derivatives (导数)

