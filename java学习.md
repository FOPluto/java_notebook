[TOC]

------

# YSU-java课上学习

本节是课程上的要注意的点，或者是之前没有学的很细致的地方，防止忘记。

## 1，第一节课

字符串是引用类型

引用类型：引用变量指向一个栈中的一个指针，指针指向堆里的数据

堆与栈：

堆灵活性好，运行时动态分配，但是读取慢

类型转换需要考虑精度丢失问题

关系运算符中的==，两个操作数如果类型不同，但是实际值相同，则返回true

## 2，第二节课

### 数组相关

动态初始化和静态初始化：

静态就是直接赋值，在【】里边不能有具体数字。

动态的就是直接new一个具体的空间

```java
int[] a = new a[]{1, 2, 3, 4};  // 静态
int[] a = new a[7];  // 动态
```

数组动态初始化：

```java
int [][]b = new int[2][];
b[0] = new int[20];
b[1] = new int[10];

for(int i = 0;i < b.length;i++){
    for(int j = 0;j < b[i].length;j++){
        System.out.print(b[i][j] + " ");
    }
    System.out.println();
}
```

可以使用length属性来获取数组的长度

```java
Person p; // 在栈里边声明地址
p = new Person(); // 在堆里面实例化对象，默认值
Person pp = null; //不给空间，但是不能调用对象中的方法
Object // 所有类的父类
```

## 3，第三节课

### a. 类的一些方法

构造方法：

1. 默认构造方法（如果自己没有写构造方法，系统默认生成，如果自己写了一个函数，系统不默认生成）
2. 带参构造方法

方法重载：同一个类中，同名，参数列表不同（数据类型，数量，顺序不同）

方法重写：不用类？两个不同

可变参数：允许定义的变量个数可变，可变参数只能放在最后，并且只能有一个

```java
package test;
public class First {
    public static void main(String[] args) {
        System.out.println(Integer.toString(add(1, 2, 3, 4, 5, 6)));
    }
    public static int add(int a, int... b){
        for(int item : b){
            a += item;
        }
        return a;
    }
}
```

### b. 包

主要是提供一个命名空间，一个类文件里边只有一个public类，一个包里边可以有多个类文件。

### c. 封装

#### 动态成员

public private protected

多使用private封装

#### 静态成员

用static修饰，是类的成员，而不是对象的成员，可以直接使用类名调用。常用于工具类。

和类相关，**都在栈里边开辟空间**

**new在堆中开辟空间**

所有类中公用，可以看成类中的全局变量，之前静态变量没有怎么实际用过。

### d. 对象数组

略，我也不知道为啥要讲。

行吧，内存管理可以看一下，内存示意图：

<img src="C:\Users\HUAWEI\AppData\Roaming\Typora\typora-user-images\image-20230323110342134.png" alt="image-20230323110342134" style="zoom:50%;" />

需要注意的是，这个创建的过程有两个new空间的过程。



# 自己总结

## 1，Java语法基础（略）

java基本语法部分就略过了，大概从类与对象的章节开始总结：

## 2，JAVA类与对象

类与对象的思想：java作为一个面向对象的语言，主要有以下几个概念：

- 多态

  前提：类的继承关系；方法的重写

  当调用子类、父类同名同参数的方法时，实际执行子类中重写父类的方法。

- 继承

  优点：

  - 减少代码的冗余性和提高代码的复用性
  - 便于代码的扩展
  - 方便后续多态性的使用

- 封装

  隐藏内部的复杂性，只是提供一个对外简单的接口。

  如何进行封装呢？

  比如说，类的成员变量和函数大部分的都需要设置为private，这样就实现了算法的封装。对外就是一个public的接口。

- 抽象

  我们之前所说的猫，狗，猪，熊猫，老虎等等都是动物具体的例子， 而动物本身是一个抽象的概念

- 类

  是对象的抽象

- 对象

  是类的实例化

- 实例

  实际存在的个体，类通过实例化，形成实例

- 方法

  类中可以改变对象的参数和状态的行为

- 重载

  同C++重载

## 3，Java Number和Math

因为我们在使用java时，有时候需要使用类，而不是内置的基本类型，所以说java对基本类型都做了一个装箱操作。所有基本类型的封装类：

| 基本类型 |  封装类   |
| :------: | :-------: |
|   int    |  Integer  |
| boolean  |  Boolean  |
|  double  |  Double   |
|  float   |   Float   |
|   long   |   Long    |
|   char   | Character |
|  short   |   Short   |
|   byte   |   Byte    |

