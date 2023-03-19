[TOC]

------



# YSU-java学习

本节是课程上的要注意的点，或者是之前没有学的很细致的地方，防止忘记。

## 1，第一节课

字符串是引用类型

引用类型：引用变量指向一个栈中的一个指针，指针指向堆里的数据

堆与栈：

堆灵活性好，运行时动态分配，但是读取慢

类型转换需要考虑精度丢失问题

关系运算符中的==，两个操作数如果类型不同，但是实际值相同，则返回true



## 2，第二节课

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

​		在使用时发现在创建时方式不同：int型直接给一个变量名并赋值即可；而Integer需要创建一个对象，再为这个对象传入一个参数。但是最后输出的结果却是一样的。

![image-20230319174121536](C:\Users\HUAWEI\AppData\Roaming\Typora\typora-user-images\image-20230319174121536.png)

但是IDE却报了一个警告，说此处的 Integer 是不必要的装箱并弃用，并且建议改为 int 型

这里就是java有个自动装箱和拆箱的过程

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

###   c. Math类

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

#### a. Character简介

​		Character类其实就是对基本类型char进行了一次封装。实际开发过程中我们虽然经常使用char这一基本的数据类型，但是很多时候我们更需要的是面向对象的编程思想，所以Java语言为char提供了一个封装的类Character。

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

#### b. Character 方法

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