---
title: "Java集合框架"
date: 2021-07-27T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: Java集合框架
    identifier: Java集合框架
    parent: Java
    weight: 10
---

# Java集合框架

---

## 1 继承关系图

![image-20210729114627296](/images/posts/java/image-20210729114627296.png)

## 2 常用函数总结


* push()

> `java.util.Stack`中，加入尾部
>
> `java.util.LinkedList`中(接口`Deque`中规定)，加入头部。

* add()

> 加入尾部，`java.util.Collection`中规定

* pop()

>  `java.util.Stack`中，弹出尾部
>
>  `java.util.LinkedList`中(接口`Deque`中规定)，弹出头部

* get(int  index)

> 由于`Deque`接口中没有get方法（`Deque`继承自`Queue`），故使用`LinkedList`时无法用get
>
> 而`Stack`继承自`Vector`->`List`，故使用`Stack`时可以用get
