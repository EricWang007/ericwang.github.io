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


* E push(E item)

> `java.util.Stack`中，加入尾部
>
> `java.util.LinkedList`中(接口`Deque`中规定)，加入头部

* boolean add(E e)

> 加入尾部，两种方法均可使用，`java.util.Collection`中规定

* E pop()

>  `java.util.Stack`中，弹出尾部
>
>  `java.util.LinkedList`中(接口`Deque`中规定)，弹出头部

* E get(int  index)

> 由于`Deque`接口中没有get方法（`Deque`继承自`Queue`），故使用`LinkedList`时无法用get
>
> 而`Stack`继承自`Vector`->`List`，故使用`Stack`时可以用get

* E poll()

> `java.util.LinkedList`中(接口`Deque`中规定)，弹出头部，同pop
>
> `java.util.Stack`中无法使用

* E peek()

> `java.util.Stack`中，返回尾部
>
> `java.util.LinkedList`中(接口`Deque`中规定)，返回头部

### Map

* V put(K key, V value)

### Size & Length

* int size()

> `java.util.Collection`中的一个方法

* length

> 任何`数组`的属性

* int length()

> `java.lang.String`的一个方法

### String & StringBuffer

* void setCharAt(int index, char ch)

> `StringBuffer`中的一个方法，String无法使用

### Integer 和 String

```java
Integer a = Integer.valueOf("124");
String str = String.valueOf(123);
```

### equals和==的区别

* == 比较的是\**变量(栈)内存中存放的对象的(堆)内存地址，\**用来判断两个对象的地址是否相同，即是否是指相同一个对象
* equals用来比较的是两个对象的内容是否相等

### Arrays.sort自定义

sort默认为升序

几种降序定义

```java
Integer[] arr = {5,4,7,9,2,12,54,21,1};
// Method 1
Arrays.sort(arr, new Comparator<Integer>() {
            public int compare(Integer a, Integer b) {
                return b-a;
            }
        });

// Method 2
Arrays.sort(arr, (a, b) -> {
            return b-a;
        });

// Method 3
Arrays.sort(arr, (a, b) -> (b-a));

// Method 4
Arrays.sort(arr, (a, b) -> b.compareTo(a));
```

### PriorityQueue自定义

```java
Queue<Integer> A = new PriorityQueue<>((x, y) -> (y - x)); // 大顶堆
```

