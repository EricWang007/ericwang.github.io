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

> 参考：https://docs.oracle.com/javase/8/docs/api/index.html

## 1 继承关系图

![image-20210729114627296](/images/posts/java/image-20210729114627296.png)

## 2 常用函数总结

### 栈和队列

栈的两种实现形式

```java
Deque<Integer> queue = new LinkedList<Integer>(); // 推荐
Stack<Integer> queue2 = new Stack<Integer>();
```


* push()

> `java.util.Stack`中，加入尾部
>
> `java.util.LinkedList`中(接口`Deque`中规定)，加入头部

* add()

> 加入尾部，两种方法均可使用，`java.util.Collection`中规定

* pop()

>  `java.util.Stack`中，弹出尾部
>
>  `java.util.LinkedList`中(接口`Deque`中规定)，弹出头部

* get(int  index)

> 由于`Deque`接口中没有get方法（`Deque`继承自`Queue`），故使用`LinkedList`时无法用get
>
> 而`Stack`继承自`Vector`->`List`，故使用`Stack`时可以用get

* poll()

> `java.util.LinkedList`中(接口`Deque`中规定)，弹出头部，同pop
>
> `java.util.Stack`中无法使用

* peek()

> `java.util.Stack`中，返回尾部
>
> `java.util.LinkedList`中(接口`Deque`中规定)，返回头部

### Size & Length

* size()

> `java.util.Collection`中的一个方法

* length

> 任何`数组`的属性

* length()

> `java.lang.String`的一个方法

