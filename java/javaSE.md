<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [2021秋招技术岗面试笔记](#2021%E7%A7%8B%E6%8B%9B%E6%8A%80%E6%9C%AF%E5%B2%97%E9%9D%A2%E8%AF%95%E7%AC%94%E8%AE%B0)
  - [java SE基础](#java-se%E5%9F%BA%E7%A1%80)
    - [请你谈谈Java中是如何支持正则表达式操作的？](#%E8%AF%B7%E4%BD%A0%E8%B0%88%E8%B0%88java%E4%B8%AD%E6%98%AF%E5%A6%82%E4%BD%95%E6%94%AF%E6%8C%81%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%93%8D%E4%BD%9C%E7%9A%84)
    - [请你说明一下，在Java中如何跳出当前的多重嵌套循环？](#%E8%AF%B7%E4%BD%A0%E8%AF%B4%E6%98%8E%E4%B8%80%E4%B8%8B%E5%9C%A8java%E4%B8%AD%E5%A6%82%E4%BD%95%E8%B7%B3%E5%87%BA%E5%BD%93%E5%89%8D%E7%9A%84%E5%A4%9A%E9%87%8D%E5%B5%8C%E5%A5%97%E5%BE%AA%E7%8E%AF)
    - [java的数据类型](#java%E7%9A%84%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
      - [基础数据类型](#%E5%9F%BA%E7%A1%80%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
      - [浮点数](#%E6%B5%AE%E7%82%B9%E6%95%B0)
      - [类型转换](#%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2)
    - [Array与ArrayList对比](#array%E4%B8%8Earraylist%E5%AF%B9%E6%AF%94)
    - [请你解释为什么会出现4.0-3.6=0.40000001这种现象？](#%E8%AF%B7%E4%BD%A0%E8%A7%A3%E9%87%8A%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BC%9A%E5%87%BA%E7%8E%B040-36040000001%E8%BF%99%E7%A7%8D%E7%8E%B0%E8%B1%A1)
    - [Lambda表达式特征](#lambda%E8%A1%A8%E8%BE%BE%E5%BC%8F%E7%89%B9%E5%BE%81)
    - [HashMap原理](#hashmap%E5%8E%9F%E7%90%86)
      - [hashcode与equals](#hashcode%E4%B8%8Eequals)
      - [TreeMap](#treemap)
      - [LinkedHashMap](#linkedhashmap)
      - [**请你介绍一下map的分类和常见的情况**](#%E8%AF%B7%E4%BD%A0%E4%BB%8B%E7%BB%8D%E4%B8%80%E4%B8%8Bmap%E7%9A%84%E5%88%86%E7%B1%BB%E5%92%8C%E5%B8%B8%E8%A7%81%E7%9A%84%E6%83%85%E5%86%B5)
    - [方法重写（override）与重载（overload）](#%E6%96%B9%E6%B3%95%E9%87%8D%E5%86%99override%E4%B8%8E%E9%87%8D%E8%BD%BDoverload)
    - [请说明内部类可以引用他包含类的成员吗，如果可以，有没有什么限制吗？](#%E8%AF%B7%E8%AF%B4%E6%98%8E%E5%86%85%E9%83%A8%E7%B1%BB%E5%8F%AF%E4%BB%A5%E5%BC%95%E7%94%A8%E4%BB%96%E5%8C%85%E5%90%AB%E7%B1%BB%E7%9A%84%E6%88%90%E5%91%98%E5%90%97%E5%A6%82%E6%9E%9C%E5%8F%AF%E4%BB%A5%E6%9C%89%E6%B2%A1%E6%9C%89%E4%BB%80%E4%B9%88%E9%99%90%E5%88%B6%E5%90%97)
    - [异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)
      - [抛出（throw）与声明（throws）异常](#%E6%8A%9B%E5%87%BAthrow%E4%B8%8E%E5%A3%B0%E6%98%8Ethrows%E5%BC%82%E5%B8%B8)
      - [捕获并处理异常](#%E6%8D%95%E8%8E%B7%E5%B9%B6%E5%A4%84%E7%90%86%E5%BC%82%E5%B8%B8)
    - [抽象类和接口的区别](#%E6%8A%BD%E8%B1%A1%E7%B1%BB%E5%92%8C%E6%8E%A5%E5%8F%A3%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [StringBuffer与StringBuilder](#stringbuffer%E4%B8%8Estringbuilder)
      - [String的不可变性](#string%E7%9A%84%E4%B8%8D%E5%8F%AF%E5%8F%98%E6%80%A7)
    - [java集合框架](#java%E9%9B%86%E5%90%88%E6%A1%86%E6%9E%B6)
      - [集合](#%E9%9B%86%E5%90%88)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 2021秋招技术岗面试笔记
## java SE基础
### 请你谈谈Java中是如何支持正则表达式操作的？
Java中的String类提供了支持正则表达式操作的方法，包括：matches()、replaceAll()、replaceFirst()、split()。此外，Java中可以用Pattern类表示正则表达式对象，它提供了丰富的API进行各种正则表达式操作，如：
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;
class RegExpTest {
    public static void main(String[] args) {
        String str = "成都市(成华区)(武侯区)(高新区)";
        Pattern p = Pattern.compile(".*?(?=\\()");
        Matcher m = p.matcher(str);
        if(m.find()) {
            System.out.println(m.group());
        }
    }
}
```
> 在编写处理字符串的程序时，经常会有查找符合某些复杂规则的字符串的需要。正则表达式就是用于描述这些规则的工具。换句话说，正则表达式就是记录文本规则的代码。计算机处理的信息更多的时候不是数值而是字符串，正则表达式就是在进行字符串匹配和处理的时候最为强大的工具，绝大多数语言都提供了对正则表达式的支持。

### 请你说明一下，在Java中如何跳出当前的多重嵌套循环？
在最外层循环前加一个标记如A，然后用break A;可以跳出多重循环。
```java
public class LoopWithLabel {
    public static void main(String[] args) {
        A:
        for(int i=0;i<5;i++) {
            for(int j=0;j<5;j++) {
                if(j==3) {
                    break A;
                }
                System.out.print(""+i+j+" ");
            }
            System.out.println();
        }
        System.out.println("This is end");
    }
}
```  

### java的数据类型
#### 基础数据类型
> int, char, boolean, short, long, float, double
#### 缺省值
> 对象引用类型的缺省值为null  
> 基础数据类型的缺省值与其类型有关，例如int-0、boolean-false
#### 整数类型对比（由小到大）  

| 数据类型 | 大小（位数） | 取值范围 | 默认值 |
| ------ | ------ | ------ | ------ |
| byte | 1Byte(8bit) | -128（-2^7）- 127（2^7-1）| 0 |
| short | 2Byte(16bit) | -32768（-2^15）- 32767（2^15 - 1）| 0 |
| int | 4Byte(32bit)| -2^31~2^31-1 | 0 |
| long | 8Byte(64bit) | -2^63~2^63-1 | ***0L*** |  

> long赋值需要以L结尾  
> long gg = 44;//错误  
> long gg = 44L；//正确

#### 浮点数
> float 单精度浮点数 32bit 0.0f  
> double 双精度浮点数 64bit 0.0d

#### 类型转换
大小关系
> double > float > long > int > short > byte   

小类型到大类型直接隐式转换
```java
int onef = 654;
int twof = 957;

long threef = onef + twof;
```

大类型到小类型需要强制转换（可能会造成精度丢失或溢出）
```java
double ttf=7.55684954444444444;

float rrf=(float) ttf;//会造成精度的损失，结果为7.5568495
```

### Array与ArrayList对比
>Array可以存储任何数据类型，ArrayList只能存储对象类型  
>Array大小固定，ArrayList长度可变
>ArrayList提供更多方法 addAll(), removeAll(), iterator()  
>对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。

拆箱与装箱
> java编译器对基本数据类型与对象类型的自动转换  
>装箱 基本数据类型-> 对象类型  反之为拆箱

### 请你解释为什么会出现4.0-3.6=0.40000001这种现象？
2进制的小数无法精确表达10进制的小数，计算时需要转为2进制，这个时候出现了误差

### Lambda表达式特征
* 可选类型声明：不需要声明参数类型，编译器可以统一识别参数值。
* 可选的参数圆括号：一个参数无需定义圆括号，但多个参数需要定义圆括号。
* 可选的大括号：如果主体包含了一个语句，就不需要使用大括号。
* 可选的返回关键字：如果主体只有一个表达式返回值则编译器会自动返回值，大括号需要指定明表达式返回了一个数值。

实例
```java
// 1. 不需要参数,返回值为 5  
() -> 5  
  
// 2. 接收一个参数(数字类型),返回其2倍的值  
x -> 2 * x  
  
// 3. 接受2个参数(数字),并返回他们的差值  
(x, y) -> x – y  
  
// 4. 接收2个int型整数,返回他们的和  
(int x, int y) -> x + y  
  
// 5. 接受一个 string 对象,并在控制台打印,不返回任何值(看起来像是返回void)  
(String s) -> System.out.print(s)
```

### HashMap原理
数组 + 链表 + 红黑树（链表长度过大后）
非线程安全，多个线程可以同时修改

![CZu4l.jpg](https://wx2.sbimg.cn/2020/07/15/CZu4l.jpg)

基于哈希表，先依赖hashcode进行定位，速度较快
根据key的hash值确定在entry数组中的位置
* 如果没有重复的，直接插入
* 如果存在重复（hash冲突），用equals比较，如果不相同，放入该位置链表的下一个
#### hashcode与equals
默认的Object.hashcode()返回该对象在内存中的地址
对于自定义类，要同时改写hashcode与equals方法，原因如下：
> HashMap在对比key时，先对比hashcode，hashcode相同时调用equals

#### TreeMap
按照key的值排序，默认按照升序排列

#### LinkedHashMap
按照插入顺序进行排序

#### **请你介绍一下map的分类和常见的情况**
>java为数据结构中的映射定义了一个接口java.util.Map;它有四个实现类,分别是HashMap Hashtable LinkedHashMap 和TreeMap.
 >
> Map主要用于存储健值对，根据键得到值，因此不允许键重复(重复了覆盖了),但允许值重复。
 >
 >Hashmap 是一个最常用的Map,它根据键的HashCode值存储数据,根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的。 HashMap最多只允许一条记录的键为Null;允许多条记录的值为 Null;HashMap不支持线程的同步，即任一时刻可以有多个线程同时写HashMap;可能会导致数据的不一致。如果需要同步，可以用 Collections的synchronizedMap方法使HashMap具有同步的能力，或者使用ConcurrentHashMap。
 >
 >Hashtable与 HashMap类似,它继承自Dictionary类，不同的是:它不允许记录的键或者值为空;它支持线程的同步，即任一时刻只有一个线程能写Hashtable,因此也导致了 Hashtable在写入时会比较慢。
 >
 >LinkedHashMap 是HashMap的一个子类，保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的.也可以在构造时用带参数，按照应用次数排序。在遍历的时候会比HashMap慢，不过有种情况例外，当HashMap容量很大，实际数据较少时，遍历起来可能会比 LinkedHashMap慢，因为LinkedHashMap的遍历速度只和实际数据有关，和容量无关，而HashMap的遍历速度和他的容量有关。
 >
 >TreeMap实现SortMap接口，能够把它保存的记录根据键排序,默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator 遍历TreeMap时，得到的记录是排过序的。
 >
 >一般情况下，我们用的最多的是HashMap,在Map 中插入、删除和定位元素，HashMap 是最好的选择。但如果您要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。如果需要输出的顺序和输入的相同,那么用LinkedHashMap 可以实现,它还可以按读取顺序来排列.
 >
 >HashMap是一个最常用的Map，它根据键的hashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度。HashMap最多只允许一条记录的键为NULL，允许多条记录的值为NULL。
 >
 >HashMap不支持线程同步，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致性。如果需要同步，可以用Collections的synchronizedMap方法使HashMap具有同步的能力。
 >
 >Hashtable与HashMap类似，不同的是：它不允许记录的键或者值为空；它支持线程的同步，即任一时刻只有一个线程能写Hashtable，因此也导致了Hashtable在写入时会比较慢。
 >
 >LinkedHashMap保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的。
 >
 >在遍历的时候会比HashMap慢TreeMap能够把它保存的记录根据键排序，默认是按升序排序，也可以指定排序的比较器。当用Iterator遍历TreeMap时，得到的记录是排过序的。

### 方法重写（override）与重载（overload）
> 方法重载：同一类下多个同名的方法（接受不同参数）  
> 方法重写： 子类继承父类的方法后重写

_二者都是多态的体现，重写是编译时的体现，重载是运行时的体现_

### 请说明内部类可以引用他包含类的成员吗，如果可以，有没有什么限制吗？
>一个内部类对象可以访问创建它的外部类对象的内容，内部类如果不是static的，那么它可以访问创建它的外部类对象的所有属性内部类如果是sattic的，即为nested class，那么它只可以访问创建它的外部类对象的所有static属性一般普通类只有public或package的访问修饰，而内部类可以实现static，protected，private等访问修饰。

### 异常处理
#### 抛出（throw）与声明（throws）异常
```java
import java.io.*;
public class className
{
  public void deposit(double amount) throws RemoteException
  {
    // Method implementation
    throw new RemoteException();
  }
  //Remainder of class definition
}
```
#### 捕获并处理异常
```java
try{
  // 程序代码
}catch(异常类型1 异常的变量名1){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}finally{
  // 程序代码
}
```

### 抽象类和接口的区别
>Java提供和支持创建抽象类和接口。它们的实现有共同点，不同点在于：
 接口中所有的方法隐含的都是抽象的。而抽象类则可以同时包含抽象和非抽象的方法。
 类可以实现很多个接口，但是只能继承一个抽象类
 类可以不实现抽象类和接口声明的所有方法，当然，在这种情况下，类也必须得声明成是抽象的。
 抽象类可以在不提供接口方法实现的情况下实现接口。
 Java接口中声明的变量默认都是final的。抽象类可以包含非final的变量。
 Java接口中的成员函数默认是public的。抽象类的成员函数可以是private，protected或者是public。
 接口是绝对抽象的，不可以被实例化。抽象类也不可以被实例化，但是，如果它包含main方法的话是可以被调用的。
 也可以参考JDK8中抽象类和接口的区别  

### StringBuffer与StringBuilder
* 两者均可多次修改而不产生多余的字符串对象
* StringBuffer相比StringBuilder，是线程安全的，原因是多了synchronized 修饰符
* StringBuilder相比StringBuffer速度更快，通常情况下使用
#### String的不可变性
String的实现是char数组，用final修饰，不可变，不可被继承

### java集合框架
集合Collection 图Map
![Ca1nj.png](https://wx1.sbimg.cn/2020/07/15/Ca1nj.png)

#### 集合
* Set 无序，不允许重复
* List 有序，允许重复
> List
> * ArrayList - 以数组实现，随机查找效率高，插入效率低，非线程安全，多线程操作时有数组越界的风险
> * LinkedList - 以双向链表实现，插入效率高，查找效率低，占空间较大（需要存储指向前后节点的指针），非线程安全
> * Vector - 以数组实现，遗留类，线程安全  
> * 线程安全包装`Collections.synchronizedList()`
