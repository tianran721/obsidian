时区

国家与地区的经度不同，各地区的时间也有所不同，因此会划分为不同的时区。

0 时区 : 世界标准时间（UTC)

中国标准时间：世界标准时间（UTC)+ 8 hours

# ZoneId：时区 Id

洲名／城市名 Asia/Shanghai Asia/Chongqing 

国家名／城市名 America/New_York

# ZoneId static method

public static ZoneId systemDefault（)：获取系统默认的时区

```
ZoneId systemDefaultZone = ZoneId.systemDefault()
 

// compiler will call systemDefaultZone.toString()
System.out.println(systemDefaultZone)
// Asia/Shanghai

systemDefaultZone.getId()// Asia/Shanghai
```

public static Set＜String＞ getAvailableZoneIds（)：获取 Java 支持的全部时区 Id

```
System.out.println(ZoneId.getAvailableZoneIds())

//[Asia/Aden, America/Cuiaba, Etc/GMT+9,…]
```

public static ZoneId of（String zoneId)：把某个时区 id 封装成 ZoneId 对象。

```
ZoneId zoneId1 = ZoneId.of("Asia/Shanghai")
  
System.out.println(zoneId1)
//Asia/Shanghai
```

# ZonedDateTime：带时区的时间

# ZonedDateTime static method

public static ZonedDateTime now（ZoneId zone)：获取某个时区的 ZonedDateTime 对象。

```
ZoneId zoneId1 = ZoneId.of("Asia/Shanghai")
  
System.out.println(ZonedDateTime.now(zoneId1))
  
//2024-01-18T11:39:52.647805+08:00[Asia/Shanghai]
```

public static ZonedDateTime now（)：获取系统默认时区的 ZonedDateTime 对象

```
 // get UTC time 世界标准时间
System.out.println(ZonedDateTime.now(Clock.systemUTC()))
  
// 2024-01-18T03:41:35.918508Z
```

## zoneDateTime method

```
ZoneId zoneId1 = ZoneId.of("Asia/Shanghai")
  
  
ZonedDateTime zonedDateTime = ZonedDateTime.now(zoneId1)
  
System.out.println(zonedDateTime.getYear())
//2024  
System.out.println(zonedDateTime.withYear(1111))
//1111-01-18T11:45:01.813359+08:05:43[Asia/Shanghai]  
// minusYear plusYear ….
```
