方法引用

```
这个println它是一个方法
然后这个out呢就是一个对象
他是用这个对象在调这个方法
然后前后参数又有一样的情况下
可以用方法引用
```

## 方法引用

JDK8 新特性

进一步简化 Lambda 表达式的

**方法引用的标志性符号 ::**

### 静态方法的引用

格式 类名:: 静态方法

[[Lambda#example]]


如果某个 Lambda 表达式里只是调用一个静态方法，并且前后参数的形式一致.就可以使用静态方法引用

```
//按照年龄升序排序的比较规则

public class CompareByData{
	public static int compareByAge(Student o1, Student o2){ 			return o1.getAge（) - o2.getAge（) 
	 }
}


Arrays.sort(students,(o1, o2)->CompareByData.compareByAge(o1, o2)) 
 
lambda表达式里只调用一个静态方法并且前后参数形式一样,就可以使用静态方法引用

// 静态方法引用
Arrays.sort(students, CompareByData::compareByAge) 

```

### 实例方法的引用

[06:15](https://www.bilibili.com/video/BV1Cv411372m?p=128#t=375.634249)

**对象名 :: 实例方法**

Lambda 只是调用一个实例方法，前后参数的形式一致，可以使用实例方法引用

Desc: 降序

```
public int compareByAgeDesc(Student o1, Student o2){ 
 return o2.getAge（)-o1.getAge（) 
}

CompareByData compare = new CompareByData() 
 
Arrays.sort(students, (o1, o2) -> compare.compareByAgeDesc(o1, o2)) 

Arrays.sort(students, compare::compareByAgeDesc) 

```

### 特定类型方法的引用

[10:39/ 25:45](https://www.bilibili.com/video/BV1Cv411372m?p=128#t=636.945031)

**类型:: 方法。**

 Lambda 只是调用一个实例方法，并且前面参数列表的第一个参数是作为方法主调，  
后面的所有参数都是作为该实例方法的入参的，则此时就可以使用特定类型的方法引用。

```
String[] names = {"boby", "angela", "Andy" ,"dlei", "caocao", "Babo", "jack", "Cici"} 
 
 //进行排序
Arrays.sort(names) 
System.out.println(Arrays.toString(names)) 

它会按照这些内容的首字符的编号进行排序的
你比如说大a的编号它是65
小a是97开头


要求忽略首字符大小写进行排序。
他是个string对象吧
然后呢你调它的一个方法叫.compareToIgnoreCase
这是string提供出来的一个对象方法

他会认为大a和小a相当于都是小a

这个方法内部会返回正整数
大a和小a他认为是相等的
它就会返回零的

```

TODO:

构造器引用
