## 09.Lambda 表达式

JDK8 新特性

用于简化匿名内部类的代码写法。

![300](https://raw.githubusercontent.com/tianran721/img/main/img/20240110141105.png)


Lambda 简化==函数式接口 ==(有且只有一个抽象方法) 的匿名内部类。

函数式接口 (有且只有一个抽象方法)

compiler 能反推出代码完整形式

有`＠Functionallnterface `注解的接口就必定是函数式接口。

![400](https://raw.githubusercontent.com/tianran721/img/main/img/20240110142223.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110144147.png)

Lambda 表达式的省略规则:

参数类型可以省略不写

如果只有一个参数，参数类型,()可以省略。

如果方法体代码只有一行代码，可以省略大括号不写，同时要省略分号！如果这行代码是 return 语句，也必须去掉 return

## example

```

Student[] students = new Student[4] 

students［0］ = new Student（ name：＂蜘蛛精＂，height：169.5， age：23) 

students［1］ = new Student（ name： ＂紫霞＂， height： 163.8， age：26) 
students［2］ = new Student（ name：＂紫霞＂， height： 163.8， age：26)
students［3］= new Student（ name：＂至尊宝＂，height：167.5， age：24) 
 

//原始写法：对数组中的学生对象，按照年龄升序排序
Arrays.sort(students, new Comparator<Student>() { 
	@Override
	public int compare(Student o1, Student o2) {
		return o1.getAge（)o2.getAge（)
	}
}
//使用Lambda简化后的形式
Arrays.sort(students, (o1, o2) -> o1.getAge() - o2.getAge)
```