### a. 基本类型与封装类的区别

  在使用时发现在创建时方式不同：int型直接给一个变量名并赋值即可；而Integer需要创建一个对象，再为这个对象传入一个参数。但是最后输出的结果却是一样的。

![image-20230319174121536](C:\Users\HUAWEI\AppData\Roaming\Typora\typora-user-images\image-20230319174121536.png)

但是IDE却报了一个警告，说此处的 Integer 是不必要的装箱并弃用，并且建议改为 int 型

这里就是java有个自动装箱和拆箱的过程，我们在使用封装基本变量的时候最好习惯使用自动装箱拆箱功能

```java
// 装箱
Integer num = new Integer(1);   //Java5之前
Integer num = 1;    //Java5之后
// 拆箱
int num2 = num;
```

 所以由此看来，在数值方面，两者是一样的。只是引用他们的值的话，甚至会建议使用基本数据类型。

而两者之间的区别是 Integer 是一个类，其中封装了许多方法和属性，然后就可以利用这些方法和属性来处理数据，而 int 数据类型就做不到。另一个区别在于两者的默认值不同，int型的默认值为0，而对于Integer来说，因为封装类产生的是一个对象，所以其的默认值为null。

而当Integer对象调用相应的方法后，就已经不是单纯的值了，甚至已经将赋值转化成了其他类型。

### b. 使用封装类的原因

- 有使用需求：

  java是一门面向对象的语言，我们在使用java的过程中，时时刻刻创建对象，时时刻刻都在对象中操作，改变其成员变量，调用其方法。

  而将某个基本数据类型进行封装后相当于就是一个对象，就可以拥有自己的属性和方法，当有了这些方法后，我们就可以利用其来处理数据了。

- 安全性好：

  将基本类型封装成类内部的结构可以自由修改，对数据的操作也更适合控制。对象的数据不会在外部被随意更改。

- 结构不同
       在性能结构上来说，基本数据类型（int i）是在栈上创建的，而对象类型（new Integer()）在堆上创建。堆能获得的空间较大，且堆中的具体内容是人为安排的，这样就能更方便地使用一些基本类型不具备的方法。

- 隐藏细节，对外提供接口方便使用

- 可维护性好，方便重用

     在需要的时候，只需要进行内部结构和数据的更改，而不改变对外接口，，对其的引用就不会受到影响；在需要重复使用时也可以直接引用，就像一辆车可以给很多人开。

### c. Math类

Math类在java中算是一个工具类，其中都是静态方法，从源码上来看，工具类的构造方法普遍设置为私有的，实例代码如下：

```java
public class Test {  
    public static void main (String []args)  
    {  
        System.out.println("90 度的正弦值：" + Math.sin(Math.PI/2));  
        System.out.println("0度的余弦值：" + Math.cos(0));  
        System.out.println("60度的正切值：" + Math.tan(Math.PI/3));  
        System.out.println("1的反正切值： " + Math.atan(1));  
        System.out.println("π/2的角度值：" + Math.toDegrees(Math.PI/2));  
        System.out.println(Math.PI);  
    }  
}
```

```output
90 度的正弦值：1.0
0度的余弦值：1.0
60度的正切值：1.7320508075688767
1的反正切值： 0.7853981633974483
π/2的角度值：90.0
3.141592653589793
```

## 4，Java Character类

### a. Character简介

  Character类其实就是对基本类型char进行了一次封装。实际开发过程中我们虽然经常使用char这一基本的数据类型，但是很多时候我们更需要的是面向对象的编程思想，所以Java语言为char提供了一个封装的类Character。

实例化过程：

```java
public class Main {
    public static void main(String[] args) {
        char ch = '1';
        Character cha = new Character(ch);
        Character test = ch; // 也可以自动装箱
    }
}
```

### b. Character 方法

下面是Character类的一些方法函数：

```java
isLetter();      // 判断是否是一个字母
isDigi();        // 判断是否为一个数字
isWhitespace();  // 判断是否为一个空白字符
isUpperCase();   // 判断是否为一个大写字母
isLowerCase()    // 判断是否是一个小写字母
toUpperCase()    // 指定字母的大写形式
toLowerCase()    // 指定字母的小写形式
toString()       // 返回字符的字符串形式，字符串的长度仅为1
```

## 5，Java String类

字符串在java中广泛应用，Java字符串属于对象，Java 提供了 String 类来创建和操作字符串。

### a. 如何创建字符串

