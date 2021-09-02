---
title: "1 Introduction"
date: 2021-08-30T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: 1 Introduction
    identifier: 1 Introduction
    parent: Database
    weight: 10
---

# 1 Introduction

---

**DBMS & DBS**

* DBS：数据库系统
  * 包括：DBMS、数据库、数据库应用程序、数据库管理人员
* DBMS：数据库管理系统
  * 对数据的管理包括：定义信息的存储格式、提供操作信息的方法



**三级模式结构**

* 内模式（物理层）：数据如何存储、第层数据结构
* 逻辑模式（逻辑层）：描述数据库中存的是什么数据，以及这些数据之间的关系，数据库管理人员运用逻辑层的抽象。是一个全局逻辑结构。
* 外模式（视图层）：数据库用户能够看到的和使用的局部数据的逻辑结构。系统可以为同一个数据库提供多个视图。

<img src="/images/posts/Database/image-20201005112347267.png" alt="image-20201005112347267" style="zoom:47%;" />

**逻辑数据独立性**：当概念模式变化时，可以不改变外部模式和应用程序。

**物理数据独立性**：当内部模式变化时，可以不改变概念模式和外部模式。



* Instance（实例）：某一时刻，数据库中存储的数据集合
* Schema（模式）：数据库系统的总体设计



* Data-Definition Language (DDL)：create、alter、drop
* Data-Manipulation Language (DML)：如SQL中的insert、delete from、update





