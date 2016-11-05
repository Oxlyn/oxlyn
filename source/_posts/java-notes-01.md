---
title: Java Notes (一)
date: 2016-06-01 20:33:23
tags: Java
---

### 1. HelloWorld
 - 文件名必须和public修饰的类名一致；如果定义的类不是public的，则文件名和类名可以不同。
 - 一个Java文件中可以有多个class，但是只能有一个public修饰的类。
 - Java源代码编译后，一个类对应生成一个class文件。
 - 一个Java应用程序应该包含一个main()方法，且其签名是固定的，是程序的入口。可以定义在任意类中，不一定非得是public修饰的类。
```
javac -d . HelloWorld.java
java mypack.HelloWorld
```
<!--more-->

### 2.  面向对象的特性
 - 抽象
 - 封装
 - 继承
 - 多态

### 3. Java的数据类型
1. 整型
 |byte |1B|8位 |-128 ~ 127      |
 |---  |--|--- |---             |
 |short|2B|16位|-2^15 ~ (2^15)-1|
 |int  |4B|32位|-2^31 ~ (2^31)-1|
 |long |8B|64位|-2^63 ~ (2^63)-1|
2. 浮点型
 |float|4B |32位|
 |---  |---|--- |
 |double|8B |64位|
3. 字符型
 `char 2B 16位`
4. 布尔型
 `boolean true/false`
5. 类型转换
  自动类型转换：`byte -> short -> int -> long -> float -> double`
  强制转换：`int a = (int)3.14;`
  默认浮点类型为double，float类型的后缀为f/F。
  long类型的后缀为l/L。
```
byte a = 1;
byte b = 1;
a = a + b  // Compile Error
a += b     // Success
```

### 5. 引用数据类型
 - 类
 - 接口
 - 数组