最简单的创建方式如下：

```java
public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        String str = "aaa";
    }
}
```

当然既然String是一个对象，那么我们也可以通过构造的方法进行创建：

```java
public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        String str = new String("aa");
    }
}
```

String创建的字符串存储在公共池中，而new则直接创建在堆中

```java
public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        String s1 = "Runoob";              // String 直接创建
        String s2 = "Runoob";              // String 直接创建
        String s3 = s1;                    // 相同引用
        String s4 = new String("Runoob");   // String 对象创建
        String s5 = new String("Runoob");   // String 对象创建
    }
}
```

下图引用自菜鸟教程：

<img src="C:\Users\HUAWEI\AppData\Roaming\Typora\typora-user-images\image-20230320091802466.png" alt="image-20230320091802466" style="zoom:50%;" />

当然还有一种创建的方式，就是通过char数组进行创建：

```java
public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        char [] ch = new char[]{'a', 'b', 'c'};
        String str = new String(ch);
        System.out.println(str);
    }
}
```

### b. 字符串String的连接

跟C++类似，java的字符串的连接可以直接+连接。

```java
String s1 = "name: ";
String s2 = "可莉";
String s = s1 + s2;
```

### c. 如何创建格式化String

我们知道输出格式化的字符串可以采用printf和format方法。

String类中有一个静态的方法format()返回一个String对象，而不是PrintStream对象。

String 类的静态方法 format() 能用来创建可复用的格式化字符串，而不仅仅是用于一次打印输出。

例子如下：

```java
public class Main {
    public static void main(String[] args) throws FileNotFoundException {
        System.out.printf("浮点型变量的值为 " +
                "%f, 整型变量的值为 " +
                " %d, 字符串变量的值为 " +
                "is %s", floatVar, intVar, stringVar);
        String fs;
        fs = String.format("浮点型变量的值为 " +
                           "%f, 整型变量的值为 " +
                           " %d, 字符串变量的值为 " +
                           " %s", floatVar, intVar, stringVar);
    }
}
```



### d. String对象的方法

