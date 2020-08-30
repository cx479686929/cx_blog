---
id: java-keyword
title: java关键字
author: 一代风流～
author_title: To be the weirdest person
author_url: https://blog.csdn.net/qq_43176366
author_image_url: /img/cx-head.jpg


---

java中关键字有50个，当然还有2个保留字（goto、const），其实goto在c和c++中已经尽可能地避免使用了，而const在java中可以用final替代。

<!--truncate-->

# **1.关键字列表**

| abstract   | assert       | bollean   | break      | byte   |
| ---------- | ------------ | --------- | ---------- | ------ |
| case       | catch        | char      | class      | const  |
| continue   | default      | do        | double     | else   |
| enum       | extends      | final     | finally    | float  |
| for        | goto         | if        | implements | import |
| instanceof | int          | interface | long       | native |
| new        | packge       | private   | protected  | public |
| return     | strictfp     | short     | static     | super  |
| switch     | synchronized | this      | throw      | throws |
| transient  | try          | void      | volatile   | while  |

# 2.分类介绍

###  

### 1.类和接口

class：定义类的关键字

interface：定义接口的关键字

abstract class：定义抽象类的关键字

enum：定义枚举的关键字

extends：继承类或者继承接口的关键字

implements：实现接口的关键字

new：实例化对象的关键字

null：表示对象为空

this：表示当前对象

super：表示父类的对象

###  

###  

### 2.数据类型

| 数据类型     | 关键字  | 位数 | 取值范围              | 默认值   |
| ------------ | ------- | ---- | --------------------- | -------- |
| 布尔型       | boolean | 8    | true,false            | false    |
| 字节型       | byte    | 8    | -128~127              | 0        |
| 短整形       | short   | 16   | -32768 ~ 32767        | 0        |
| 整型         | int     | 32   | -2^31-1~2^31          | 0        |
| 长整型       | long    | 64   | -2^63-1~2^63          | 0        |
| 字符型       | char    | 16   | 0~65535               | '\u0000' |
| 单精度浮点型 | float   | 32   | 1.4013E-45~3.4028E+38 | 0.0F     |
| 双精度浮点型 | double  | 64   | 4.9E-324~1.7977E+308  | 0.0D     |

注：byte，short,  int，long使用的是十进制计数

​    而 float，double使用的是科学计数法。所以在这两者之间转换时必须使用强制转换。

###  

### 3.访问范围

| Modifier    | Class | Package | Subclass | World |
| ----------- | ----- | ------- | -------- | ----- |
| public      | Y     | Y       | Y        | Y     |
| protected   | Y     | Y       | Y        | N     |
| no modifier | Y     | Y       | N        | N     |
| private     | Y     | N       | N        | N     |

注： 在java中不注明属性的访问类型的时候就是no modifier类型 ，称为友好访问类型。

###  

### 4.流程控制

for  \ while \do  while  :  循  环

break：中断switch语句的执行，在循环语句中，同样也是结束循环语句的执行。

continue：只跳出本次循环，还要继续执行下一次的循环。break完全跳出所在或者是所标记的循环。

if、else   \switch  、case：表示判断（开关）

default：表示除此以外的其他情况

assert：断言（不常用）

return：返回结果

###  

### 5.异常处理

处理异常，在程序运行时不会因为异常而终止，能够让后面没有异常的代码继续执行 

try：用来检测语句块中是否有异常

catch：用来捕获异常，然后进行处理 

finally：不管是否发生异常，都会执行的语句块

如果程序出现异常后，还能继续执行。

throw：把方法中的发生的异常抛出给方法自身

throws：把方法中的的异常抛出给调用此方法的对象，方法。

volatile：数据同步

synchronized：同步

###  

### 6.其他

static： 静态
       所有使用static的关键字修饰的内容，全部存储在静态内存中
       所有使用static关键字修饰的内容都只有唯一的一份。
   package：定义包的关键字
   import：导入包或者类的关键字
   instanceof：检测对象是否是类的实例
   transient：瞬时的   IO流的对象流
   native：调用C和C++的代码
   final：最终的
      能修饰
       普通方法、属性、变量、形参、常量、类、内部类
       普通方法：表示方法不能被重写；
       属性、变量、形参：表示值不能被改变；
       类：表示不能被继承。
       属性、变量、形参、常量：名字中存储的内容不能改变。
     
   static和final可以用来一起修饰属性(常量)、普通方法、内部类