SimpleDateFormat(JDK8 之前传统的日期,时间)

# Date 构造器

```
public Date()  创建一个 Date 对象，代表系统此刻日期时间。
(Tue Sep 13 14:35:43 CST 2022)

public Date(long time)  
把时间毫秒值转换成Date 日期对象

```

## Date method

```
public long getTime() 拿到时间毫秒值。  
返回从 1970 年 1 月 1 日 00：00：00 走到此刻的总的毫秒数
```

### 问题: 2s 之后的时间是多少

1000ms(毫秒) = 1s

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110233258.png)

```
public void setTime（long time) 设置日期对象的时间为当前时间毫秒值对应的时间

它是可以直接把日期对象的时间设置为某个时间毫秒值对应的时间
```

[[SimpleDateFormat Class]]
