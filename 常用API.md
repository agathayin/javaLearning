### Object

toString() 返回字符 `s1.toString()`

equals() 对比地址是否一致。和s2 == s1 相同。主要用于子类重写
```
@Override
public boolean equals(Object o) {
  if (this == o) return true;
  if (o == null || this.getClass() !=o.getClass()) return false;
  Student student = (Student) o;
  return this.age == student.age && Objects.equals(this.name,student.name);
}
```

Objects.equals(s1,s2) 比较是否一致，如果为null不会出错。

clone() 对象克隆，复制一个一样的对象并返回。

1. 重写clone方法`return super.clone()`  
2. 被克隆的类必须有标记接口，如`public class Uber impletments Cloneable`

浅拷贝
```
@Override
protected Object clone() {
  return super.clone();
}
```
深拷贝
```
@Override
protected Object clone() {
  User u2 = (User) super.clone();
  u2.scores = u2.scores.clone();
  return u2;
}
```

isNull(Object obj) 是否为null

nonNull(Object obg) 是否不是null

### 包装类
Byte, Short, Integer, Long, Character, Float, Double, Boolean
```
Integer a3 = 12;
String rs1 = Integer.toString(a3)
int a4 = a3;
ArrayList<Integer> list = new ArrayList<>();
String ageStr = "29";
int ageI = Integer.parseInt(ageStr);
int ageI2 = Integer.valueOf(ageStr);
```

### StringBuilder, StringBuffer
字符要变的时候使用，性能更好，String只在字符不需要操作的时候使用。 
StringBuffer线程安全。  
StingBuilder s = new StringBuilder("itheima");  
s.append(12); 增加字符  
s.reverse(); 字符反转  
s.length(); 字符长度  
s.toString(); 转成字符  

### StringJoiner
StringJoiner(间隔符号，开始符号，结束符号)
StringJoiner s = new StringJoiner(", ", "[", "]");
s.add("java1");
s.add("java2");
s.length();
s.toString();

### Math
Math.abs() 绝对值  
Math.ceil() 向上取整  
Math.floor() 向下取整  
Math.round() 四舍五入  
Math.max(10,20) 最大值  
Math.min(10,20) 最小值  
Math.pow(2,3) 2的3次方=8  
Math.random >=0 <1的数

### System
System.exit(0) 人为终止虚拟机  
System.currentTImeMillis() unixTimestamp  

### Runtime
Runtime r = Runtime.getRuntime() 返回当前程序关联的运行时对象  
r.exit(0) 停止虚拟机  
r.availableProcessors() 可使用处理器数  
r.totalMemory() 内存总数，单位为K  
r.freeMemory() 可用内存量  
r.exec(command) 启动某个程序，返回改程序的对象  
Thread.sleep(5000) 延迟5秒  
r.destroy() 停止程序  

### BigDecimal
```
double a = 0.1;
double b = 0.2;
BigDicimal a1 = BigDecimal.valueOf(a);
BigDecimal b1 = BigDecimal.valueOf(b);
BigDecimal c1 = a1.add(b1);
BigDecimal c2 = a1.subtract(b1);
BigDecimal c3 = a1.mutiply(b1);
BigDecimal c4 = a1.divide(b1,2,RoundingMode.HALF_UP);
double rs = c1.doubleValue();
```
### Date, SimpleDateFormat, Calendar
旧 （不用特别记）
```
// Date
Date d = new Date();  
long time = d.getTime();
Date d2 = new Date(time+2000);
Date d3 = new Date();
d3.setTime(time);

// SimpleDateFormat
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss EEE a");
String rs = dsf.format(d);
String rs2 = dsf.format(time);

String dateStr = "2022-12-12 12:12:11";
SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
Date d2 = sdf2.parse(dateStr);

// Calendar
Calendar now = Calendar.getInstance();
int year = now.get(Calendar.YEAR);
Date d = now.getTime();
long time = now.getTimeInMillis();

// 改成10月
now.set(Calendar.MONTH,9);
// 加10年
now.add(Calendar.DAY_OF_YEAR,10)

```
JDK8之后
```
LocalDate ld = LocalDate.now()

int year = ld.getYear();
int month = ld.getMonthValue(); // 1-12
int day = ld.getDayOfMonth();
int dayOfYear = ld.getDayOfYear();
int dayOfWeek = ld.getDayOfWeek().getValue(); // 星期几

// 修改
LocalDate ld2= ld.withYear(2099);
LocalDate ld3 = ld.withMonth(12);
LocalDate ld4 = LocalDate.of(2023,12,12);
// 加： plusYears, plusMonths,plusDays, plusWeeks
// 减： minusYears, minusMonths, minusDays, minusWeeks;
// 判断： equals, isBefore, isAfter

LocalTime lt = LocalTime.now();
// 获取： getHour, getMinute, getSecond, getNano
// 修改： withHour, withMinute, withSecond, withNano
// 加：plusHours, plusMinutes, plusSeconds, plusNanos,
// 减：minusHours, minusMinutes, minutSeconds, minusNanos,
// 判断： equals, isBefore, isAfter

LocalDateTime ldt = LocalDateTime.now();
// 有上面所有方法
LocalDateTime ldt1 = LocalDateTime.of(2023,12,12,12,12,12,0)
LocalDate ld = ldt.toLocalDate();
LocalTime lt = ldt.toLocalTime();

// 时区
ZoneId zoneId = ZoneId.systemDefault();
String zStr = zoneId.getId();
// 所有时区ZoneId.getAvailableZSoneIds()
Zone Id zoneId1 = ZoneId.of("America/New_York");
//带时区时间
ZoneDateTime now = ZoneDateTime.now(zone1);
ZoneDateTime nowUTC = ZoneDateTime.now(Clock.systemUTC());
// ZoneDateTime有和LocalDateTime一样的方法

// Instant
Instant now = Instant.now();
long second = now.getEpochSecond();
int nano = now.getNano();
Instant i2 = nano.plusNanos(1);
Instant i3 = nano.minus(1);
// 判断： equals, isBefore, isAfter

// DateTimeFormatter
DateTimeFormattoer formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
LocalDateTime now = LocalDateTime.now();
String rs = formatter.format(now);
String rs2 = now.format(formatter);
LocalDateTime ldt = LocalDateTime.parse("2022-12-12",formatter);

// Period
// 计算两个LocalDate对象相差的年数，月数，日数
Period period = Period.between(start,end);
// 获取getYears,getMonths, getDays

// Duration
// LocalTime, LocalDateTime, Instant等时间相差的天、小时、分、秒、纳秒
Period period = Period.between(start,end);
// Period.between
// toDays, toHours, toMinutes, toSeconds, toMillis, toNanos

```



