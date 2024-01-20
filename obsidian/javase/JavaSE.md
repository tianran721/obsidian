# java 入门

## 17.变量使用时的注意事项

变量是什么类型，就应该用来装什么类型的数据，否则报错 

变量是从定义开始到 " ｝" 截止的范围内有效 

变量定义的时候可以不赋初始值 

但在使用时，变量里必须赋值，否则报错。

# java 语法

## 02.变量里的数据在计算机中的存储原理

二进制

十进制转二进制的算法

6 转二进制

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109133718.png)

字节

计算机中表示数据的最小单元：一个字节（byte，简称 B，是使用 8 个二进制位组成的)

字节中的每个二进制位就称为位（bit，简称 b)，1B = 8b

[[char , picture , video 's store]]

[[Scanner Class]]

# 流程控制

[[Random Class]]

# 面向对象基础

[[Object]]

[[this keyword]]  
[[constructor]]

## 05.封装

[[encapsulation]]

# 常用 API

api: 就是别人写好的一些程序，给咱们程序员直接拿去调用即可解决问题的。

[[package]]

[[String Class]]  

[[ArrayList Class]]

# 面向对象高级一

[[static keyword]]

[[extend]]

# 面向对象高级二

[[polymorphism]]

[[Final , variable ,constant]]

[[Abstract Class]]

[[Interface]]

# 面向对象高级三

[[Nested Class]]

[[Enum Class]]

[[generic]]

# 常用 API(一)

[[Object Class]]

[[Objects Class]]

[[wrapper class]]

# 常用 API(二)

[[Date Class]]

## 为啥要学习 JDK8 新增的时间  

```
	
传统的时间API
1,设计不合理，使用不方便很多都被淘汰了。
2,都是可变对象，修改后会丢失最开始的时间信息。
3,线程不安全。
4,只能精确到毫秒。

1秒=1000毫秒
1毫秒=1000微妙
1微妙=1000纳秒


 JDK8开始之后新增的时间API
1,设计更合理，功能丰富，使用更方便。
2,都是不可变对象，修改后会返回新的时间对象，不会丢失最开始的时间。3,线程安全。
4,能精确到毫秒,纳秒。
```

[[JDK8 LocalDate]]  
[[JDK8 LocalDateTime]]  
[[ZoneId Class and ZonedDateTime Class]]  
[[Instant Class]]  
[[Period Class Duration Class]]

[[Arrays Class]]

[[Lambda]]  
[[method reference]]

# 异常

[[Exception]]

# 集合框架 (一)

[[List Collection]]

[[ArrayList principle]]

[[LinkedList Collection]]

[[Set Collection]]

# # 集合框架 (二)

[[variable parameter]]

[[Stream Interface]]

# java 高级

## 02.认识反射

在讲解反射之前  
有几个点要跟大家提前交代一下  
我们接下来要学习的反射,注解  
还有动态代理  
这些知识在我们平时的业务开发中极少会用到  
这些技术  
都是属于学习框架或者做框架时的底层源码  
我们讲这些东西是为大家今后理解框架  
或者以后自己开发框架给别人用做铺垫的

### Refection

反射就是：加载类 (比如说它的整个字节码文件加载到内存中) 并允许以编程的方式解剖类中的各种成分（成员变量,方法,构造器等)。

学习获取类的信息,操作它们  
1.反射第一步：加载类，获取类的字节码：Class 对象

字节码文件它本身也会是一个对象  
因此 java 就提供了一个 class 类来代表字节码  
到时候我们获取类其实获取的就是一个 class 对象  
这个 class 对象  
它会封装我们的这个类的各种信息啊

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111130217.png)

### 获取 Class 对象的三种方式

```
Class c1= 类名.class
System.out.println（c1.getName（)) //全类名
System.out.println（c1.getSimpleName（)) //简名：Student
```

2.调用 Class 提供方法：`public static Class forName（String package) `

你这个地方要填这个类的全类名

但是大家注意了啊  
他这个地方呢有异常  
他是担心你的这个路径写的有问题  
所以他有个异常给我们  
我们把这个异常直接抛出去

3.Object 提供的方法：

```
public Class getClass（) 
 
Class c3=对象.getClass（) 
 
```

2,获取类的构造器：Constructor 对象

3,获取类的成员变量：Field 对象

那么你通过这个 field 的对象  
去获取该成员变量的信息  
或者对变量进行操作

4,获取类的成员方法：Method 对象

```

public static void main(String[] args) { 
	test()  //不传数据
	test（...nums： 10) //传输一个数据给它
	test（...nums： 10， 20， 30) //传输多个数据给它
	test（new int［］{10， 20， 30,40) })

}

```
