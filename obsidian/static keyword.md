# 02.static 修饰成员变量

成员变量按照有无 static 修饰 ,分为类变量和实例变量

成员变量前加上 static ,就变成类变量 (只属于当前类)

属于类，在计算机里只有一份，会被类的全部对象共享

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240108234951.png)

对象.类变量 (不推荐)

成员变量的执行原理

1. 加载 Stu 类到方法区
2. 遇到类变量会立即加载到堆内存 (默认值 null)
3. s1.name 首先在对象里找,当对象空间中找不到时,会去 stu 类中找
4. ![img](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010806.png)

static 修饰成员变量的应用场景

如果某个数据只需要一份，且希望能够被共享访问,修改，则该数据可以定义成类变量来记住。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109000142.png)

类变量使用 public 修饰

public static

在同一个类中，访问自己类的类变量/类方法 (类成员)，可以省略类名不写

# 03 static 修饰成员方法

类方法：有 static 修饰的成员方法

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109140210.png)

对象名.类方法 : 不会有代码提示

实例方法 属于对象

成员方法的执行原理

对象名.类方法: 先找到对象,再根据类地址找到类方法

实例方法不会随着实例的增多而增多。所以说实例方法和类方法一样，都只有一份，保存在方法区

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109140229.png)

搞懂 main 方法: 是类方法, JVM 通过 Test.main() 调用

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109115543.png)

String[] args 参数如何传递给 main

编译程序: javac xx.java -> 产生 HelloWorld.class

执行 java 并传入参数 : java HelloWorld 1 2 3 ![img](https://raw.githubusercontent.com/tianran721/img/main/img/20240109115805.png)

# 04.static 修饰成员方法的应用场景

类方法最常见的应用场景是做工具类。

工具类中的方法都是一些类方法，每个方法都是用来完成一个功能的，工具类是给开发人员共同使用的。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109120200.png)

代码复用 : 验证码

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109120514.png)

为什么工具类中的方法要用类方法，而不用实例方法？

实例方法需要创建对象来调用，此时对象只是为了调用方法，对象占内存，这样会浪费内存。

工具类没有创建对象的需求，建议将工具类的构造器进行私有防止创建对象

# 05.static 的注意事项

类方法中可以直接访问类的成员，不可以直接访问实例成员。

实例方法中可以直接访问类成员，可以直接访问实例成员。

在同一个类中，访问 类变量/类方法 (类成员)，可以省略类名不写  
在同一个类中，实例方法中访问 实例成员，可以省略 this 不写

实例方法中可以出现 this 关键字，类方法中不可以出现 this 关键字的

# 06 static 的应用知识：代码块

## 静态代码块

格式：static{}  
特点：类加载时自动执行，由于类只会加载一次，所以静态代码块也只会执行一次。

作用：完成类的初始化，例如：对类变量的初始化赋值。Socket 类用到静态代码块

## 实例代码块

格式：{｝  
特点：每次创建对象时，执行实例代码块，并在构造器前执行。

作用：和构造器一样，都是用来完成对象的初始化的，例如：对实例变量进行初始化赋值。日志记录 (减少构造器重复代码编写)

# 07.static 的应用知识：单例设计模式

设计模式 : 具体问题的最优解

单例设计模式

确保一个类只有一个对象。

写法:

1. 把类的构造器私有。
2. 定义一个类变量 存储 类的一个对象
3. 定义一个类方法，返回对象。

## 饿汉式单例：拿对象时，对象提前就创建好了

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109150915.png)

## 单例模式的应用场景

Runtime 类 : 因为 Java 运行时只需要一个运行环境

任务管理器

**懒汉式单例**：拿对象时，才开始创建对象

写法:

1. 把类的构造器私有。
2. 定义一个类变量 (先不存对象)
3. 定义一个类方法，这个方法要保证第一次调用时才创建一个对象，后面调用时都会用这同一个对象返回。  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109151822.png)**
