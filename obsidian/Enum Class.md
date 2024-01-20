# 认识枚举

枚举是一种特殊类。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110165355.png)

枚举是**固定对象数量**的类,在第一行要罗列枚举对象名称


反编译枚举: javap A.class

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110165557.png)

枚举类中的第一行，罗列枚举对象的名称, 是常量，每个常量都会**引用一个枚举类实例**

枚举类的**构造器都是私有的**（写不写都只能是私有的)，因此，枚举类对外不能创建对象。

枚举**都是最终类，不可以被继承**。

枚举类中，从第二行开始，可以定义类的其他各种成员。

编译器为枚举类新增了几个方法，并且枚举类都是继承 java.lang.Enum 类的，从 enum 类也会继承到一些方法 ↓。

public static A[] values() 

拿到当前所有枚举对象

public static A valueOf(java.lang.String) 

根据枚举常量名,直接得到枚举对象

```
//3,枚举类提供一个一些额外的API
A［］ as= A.values（) 
 
 
// 拿到全部对象
A a3 = A.value0f("Z") 
 
 
 
 
 

System.out.println(a3.name()) 
 
 
 
 
 
// Z
System.out.println（a3.ordinal（)) 
 
 
// 索引
```

## 抽象枚举

```
public enum B {
    x(){
        @Override
        public void go(){ }
    },Y(){
        @Override
        public void go() { }

    } 
 
 
 
 
 

    public abstract void go() 
 
 
 
 
 

}

```

不能直接写 X,Y  
因为想创建这个 b 的对象的时候 => 枚举是不能实例化

所以你要**内部重写**它  
就像匿名内部类一样  
x() 的 () **代表调用它的无参构造器** 在写大括号 再把 go 方法重写出来 

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110192741.png)

```
B y=B.Y 
 
 
 
 
 

y.go() 
 
 
 
 
 


```

```
public enum C { X 
 
 
}// 单例 

```

**枚举的常见应用场景**

做信息的分类和标志

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110193701.png)

比如说我们某一个系统是吧  
他是要根据男生和女生来决定  
选择不同的界面给这个男女看  
比如说女生可能给他一些小说  
男生给好看的视频之类的对吧

它的后台其实就会有一个方法  
负责他是要接这个男或者女这个信号啊  
他如果接到女生  
这个方法就会展示一些女生想看的东西  
接到男生就会感到展示男生想看的东西

这个**信息标志**推荐用枚举

break 语句**可以用于中断循环语句（for,while 和 do-while) 以及 switch 语句的执行**。 它的作用是让程序跳出当前的循环或者 switch 分支语句，然后继续执行后面的代码

**常量做信息标志**:

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110194447.png)

**枚举做信息标志**:

需要你不带前缀  
带前缀他都报错的  
因为 switch 知道 Constant2 是枚举对象  
枚举可以做信息标志

严格控制入参

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110194904.png)
