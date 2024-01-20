# Object 类

Object 类是 Java 中所有类的祖宗类，Java 中所有类的对象都可以直接使用 Object 类中提供的一些方法。

*protected Object* clone() 属于浅克隆

clone 使用必须在子类重写 clone, idea 快捷键 clone

并在子类中实现 Cloneable 接口 (接口内什么都没有,称为标记接口,告诉 compiler 信息)

之后就可以在子类对象中调用 clone 方法 : user.clone() (编译器还会提醒你异常处理,防止你错误编写 clone 方法) 可以抛出异常,注意返回的是 Object 对象,需要强转成子类型

浅克隆

拷贝出的新对象，与原对象中的数据一模一样（引用类型拷贝的只是地址)

对象中 username,scores 数组记录的是地址,浅克隆拷贝的是地址

深克隆

对象中基本类型的数据直接拷贝。  
对象中的字符串数据拷贝的还是地址。  
对象中的其他对象，会创建新对象。

## Object method

public String toString()  
返回对象的字符串表示形式。

```

toString（) 方法存在的意义就是为了被子类重写，以便返回对象具体的内容。

idea 可以一键生成重写的 toString()
```

public boolean equals(Object o)  
判断两个对象地址是否相等。

== : 判断两个对象地址是否相等

```
idea 可以一键生成重写的 equals() 快捷键: eq

equals 方法存在的意义就是为了被子类重写
```
