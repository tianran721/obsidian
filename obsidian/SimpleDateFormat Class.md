 线程不安全

简单日期格式化，可以用来把日期对象/时间毫秒值格式化成我们想要的形式。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110233908.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110234134.png)

# SimpleDateFormat Constructor

public SimpleDateFormat(String pattern)  
创建简单日期格式化对象，并封装时间的格式

# SimpleDateFormat method

public final String format(Date date)  
将日期格式化成日期／时间字符串

public final String format(Object time)  
将时间毫秒值式化成日期／时间字符串

Y year  
M month  
d day  
H hour (0-23  
m minute  
s second  
a 上午/下午  
EEE 星期

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110234607.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110234906.png)

**SimpleDateFormat 解析字符串时间成为日期对象**

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110235053.png)

public Date parse(String source)  
把**字符串时间**解析成日期对象

1.创建简单日期格式化对象，指定的时间格式必须与被解析的时间**格式一模一样**，否则程序会出 bug

```
你调这个 parse 方法时
它会出现一个异常的错误  
他是担心啊  你的时间格式  
和上面这个被解析的时间格式写的不一样  
是提醒你要注意  
那我们把这个异常直接抛出去
```
