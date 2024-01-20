

java.lang.String  封装了 字符串数据 和 处理字符串的方法

```
Java 程序中的所有字符串（例如 "abc") 都为此类的对象。

String name = "itheima" 
// name 记录了地址,但是 java 会根据字符串的地址打印内容出来
```

### String 类的构造器

```
public String()  
创建一个空白字符串对象，不含有任何内容  
public String(String original)  
根据传入的字符串内容，来创建字符串对象  
public String(char[] chars)  
根据字符数组的内容，来创建字符串对象  
public String(byte[] bytes)  
根据字节数组的内容，来创建字符串对象
```

### 字符数组

```
char［］ chars = {＇a＇，＇黑＇，＇马＇｝

String str = new String(chars) 
```

### 字节数组

```
byte[] bytes= {97,98,99}  //'abc'

String str = new String(bytes) 

System.out.println(str) 
```

### String 的方法



```
String str =＂黑马 Java＂

charAt(int index) : 提取字符串某个索引出的字符返回

default IntStream chars() : return IntStream

codePointAt(int index) 提取某个索引位置字符的编号 (a -> 97)

public int length() 获取字符串的长度返回

public char[] toCharArray():  将当前字符串转换成字符数组返回

public boolean equals()  
判断当前字符串与另一个字符串的内容一样，一样返回 true

public boolean equalsIgnoreCase(String anotherString)  
忽略大小写

public String substring(int beginIndex, int endIndex)  
根据开始和结束索引进行截取，得到新的字符串（包前不包后)

public String substring(int beginIndex) 包前  
从传入的索引处截取，截取到末尾，得到新的字符串返回

public String replace(CharSequence target,CharSequence replacement)  
使用新值，将字符串中的旧值替换，得到新的字符串

String info = ＂这个电影简直是个垃圾，垃圾电影！！＂ 
String str = info.replace（＂垃圾＂，"*")


public boolean contains(CharSequence s)  
判断字符串中是否包含了某个字符串

public boolean startswith(String prefix)  
判断字符串是否以某个字符串内容开头，开头返回 true，
```


字符串遍历 快捷键 str.length().fori

```
public String[] split (String regex)  
把字符串按照某个字符串内容分割成多个字符串，放到一个字符串数组中返回

var str = "a,b,c" 
String[] ch = str.split(",") 

```

## String 使用时的注意事项

String 对象的内容不可改变，被称为不可变字符串对象

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109140725.png)

String 对象的内容不可改变原理

Java 规定: 只要是以双引号 ("xxx") 方式写出的字符串对象，会在堆内存中的字符串常量池中存储且内容相同时只会存储一份。(目的是节约内存)

```
String s1 = "abc" 

String s2 = "abc" 
System.out.println(s1==s2) 
// true
```

1. 双引号字符串 (" 黑马 ") 存储在字符串常量池,并把地址 交给 字符串变量 name
2. " 程序员 " 放到常量池, 字符串拼接 产生的 新字符串会存储在堆内存中,并把新地址交给 name  
 ![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109141328.png)

结论：每次改变字符串对象实际上是产生了新的字符串对象了，变量每次都是指向了新的字符串对象，之前字符串对象的内容是没有改变的

通过 new 方式创建字符串对象，每次 new 一次都会产生一个新的对象放在堆内存中。

```
char[] chars = {'a', 'b', 'c'} 

String a1 = new String(chars) 

String a2 = new String(chars) 

System.out.println(a1 == a2) 
 // false
```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109142245.png)

#### String 笔试题

1.这行代码创建了几个对象？  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109142600.png)

2.请写出程序打印的结果是多少

Java 存在编译优化机制，程序在编译时："a"＋"b"＋"c" 会直接转成 "abc"

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109143108.png)

左边为源文件, 右边为编译后的 class 文件

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240109143005.png)
