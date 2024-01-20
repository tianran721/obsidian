入门,彻底搞懂对象

name ＋" 的平均成绩是："＋（chinese＋ math) /2.0

深刻认识面向对象

对象本质上是一种特殊的数据结构

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240108194118.png)

class 对象的模版:

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010619.png)

# 02.对象执行原理

1. test 类 加载到方法区 执行 main->
2. 加载 main 方法在栈内存中执行 ->
3. 加载学生类 (学生模版) 到方法区 ->
4. 执行到 s1 变量,在 main 中开辟空间,保存 s1 变量 ->
5. 执行到 new,在堆内存中开辟对象空间 (保存 s1 学生表)
6. 成员变量赋值为默认值,开辟类地址空间,保存当前学生对象是由那个类 (模版) 创建的地址 (指向 Student.class)
7. 学生变量的地址交给 s1![img](https://raw.githubusercontent.com/tianran721/img/main/img/20240108195827.png)

对象调用方法

1. 找到 s1 地址 ->
2. 根据对象的类地址 找到 类 ->
3. 调用类方法
4. 哪个对象调用的,就用谁的数据

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010637.png)

创建第二个对象:

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010654.png)

对象变量中存储的是对象的地址，因此变量是引用类型的变量。

类和对象的一些注意事项

成员变量默认值

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240108201044.png)

一个代码文件中，可以写多个 class 类，但只能一个用 public 修饰，且 public 修饰的类名必须成为代码文件名。

如果某个对象没有一个变量引用它，则该对象无法被操作了，该对象会成为所谓的垃圾对象。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240108202621.png)

 Java 存在自动垃圾回收机制，会自动清楚掉垃圾对象
