### 数组中存储对象的如何用 sort 排序 (2 种)

```
Student[] students = new Student[4] // 定义学生类型数组,长度 4

students［0］ = new Student（＂蜘蛛精＂，169.5，23) 
```

#### 方法一: 让该对象的类实现 Comparable 接口，然后重写 compareTo 方法，自己来制定比较规则

```
compareTo 制定的规则 是为 sort 服务的 (如按照年龄升序),

约定 1：如果认为左边对象 大于 右边对象 请您返回正整数

约定 2：如果认为左边对象 小于 右边对象 请您返回负整数

约定 3：如果认为左边对象 等于 右边对象 请您一定返回 0

this: 左边对象

@Override
public int compareTo(Student o){
	return this.age - o.age //升序
	return o.age - this.age // 降序
}	
```

#### 方式二：重载Arrays sort 方法，创建 Comparator 接口的匿名内部类对象，然后自己制定比较规则

```
public static <T> void sort（T[] arr， Comparator<？super T> c)
对数组进行排序（支持自定义排序规则)

参数一：需要排序的数组  
参数二：Comparator(接口) new 对象（用来制定对象的比较规则)
```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110160211.png)

```
public static int compare(double d1,double d2)

比较两个指定的双精度浮点数值
```


 