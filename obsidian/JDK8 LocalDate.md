cannot be modified

# static method 

public static xxxx now() : obtain Date object

# Date method

LocalDate：年,月,日 week  
LocalTime： 时,分,秒 ,nanosecond  
LocalDateTime：年,月,日,week ,分,秒 nanosecond  
ZoneId ：时区  
ZonedDateTime：带时区的时间  

```
LocalDate localDate = LocalDate.now()
//2024-01-18  
System.out.println(localDate)
  
int year1 = localDate.getYear()
  
int month1 = localDate.getMonthValue()
// 1-12  
int dayOfMonth = localDate.getDayOfMonth()
  
System.out.println(dayOfMonth)
//18  
int dayOfYear = localDate.getDayOfYear()
  
// localDate.getDayOfWeek() : obtain week object  
int dayOfWeek = localDate.getDayOfWeek().getValue()
  
System.out.println(dayOfWeek)
//4
```

# Date change method

return a new Date Object every time

withYear, withMonth, withDayOfMonth, withDayOfYear

```


LocalDate newLocalDate = localDate.withYear(2088)
  
System.out.println(newLocalDate)
//2088-01-18  
System.out.println(localDate.withMonth(12))
//2024-12-18  
localDate.withDayOfMonth(3)
  
System.out.println(localDate.withDayOfYear(1))
//2024-01-01 
```

plusYears,plusMonths,plusDays,plusWeeks

```
System.out.println(localDate.plusYears(1))
//2025-01-18
```

minusYears,minusMonths,minusDays,minusWeeks

```
System.out.println(localDate.minusYears(10))
//2014-01-18
```

public static LocalDate of(int year, int month, int dayofMonth)  
获取指定日期的 LocalDate 对象

```
LocalDate setLocalDate = LocalDate.of(1000, 1, 1)
//1000-01-01

```

equals isBefore isAfter : 判断 2 个日期对象，是否相等，在前还是在后

```
LocalDate setLocalDate = LocalDate.of(1000, 1, 1)
//1000-01-01  
System.out.println(setLocalDate.equals(localDate))
//false  
System.out.println(setLocalDate.isBefore(localDate))
//true
```

[[JDK8 LocalTime]]

```
replace SimpleDateFormat
DateTimeFormatter ：用于时间的格式化和解析  
```

Duration：时间间隔（时,分,秒，纳秒)  
Period：时间间隔（年，月，日)
