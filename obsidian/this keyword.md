this 就是一个变量，用在方法中，得到 当前对象。

this 执行原理

当对象调用方法时,会把对象的地址赋值给方法内的 this

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010717.png)

this 主要用来解决：变量名称冲突问题

解决对象的成员变量与方法内部变量 (方法的参数) 的名称一样时，导致访问冲突问题的。

方法里的 this 如何拿到对象地址:

java 编译器 在编译实例方法时会 添加 this 参数 (Student this)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109010732.png)
