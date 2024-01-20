# 01.包

重点学习:

- io
- lang
- net
- nio
- test
- time
- util

包是分门别类管理程序的文件夹

建包的语法格式:

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109004810.png)

package com.itheima.javabean 告诉编译器编译后放哪里

自己程序中调用其他包:

- 同一个包下的程序，可以直接访问
- 访问其他包下的程序，必须 import 导包才可以访问。(设置 idea 自动导包: Add unambiguous imports on the fly 即时添加明确的导入)
  - (在编程中，"on the fly" 即时的)
- 程序中调用 Java 提供的程序，也需要先导包才可以使用 

(Java.Lang 包不需要 如 System/String)

- 自己的程序中调用多个其他包下的程序，这些程序名又一样的情况下，默认只能导入一个程序，另一个程序必须带包名和类名来访问。

```
com.itheima.pkg.itcast.Demo2 d4=new com.itheima.pkg.itcast.Demo2() 

```
