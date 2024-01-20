Instant：时间戳/时间线

```
LocalTime localTime = LocalTime.now()
// get time object  
System.out.println(localTime)

//10:56:02.504122 hour:minute:second
```

```
System.out.println(localTime.getHour())
//10  
System.out.println(localTime.getMinute())
//59  
System.out.println(localTime.getSecond())
//12
```

withHour,withMinute,withSecond,withNano : change time message

```
System.out.println(localTime.withHour(23))
//23:01:12.530508  
System.out.println(localTime.withMinute(59))
//11:59:57.226913
```

plusHours,plusMinutes,plusSeconds,pLusNanos

```
System.out.println(localTime.plusHours(10))
//21:02:42.944993
```

minusHours,minusMinutes,minusSeconds,minusNanos

```
System.out.println(localTime.minusHours(10))
//01:03:35.212222
```

equals isBefore isAfter : 判断 2 个时间对象，是否相等，在前还是在后

# static method

public static LocalTime of(int hour, int minute, int second)  
获取指定时间的 LocalTime 对象：

```
System.out.println(LocalTime.of(01, 59, 59))
//01:59:59
```
