
```
System.out.println(LocalDateTime.now())

//2024-01-18T11:07:50.078713
```

# method

```
int year = localDateTime.getYear()
  
// getMonthValue  
int monthValue = localDateTime.getMonthValue()
  
int dayOfMonth = localDateTime.getDayOfMonth()
  
DayOfWeek dayOfWeek = localDateTime.getDayOfWeek()
  
int dayOfYear = localDateTime.getDayOfYear()
  

// hour minute second  
int hour = localDateTime.getHour()
  
int minute = localDateTime.getMinute()
  
int second = localDateTime.getSecond()

```

withYear, withMonth ,withDayOfMonth, withDay0fYear  
withHour withMinute withSecond withNano

```
System.out.println(localDateTime.withYear(2099))

//2099-01-18T11:13:45.043814
```

plusYears plusMonths plusDays plusWeeks  
plusHours plusMinutes plusSeconds pLusNanos

```
System.out.println(localDateTime.plusYears(1000))

```

minusDays minusYears minusMonths minusWeeks  
minusHours minusMinutes minusSeconds

```
System.out.println(localDateTime.minusYears(1000))

//1024-01-18T11:15:18.487822
```

equals, isBefore, isAfter

```

```

public LocalDate toLocalDate()  
public LocalTime toLocalTime()  
把 LocalDateTime 转换成 LocalDate 和 LocaLTime

```
LocalDateTime localDateTime1 = LocalDateTime.of(2009, 12, 12, 12, 12, 12)
  
System.out.println(localDateTime1.toLocalDate())
//2009-12-12
```

format datetime

```
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("YYYY_MM_DD HH:mm:ss")
  
// LocalDateTime,zonedDateTime,instant all can use  
LocalDateTime now = LocalDateTime.now()
  
System.out.println(now.format(dateTimeFormatter))
//2024_01_18 13:18:30
```

# static method

public static LocalDateTime of(int year, Month month, int dayOfMonth, int hour,  
int minute, int second, int nano0fSecond)

```
//2009-12-12T12:12:12  
System.out.println(LocalDateTime.of(2009, 12, 12, 12, 12, 12))

```

public static LocalDateTime of(LocalDate date, LocalTime time)

```
LocalDateTime localDateTime1 = LocalDateTime.of(2009, 12, 12, 12, 12, 12)
  
LocalDate localDate = localDateTime1.toLocalDate()
  
LocalTime localTime = localDateTime1.toLocalTime()
  
LocalDateTime localDateTime2 = LocalDateTime.of(localDate, localTime)
  
//2009-12-12T12:12:12
```

public static LocalDateTime parse(CharSequence text,DateTimeFormatter formatter) : parse time

```
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy年MM月dd日 HH：mm：ss")
  
String dateStr = "2029年12月12日 12：12：11"
  
LocalDateTime ldt = LocalDateTime.parse(dateStr, formatter)
   
System.out.println(ldt)
 //2029-12-12T12:12:11
```
