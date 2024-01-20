用于时间的格式化,解析  
线程安全  
[[SimpleDateFormat Class]]

# static method

public static DateTimeFormatter ofPattern（时间格式)  
获取格式化器对象

```
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("YYYY_MM_DD HH:mm:ss")
  
// LocalDateTime,zonedDateTime,instant all can use  
LocalDateTime now = LocalDateTime.now()
  
// format datetime  
String formatDT = dateTimeFormatter.format(now)
  
System.out.println(formatDT)
//2024_01_18 13:16:15
```

# method

public String format（时间对象)  
格式化时间
