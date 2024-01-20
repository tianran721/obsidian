## 01 多态

多态的前提:

1. 有继承/实现关系
2. 存在父类变量 引用子类对象
3. 存在方法重写

JAVA 强调行为多态

Java 中的 成员变量 不多态 (不分编译运行)

成员变量只看编译 ,编译阶段,访问的是谁的成员变量,运行时就是谁

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109140249.png)

对象多态: 你又可能是儿子 又是学生,又是男朋友

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109014133.png)

人可能是学生也可能是老师

行为多态:

学生和老师 跑步有快有慢

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109014248.png)

新建模块:

new - module -

### 对象多态 

当 teacher 继承了 people

People p = new teacher() - p 指向老师对象

合理性:

1. 小范围的老师可以给大范围的人

2. 老师属于人

### 行为多态

People p1 = new Teacher() 

p1.run() 

//慢

People p2 = new Student() 

p2.run() 

//快

编译 (写代码时候) 时:

p1.run() 编译器会去 people class 中找是否有 run 方法 : 有就不报错

运行时:

p1 地址指向的是 teacher 对象,运行时会执行 teacher 对象的方法