# 继承的快速入门

extends

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109152648.png)

子类能继承 (Java 继承是能用的意思) 父类的非私有成员

继承后对象的创建 : 子类对象创建是由子类,父类两张表共同创建的

## 继承的执行原理

1. 加载 B 类是,B 类继承了 A,所以 A 类也加载到方法区
2. new B 时, b 对象中会有 A 和 B 的成员

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109153748.png)

继承的应用场景

减少重复代码

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109153945.png)

# 09.继承相关的注意事项

## 权限修饰符

任意包下的子类里 = 非同一包下创建的子类里

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109154632.png)

public

private: 只能在本类访问

### 缺省 : 不写权限修饰符

如 Exception

在 本类 或 同一个包下类 访问

### protected

如: DateFormat,clone

本类，同一个包下的类，任意包下的子类 **但是 不是在子类对象中访问**

# 10.单继承,Object,方法重写

Java 是单继承的，Java 中的类不支持多继承，但是支持多层继承

为何 Java 中的类不支持多继承

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109162141.png)

## Object 类

object 类是 java 所有类的祖宗类。我们写的任何一个类，默认都是 object 的子类或子孙类。

## 方法重写

当子类觉得父类中的某个方法不好用，或者无法满足自己的需求时，子类可以重写一个方法名称,参数列表,返回值 (签名) 一样的方法，去覆盖父类的方法

重写后，方法的访问，Java 会遵循就近原则

方法重写的其它注意事项

使用 Override 注解，他可以指定 java 编译器，检查我们方法重写的格式是否正确

子类重写父类方法时，访问权限必须等于或大于父类该方法的权限修饰符（public ＞ protected ＞缺省)

重写的方法 返回值类型，必须与被重写方法的返回值类型一样，或者范围更小。

私有方法,静态方法不能被重写

## 方法重写在应用场景

子类重写 Object 类的 toString（) 方法，以便返回对象的内容:

因为 toString() 返回的是地址

对象调用时默认会调用 toString() // System.out.println(s) 

ArrayList 就把 Object 的 toString() 进行了重写

快捷键 :

generate - toString

# 11.子类中访问其他成员的特点

在子类方法中访问其他成员（成员变量,成员方法)，是依照就近原则的

实例方法里,局部变量和实例变量同名,想访问实例变量: 使用 this

this.name

局部变量和实例变量,父类实例变量同名,想访问父类实例变量: 使用 super

super.name

# 12.子类构造器的特点

子类的全部构造器，都会先调用父类的构造器，再执行自己

原因: 子类的全部构造器第一行 , 都会默认有 super() 代码 ,调用父类的无参构造器

如果父类只有有参构造器,子类必须在全部构造器第一行调用父类有参构造器 super(" 黑马 ")

子类构造器中调用父类有参构造器 (super(name,age)),为对象成员完整赋值:

原因是继承使对象的不同成员拆到不同类里所以对象要调用多个构造器才能完整赋值:

子类构造器调用父类构造器的应用场景

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109173133.png)

this（…) 调用兄弟构造器

任意类的构造器中，都可以通过 this（…) 去调用该类的其他构造器。(复用代码)

不能在一个构造器中同时写 this 和 super,

因为 super 会被调用 2 次, this 和 super 都要在第一行

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109173739.png)