| 变量和类型       | 方法                                                         | 描述                                                         |
| :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| `char`           | `charAt(int index)`                                          | 返回指定索引处的 `char`值。                                  |
| `IntStream`      | `chars()`                                                    | 返回 `int`的流，将此序列中的 `char`值零扩展。                |
| `int`            | `codePointAt(int index)`                                     | 返回指定索引处的字符（Unicode代码点）。                      |
| `int`            | `codePointBefore(int index)`                                 | 返回指定索引之前的字符（Unicode代码点）。                    |
| `int`            | `codePointCount(int beginIndex, int endIndex)`               | 返回此 `String`的指定文本范围内的Unicode代码点数。           |
| `IntStream`      | `codePoints()`                                               | 返回此序列中的代码点值流。                                   |
| `int`            | `compareTo(String anotherString)`                            | 按字典顺序比较两个字符串。                                   |
| `int`            | `compareToIgnoreCase(String str)`                            | 按字典顺序比较两个字符串，忽略大小写差异。                   |
| `String`         | `concat(String str)`                                         | 将指定的字符串连接到此字符串的末尾。                         |
| `boolean`        | `contains(CharSequence s)`                                   | 当且仅当此字符串包含指定的char值序列时，才返回true。         |
| `boolean`        | `contentEquals(CharSequence cs)`                             | 将此字符串与指定的 `CharSequence` 。                         |
| `boolean`        | `contentEquals(StringBuffer sb)`                             | 将此字符串与指定的 `StringBuffer` 。                         |
| `static String`  | `copyValueOf(char[] data)`                                   | 相当于 [`valueOf(char[\])`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/String.html#valueOf(char[])) 。 |
| `static String`  | `copyValueOf(char[] data, int offset, int count)`            | 相当于 [`valueOf(char[\], int, int)`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/String.html#valueOf(char[],int,int)) 。 |
| `boolean`        | `endsWith(String suffix)`                                    | 测试此字符串是否以指定的后缀结尾。                           |
| `boolean`        | `equals(Object anObject)`                                    | 将此字符串与指定的对象进行比较。                             |
| `boolean`        | `equalsIgnoreCase(String anotherString)`                     | 将此 `String`与另一个 `String`比较，忽略了大小写。           |
| `static String`  | `format(String format, Object... args)`                      | 使用指定的格式字符串和参数返回格式化字符串。                 |
| `static String`  | `format(Locale l, String format, Object... args)`            | 使用指定的语言环境，格式字符串和参数返回格式化的字符串。     |
| `byte[]`         | `getBytes()`                                                 | 使用平台的默认字符集将此 `String`编码为字节序列，将结果存储到新的字节数组中。 |
| `void`           | `getBytes(int srcBegin, int srcEnd, byte[] dst, int dstBegin)` | **已过时。**此方法无法将字符正确转换为字节。                 |
| `byte[]`         | `getBytes(String charsetName)`                               | 使用命名的字符集将此 `String`编码为字节序列，将结果存储到新的字节数组中。 |
| `byte[]`         | `getBytes(Charset charset)`                                  | 使用给定的[charset](https://www.runoob.com/manual/jdk11api/java.base/java/nio/charset/Charset.html)将此`String`编码为字节序列，将结果存储到新的字节数组中。 |
| `void`           | `getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)` | 将此字符串中的字符复制到目标字符数组中。                     |
| `int`            | `hashCode()`                                                 | 返回此字符串的哈希码。                                       |
| `int`            | `indexOf(int ch)`                                            | 返回指定字符第一次出现的字符串中的索引。                     |
| `int`            | `indexOf(int ch, int fromIndex)`                             | 返回指定字符第一次出现的此字符串中的索引，从指定索引处开始搜索。 |
| `int`            | `indexOf(String str)`                                        | 返回指定子字符串第一次出现的字符串中的索引。                 |
| `int`            | `indexOf(String str, int fromIndex)`                         | 从指定的索引处开始，返回指定子字符串第一次出现的字符串中的索引。 |
| `String`         | `intern()`                                                   | 返回字符串对象的规范表示。                                   |
| `boolean`        | `isBlank()`                                                  | 如果字符串为空或仅包含 [`white space`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/Character.html#isWhitespace(int))代码点，则返回 `true` ，否则 `false` 。 |
| `boolean`        | `isEmpty()`                                                  | 返回 `true` ，当且仅当， [`length()`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/String.html#length())是 `0` 。 |
| `static String`  | `join(CharSequence delimiter, CharSequence... elements)`     | 返回由 `CharSequence elements`的副本组成的新String，该副本与指定的 `delimiter`的副本连接在一起。 |
| `static String`  | `join(CharSequence delimiter, Iterable<? extends CharSequence> elements)` | 返回由 `String`的副本组成的新 `String` ，其中 `CharSequence elements`指定的 `delimiter`的副本。 |
| `int`            | `lastIndexOf(int ch)`                                        | 返回指定字符最后一次出现的字符串中的索引。                   |
| `int`            | `lastIndexOf(int ch, int fromIndex)`                         | 返回指定字符最后一次出现的字符串中的索引，从指定的索引开始向后搜索。 |
| `int`            | `lastIndexOf(String str)`                                    | 返回指定子字符串最后一次出现的字符串中的索引。               |
| `int`            | `lastIndexOf(String str, int fromIndex)`                     | 返回指定子字符串最后一次出现的字符串中的索引，从指定索引开始向后搜索。 |
| `int`            | `length()`                                                   | 返回此字符串的长度。                                         |
| `Stream<String>` | `lines()`                                                    | 返回从此字符串中提取的行的流，由行终止符分隔。               |
| `boolean`        | `matches(String regex)`                                      | 判断此字符串是否与给定的 [regular expression](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum)匹配。 |
| `int`            | `offsetByCodePoints(int index, int codePointOffset)`         | 返回此 `String`中的索引，该索引从给定的 `index`偏移 `codePointOffset`代码点。 |
| `boolean`        | `regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)` | 测试两个字符串区域是否相等。                                 |
| `boolean`        | `regionMatches(int toffset, String other, int ooffset, int len)` | 测试两个字符串区域是否相等。                                 |
| `String`         | `repeat(int count)`                                          | 返回一个字符串，其值为此字符串的串联重复 `count`次。         |
| `String`         | `replace(char oldChar, char newChar)`                        | 返回从替换所有出现的导致一个字符串 `oldChar`在此字符串 `newChar` 。 |
| `String`         | `replace(CharSequence target, CharSequence replacement)`     | 将此字符串中与文字目标序列匹配的每个子字符串替换为指定的文字替换序列。 |
| `String`         | `replaceAll(String regex, String replacement)`               | 将给定替换的给定 [regular expression](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum)匹配的此字符串的每个子字符串替换。 |
| `String`         | `replaceFirst(String regex, String replacement)`             | 将给定替换的给定 [regular expression](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum)匹配的此字符串的第一个子字符串替换。 |
| `String[]`       | `split(String regex)`                                        | 将此字符串拆分为给定 [regular expression的](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum)匹配 [项](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum) 。 |
| `String[]`       | `split(String regex, int limit)`                             | 将此字符串拆分为给定 [regular expression的](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum)匹配 [项](https://www.runoob.com/manual/jdk11api/java.base/java/util/regex/Pattern.html#sum) 。 |
| `boolean`        | `startsWith(String prefix)`                                  | 测试此字符串是否以指定的前缀开头。                           |
| `boolean`        | `startsWith(String prefix, int toffset)`                     | 测试从指定索引开始的此字符串的子字符串是否以指定的前缀开头。 |
| `String`         | `strip()`                                                    | 返回一个字符串，其值为此字符串，并删除了所有前导和尾随 [`white space`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/Character.html#isWhitespace(int)) 。 |
| `String`         | `stripLeading()`                                             | 返回一个字符串，其值为此字符串，并删除了所有前导 [`white space`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/Character.html#isWhitespace(int)) 。 |
| `String`         | `stripTrailing()`                                            | 返回一个字符串，其值为此字符串，并删除所有尾随 [`white space`](https://www.runoob.com/manual/jdk11api/java.base/java/lang/Character.html#isWhitespace(int)) 。 |
| `CharSequence`   | `subSequence(int beginIndex, int endIndex)`                  | 返回作为此序列的子序列的字符序列。                           |
| `String`         | `substring(int beginIndex)`                                  | 返回一个字符串，该字符串是此字符串的子字符串。               |
| `String`         | `substring(int beginIndex, int endIndex)`                    | 返回一个字符串，该字符串是此字符串的子字符串。               |
| `char[]`         | `toCharArray()`                                              | 将此字符串转换为新的字符数组。                               |
| `String`         | `toLowerCase()`                                              | 使用默认语言环境的规则将此 `String`所有字符转换为小写。      |
| `String`         | `toLowerCase(Locale locale)`                                 | 使用给定 `Locale`的规则将此 `String`所有字符转换为 `Locale` 。 |
| `String`         | `toString()`                                                 | 这个对象（已经是一个字符串！）                               |
| `String`         | `toUpperCase()`                                              | 使用默认语言环境的规则将此 `String`所有字符转换为大写。      |
| `String`         | `toUpperCase(Locale locale)`                                 | 使用给定 `Locale`的规则将此 `String`所有字符转换为大写。     |
| `String`         | `trim()`                                                     | 返回一个字符串，其值为此字符串，删除了所有前导和尾随空格，其中space被定义为其代码点小于或等于 `'U+0020'` （空格字符）的任何字符。 |
| `static String`  | `valueOf(boolean b)`                                         | 返回 `boolean`参数的字符串表示形式。                         |
| `static String`  | `valueOf(char c)`                                            | 返回 `char`参数的字符串表示形式。                            |
| `static String`  | `valueOf(char[] data)`                                       | 返回 `char`数组参数的字符串表示形式。                        |
| `static String`  | `valueOf(char[] data, int offset, int count)`                | 返回 `char`数组参数的特定子数组的字符串表示形式。            |
| `static String`  | `valueOf(double d)`                                          | 返回 `double`参数的字符串表示形式。                          |
| `static String`  | `valueOf(float f)`                                           | 返回 `float`参数的字符串表示形式。                           |
| `static String`  | `valueOf(int i)`                                             | 返回 `int`参数的字符串表示形式。                             |
| `static String`  | `valueOf(long l)`                                            | 返回 `long`参数的字符串表示形式。                            |
| `static String`  | `valueOf(Object obj)`                                        | 返回 `Object`参数的字符串表示形式。                          |

## 6. Java StringBuffer和StringBuilder类

当字符串需要进行修改的时候，需要使用StringBuffer和StringBuilder类

和String类不同的是，StringBuffer和StringBuilder类的对象可以被多次的修改，并且不产生新的未使用对象。

### StringBuffer和StringBuilder的区别和关系

StringBuffer不是线程安全的，但是有速度优势

StringBuilder是线程安全的，但是稍微慢点

（之后学的很多对象，比如队列，栈，都会有线程安全和线程不安全的区别）

```java
package test;
import java.util.Scanner;
public class First {
    public static void main(String[] args) {
        StringBuilder stringBuilder = new StringBuilder(10);
        stringBuilder.append("我就是歌姬");
        stringBuilder.append("!!!");
        System.out.println(stringBuilder);
        stringBuilder.insert(8, 'a');
        System.out.println(stringBuilder);
        stringBuilder.delete(1, 3);
        System.out.println(stringBuilder);
    }
}
```

结果如下：

```output
我就是歌姬!!!
我就是歌姬!!!a
我歌姬!!!a
```

但是如果我们所开发的软件需要一个线程安全的情况下，则必须使用StringBuffer类。

```java
package test;
import java.util.Scanner;
public class First {
    public static void main(String[] args) {
        StringBuffer stringBuffer = new StringBuffer();
        stringBuffer.append("aaa");
        stringBuffer.append("bbb");
        System.out.println(stringBuffer);
    }
}
```

以下是 StringBuffer 类支持的主要方法：

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | public StringBuffer append(String s) 将指定的字符串追加到此字符序列。 |
| 2    | public StringBuffer reverse()  将此字符序列用其反转形式取代。 |
| 3    | public delete(int start, int end) 移除此序列的子字符串中的字符。 |
| 4    | public insert(int offset, int i) 将 `int` 参数的字符串表示形式插入此序列中。 |
| 5    | insert(int offset, String str) 将 `str` 参数的字符串插入此序列中。 |
| 6    | replace(int start, int end, String str) 使用给定 `String` 中的字符替换此序列的子字符串中的字符。 |

以下列表列出了 StringBuffer 类的其他常用方法：

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | int capacity() 返回当前容量。                                |
| 2    | char charAt(int index) 返回此序列中指定索引处的 `char` 值。  |
| 3    | void ensureCapacity(int minimumCapacity) 确保容量至少等于指定的最小值。 |
| 4    | void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin) 将字符从此序列复制到目标字符数组 `dst`。 |
| 5    | int indexOf(String str) 返回第一次出现的指定子字符串在该字符串中的索引。 |
| 6    | int indexOf(String str, int fromIndex) 从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引。 |
| 7    | int lastIndexOf(String str) 返回最右边出现的指定子字符串在此字符串中的索引。 |
| 8    | int lastIndexOf(String str, int fromIndex) 返回 String 对象中子字符串最后出现的位置。 |
| 9    | int length()  返回长度（字符数）。                           |
| 10   | void setCharAt(int index, char ch) 将给定索引处的字符设置为 `ch`。 |
| 11   | void setLength(int newLength) 设置字符序列的长度。           |
| 12   | CharSequence subSequence(int start, int end) 返回一个新的字符序列，该字符序列是此序列的子序列。 |
| 13   | String substring(int start) 返回一个新的 `String`，它包含此字符序列当前所包含的字符子序列。 |
| 14   | String substring(int start, int end) 返回一个新的 `String`，它包含此序列当前所包含的字符子序列。 |
| 15   | String toString() 返回此序列中数据的字符串表示形式。         |

如果系统程序需要一个多线程管理，那么可能就需要使用StringBuilder进行编程了。s

## 7. Java 日期时间



java.util包提供了一个Date封装类用来表示日期和时间，构造方法如下：

```java
Date(); // 无参构造方法
Date(long millisec) //第二个构造函数接收一个参数，该参数是从1970年1月1日起的毫秒数
```

对象经过实例化之后可以调用以下方法。

```java
boolean after(Date date); // 如果该对象在指定日期date之后则返回false，否则返回true
boolean before(Date date); // 跟上边相反
Object clone(); // 拷贝一个对象
int compareTo(Date date); // 比较两个日期，如果相等返回0，如果大于返回正数，如果小于返回负数
boolean equals(Date date); // 比较函数
long getTime(); // 返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数
String toString(); // 返回打印信息
```

使用SimpleDateFormat对象进行格式控制：

```java
package test;
import java.text.DateFormatSymbols;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;
public class First {
    public static void main(String[] args) {
        Date date = new Date();
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
        System.out.println("当前时间为: " + simpleDateFormat.format(date));
    }
}
```

解析字符串为日期时间对象

```java
import java.util.*;
import java.text.*;
  
public class DateDemo {
 
   public static void main(String[] args) {
      SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd"); 
 
      String input = args.length == 0 ? "1818-11-11" : args[0]; 
 
      System.out.print(input + " Parses as "); 
 
      Date t; 
 
      try { 
          t = ft.parse(input); 
          System.out.println(t); 
      } catch (ParseException e) { 
          System.out.println("Unparseable using " + ft); 
      }
   }
}
```

