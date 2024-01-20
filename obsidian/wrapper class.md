包装类就是把基本类型的数据包装成对象。

基本类型的数据 :  
byte Byte  
short Short

int Integer

**基本类型的数据包装成对象的方案**  
public static Integer valueOf(int i) 返回指定值的包装类

```
Integer a2 = Integer.value0f(12) 
```

**自动装箱**：可以自动把基本类型的数据转换成对象。

```
Integer a =12 
```

**自动拆箱**：自动把包装类型的对象转换成对应的基本数据类型。

泛型和集合只支持引用数据类型

long Long

char Character

float Float

double Double  
boolean Boolean

# static method

public static String toString(double d)

```
Integer a = 23 
String rs1 = Integer.toString(a) // "23"
System.out.println(rs1 + 1) // 231

// 方法二
String a = a + ""
```

public static int parselnt(String s)

public static Integer valueOf(String s) 所有基本类型通用方法
