# javaLearning

personal learning note for JAVA

### basic steps

1.create MyFirstJavaClass.java (the class name (CamelCase) is same as the file name.)

```
public class HelloWorld {
    public static void main(String[] args){
            System.out.println("Hello World");
    }
}
```

2.`javac MyFirstJavaClass.java` to created MyFirstJavaClass.class

3.`java MyFirstJavaClass` to run MyFirstJavaClass

### JAVA_HOME (win version)

to tell the operation system the jdk path. For example: `Path %JAVA_HOME%\bin`

### type

byte, short, int(default), long

float, double (default), char, boolean

String

**auto type transfer**
(byte,short,char) == int -> long -> float -> double

```
type a = 12
int b = a
System.out.println(b) // 12
```

**force type transfer**

```
int a = 20;
byte b = (byte)a;
```

### operations

"/" int divide int is still int. e.g. `5 / 2 = 2`. To get `5 / 2 = 2.5`, use `1.0 * 5 / 2 = 2.5`

++,-- :plus 1, minus 1

```
int a = 10;
a++ // a=11;

int i = 10;
int rs = ++1;
// plus first, then set value
// rs=11; i=11;

int j = 10;
int rs2 = j++;
// set value first, then plus
// rs2=11; j=10;
```

=，+=，-=，\*=, /=, %= // calculate first, then set value

> , >=,<,<=, ==, !=

&, |, !, ^ , &&, ||

```
&& is Short-circuit evaluation, only run left logic if left is false. its result is the same as &
&& is prior to ||
*/ is prior to +-
^ return if two logic are different
2 >1 ^ 3>1 // =false,
```

### flow

if, switch, for, while, do{}while(),

### random

```
import java.util..Random;
Random r = new Random();
int data = r.nextInt(10); // 0-9
```

### array

int[] arr = {20,10,80};

String[] arr2 = {"Adam","Ben", "Charlie"};

int arr3[] = {1,2,3};

int[] arr = new int[3] // create an array whose length is 3

### input: Scanner

allow user to input a double

```
import java.util.Scanner
Scanner sc = new Scanner(System.in)
double score = sc.nextDouble()
```

### method

```
              void
public static int sum(int a,int b){
    int c = a+b;
    return c; // type is the same as the return type above
}
```

### constructor

init Class Object

```
public Student(){

}
public Student(String name, double score){

}
```

### Encapsulation

private, public

### import

`import package.class`

#### Java Base API

**java.lang.String** (No need to import java.lang.\*)

String name = "test"; (string is unchanged object)

String str = public String(STRING/CHAR[]/BYTE[]);

length()

charAt(int index)

toCharArray()

equals(Object anObject)

```
String s1="abc";
String s2="ab";
String s3=s2+"c;
String s4="a"+"b"+"c"

// s1 == s3 returns false;
// s1.equals(s3) returns true;
// s1 == s4 returns true;

```

equalsIgnoreCase(String str)

substring(int startIndex, int endIndex?)

replace(CharSequence target, CharSquence replacement)

contains(CharSequence s)

startsWith(String prefix)

split(String regex)

**java.util.ArrayList**
ArrayList()

add(E element) // to the last

add(int index, E element)

remove(int index);

remove(Object o);

get(int index)

size()

set(int index,E element)
