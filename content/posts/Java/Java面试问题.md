---
title: "Java面试问题"
date: 2021-08-27T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: Java面试问题
    identifier: Java面试问题
    parent: Java
    weight: 10
---
# Java面试问题

---

## 底层实现

**`Arrays.sort`的底层实现原理**：

* 数据量小于等于60：使用<u>插入排序</u>
* 数据量大于60：根据数据类型选择排序方式：
  * 基本类型：使用<u>快速排序</u>。因为基本类型相等的值都指向同一个常量池，故不需要考虑稳定性。
  * Object类型：使用<u>归并排序</u>。因为其具有稳定性。

