---
title: "Relation Database"
date: 2021-08-30T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
menu:
  sidebar:
    name: Relation Database
    identifier: Relation Database
    parent: Database
    weight: 10
---

# 2 Relation Database

---

* 关系模式

  ![image-20210831152231553](/images/posts/Database/image-20210831152231553.png)

* 关系实例

  ![image-20210831152249980](/images/posts/Database/image-20210831152249980.png)



* **super key**：一个或多个属性的集合，这些属性的组合可以使我们在一个关系中唯一地标识一个元组。
* **candidate key**：最小的super key 
* **primary key**：被设计者选中的 candidate key
* **foreign key: ** 一个关系模式（r1）在它的属性中包括另一个关系模式（r2）的 primary key，则这个属性在r1上称作参照r2的 foreign key.
  * r1称作 foreign key 依赖的**参照关系（referencing relation）**，r2称作 foreign key 的**被参照关系(referenced relation)**。
  * **参照完整性约束(referential integrity constraint): **在参照关系中任意元组在特定属性上的取值必然等于被参照关系在特定属性上的取值。







