Instant：时间线上的某个时刻／时间戳

通过获取 Instant 的对象可以拿到此刻的时间，该时间由两部分组成：  
 从 1970—01—01 00：00：00 开始走到此刻的总秒数 + 不够 1 秒的纳秒数  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118114923.png)

# static method

public static Instant now()  
获取当前时间的 Instant 对象（标准时间)

```
Instant instant = Instant.now()
  
System.out.println(instant)
//2024-01-18T03:51:22.693318Z
```

# method

public long getEpochSecond() 纪元  
获取从 1970—01—01T00：00：00 开始的 all 秒数。

```
Instant instant = Instant.now()
  
System.out.println(instant.getEpochSecond())
//1705549999
```

public int getNano()  
获取纳秒数

```
Instant instant = Instant.now()
  
  
System.out.println(instant.getNano())
//695001000
```

plusMillis plusSeconds plusNanos

minusMillis minusSeconds minusNanos

equals,isBefore,isAfter

## Instant 对象的作用

做代码的性能分析，或者记录用户的操作时间点

```
Instant now1 = Instant.now()

// 代码执行。。
Instant now2 = Instant.now()

```
