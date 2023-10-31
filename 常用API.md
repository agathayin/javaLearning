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




