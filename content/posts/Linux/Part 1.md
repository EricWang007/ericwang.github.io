---

title: "Part 1"
date: 2021-09-02T06:00:20+06:00
hero: /images/posts/writing-posts/hugo-logo.svg
math: true
menu:
  sidebar:
    name: Part 1
    identifier: Part 1
    parent: Linux
    weight: 10
---

# Part 1

---

## 1 Linux终端与主机

![image-20211114193259869](/images/posts/Linux/image-20211114193259869.png)

![image-20211114193732768](/images/posts/Linux/image-20211114193732768.png)

* Ctrl-A的ASCII码是1，Ctrl-B的ASCII码是2，Ctrl-C的ASCII码是3，。。。，Ctrl-Z的ASCII码是26

* Esc的ASCII码是27

* 行律功能调整：stty

  * 查看：stty -a
  * stty erase ^H

![image-20211114195924460](/images/posts/Linux/image-20211114195924460.png)



  流控方式：

* 硬件方式：RS232接口的CTS信号（Clear To Send）（不好）
* 软件方式：利用流控字符Xon（Ctrl-S, 17）和Xoff（Ctrl-Q，19）

![image-20211114202446471](/images/posts/Linux/image-20211114202446471.png)

## 2 系统状态查看

### 2.1 用户登录

Linux用户分为：

* root用户（超级用户）
* 普通用户

创建新用户：

* 由root用户创建（useradd命令），用户信息存放在/etc/passwd文件中，包括用户名和用户ID，以及Home目录，登录shell
  * 登录shell：一般为bash，也可以选其它shell，甚至自己设计的程序。

登录后的shell提示符：

* $：Bourne Shell系列（sh，ksh，bash）
* #：当前用户为超级用户root

### 2.2 查看手册、时间、计算器、口令维护

Linux命令大小写敏感。

几种常用的系统命令：

* **man**：查看系统常用手册

  <img src="/images/posts/Linux/image-20211114211451265.png" alt="image-20211114211451265" style="zoom:50%;" /> 

* **date**：读取系统日期和时间

  <img src="/images/posts/Linux/image-20211114211825529.png" alt="image-20211114211825529" style="zoom:50%;" />  

* **cal**：日历

  * cal 10 2019
  * cal 2019

* **bc**：计算器

  <img src="/images/posts/Linux/image-20211114212050596.png" alt="image-20211114212050596" style="zoom:50%;" /> 

* **passwd**：更换口令

  * <img src="/images/posts/Linux/image-20211114212645426.png" alt="image-20211114212645426" style="zoom:50%;" /> 
  * 安全性：无法由哈希值倒推出原口令

### 2.3 了解系统状态

* **who**：确定谁在系统中

  <img src="/images/posts/Linux/image-20211114212952399.png" alt="image-20211114212952399" style="zoom:50%;" /> 

* **uptime**：已开机时间（年龄）

* **top**：列出资源占用排名靠前的进程

  <img src="/images/posts/Linux/image-20211114213355919.png" alt="image-20211114213355919" style="zoom:67%;" /> 

* **ps**：查阅进程状态（process status）

  * ps / ps -e / ps -ef / ps -el
  
* **free**：了解内存使用情况

## 3 文本文件的处理

### 3.1 文本文件处理工具

进程的标准输入/输出：

* stdin（键盘）
* stdout（屏幕）

重定向机制：

* 输出重定向：ls -l > filelist.txt
* 输入重定向：sort < filelist.txt

管道机制：

* ls -l | sort

### 3.2 文本文件读取

* **more/less**：逐屏显示文件

  <img src="./images/posts/Linux/image-20211115174425288.png" alt="image-20211115174425288" style="zoom:50%;" /> 

  <img src="./images/posts/Linux/image-20211115174702395.png" alt="image-20211115174702395" style="zoom:67%;" /> 

  <img src="./images/posts/Linux/image-20211115174727451.png" alt="image-20211115174727451" style="zoom:67%;" /> 

* **cat与od**：列出文件内容

  <img src="./images/posts/Linux/image-20211115174842691.png" alt="image-20211115174842691" style="zoom:50%;" /> 

  <img src="./images/posts/Linux/image-20211115175621338.png" alt="image-20211115175621338" style="zoom:67%;" /> 

* **head和tail**：显示文件的头部或者尾部

### 3.3 文本数据的处理

* **tee**：三通

  * ./mymap | tee mymap.log，将应当在屏幕上输出的信息同时抄送到文件中

* **wc**：字计数

  * wc -l：统计行数

* **sort**：排序

* **tr**：翻译字符

  * <img src="/images/posts/Linux/image-20211115181351428.png" alt="image-20211115181351428" style="zoom:50%;" /> 
  * <img src="/images/posts/Linux/image-20211115181421851.png" alt="image-20211115181421851" style="zoom:50%;" /> 

* **uniq**：筛选文件中的重复行（**上下紧邻**的两行重复）

  <img src="/images/posts/Linux/image-20211115181524584.png" alt="image-20211115181524584" style="zoom:67%;" /> 

  







