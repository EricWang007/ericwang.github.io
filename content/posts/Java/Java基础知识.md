---
title: "Java基础语法"
date: 2021-07-27T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: Java基础语法
    identifier: Java基础语法
    parent: Java
    weight: 10
---

# I. Java 基础语法

## 基本语法

* **类名的首字母应该大写**。如果类名由若干单词组成，那么每个单词的首字母应该大写。
* **方法名应该以小写字母开头**。如果方法名含有若干单词，则后面的每个单词首字母大写。
* **源文件名必须和类名相同**。
* **一个源文件中只能有一个 public类，可以有多个非 public类**
* 所有的 Java 程序由 **public static void main(String[] args)** 方法开始执行。

## Java 源程序与编译型运行区别

![image-20210727210056453](/images/posts/java/image-20210727210056453.png)

## Java 基本数据类型

| 类型   | 数据类型 | 长度(位) |
| ------ | -------- | -------- |
| 整型   | byte     | 8        |
| 整型   | short    | 16       |
| 整型   | int      | 32       |
| 整型   | long     | 64       |
| 整型   | boolean  | 1        |
| 整型   | char     | 16       |
| 浮点型 | float    | 32       |
| 浮点型 | double   | 64       |

### 自动类型转环

> byte,short,char—> int —> long—> float —> double 

## Java 变量

> Java 变量包括包括：局部变量、类变量（静态变量）、成员变量（非静态变量）

```java
public class Variable{
    static int allClicks=0;    // 类变量 
    String str="hello world";  // 实例变量 
    public void method(){ 
        int i =0;             // 局部变量
    }
}
```

* **局部变量**：栈上分配，无默认值
* **类变量**：
  * 无论一个类创建了多少个对象，类只拥有类变量的一份拷贝。
  * 静态变量储存在静态存储区
  * 静态变量可以通过：ClassName.VariableName的方式访问。
* **实例变量**：有默认值，通常为0

## Java 数组

> 数组是储存在堆上的对象

## 传值与传引用

> **基本类型**，**Integer、Long、Byte、Double、Float、Short**，及**String**作为参数传递时，是传递值的拷贝，无论你怎么改变这个拷贝，原值是不会改变的；
>
> 其它对象作为参数传递时，是把对象在内存中的地址拷贝了一份传给了参数。

