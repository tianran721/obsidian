封装的设计规范

合理暴漏和隐藏

使用 getter/setter

实体 JavaBean(又称实体类)

要求:

1. 这个特殊的类中的成员变量都要私有，并且要对外提供相应的 getXxx，setXxx 方法
2. 类中必须要有一个公共的无参的构造器。

符合要求的类称为实体类

generate - getter/setter

自动生成构造器

generate - constructor select none(无参构造器)

实体类应用场景

实体类只负责数据存取，而对数据的处理交给其他类来完成，以实现数据和数据业务处理相分离。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010749.png)
