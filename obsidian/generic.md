# 认识泛型，泛型类和泛型接口

定义类,接口,方法时，同时==声明==了一个或者多个类型变量（如：＜ E ＞`<t>`)，称为泛型类,泛型接口，泛型方法

ArrayList `<E>` E 代表创建集合对象时可以指定具体的引用数据类型

不写<> 代表集合可以存储任意类型的数据

ArrayList `<String>` list = new ArrayList `<String>`()

JDK1.7 开始支持的简写法: ArrayList `<String>` list = new ArrayList `<>`()

## 泛型原理 

把具体的数据类型作为参数传给类型变量。

ArrayList `<String>` ,的 string 作为 参数传给了 ArrayList `<E>`, 之后 ArrayList 类中的所有 E 都需要为 String 类型

泛型提供了在编译阶段约束所能操作的数据类型，可以避免强制类型转换，出现的异常。

`<E>` or <`T> (规范使用大写,E,T K V 都行)`

no differencethey're just using different names for the *type parameter* (`E` or `T`).

## 泛型类

[04,面向对象高级三：认识泛型，泛型类和泛型接口\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1Cv411372m?p=114) 12:52

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110151057.png)

```
带有 `<E>的类叫泛型类` 

一旦你这样写了之后呢
那么这个类以后我们就把它称之为泛
型类

类型变量可以定义多个 ArrayList<E,K>

`<E extends Animal>`

`extends ` 限制传入的 E 必须是 Animal 或它的子类
```

```
模拟
public class MyArrayList<E>{ 
	public boolean add(E e){ return true 
	}
	public E get(int index){ return null 


	}
}
如果你不使用它的泛型
那么这些泛型的类型变量一都将是
object类型好


 // 泛型类 不考虑扩容
public class MyArrayList<E> {
	private Object[] arr = new 0bject[10] 

	private int size 
 
 
 //记录当前位置的 
	
	public boolean add(E e){
	arr[size++]=e 

 return true 

 
 }
	
	public E get(int index){ return (E) arr[index] 

 }

}
我们这边在调get方法时候
外界也就不用强转了啊
这其实就是泛型的一个作用

```

```
public class MyClass3<E extends Animal>
}
}

比如说让 E 去继承一下animal
那也就是说到时候你使用这个泛型类
的时候
那么你填的这个泛型的这个具体的数
据类型啊
他必须要是继承了animal类型或者animal类的才
可以的


```

## 泛型接口

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110152954.png)

-

### 场景 ：系统需要处理学生和老师的数据

需要提供 2 个功能：保存对象数据。根据名称查询数据。

```

public interface Data<T> { 

	void add(T t) 

	ArrayList<T> getByName(String name) 
 
}
因为人家既可能要保存学生对象
又可能要保存老师对象
那这个时候呢
其实我们就可以考虑使用泛型来解决
了
你可以在这个地方声明一个尖块
写上一个T



那这样的好处就是我这个data方法
到时候既能够添加老师对象
也能够添加学生对象



```

```
如果说我们现在还需要对这个老师
数据进行处理
public class TeacherData implements Data<Teacher>{
	
	@Override
	public void add(Teacher teacher){ }
	@Override
	public ArrayList<Teacher> getByName(String name){ return null 

} 
}
```

```

public interface Data<T extends Animal> { 
void add(T t) 

ArrayList<T> getByName(String name) 
 
 }


public class StudentData implements Data<Cat>

@Override
public void add(Cat cat){ }
@Override
public ArrayList<Cat> getByName(String name) { return null 
 

}

```

# 05.泛型方法

修饰符＜类型变量，类型变量，…＞ 返回值类型 方法名（形参列表){}

他指的是你在==定义方法==的时候  
你可以在这个修饰符的后面声明一个  
尖括号  
在这里面去声明一些类型变量  
一旦你声明的这些类型变量了  
这个方法就是泛型方法

```
public static <T> void test(T t){}
```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110200500.png)

比如说 get 方法  
它这个地方也是有一个类型变量的  
但是这个方法它不是泛型方法

因为他这个类型变量 E  
它不是这个方法自己定义的  
而是这个泛型类它声明后给到这些方法使用的

```
 test(new Dog())

//泛型方法
public static <T> T test(T t){
	 return t 
}

```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113161215.png)

## 需求：所有的汽车可以一起参加比赛 

```

ArrayList<Car> cars = new ArrayList<>() 
cars.add(new BMW())
cars.add(new BENZ()) 
go(cars)

public static <T extends Car> void go(ArrayListyT> cars){ }

```

[[wildcard 通配符]]

```
ArrayList<BMW>
ArrayList<BENZ>
ArrayList<Car> 
三者之间没有关系

ArrayList<Dog> dogs = new ArrayList<>()
 dogs.add(new Dog())

dogs.add(new Dog())
 go(dogs)

这就是说我限定了这个t能接的类型
一定是car或者是car的子类

public static extends <T extends Car> void go(ArrayList<T> cars){ }


```

^1f67ff

### 通配符 [[#Collections]]

就是我们 [[#^1f67ff]]ArrayList  
它本身就是一个泛型类  
那我们这个地方呢又单独自己去定义  
一个 泛型的话呢  
其实呢也是没有必要的

```
同学们注意
你就不用再自己去定义这个泛型的
也就是不用自己去定义这个泛型方法

//？通配符，在使用泛型的时候可以代表一切类型
public static void go
(ArrayList<? extends Car> cars){ 
}


```

### 使用泛型

^e43437

你看这个 ArrayList 它本身就是一个存  
在的泛型  
是别人已经定好的  
所以我们是在使用这个泛型  
那么在使用这个泛型的时候呢  
我们可以用?代表一切类型

我们之前这个 t 呢是我们自己定义的啊  
我们定义的时候一般用 etkv

? 也有上下限

```
ArrayList<? extends Car>  ? 代表car或car的子类
ArrayList<? super Car>  ? 代表car或car的父类
```

# **泛型通配符,上下限** ^fd44c9

[05,面向对象高级三：泛型方法,泛型的通配符和泛型的上下限,泛型注意事项\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1Cv411372m?p=115) 11:31 / 19:33

## 通配符 Wildcards

就是 "？"，可以在 [[#使用泛型]] 的时候代表一切类型 

ETKV 是在==定义泛型==的时候使用。

? : 通配符 在 " 使用泛型 " 的时候可以代表一切类型 

? extends Car : ?只能接受 car 或 car 子类

```
public static void go(ArrayList<? extends Car> cars){ }
```

? super Car : ?只能使用 Car 或 Car 的父类 ^12e3c6

**泛型的注意事项：擦除问题,基本数据类型问题**

# 泛型擦除

泛型是**工作在编译阶段**的，一旦程序**编译成 class 文件**，class 文件中就不存在泛型声明 (<>) 了，这就是泛型擦除

泛型不支持基本数据类型，**只能支持对象类型**（引用数据类型)。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110202518.png)

```
泛型擦除后
ArrayList list= new ArrayList() 
 
 
list.add("javal") 
 

list.add("java2") 
 
list.add("java3") 
 
String rs=(String)list.get(2) 
 
 System.out.println(xs) 
 

```
