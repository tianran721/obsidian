```
哈希值 int 类型 （—21亿多～21亿多) 
Object类 method : public int hashCode（)：返回对象的哈希码值。

var stu1 = new Student("tony")
  
var stu2 = new Student("bob")

//212030968  
//212030968  
//1174019283  
System.out.println(stu1.hashCode())

System.out.println(stu1.hashCode())

System.out.println(stu2.hashCode())

```

```
哈希碰撞 : 创建超过42亿对象后会出现
var str1 = new String("abc")
  
var str2 = new String("acD")
  
//96354  
//96354  
System.out.println(str1.hashCode())
  
System.out.println(str2.hashCode())

```