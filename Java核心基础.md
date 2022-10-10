# Java核心基础



## 第1章  数据类型和运算符

### 1.1 注释

- 单行注释

- 多行注释

- 文档注释
	- **javadoc命令**：对源文件、包生成API文档
  
    `javadoc 选项 Java源文件|包`
  
    -d <directory>：该选项指定一个路径，用于将生成的API文档存放到指定目录下
  
    -windowtitle <text>：该选项指定一个字符串，用于设置API文档的浏览器窗口标题
  
    -doctitle <html-code>：该选项指定一个HTML格式的文本，用于指定页面概述的标题
  
    -header <html-code>：该选项指定一个HTML格式的文本，包含每个页面的页眉

- 示例：

```java
/**
 * 这里时文档注释
 * Description:
 * 网站: <a href="http://www.crazyit.org">疯狂Java联盟</a><br>
 * Copyright (C), 2001-2020, Yeeku.H.Lee<br>
 * This program is protected by copyright laws.<br>
 * Program Name:<br>
 * Date:<br>
 * @author Yeeku.H.Lee kongyeeku@163.com
 * @version 5.0
 */
public class CommentTest{
	/*
	这里面的内容全部是多行注释
	Java语言真的很有趣，
	*/
	public static void main(String[] args){
		// 这是一行简单的注释
		System.out.println("Hello World!");
		// System.out.println("这行代码被注释了，将不会被编译、执行!");
	}
}
```



### 1.2 标识符和关键字

#### 1.2.1 分隔符

- 分号、花括号、方括号、圆括号、空格、圆点

#### 1.2.2 标识符规则

**标识符**就是用于给程序中的变量、类、方法命名的符号

- 标识符可以由字母、数字、下划线（_）和美元符号（$）组成，其中数字不能打头
- 标识符不能是Java关键字和保留字，但可以包含关键字和保留字
- 标识符不能包含空格
- 标识符只能包含美元符号（$），不能包含 @、# 等其他特殊符号

#### 1.2.3 Java 中名称的命名规范

- **包名**：多个单词组成时所有字母都小写，xxxyyyzzz
- **类名、接口名**：多个单词组成时所有单词的首字母都大写，XxxYyyZzz
- **变量名、方法名**：多单词组成时，第一个单词首字母小写，第二个单词开始每个 单词首字母大写，xxxYyyZzz
- **常量名**：所有字母都大写。多单词时每个单词用下划线连接，XXX_YYY_ZZZ

#### 1.2.4 Java关键字

Java语言中一些**具有特殊用途的单词**被称为关键字（keyword），Java中所有关键字都是小写的



### 1.3 数据类型分类

#### 1.3.1 数据类型

- **基本数据类型**

<table>
    <tr>
        <td><h5>四类</h5></td>
    	<td><h5>八种</h5></td>
    	<td><h5>字节数</h5></td>
    	<td><h5>表示数据范围</h5></td>
    </tr>
    <tr>
        <td rowspan="4">整数类型</td>
        <td>byte</td>
        <td>1</td>
        <td>-128(-2<sup>7</sup>) ~ 127(2<sup>7</sup>-1)</td>
	</tr>
    <tr>
        <td>short</td>
        <td>2</td>
        <td>-32768(-2<sup>15</sup>) ~ 32767(2<sup>15</sup>-1)</td>
	</tr>
    <tr>
        <td>int</td>
        <td>4</td>
        <td>-2147483648(-2<sup>31</sup>) ~ 2147483647(2<sup>31</sup>-1)</td>
	</tr>
    <tr>
        <td>long</td>
        <td>8</td>
        <td>(-2<sup>63</sup>) ~ (2<sup>63</sup>-1)</td>
	</tr>
    <tr>
        <td>字符类型</td>
        <td>char</td>
        <td>2</td>
        <td>表示一个字符，如（'a','A','0','家'）</td>
    </tr>
    <tr>
        <td rowspan="2">浮点类型</td>
        <td>float</td>
        <td>4</td>
        <td>-3.403E38 ~ 3.403E38</td>
    </tr>
     <tr>
        <td>double</td>
        <td>8</td>
        <td>-1.798E308 ~ 1.798E308</td>
    </tr>
    <tr>
        <td>布尔类型</td>
        <td>boolean</td>
        <td>1</td>
        <td>true、false</td>
    </tr>


1. ***整数类型***
 > - 如果直接将一个较小的整数值（在byte或short类型的表数据范围内）赋给一个byte或short变量，系统会自动将这个整数当成byte或short类型处理
> - 如果使用一个巨大的整数（超过了int类型的表示数据范围）时，Java不会把这个整数值当成long类型处理，必须在这个整数值后增加 **l** 或 **L** 作为后缀

- Java中数值由四种表示方式
  - 十进制
  - 二进制：以 **0b** 或 **0B** 开头，最高位是符号位
  - 八进制：以 **0** 开头
  - 十六进制：以 **0x** 或 **0X** 开头，其中 10 ~ 15 分别以 a ~ f （不区分大小写）来表示

 - **引用数据类型**
   - 类
   - 接口
   - 数组

2. ***字符型***

> - 直接通过单个字符来指定字符型值，例如 'A'、'0' 和 '9' 等
> - 通过转义字符表示特殊字符型值，例如 '\n'、'\t' 等
> - 直接使用Unicode值来表示字符型值，格式是 '\uXXXX'，其中XXXX代表一个十六进制整数

<center>Java语言中常用的转义字符</center>

| 转义字符 |  说明  | Unicode表示方式 |
| :------: | :----: | :-------------: |
|    \b    | 退格符 |     \u0008      |
|    \n    | 换行符 |     \u000a      |
|    \r    | 回车符 |     \u000d      |
|    \t    | 制表符 |     \u0009      |
|   \\''   | 双引号 |     \u0022      |
|   \\'    | 单引号 |     \u0027      |
|   \\\    | 反斜线 |     \u005c      |

2. ***浮点型***

> - 浮点数必须包含一个小数点，否则将被当成 int 类型处理
> - Java语言浮点类型默认是double类型，在这个浮点数后面加 f 或 F 表示float类型
> - Java提供了三种特殊的浮点数：
>   - 正无穷大：POSITIVE_INFINITY
>   - 负无穷大：NEGATIVE_INFINITY
>   - 非数：NaN

==数值中可以使用下划线分割==，便于直观的分辨由多少位

3. ***布尔型***

#### 1.3.2 使用 var 定义变量

var相当于一个动态类型，使用var定义的局部变量的类型由编译器自动推断

- 使用 var 定义局部变量时，必须在定义局部变量的同时指定初始值

- 如果局部变量的初始值的类型很容易确定，那么此时可以使用 var 定义局部变量
- 对于以下几种情况，应该避免使用 var 定义局部变量
  - 变量类型不易判断
  - 局部变量的使用范围很大



### 1.4 基本类型的类型转化

#### 1.4.1 自动类型转换

![自动类型转换图](Java核心基础.assets\自动类型转换图.png)

<center>自动类型转换图</center>

- 当把任何基本类型的值和字符串值进行连接运算时，基本类型的值将自动转换为字符串类型

#### 1.4.2 强制类型转换

- 将上图中箭头右边的数据类型转换为左边的类型，需要使用强制类型转换
- 语法格式：

```java 
(targetType) value
```

==注意：强制类型转换，可能会有数据溢出，造成数据精度的损失==

#### 1.4.3 表达式类型的自动提升

当一个算术表达式中包含多个基本数据类型时，整个算术表达式的数据类型将发生自动提升

- 所有的byte类型、short类型和 char类型将被提升到 int 类型
- 整个算术表达式的数据类型自动提升到与表达式中最高等级操作数同样的类型



### 1.5 运算符

#### 1.5.1 算术运算符

Java支持所有的基本算术运算符，**加（+）、减（-）、乘（*）、除（/）、取余（%）、自加（++）、自减（--）**

- 如果除法运算符的两个操作数都是整数，则计算结果也是整数；且除数不可以为 0 ，否则引发除以 0 异常。如果有一个或两个浮点数，计算结果也是浮点数；此时允许除数是 0 或 0.0 ，得到的结果是**正无穷大**或**负无穷大**
- 求余运算的结果不一定是整数，如果两个操作数都是整数，第二个操作数不可以为 0 ，否则引发除以 0 异常。如果有一个或两个浮点数，此时允许第二个操作数是 0 或 0.0 ，得到的结果是**NaN**
- 自加、自减运算符：
  - 是单目运算符，只能操作一个操作数
  - 只能用于操作变量，不能用于操作数值直接量、常量或表达式
  - 若将++、--放在操作数**左边**，则**先将操作数加1，然后再进行运算**；若放在操作数**右边**，则**先进行运算，再将操作数加1**

#### 1.5.2 赋值运算符

**赋值运算（=）**符用于为变量指定变量值，赋值运算符可以与算术运算符、位运算符结合，扩展成功能更强大的运算符。

**+=、-=、*=、/=、%=、&=、|=、^=、<<=、>>=、>>>=**

将左右两边的操作数进行运算然后赋值给左边的变量

#### 1.5.3 位运算符

- **&：**按位与。当两位同时为1时才返回1
- **|：**按位或。只要有一位为1即可返回1
- **~：**按位非。单目运算符，将操作数的每个位（包括符号位）全部取反
- **^：**按位异或。当两位相同时返回0，不同时返回1
- **<<：**左移运算符
- **\>>：**右移运算符
- **\>>>：**无符号右移运算符

一般来说，位运算符只能操作整数类型的变量或值

==移位运算规则：==对于低于int类型的操作数总是先自动类型转换位int后再进行移位；对于int类型的整数移位a>>b，**当b>32时，先用b对32求余**，再进行移位；对于long类型的同理

#### 1.5.4 比较运算符

比较运算符用于判断两个变量或常量的大小，比较运算符的结果是一个布尔值（true 或 false）

**>、>=、<、<=、==、!=**

#### 1.5.5 逻辑运算符

逻辑运算符用于操作两个布尔型的变量或常量

**&&、&、||、|、!、^**

==&&与&、||与|区别：==&和|总会计算前后两个操作数，而&&和||会先计算左边操作数，如果左边的操作数可以直接确定结果，就不会计算右边操作数

#### 1.5.6 三目运算符

三目运算符只有一个：**? : ;**

语法格式：`(expression) ? if-true-statement : if-false-statement; 

#### 1.5.7 运算符的结合性和优先级

<center>运算符优先级（上一行优先于下一行）</center>

|     运算符说明     |                          Java运算符                          |
| :----------------: | :----------------------------------------------------------: |
|       分隔符       |                   .   []   ()   {}   ,  ;                    |
|     单目运算符     |                       ++   --   ~   !                        |
| 强制类型转换运算符 |                            (type)                            |
|   乘法/除法/求余   |                          \*   /   %                          |
|     加法/减法      |                            +   -                             |
|     移位运算符     |                        <<   >>   >>>                         |
|     关系运算符     |                 <   <=   >   >=   instanceof                 |
|     等价运算符     |                           ==   !=                            |
|       按位与       |                              &                               |
|      按位异或      |                              ^                               |
|       按位或       |                              \|                              |
|       条件与       |                              &&                              |
|       条件或       |                             \|\|                             |
|     三目运算符     |                             ? :                              |
|        赋值        | =   +=   -=   \*=   /=   %=   &=   \|=   ^=   <<=   >>=   >>>= |

- ==注意：==其中只有**单目运算符、赋值运算符、三目运算符**是从右向左结合的，其余都是从左向右结合



## 第2章  流程控制与数组

### 2.1 顺序结构

- 顺序结构就是程序**从上到下逐行**地执行，中间没有任何的判断和跳转



### 2.2 分支结构

#### 2.2.1 if 条件语句

- if 语句使用布尔表达式或布尔值作为分支条件进行分支控制。if 语句有如下三种形式

  - 第一种形式

  ```java
  if (logic expression) {
      statement...
  }
  ```

  - 第二种形式

  ```java
  if (logic expression) {
      statement...
  } else {
      statement...
  }
  ```

  - 第三种形式

  ```java
  if (logic expression) {
      statement..
  } else if (logic expression) { //可以有多个 else if 语句
      statement...
  } else { //最后的 else 语句也可以省略
      statement...
  } 
  ```

 - - 放在 if 之后花括号里的只能是一个逻辑表达式，及这个表达式的返回值只能是 true 或 false
    - 如果 if、else if、else 后面的代码块**只有一条执行语句**时，则可以省略花括号，==但不建议省略==；如果省略花括号，**那么条件只控制到紧跟该条件语句的第一个分号处**
    - 使用 if...else 时，总是**优先包含范围小的条件放在前面处理**

#### 2.2.2 Java11 改进的 switch 分支语句

- switch 语句由一个控制表达式和多个 case 标签组成，和 if 语句不同的是，switch 语句后面的控制表达式的数据类型只能是 **byte、short、char、int 四种整数类型，枚举类型和 java.lang.String 类型（从 Java7 才允许），**不能是 boolean 类型。switch 语句的语法格式如下：

 ```java
  switch (expression) {
      case condition1:
          statement(s)
          break;
      case condition2:
          statement(s)
          break;
      ...
      case conditionN:
          statement(s)
          break;
      default:
          statement(s)
  }
 ```

  - switch 分支语句的执行是先对 expression 求值，然后依次匹配 condition1、condition2、...、conditionN 等值，遇到匹配的值就执行对应的执行体；如果 case 标签后的值都不与 expression 表达式的值相等，则执行 default 标签后的代码块
  - 在 case 标签后的**每个代码块后都有一条 break 语句**，如果省略，将会引入一个陷阱。switch 语句一旦遇到相等的值，程序就开始执行 case 标签后的代码，不再判断与后面 case、default 标签的条件是否匹配，除非遇到 break; 才会结束



### 2.3 循环结构

- 循环语句可以在满足循环条件的情况下，反复执行某一段代码。循环语句可能包含如下4个部分：
  - **初始化语句（init_statement）：**一条或多条语句，用于完成一些初始化工作，初始化语句在循环开始之前执行
  - **循环条件（test_expression）：**是一个 boolean 表达式，这个表达式能决定是否执行循环体
  - **循环体（body_statement）：**循环的主体，如果循环条件允许，代码块将被重复执行。如果只有一条语句，花括号可以省略
  - **迭代语句（iteration_statement）：**在一次循环体执行结束后，对循环条件求值之前执行，通常控制循环条件中的变量，使得循环在合适的时候结束

#### 2.3.1 while 循环语句

- while 循环的语法格式如下：

```java 
[init_statement]
while (test_expression) {
    statement;
    [iteration_statement]
}
```

#### 2.3.2 do while 循环语句

- do while 循环的语法格式如下：

```java
[init_statement]
do {
    statement;
    [iteration_statement]
} while (test_expression);
```

#### 2.3.3 for 循环

- for 循环的基本语法格式如下：

```java
for ([init_statement]; [test_expression]; [iteration_statement]) {
    statement;
}
```

#### 2.3.4 嵌套循环

- 如果把一个循环凡在另一个循环体内，那么就可以形成嵌套循环

<img src="Java核心基础.assets\嵌套循环的执行流程.png" alt="嵌套循环的执行流程" style="zoom:70%;" />

<center>嵌套循环的执行流程</center>



### 2.4 控制循环结构

#### 2.4.1 使用 break 结束循环

- break 用于**完全结束一个循环，跳出循环体**
- break 还可用于直接结束其外层循环，此时需要在 break 后紧跟一个标签，这个标签用于标识一个外层循环

> Java 标签就是一个紧跟着英文冒号（:）的标识符。与其他语言不同，Java 中的标签只有放在循环语句之前才有用

==注意：==通常紧跟 break 之后的标签，必须在 break 所在的循环的外层循环之前定义才有意义

#### 2.4.2 使用 continue 忽略本次循环的剩下语句

- continue 的功能和 break 有点类似，区别是 continue 只是**忽略本次循环的剩下语句，接着开始下一次循环，并不会终止循环**
- continue 后也可紧跟一个标签，用于直接跳过标签所标识循环的当此循环的剩下语句，重新开始下一次循环

#### 2.4.3 使用 return 结束方法

- return 关键字并不是专门用于结束循环的，return 的功能是**结束一个方法**。当一个方法执行到一个 return 语句时（ return 关键字后还可紧跟变量、常量和表达式），这个方法将被结束
- 与 break 和 continue 不同的是，return 直接结束整个方法，不管这个 return 处于多少层循环之内



### 2.5 数组类型

#### 2.5.1 定义数组

- Java语言支持两种语法格式来定义数组：

```java 
type[] arrayName;
type arrayName[];
```

- - 通常推荐使用第一种格式
  - ==注意：==定义数组时不能指定数组的长度

#### 2.5.2 数组的初始化

1. **静态初始化**

   - 静态初始化的语法格式如下：

     ```java
     arrayName = new type[] {element1, element2, element3, ...};
     ```

   - 除此之外，静态初始化还有如下简化的语法格式：

     ```java
     type[] arrayName = {element1, element2, element3, ...};
     ```

     > ==注意：==只有在定义数组的同时执行数组的初始化才支持使用简化的静态初始化

2. **动态初始化**

   - 动态初始化**只指定数组的长度**，由系统为每个数组元素指定初始值。动态初始化的语法格式如下：

     ```java
     arrayName = new type[length];
     ```

   - 指定初始值时，系统按如下规则分配初始值

     - 整数类型（byte、short、int 和 long）：0
     - 浮点类型（float、double）：0.0
     - 字符类型（char）：'\u0000'
     - 布尔类型（boolean）：false
     - 引用类型（类、接口和数组）：null

   - 在定义数组类型的局部变量时，同样可以使用 var 来定义变量

     `var names = new String[] {"yeeku", "nono"};`

     > ==注意：==使用静态初始化简化语法执行初始化的数组不能使用 var 定义数组变量

==注意：不要同时使用动态初始化和静态初始化==

#### 2.5.3 使用数组

- 访问数组元素都是通过在数组引用变量后紧跟一个方括号（[]），方括号里是数组的索引值。访问到数组元素后，就可以将其当成一个普通的变量使用
- Java 语言的**数组索引是从 0 开始**的，第一个数组元素的索引值为 **0**，最后一个数组元素的索引值为**数组长度减 1**
- 如果访问数组元素时指定的索引值小于 0，或者大于等于数组的长度，编译程序不会出现错误，但运行时出现异常：java.lang.ArrayIndexOutOfBoundsException:N（数组索引越界异常），N 是试图访问的数组索引

#### 2.5.4 foreach 循环

- 使用 foreach 循环遍历数组和集合元素时，**无需获得数组和集合长度，无需根据索引来访问数组元素和集合元素**，foreach 循环自动遍历数组和集合的每个元素，语法格式如下：

  ```java
  for (type variableName : array | collection) {
      //variableName 自动迭代访问每个元素...
  }
  ```

  > ==注意：==使用 foreach 循环迭代数组元素时，并不能改变数组元素的值，因此不要对 foreach 的循环变量进行赋值



### 2.6 深入数组

#### 2.6.1 内存中的数组

- 数组引用变量只是一个引用，这个引用变量可以指向任何有效的内存，只有当该引用指向有效内存后，才可通过该数组变量来访问数组

- 实际的数组对象被存储在堆（heap）内存中；如果引用该数组对象的数组引用变量是一个局部变量，那么它被存储在栈（stack）内存中。

  <img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\数组在内存中的存储示意图.png" alt="数组在内存中的存储示意图" style="zoom:70%;" />

  <center>数组在内存中的存储示意图</center>

#### 2.6.2 基本类型数组的初始化

- 对于基本类型数组而言，数组元素的值直接存储在对应的数组元素中，因此，初始化数组时，先为该数组分配内存空间，然后直接将数组元素的值存入对应的数组元素中

  ![基本类型数组的初始化](Java核心基础.assets\基本类型数组的初始化.png)

  <center>基本类型数组的初始化</center>

#### 2.6.3 引用类型数组的初始化

- 引用型数组的数组元素是引用。每个数组元素里存储的还是引用，它指向另一块内存，这块内存里存储了有效数据

  ![引用类型数组的初始化](Java核心基础.assets\引用类型数组的初始化.png )

  <center>引用类型数组的初始化</center>

#### 2.6.4 二维数组

- 从数组底层运行机制上来看，没有多维数组；二维数组只是一维数组的元素是另一个一维数组

- 定义和初始化二维数组的语法：

  ```java 
  //动态初始化
  type[][] arrayName = new type[length][length]; //其中第二个length可以不在这初始化
  //静态初始化
  String[][] str1 = new String[] {new String[3], new String[] {"hello"}};
  //静态初始化简化语法
  String[][] str2 = {new String[3], new String[] {"hello"}};
  ```

- 二维数组的内存解析

  <img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\二维数组内存解析.png" alt="二维数组的内存解析" style="zoom:70%;" />

  <center>二维数组内存解析</center>

#### 2.6.5 操作数组的工具类：Arrays

- static 修饰的静态方法：

  - ==**binarySearch(type[] a, type key)**==：使用二分法查找 key 元素值在 a 数组中出现的索引；如果未找到，则返回负数。调用该方法时要求数组中的元素已经按升序排列
  - ==**binarySearch(type[] a, int fromIndex, int toIndex, type key)**==：与前一个方法类似，但只搜索 a 数组中 fromIndex 到 toIndex 索引的元素
  - ==**type[] copyOf(type[] original, int length)**==：把 original 数组复制成一个新数组，其中 length 是新数组的长度。如果 length 小于 original 数组的长度，则新数组就是原数组的前面 length 个元素；如果 length 大于 original 数组的长度，则新数组前面的元素就是原数组的所有元素，后面补充 0（数值类型）、false（布尔类型）或者 null（引用类型）
  - ==**type[] copyOfRange(type[] original, int from, int to)**==：与前一个方法类似，但只复制 original 数组的 from 索引到 to 索引的元素
  - ==**boolean equals(type[] a, type[] a2)**==：如果 a 数组和 a2 数组的长度相等，而且 a 数组和 a2 数组的数组元素也一一相同，该方法返回 true
  - ==**void fill(type[] a, type val)**==：把 a 数组的所有元素都赋值为 val
  - ==**void fill(type[] a, int fromIndex, int toIndex, type val)**==：与前一个方法类似，该方法仅将 a 数组的 fromIndex 到 toIndex 索引的数组元素赋值为 val
  - ==**void sort(type[] a)**==：对 a 数组元素进行排序
  - ==**void sort(type[] a, int fromIndex, int toIndex)**==：与前一个方法类似，该方法仅对 fromIndex 到 toIndex 索引的元素排序
  - ==**String toString(type[] a)**==：将一个数组转换成一个字符串。按顺序把多个数组元素连缀在一起，多个数组元素使用英文逗号（,）和空格隔开

- Java 8 增强的 Arrays 类的功能：

  - ==**void parallelPrefix(xxx[] array, XxxBinaryOperator op)**==：该方法使用 op 参数指定的计算公式计算得到的结果作为新的数组元素。op 计算公式包括left、right 两个参数，其中 left 代表新数组中前一个索引处的元素，right 代表 array 数组中当前索引处的元素。新数组的第一个元素无需计算，直接等于 array 数组的第一个元素

  - ==**void parallelPrefix(xxx[] array, int fromIndex, int toIndex, XxxBinaryOperator op)**==：与前一个方法类似，但只重新计算  fromIndex 到 toIndex 索引的元素

  - ==**void setAll(xxx[] array, IntToXxxFunction generator)**==：使用指定的生成器（generator）为所有数组元素设置值，该生成器控制数组元素的值的生成算法

  - ==**void parallelSetAll(xxx[] array, IntToXxxFunction generator)**==：与前一个方法类似，只是增加了并行能力

  - ==**void  parallelSort(xxx[] a)**==：与 Arrays 类以前就有的 sort() 方法类似，只是增加了并行能力

  - ==**void parallelSort(xxx[] a, int fromIndex, int toIndex)**==：与前一个方法类似，该方法仅对 fromIndex 到 toIndex 索引的元素排序

  - ==**Spliterator.OfXxx spliterator(xxx[] array)**==：将该数组的所有元素转换成对应的 Spliterator 对象

  - ==**Spliterator.OfXxx spliterator(xxx[] array, int startInclusive, int endExclusive)**==：与前一个方法类似，该方法仅对转换startInclusive 到 endExclusive 索引的元素

  - ==**XxxStream stream(xxx[] array)**==：将数组转换成 Stream，Stream 是 Java 8 新增的流式编程的 API

  - ==**XxxStream stream(xxx[] array, int startInclusive, int endExclusive)**==：与前一个方法类似，该方法仅对转换startInclusive 到 endExclusive 索引的元素

    > 所有以 parallel 开头的方法都表示该方法利用 CPU 并行能力来提高性能



## 第3章  面向对象（上）

### 3.1 类和对象

#### 3.1.1 定义类

- Java语言里定义**类**的简单语法如下：

  ```java
  [修饰符] class 类名 {
      零到多个构造器定义..
      零到多个成员变量..
      零到多个方法..
  }
  ```

  - 修饰符可以是 **public、final、abstract**，或者完全**省略**这三个修饰符

  - static 修饰的成员不能访问不能访问没有 static 修饰的成员，static 修饰的成员表示它是**属于类的**，而不属于单个实例

  - 构造器用于构造该类的实例，Java语言通过 **new 关键字**来调用构造器，从而返回该类的实例；如果程序员没有为一个类编写构造器，则系统为该类提供一个默认的构造器，一旦程序员为一个类提供了构造器，系统将不在为该类提供构造器

  - 定义**成员变量**的语法格式如下：

    ```java
    [修饰符]  类型 成员变量名 [= 默认值];
    ```

    - 修饰符：可以省略，也可以是 public、protected、private、static、final，其中 public、protected、private 只能出现一个，可以与 static、final 组合起来修饰成员变量
    - 类型：可以是 Java 语言允许的任何数据类型
    - 成员变量名：合法的标识符，遵守 Java 名称命名规范
    - 默认值：定义成员变量时还可以指定一个可选的默认值

  - 定义**方法**的格式如下：

    ```java
    [修饰符] 方法返回值类型 方法名(形参列表) {
        //有零到多条可执行语句组成的方法体
    }
    ```

    - 修饰符：可以省略，也可以是 public、protected、private、static、final、abstract，其中 public、protected、private 只能出现一个，final 和 abstract 只能出现一个，可以与 static 组合起来修饰方法
    - 方法返回值类型：可以是 Java 语言允许的任何数据类型，如果声明了方法返回值类型，则方法体内必须有一个**有效的return 语句**，该语句返回一个变量或表达式（类型必须与声明的类型匹配）；如果一个方法没有返回值，则使用 **void** 来声明
    - 方法名：合法的标识符，遵守 Java 名称命名规范
    - 形参列表：用于定义该方法可以接受的参数，有零到多组**“参数类型 形参名”**组合而成，多组参数之间用**英文逗号（,）**隔开，形参类型和形参名之间以英文空格隔开，一旦指定了形参列表，则调用该方法时必须传入对应的参数值

  - 定义**构造器**的语法如下：

    ```java
    [修饰符] 构造器名(形参列表) {
        //有零到多条可执行语句组成的构造器执行体
    }
    ```

    - 修饰符：可以省略，也可以使用 public、protected、private 其中之一
    - 构造器名：**必须与类名相同**
    - 形参列表：和定义方法形参列表的格式完全相同
  
- 示例：

```java
class Person{
	// 下面定义了两个成员变量
	public String name;
	public int age;
	// 下面定义了一个say方法
	public void say(String content){
		System.out.println(content);
	}
}
public class PersonTest{
	public static void main(String[] args){
		// 使用Peron类定义一个Person类型的变量
		Person p;
		// 通过new关键字调用Person类的构造器，返回一个Person实例，
		// 将该Person实例赋给p变量。
		p = new Person();

		// 访问p的name实例变量，直接为该变量赋值。
		p.name = "李刚";
		// 调用p的say方法，声明say()方法时定义了一个形参，
		// 调用该方法必须为形参指定一个值
		p.say("Java语言很简单，学习很容易！");
		// 直接输出p的name实例变量，将输出 李刚
		System.out.println(p.name);

		// 将p变量的值赋值给p2变量
		var p2 = p;
	}
}
```



#### 3.1.2 对象的产生和使用

- 对象的创建：

  ```java
  类名 对象名 = new 类名()
  ```
- Java 的对象大致有如下作用：

  - 访问对象的实例变量
  - 调用对象的方法

  ```java
  对象名.实例变量|方法
  ```

  - static 修饰的方法和成员变量，既可以通过类来调用，也可以通过实例来调用；没有 static 修饰的只能通过实例来调用

  ```java
  类.类变量|方法
  ```


#### 3.1.3 对象的内存解析

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\对象的内存解析.png" alt="对象的内存解析" style="zoom:70%;" />

<center>引用变量指向实际对象的示意图</center>

#### 3.1.4 对象的 this 引用

- this 关键字总是指向调用该方法的对象。根据 this 出现的位置不同，this 作为对象的默认引用有两种情形

  1. 构造器中引用该构造器**正在初始化的对象**
  2. 在方法中引用**调用该方法的对象**

- Java 允许对象的一个成员直接调用另一个成员，可以省略 this 前缀。大部分时候，一个方法访问该类中定义的其他方法、成员变量时加不加 this 前缀的效果是完全一样的

- 对于 static 修饰的方法而言，则可以使用类直接调用该方法。**static 修饰的方法不能使用 this 引用。**

  > ==**静态成员不能直接访问非静态成员**==

- 大部分时候，访问其他成员变量和方法是可以省略 this 前缀，但如果有一个**与成员变量同名的局部变量**，又必须**访问这个被覆盖的成员变量**，**则必须使用 this 前缀**

- 在构造器中使用 **this 调用另一个重载的构造器**时，必须作为**构造器执行体的第一条语句**



### 3.2 方法详解

#### 3.2.1 方法的所属性

- 方法不能独立定义，方法只能在类体内定义
- 从逻辑意义上看，方法要么属于类本身，要么属于该类的一个对象
- 永远不能独立执行方法，执行方法必须使用类或对象作为调用者

#### 3.2.2 方法的值传递机制

- Java 里方法的参数传递方式只有一种：**值传递**。所谓值传递，就是将实际参数值的副本（复制品）传入方法内，而参数本身不受影响

- **值传递的实质**：当系统开始执行方法时，系统为形参执行初始化，就是把实参变量的值赋给方法的形参变量，方法里操作的并不是实际的实参变量

- 基本类型的参数传递：

  ```java
  public static void swap(int a, int b){
  	// 下面三行代码实现a、b变量的值交换。
  	// 定义一个临时变量来保存a变量的值
  	var tmp = a;
  	// 把b的值赋给a
  	a = b;
  	// 把临时变量tmp的值赋给b
  	b = tmp;
  	System.out.println("swap方法里，a的值是"+ a + "；b的值是" + b); // a:9 b:6
  }
  public static void main(String[] args){
  	var a = 6;
  	var b = 9;
  	swap(a, b);
  	System.out.println("交换结束后，变量a的值是"+ a + "；变量b的值是" + b); // a:6 b:9
  }
  ```

  <img src="Java核心基础.assets\基本类型的参数传递.png" alt="基本类型的参数传递" style="zoom:70%;" />

- 引用类型的值传递：

  ```java
  class DataWrap{
  	int a;
  	int b;
  }
  public class ReferenceTransferTest{
  	public static void swap(DataWrap dw){
  		// 下面三行代码实现dw的a、b两个成员变量的值交换。
  		// 定义一个临时变量来保存dw对象的a成员变量的值
  		var tmp = dw.a;
  		// 把dw对象的b成员变量值赋给a成员变量
  		dw.a = dw.b;
  		// 把临时变量tmp的值赋给dw对象的b成员变量
  		dw.b = tmp;
  		System.out.println("swap方法里，a成员变量的值是"+ dw.a + "；b成员变量的值是" + dw.b); // a:9 b:6
  		// 把dw直接赋为null，让它不再指向任何有效地址。
  		dw = null;
  	}
  public static void main(String[] args){
  		var dw = new DataWrap();
  		dw.a = 6;
  		dw.b = 9;
  		swap(dw);
  		System.out.println("交换结束后，a成员变量的值是"+ dw.a + "；b成员变量的值是" + dw.b); // a:9 b:6
  	}
  }
  ```

  <img src="Java核心基础.assets\引用类型的参数传递.png" alt="引用类型的参数传递" style="zoom:70%;" />

#### 3.2.3 形参可变的方法

- 从 JDK 1.5 之后，Java 允许定义**形参个数可变的参数**，从而允许为方法指定数量不确定的形参。如果在定义方法时，在**最后一个形参从类型后加三个点（...）**，则表名该形参可以接受多个参数值，多个参数值被当成数组传入
- 个数可变的形参**只能处于形参列表的最后**。一个方法中**最多只能包含一个**个数可变的形参。
- 个数可变的形参**本质就是一个数组类型的形参**，因此调用时既可传入多个参数，也可传入一个数组

#### 3.2.4 递归方法

- **一个方法体内调用它自身**，被称为方法递归。方法递归包含一种隐式的循环，它会重复执行某段代码，但无需循环控制
- 当一个方法不断调用它本身时，必须在某个时刻方法的返回值时确定的，即不再调它本身，否则这种递归就变成了无穷递归。因此定义递归方法时有一条重要的规定：==**递归一定要向已知方向递归**==

#### 3.2.5 方法重载

- Java 允许同一个类中定义多个同名方法，只要形参列表不同就行。如果一个类中包含了**两个或两个以上方法的方法名相同，但形参列表不同**，则被称为方法重载
- 方法重载的要求是**两同一不同**：同一个类中方法名相同，参数列表不同。



### 3.3 成员变量和局部变量

- 变量的分类：

  <img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\变量分类图.png" alt="变量的分类图" style="zoom:70%;" />

- 成员变量是指在类里定义的变量，也就是前面所说的 field

  - 类变量：作用域与**这个类的生存范围相同**
  - 实例变量：作用域**对应实例的生存范围相同**

  > 成员变量**无需显示初始化**，只要为一个类定义了成员变量，系统就会在这个类的准备阶段或创建该类的实例时进行**默认初始化**

- 局部变量是指在方法里定义的变量

  - 形参：作用域在**整个方法内有效**
  - 方法局部变量：作用域**从定义该变量的地方生效，到该方法结束时失效**
  - 代码块局部变量：作用域**从定义该变量的地方生效，到该代码块结束时失效**

  > 局部变量**除形参之外，都必须显示初始化**

- 一个类里不能定义两个同名的成员变量，一个方法里不能定义两个同名的方法局部变量，方法局部变量与形参也不能同名

- Java 允许成员变量和局部变量同名，如果方法里的局部变量和成员变量同名，**局部变量会覆盖成员变量**，如果需要在这个方法引用被覆盖的成员变量，则可使用 **this （对于实例变量）或类名（对于类变量）**作为调用者来限定访问成员变量



### 3.4 隐藏和封装

> **封装（Encapsulation）是面向对象的三大特征之一（另外两个是继承和多态），它指的是将对象的状态信息隐藏在对象内部，不允许外部程序直接访问，而是通过该类所提供方法来实现对内部信息的操作和访问**

- Java 提供了 3 个访问控制符：private、protected 和 public，分别代表了 3 个访问控制级别，另外还提供了一个不加任何访问控制符的访问控制级别，一共 4 个访问控制级别

  <img src="Java核心基础.assets\访问控制级别图.png" style="zoom:80%;" />

  <center>访问控制级别图</center>
  
  - **==private==（当前访问权限）**：这个成员只能在当前类的内部被访问
  - **==*default*==（包访问权限）**：这个成员或外部类可以被相同包下的其他类访问
  - **==protected==（子类访问权限）**：这个成员既可以被同一个包的其他类访问，也可以被不同包中的子类访问
  - **==public==（公共访问权限）**：这个成员或外部类可以被所有类访问
  
  <center>访问控制级别表</center>
  
  |            | private | default | protected | public |
  | :--------- | :-----: | :-----: | :-------: | :----: |
  | 同一个类中 |    √    |    √    |     √     |   √    |
  | 同一个包中 |         |    √    |     √     |   √    |
  | 子类       |         |         |     √     |   √    |
  | 全局范围   |         |         |           |   √    |
  
- 关于访问控制符的使用，存在如下几条基本规则：

  - 类里的绝大部分成员变量都应该使用 private 修饰，只有一些 static 修饰的、类似全局变量的成员变量，才可能考虑使用 public 修饰。有些方法只用于辅助实现该类的其他方法（工具方法）也应该使用 private 修饰
  - 如果某个类主要用作其他类的父类，该类中包含的大部分方法可能仅希望被其子类重写，而不像被外界直接调用，应使用protected 修饰
  - 希望暴露出来给其它类自由调用的方法应该使用 public 修饰



### 3.5 类的继承

> **继承是面向对象的三大特征之一，也是实现软件复用的重要手段。Java 的继承具有单继承的特点，每个子类只有一个直接父类**

#### 3.5.1 继承的特点

- Java 的继承通过 ==**extends 关键字**==来实现，实现继承的类被称为子类，被继承的类称为父类。父类和子类的关系，是一种一般和特殊的关系。Java 中子类继承父类的语法格式如下：

  ```java
  修饰符 class SubClass extends SuperClass {
      //类定义部分
  }
  ```

- 子类只能从被扩展的父类获得**成员变量、方法和内部类（包括内部接口、枚举）**，不能获得构造器和初始化块

- Java 类只能有一个直接父类，但可以有无限个间接父类。如果定义一个 Java 类时并未显式的指定这个类的直接父类则这个类默认扩展 java.lang.Object 类。因此 java.lang.Object 类是所有类的父类，所有 Java 对象都可以调用其定义的实例方法

#### 3.5.2 重写父类的方法

- 子类包含与父类同名方法的现象被称为**方法重写（Override）**，也被称为**方法覆盖**

- 方法重写要遵循 **“两同两小一大”** 规则：

  - 两同：方法名相同、形参列表相同
  - 两小：子类方法返回值类型比父类的更小或相等，子类方法声明抛出的异常类比父类方法的更小或相等
  - 一大：子类方法的访问权限应比父类的更大或相等

  ==注意：==覆盖方法和被覆盖的方法要么都是类方法，要么都是实例方法

- 当子类覆盖了父类方法后，子类对象将无法访问父类中被覆盖的方法，但可以在子类中**调用父类中被覆盖的方法**。使用 **super （被覆盖的是实例方法）**或者**父类类名（被覆盖的是类方法）**作为调用者来调用父类中被覆盖的方法

#### 3.5.3 super 限定

- **super** 是 Java 提供的一个关键字，用于**限定该对象调用他从父类继承得到的实例变量或方法**。不能出现在 static 修饰的方法中
- 如果在构造器中使用 super ，则 super 用于限定该构造器初始化的是**该对象从父类继承得到的实例变量**，而不是该类自己定义的实例变量
  - 使用 super 调用父类构造器也必须出现在**子类构造器执行体的第一行**，所有 this 调用和 super 调用**不会同时出现**
  - 不管是否使用 super 调用来执行父类构造器的初始化代码，**子类构造器总会调用父类构造器一次**。分如下情况：
    - 子类构造器执行体的第一行使用 **super 显式调用父类构造器**，系统将**根据 super 调用里传入的实参列表调用父类对应的构造器**
    - 子类构造器执行体的第一行使用 **this 显式调用本类中重载的构造器**，系统将根据 **this 调用里传入的实参列表调用本类中另一个构造器**。执行本类中另一个构造器时也会先调用父类构造器
    - 子类构造器执行体中**既没有 super 调用，也没有 this 调用**，系统将会在执行子类构造器之前，**隐式调用父类无参构造器**
- 如果子类定义了和父类同名的实例变量，则会发生子类实例变量隐藏父类实例变量的情形。可以通过 super 访问父类中被隐藏的实例变量。如果没有显式的指定调用者，则系统查找顺序为：
  - 该方法 - - > 当前类  - - > 直接父类及所有父类



### 3.6 多态

> **Java 引用变量有两个类型：编译时类型和运行时类型。编译时类型由声明该变量时使用的类型决定，运行时类型由实际赋给该变量的对象决定。如果编译时类型和运行时类型不一致，就可能出现所谓的多态（Polymorphism）**

#### 3.6.1 多态性

- 因为子类其实是一种特殊的父类，因此 Java 允许**把一个子类对象直接赋给一个父类引用变量**，无需任何类型转换，或者被称为**向上转型**，向上转型由系统自动完成
- 当把一个子类对象直接赋给父类引用变量时，编译时类型是父类类型，而运行时类型是子类类型，当运行时调用该引用变量的方法时，其**方法行为总是表现出子类方法的特征**，这就可能出现：**相同类型的变量，调用同一个方法时呈现出多种不同的行为特征**，这就是**多态**
- **==注意：==**引用变量在编译阶段只能调用其编译时类型所具有的方法，但运行时则执行它运行时类型所具有的方法。因此，在编写 Java 代码的时，==**引用变量只能调用声明该变量时所用类型包含的方法**==。
- **==注意：==**通过引用变量来访问其包含的实例变量时，系统总是试图访问它编译时类型所定义的成员变量，而不是它运行时类型所定义的

#### 3.6.2 引用变量的强制类型转换 与 instanceof 运算符

- 在编写 Java 程序时，引用变量只能调用它编译时类型的方法，而不能调用它运行时类型的方法，如果要让这个引用变量调用它运行时类型的方法，则必须把**它强制类型转换成运行时类型：`(type) variable`**，进行转换时需注意：
  - 基本类型之间的转换只能在数值类型（整数型、字符型和浮点型）之间进行。但数值类型和布尔类型之间不能进行类型转换
  - 引用类型之间的转换只能在**具有继承关系的两个类之间进行**，如果是两个没有任何继承关系的类型，则无法进行类型转换，否则编译时会出现错误。如果试图将一个父类实例转换成子类类型，则**这个对象必须实际上是子类实例**（即编译时是父类类型，而运行时是子类类型），否则将在运行时引发 ClassCastException 异常
- 考虑到进行强制类型转换时可能出现异常，**在进行强制类型转换之前，先用 instanceof 运算符判断是否可以成功转换**，从而避免出现ClassCastException 异常
  - instanceof 运算符的**前一个操作数通常是一个引用变量类型，后一个操作数通常是一个类（也可以是接口）**，用于判断前面的对象是否是后面的类、或者子类、实现类的实例。如果是，则返回 true，否则返回 false
  - ==注意==：前面操作数的编译时类型要么与后面的**类型相同**，要么与后面的类**具有父子继承关系**，否则会引起编译错误
  - instanceof 运算符的作用是：在进行强制类型转换之前，首先判断前一个对象是否是后一个类的实例，是否可以成功转换
  - instanceof 和 (type) 是 Java 提供的两个相关的运算符，通常**先用 instanceof 判断一个对象是否可以强制类型转换，然后在使用 (type) 运算符进行强制类型转换**，从而保证程序不会出现错误



### 3.7 组合与继承

#### 3.7.1 使用继承的注意点

- 为了保证父类具有良好的封装性，不会被子类随意改变，设计父类通常会遵循如下规则：
  - **尽量隐藏父类的内部数据。**尽量把父类的所有成员变量都设置成 private 访问类型，不要让子类直接访问父类的成员变量
  - **不要让子类可以随意访问、修改父类的方法。**父类中那些仅为辅助其他方法的工具方法应该使用 private 修饰，让子类无法访问该方法；如果父类中的方法需要被外部类调用，则必须以 public 修饰，但又不希望子类重写该方法，可以使用 final 修饰符来修饰；如果希望父类中的某个方法被子类重写，但不希望被其他类自由访问，可以使用 protected 来修饰
  - **尽量不要在父类构造器中调用将要被子类重写的方法**
- 如果想把某些类设置成最终类，即不能被当成父类，则可以使用 final 修饰这个类。除此之外，使用 private 修饰这个类的所有构造器，使无法继承该类，可另外提供一个静态方法用于创建该类的实例
- 何时需要从父类派生出新的子类，不仅需保证子类使特殊的父类，还要具备以下两个条件之一：
  - 子类需要额外增加成员变量，而不仅仅是变量值的改变
  - 子类需要增加自己独有的行为方式（包括增加新的方法或重写父类的方法）

#### 3.7.2 利用组合实现复用

- 组合是把旧类对象作为新类的成员变量组合进来，用以实现新类的功能，通常需要在新类里使用 private 修饰被组合的旧类对象

```java
class Animal {
	private void beat() {
		System.out.println("心脏跳动...");
	}
	public void breathe() {
		beat();
		System.out.println("吸一口气，吐一口气，呼吸中...");
	}
}
class Bird {
	// 将原来的父类组合到原来的子类，作为子类的一个组合成分
	private Animal a;
	public Bird(Animal a) {
		this.a = a;
	}
	// 重新定义一个自己的breathe()方法
	public void breathe() {
		// 直接复用Animal提供的breathe()方法来实现Bird的breathe()方法。
		a.breathe();
	}
	public void fly() {
		System.out.println("我在天空自在的飞翔...");
	}
}
class Wolf {
	// 将原来的父类组合到原来的子类，作为子类的一个组合成分
	private Animal a;
	public Wolf(Animal a) {
		this.a = a;
	}
	// 重新定义一个自己的breathe()方法
	public void breathe() {
		// 直接复用Animal提供的breathe()方法来实现Wolf的breathe()方法。
		a.breathe();
	}
	public void run() {
		System.out.println("我在陆地上的快速奔跑...");
	}
}
public class CompositeTest {
	public static void main(String[] args) {
		// 此时需要显式创建被组合的对象
		var a1 = new Animal();
		var b = new Bird(a1);
		b.breathe();
		b.fly();
		// 此时需要显式创建被组合的对象
		var a2 = new Animal();
		var w = new Wolf(a2);
		w.breathe();
		w.run();
	}
}
```



### 3.8 初始化块

#### 3.8.1 使用初始化块

- **初始化块**是 Java 类里可能出现的第 4 中成员（前面依次有**成员变量、方法和构造器**），一个类里可以有多个初始化块，相同类型的初始化块之间由顺序：**前面定义的初始化块先执行，后面定义的初始化块后执行**。初始化块的语法格式如下：

  ```java
  [修饰符] {
      //初始化块的可执行代码
  }
  ```

- 初始化块的**修饰符只能是 static **，使用 static 修饰的初始化块被称为**类初始化块（静态初始化块）**，没有 static 修饰的初始化块被称为**实例初始化块（非静态初始化块）**。初始化块里的代码可以包含任何可执行语句，包括定义局部变量、调用其他对象的方法，以及使用分支、循环语句等

- **实例初始化块只在创建 Java 对象时隐式执行，而且在构造器执行之前自动执行。类初始化块则在类初始化阶段自动执行**

- 实例化初始化块、声明实例变量指定的默认值都可以认为是对象的初始化代码，他们的**执行顺序与源程序中的排列顺序相同**

#### 3.8.2 实例初始化块和构造器

- 实例初始化块是一段固定执行的代码，他不能接收任何参数。如果有**一段初始化处理代码对所有对象完全相同**，**且无需接收任何参数**，就可以把这段初始化处理代码**提取到实例初始化块**中。

  <img src="Java核心基础.assets\将构造器中的代码提取成实例初始化块.png" style="zoom:70%;" />

- 与构造器类似，创建一个 Java 对象时，不仅会执行该类的实例初始化块和构造器，而且系统会一直上溯到 java.lang.Object 类，先执行 java.lang.Object 类的实例初始化块，开始执行 java.lang.Object 的构造器，依次向下执行其父类的实例初始化块，开始执行其父类的构造器……最后才执行该类的实例初始化块和构造器，返回该类的对象

- 如果希望在类加载后**对整个类进行某些初始化操作**，此时需要使用 **static 关键字来修饰初始化块**

#### 3.8.3 类初始化块

- 如果定义初始化块时使用了 static 修饰符，则这个初始化块就变成了类初始化块，也成为静态初始化块（**实例初始化块负责对对象进行初始化，类初始化块则负责对类进行初始化**）
- 类初始化块是类相关的，系统将在**类初始化阶段执行类初始化块**，而不是在创建对象时才执行。因此类**初始化块总比实例初始化块先执行**
- ==注意：==Java 系统加载并初始化某个类时，总是保证该类的所有父类（包括直接父类和间接父类）全部加载并初始化



## 第4章  面向对象（下）

### 4.1 包装类

- 为了解决 8 种基本数据类型的变量不能当成 Object 类型的变量使用的问题，Java 提供了包装类（Wrapper Class）的概念，为 8 种基本数据类型分别定义了相应的引用类型，并称之为**基本数据类型的包装类**

  | 基本数据类型 |  包装类   |
  | :----------: | :-------: |
  |     byte     |   Byte    |
  |    short     |   Short   |
  |     int      |  Integer  |
  |     long     |   Long    |
  |     char     | Character |
  |    float     |   Float   |
  |    double    |  Double   |
  |   boolean    |  Boolean  |

- JDK 1.5 以前基本类型变量与包装类实例之间的转换

<img src="Java核心基础.assets\基本类型变量与包装类实例之间的转换.png" alt="基本类型变量与包装类实例之间的转换" style="zoom:80%;" align=left />

- JDK 1.5 提供了**自动装箱（Autoboxing）和自动拆箱（AutoUnboxing）**功能

```java
public class AutoBoxingUnboxing{
	public static void main(String[] args){
		// 直接把一个基本类型变量赋给Integer对象
		Integer inObj = 5;
		// 直接把一个boolean类型变量赋给一个Object类型的变量
		Object boolObj = true;
		// 直接把一个Integer对象赋给int类型的变量
		int it = inObj;
		if (boolObj instanceof Boolean){
			// 先把Object对象强制类型转换为Boolean类型，再赋给boolean变量
			boolean b = (Boolean) boolObj;
			System.out.println(b);
		}
	}
}
```

- 包装类还可以实现**基本数据类型和字符串**之间的转换
  - 字符串类型 ---> 基本数据类型
    1. 利用包装类提供的 ==**parseXxx(String s)**== 静态方法
    2. 利用包装类提供的 ==**valueOf(String s)**== 静态方法
  - 基本数据类型 ---> 字符串类型
    1. ==**String.valueOf(Xxx x)**== 方法
    2. 通过 **基本类型变量 + ""**

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\基本类型变量和字符串之间的转换.png" alt="基本类型变量和字符串之间的转换" style="zoom:80%;" align="left"/>

- 两个包装类示例进行比较

```java
var a = Integer.valueOf(6);
System.out.println("6的包装类实例是否大于5.0" + (a > 5.0));// 输出true
System.out.println("比较2个包装类的实例是否相等："+ (Integer.valueOf(2) == Integer.valueOf(2))); // 输出false
// 通过自动装箱，允许把基本类型值赋值给包装类的实例
Integer ina = 2;
Integer inb = 2;
System.out.println("两个2自动装箱后是否相等："+ (ina == inb)); // 输出true
Integer biga = 128;
Integer bigb = 128;
System.out.println("两个128自动装箱后是否相等："+ (biga == bigb)); // 输出false

// java.lang.Integer 类的源代码
//定义一个长度为 256 的 Integer 数组
static final Integer[] cache = new Integer[-(-128) + 127 + 1];
static {
    // 执行初始化，创建 -128 ~ 127 的 Integer 实例，并放入 cache 数组中
    for (int i = 0; i < cache.length; i++)
        cache[i] = new Integer[i - 128];
}
```

​	==注意：==系统把一个 -128 ~ 127 之间的整数自动装箱成 Integer 实例，并放入了一个名为 cache 的数组中缓存起来。如果把 **-128 ~ 127 之间**的同一个整数自动装箱成 Integer 实例时，永远都是**引用的 cache 数组的同一个数组元素**，所以他们**全部相等**；但把**不在 -128 ~ 127 范围**的整数自动装箱成 Integer 实例时，系统总是**重新创建一个 Integer 实例**，所以会出现如上结果



### 4.2 处理对象

#### 4.2.1 打印对象和 toString 方法

- toString() 方法是Object 类里的一个实例方法，所有 Java 类都是 Object 的子类，因此**所有 Java 对象都具有 toString() 方法**
- 当要**打印输出一个 Java 对象或和字符串进行连接运算**时，系统**自动调用 Java 对象的 toString() 方法的返回值**
- toString() 方法是一个 “自我描述” 方法，总是返回该对象实现类的 “**类名 + @ + hashCode**” 值，这个值并不能实现 “自我描述” 功能，因此，就必须**重写 Object 类的 toString() 方法**

```java
class Apple{
	private String color;
	private double weight;
	public Apple(){	}
	// 重写toString方法，用于实现Apple对象的"自我描述"
	public String toString(){
		return "Apple[color=" + color + ",weight=" + weight + "]";
	}
}
```

#### 4.2.2 == 和 equals 方法

- Java 程序中测试两个变量是否相等有两种方式：**一是利用 == 运算符，另一种是利用 equals() 方法**
  - 当使用 **== **来判断两个变量是否相等时，如果两个变量是**基本数据类型**，且都是**数值类型**（不一定要求数据类型严格相同），只要**两个变量的值相等，就将返回 true**
  - 但对于两个**引用类型变量**，只有他们**指向同一个对象时，== 判断才会返回 true**。== 不可用于比较类型上没有父子关系的两个对象

```java
var it = 65;
var fl = 65.0f;
// 将输出true
System.out.println("65和65.0f是否相等？" + (it == fl));
var ch = 'A';
// 将输出true
System.out.println("65和'A'是否相等？" + (it == ch));
var str1 = new String("hello");
var str2 = new String("hello");
// 将输出false
System.out.println("str1和str2是否相等？" + (str1 == str2));
// 将输出true
System.out.println("str1是否equals str2？" + (str1.equals(str2)));
// 由于java.lang.String与EqualTest类没有继承关系，
// 所以下面语句导致编译错误
//System.out.println("hello" == new EqualTest());
```

- 当 Java 程序直接使用形如 “hello” 的字符串直接量（包括可以直接在编译时就计算出来的字符串值）时，JVM 将会使用常量池来管理这些字符串，**JVM 常量池保证相同的字符串直接量只有一个，不会产生多个副本**；当使用 new String("hello") 时，JVM会先使用常量池来管理 “hello” 直接量，再调用 String 类的构造器来创建一个新的 String 对象，新创建的 String 对象被保存再堆内存中

```java
// s1直接引用常量池中的"疯狂Java"
var s1 = "疯狂Java";
var s2 = "疯狂";
var s3 = "Java";
// s4后面的字符串值可以在编译时就确定下来
// s4直接引用常量池中的"疯狂Java"
var s4 = "疯狂" + "Java";
// s5后面的字符串值可以在编译时就确定下来
// s5直接引用常量池中的"疯狂Java"
var s5 = "疯" + "狂" + "Java";
// s6后面的字符串值不能在编译时就确定下来，
// 不能引用常量池中的字符串
var s6 = s2 + s3;
// 使用new调用构造器将会创建一个新的String对象，
// s7引用堆内存中新创建的String对象
var s7 = new String("疯狂Java");
System.out.println(s1 == s4); // 输出true
System.out.println(s1 == s5); // 输出true
System.out.println(s1 == s6); // 输出false
System.out.println(s1 == s7); // 输出false
```

- equals() 方法是 Object 类提供的一个实例方法，但判断两个对象相等的标准与 == 相同，如果希望采用自定义的相等标准，则可**重写 equals() 方法**，正确的重写 equals() 方法应满足下列条件：
  - ==**自反性**==：对任意 x，x.equals(x) 一定返回 true
  - ==**对称性**==：对任意 x 和 y，如果 y.equals(x) 返回 true，则 x.equals(y) 也返回 true
  - ==**传递性**==：对任意 x，y，z，如果 x.equals(y) 返回 true，y.equals(z) 返回 true，则 x.equals(z) 一定返回 true
  - ==**一致性**==：对任意 x 和 y，如果对象中用于等价比较的信息没有改变，那么无论调用 x.equals(y) 多少次，返回的结果应该保持一致，要么一直是 true，要么一直是 false
  - 对于任何不是 null 的 x，x.equals(null) 一定返回 false

```java
class Person {
	private String name;
	private String idStr;
	public Person(){}
	// 重写equals()方法，提供自定义的相等标准
	public boolean equals(Object obj) {
		// 如果两个对象为同一个对象
		if (this == obj)
			return true;
		// 只有当obj是Person对象
		if (obj != null && obj.getClass() == Person.class) {
			var personObj = (Person) obj;
			// 并且当前对象的idStr与obj对象的idStr相等才可判断两个对象相等
			if (this.getIdStr().equals(personObj.getIdStr())) {
				return true;
			}
		}
		return false;
	}
}
```



### 4.3 单例（Singleton）类

- 如果一个类始终只能创建一个实例，则这个类被称为单例类

- 饿汉式

```java
public class Singleton {
    // 将构造器使用private修饰，隐藏该构造器
    private Singleton(){}
    // 使用一个类变量来缓存曾经创建的实例，创建Singleton对象
    private static Singleton instance = new Singleton1();
    // 提供一个静态方法，用于返回Singleton实例
	// 该方法可以加入自定义的控制，保证只产生一个Singleton对象
    public static Singleton getInstance(){
        return instance;
    }
}
```

- 懒汉式

```java
public class Singleton {
    // 将构造器使用private修饰，隐藏该构造器
    private Singleton() {}
    // 使用一个类变量来缓存曾经创建的实例
    private static Singleton singleton = null;
    // 提供一个静态方法，用于返回Singleton实例
	// 该方法可以加入自定义的控制，保证只产生一个Singleton对象
    public static Singleton getInstance() {
        // 如果instance为null，表明还不曾创建Singleton对象
		// 如果instance不为null，则表明已经创建了Singleton对象，将不会重新创建新的实例
        if (singleton == null) {
            // 线程同步，防止发生安全问题
            synchronized (Singleton.class) {
                if (singleton == null) {
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}
```



### 4.4 final 修饰符

- **final 关键字可用于修饰类、变量和方法。**final 修饰变量时，表示该变量一旦获得了初始值就不可被改变

#### 4.4.1 final 成员变量

- Java 语法规定：==**final 修饰的成员变量必须由程序员显式地指定初始值**==
  - 类变量：必须在**静态初始化块**或**声明该类变量**时指定初始值，而且只能在两个地方的其中之一指定
  - 实例变量：必须在**非静态初始化块**、**声明该实例变量**或**构造器中**指定初始值，而且只能在三个地方其中之一指定

```java
// 定义成员变量时指定默认值，合法。
	final int a = 6;
	// 下面变量将在构造器或初始化块中分配初始值
	final String str;
	final int c;
	final static double d;
	// 既没有指定默认值，又没有在初始化块、构造器中指定初始值，
	// 下面定义的ch实例变量是不合法的。
//	final char ch;
	// 初始化块，可对没有指定默认值的实例变量指定初始值
	{
		//在初始化块中为实例变量指定初始值，合法
		str = "Hello";
		// 定义a实例变量时已经指定了默认值，
		// 不能为a重新赋值，因此下面赋值语句非法
//		a = 9;
	}
	// 静态初始化块，可对没有指定默认值的类变量指定初始值
	static {
		// 在静态初始化块中为类变量指定初始值，合法
		d = 5.6;
	}
	// 构造器，可对既没有指定默认值、有没有在初始化块中
	// 指定初始值的实例变量指定初始值
	public FinalVariableTest() {
		// 如果在初始化块中已经对str指定了初始化值，
		// 构造器中不能对final变量重新赋值，下面赋值语句非法
//		str = "java";
		c = 5;
	}
	public void changeFinal() {
		// 普通方法不能为final修饰的成员变量赋值
//		d = 1.2;
		// 不能在普通方法中为final成员变量指定初始值
//		ch = 'a';
	}
```

#### 4.4.2 final 局部变量

- final 修饰局部变量时，可以在定义时指定默认值，也可以在后面代码中赋初始值，但不能重复赋值。final 修饰的形参由传入的参数完成初始化，不能被赋值

```java
	public void test(final int a) {
		// 不能对final修饰的形参赋值，下面语句非法
		// a = 5;
	}
	public static void main(String[] args) {
		// 定义final局部变量时指定默认值，则str变量无法重新赋值
		final var str = "hello";
		// 下面赋值语句非法
		// str = "Java";
		// 定义final局部变量时没有指定默认值，则d变量可被赋值一次
		final double d;
		// 第一次赋初始值，成功
		d = 5.6;
		// 对final变量重复赋值，下面语句非法
//		d = 3.4;
	}
```

#### 4.4.3 final 修饰基本类型变量和引用类型变量的区别

- 当使用 final 修饰基本数据类型变量时，不能重新赋值，因此基本类型变量不能被改变；但对于引用类型变量而言，final 只保证这个**引用类型变量所引用的地址不会改变**，即**一直引用同一个对象**，但这个**对象完全可以发生改变**

```java
    // final修饰数组变量，iArr是一个引用变量
    final int[] iArr = {5, 6, 12, 9};
    System.out.println(Arrays.toString(iArr));
    // 对数组元素进行排序，合法
    Arrays.sort(iArr);
    System.out.println(Arrays.toString(iArr));
    // 对数组元素赋值，合法
    iArr[2] = -8;
    System.out.println(Arrays.toString(iArr));
    // 下面语句对iArr重新赋值，非法
    // iArr = null;
    // final修饰Person变量，p是一个引用变量
    final var p = new Person(45);
    // 改变Person对象的age实例变量，合法
    p.setAge(23);
    System.out.println(p.getAge());
    // 下面语句对p重新赋值，非法
    //p = null;
```

#### 4.4.4 可执行 “宏替换” 的 final 变量

- 对于一个 final 变量来说，不管它是类变量、实例变量，还是局部变量，只要满足三个条件，这个 final 变量就不再是一个变量，而是相当于一个直接量

  - 使用 **final** 修饰符修饰
  - 在定义该 final 变量时**指定了初始值**
  - 该初始值可以**在编译时就被确定下来**

  ==注意：==那么这个 final 变量本质上就是一个 **“宏变量”**，**编译器会把所有用到该变量的地方直接替换成该变量的值**

```java
    // 下面定义了4个final“宏变量”
    final var a = 5 + 2;
    final var b = 1.2 / 3;
    final var str = "疯狂" + "Java";
    final var book = "疯狂Java讲义：" + 99.0;
    // 下面的book2变量的值因为调用了方法，所以无法在编译时被确定下来
    final var book2 = "疯狂Java讲义：" + String.valueOf(99.0);  // ①
    System.out.println(book == "疯狂Java讲义：99.0");
    System.out.println(book2 == "疯狂Java讲义：99.0");
```

#### 4.4.5 final 方法

- final 修饰的方法**不可被重新**，但**可以被重载**
- 对于一个 **private 修饰**的方法，子类无法重写该方法，如果子类中定义了一个完全相同的方法，只是重新定义了一个新方法，不是方法重写，因此即使使用 **final 修饰**，依然**可以在子类中定义完全相同的方法**

```java
public class FinalMethodTest {
	public final void test1(){}
    private final void test2(){}
}
class Sub extends FinalMethodTest {
	// 下面方法定义将出现编译错误，不能重写final方法
	public void test1(){}
    // 下面方法定义将不会出现问题
	public void test2(){}
    // final修饰的方法只是不能被重写，完全可以被重载
	public final void test(){}
	public final void test(String arg){}
}

```

#### 4.4.6 final 类

- **final 修饰的类**不可以有子类，即**不可被继承**

```java
public final class FinalClass {}
// 下面的类定义将出现编译错误
public Sub extends FinalClass {}
```

#### 4.4.7 不可变类

- **不可变（immutable）类的意思是创建该类的实例后，该实例的实例变量是不可改变的**。Java 提供的 8 个包装类和 java.lang.String 类都是不可变类。如果需要创建自定义的不可变类，可遵守如下规则。
  - 使用 **private 和 final 修饰符来修饰该类的成员变量**
  - 提供**带参的构造器（或返回该实例的类方法）**，用于根据传入的参数来初始化类里的成员变量
  - **仅为该类的成员变量提供 getter 方法**，不要为该类的成员变量提供 setter 方法，因为普通方法无法修改 final 修饰的成员变量
  - 如果有必要，**重写 Object 类的 hashCode() 和 equals() 方法**。equals() 方法根据关键成员变量作为两个对象是否相等的标准，除此之外，还应该保证两个用 **equals() 方法判断为相等的对象的 hashCode() 也相等**

```java
public class Address{
	private final String detail;
	private final String postCode;
	// 在构造器里初始化两个实例变量
	public Address(String detail, String postCode){
		this.detail = detail;
		this.postCode = postCode;
	}
	// 仅为两个实例变量提供getter方法
	public String getDetail(){
		return this.detail;
	}
	public String getPostCode(){
		return this.postCode;
	}
	//重写equals()方法，判断两个对象是否相等。
	public boolean equals(Object obj){
		if (this == obj){
			return true;
		}
		if (obj != null && obj.getClass() == Address.class){
			var ad = (Address) obj;
			// 当detail和postCode相等时，可认为两个Address对象相等。
			if (this.getDetail().equals(ad.getDetail()) && this.getPostCode().equals(ad.getPostCode())){
				return true;
			}
		}
		return false;
	}
	public int hashCode(){
		return detail.hashCode() + postCode.hashCode() * 31;
	}
}
```

- 如果需要设计一个不可变类，**尤其要注意其引用类型的成员变量**，如果引用类型的成员变量的类是可变的，就必须采取保护措施来保护该成员变量所引用的对象不会被修改，这样才能真正创建不可变类

```java
class Name {
	private String firstName;
	private String lastName;
	// 省略firstName、lastName的setter和getter方法，无参、带参构造方法

}
public class Person {
	private final Name name;
	public Person(Name name) {
//		this.name = name;
		// 设置name实例变量为临时创建的Name对象，该对象的firstName和lastName
		// 与传入的name参数的firstName和lastName相同
		this.name = new Name(name.getFirstName(), name.getLastName());
	}
	public Name getName(){
//		return name;
		// 返回一个匿名对象，该对象的firstName和lastName
		// 与该对象里的name的firstName和lastName相同
		return new Name(name.getFirstName(), name.getLastName());
	}
}
```

#### 4.4.8 缓存实例的不可变类

- 如果程序经常使用相同的不可变类实例，则应该考虑缓存这种不可变类的实例

```java
class CacheImmutable {
    private static int MAX_SIZE = 10;
    // 使用数值来缓存已有的实例
    private static CacheImmutable[] cache = new CacheImmutable[MAX_SIZE];
    // 记录缓存实例在缓存中的位置，cache[pos - 1] 是最新缓存的实例
    private static int pos = 0;
    private final String name;
    private CacheImmutable (String name) {
        this.name = name;
    }
    public String getName () {
        return name;
    }
    public static CacheImmutable valueOf (String name) {
        // 遍历已缓存对象
        for (var i = 0; i < MAX_SIZE; i++) {
            // 如果已有相同实例，则直接返回该缓存的实例
            if (cache[i] != null && cache[i].getName().equals(name)) {
                return cache[i];
            }
        }
        // 如果缓存池已满
        if (pos == MAX_SIZE) {
            // 把缓存的第一个对象覆盖，即把刚刚生成的对象放在缓存池最开始位置
            cache[0] = new CacheImmutable(name);
            // 把 pos 设为 1
            pos = 1;
        } else {
            // 把新创建的对象缓存起来，pos 加 1
            cache[pos++] = new CacheImmutable(name);
        }
        return cache[pos - 1];
    }
    public boolean equals(Object obj) {
		if (this == obj) {
			return true;
		}
		if (obj != null && obj.getClass() == CacheImmutale.class) {
			var ci = (CacheImmutale) obj;
			return name.equals(ci.getName());
		}
		return false;
	}
	public int hashCode() {
		return name.hashCode();
	}
}
```

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\缓存实例的不可变类示意图.png" alt="缓存实例的不可变类示意图" style="zoom:80%;" />



### 4.5 抽象类

- 抽象方法和抽象类必须使用 ==**abstract 修饰符**==来定义，有抽象方法的类只能被定义为抽象类，抽象类里可以没有抽象方法。规则如下
  - 抽象类和抽象方法必须使用 **abstract 修饰符**来修饰，**抽象方法不能有方法体**
  - **抽象类不能被实例化**，无法使用 new 关键字来调用抽象类的构造器创建抽象类的实例
  - 抽象类可以包含成员变量、方法（普通方法和抽象方法）、构造器、初始化块、内部类（接口、枚举）5 个部分。**抽象类的构造器不能用于创建实例，主要用于被其子类调用**
  - **含有抽象方法的类**（包括直接定义了一个抽象方法；或继承了一个抽象父类，但没有完全实现父类包含的抽象方法；或实现了一个接口，但没有完全实现接口包含的抽象方法三种情况）**只能被定义为抽象类**
- 定义抽象方法只需在普通方法上**增加 abstract 修饰符**，并把**普通方法的方法体（也就是方法后花括号括起来的部分）全部去掉**，并在**方法后增加分号即可**
- 定义抽象类只需在普通类上增加 abstract 修饰符即可

```java
public abstract class Shape {
	{
		System.out.println("执行Shape的初始化块...");
	}
	private String color;
	// 定义一个计算周长的抽象方法
	public abstract double calPerimeter();
	// 定义一个返回形状的抽象方法
	public abstract String getType();
	// 定义Shape的构造器，该构造器并不是用于创建Shape对象，
	// 而是用于被子类调用
	public Shape(){}
	public Shape(String color) {
		System.out.println("执行Shape的构造器...");
		this.color = color;
	}
	// 省略color的setter和getter方法
}
public class Triangle extends Shape {
	// 定义三角形的三边
	private double a;
	private double b;
	private double c;
	public Triangle(String color, double a, double b, double c) {
		super(color);
		this.setSides(a, b, c);
	}
	// 重写Shape类的的计算周长的抽象方法
	public double calPerimeter() {
		return a + b + c;
	}
	// 重写Shape类的的返回形状的抽象方法
	public String getType() {
		return "三角形";
	}
}
```

- ==注意：==**final 和 abstract 不能同时使用，private 和 abstract 不能同时修饰方法，static 和 abstract 不能同时修饰方法，但可以修饰内部类**



### 4.6 Java 9 改进的接口

- 接口定义的是多个类共同的公共行为规范，这些行为是与外部交流的通道，这就意味着接口里通常是定义一组公用方法

#### 4.6.1 Java 9 中接口的定义

- 和类定义不同，定义接口不再使用 class 关键字，而是使用 ==**interface 关键字**==。接口定义的基本语法如下：

```java
[修饰符] interface 接口名 extends 父接口1, 父接口2... {
    //零个到多个常量定义...
    //零个到多个抽象方法定义...
    //零个到多个内部类、接口、枚举定义...
    //零个到多个私有方法、默认方法和类方法定义...
}
```

- 由于接口定义的是一种规范，因此接口里**不能包含构造器和初始化块定义**。接口里可以包含**成员变量（只能是静态常量）、方法（只能是抽象实例方法、类方法、默认方法或私有方法）、内部类（包括内部接口、枚举）定义**
  - 接口里的常量、方法、内部类和内部枚举都默认是 public 访问权限
  - 私有方法可以有方法体，但不能使用 default 修饰，可以使用 static 修饰
  - **默认方法必须使用 default 修饰**，**不能使用 static 修饰**，需要使用**接口实现类的实例来调用**
  - 接口里的**成员变量默认使用 public static final 修饰**；**普通方法默认使用 public abstract 修饰**
  - 接口里的普通方法不能有方法实现（方法体），但类方法、默认方法、私有方法都必须有方法实现（方法体）

```java
public interface Output {
	// 接口里定义的成员变量只能是常量
	int MAX_CACHE_LINE = 50;
	// 接口里定义的普通方法只能是public的抽象方法
	void out();
	void getData(String msg);
	// 在接口中定义默认方法，需要使用default修饰
	default void print(String... msgs) {
		for (var msg : msgs) {
			System.out.println(msg);
		}
	}
	// 在接口中定义类方法，需要使用static修饰
	static String staticTest() {
		return "接口里的类方法";
	}
	// 定义私有方法
	private void foo() {
		System.out.println("foo私有方法");
	}
	// 定义私有静态方法
	private static void bar() {
		System.out.println("bar私有静态方法");
	}
}

```

#### 4.6.2 接口的继承

- **接口完全支持多继承**，即一个接口可以有多个直接父接口。子接口扩展某个父接口，将会获得父接口里定义的所有抽象方法、常量
- 一个接口继承多个父接口时，多个父接口排在 extends 关键字之后，多个父接口之间以英文逗号（,）隔开

```java
interface InterfaceA {
	int PROP_A = 5;
	void testA();
}
interface InterfaceB {
	int PROP_B = 6;
	void testB();
}
interface InterfaceC extends InterfaceA, InterfaceB {
	int PROP_C = 7;
	void testC();
}
```

#### 4.6.3 使用接口

- **接口不能用于创建实例**，但可以用于**声明引用变量类型变量**，这个变量必须**引用到其实现类的对象**。此外，接口的主要用途是**被实现类实现**。接口有如下用途
  - 定义变量，也可用于进行强制类型转换
  - 调用接口中定义的常量
  - 被其他类实现

- 一个类可以实现一个或多个接口，继承使用 extends 关键字，实现则使用 ==**implements 关键字**==。类实现接口的语法如下：

```java
[修饰符] class 类名 extends 父类 implements 接口1, 接口2... {
    //类体部分
}
```

- 实现接口与继承父类相似，可以获得所实现接口里定义的常量、方法
- 一个类实现了一个或多个接口之后，这个类**必须完全实现这些接口里定义的全部抽象方法（也就是重写这些抽象方法）**，否则该类也必须定义为抽象类

```java
// 定义一个Product接口
interface Product {
	int getProduceTime();
}
// 让Printer类实现Output和Product接口
public class Printer implements Output, Product {
	private String[] printData = new String[MAX_CACHE_LINE];
	// 用以记录当前需打印的作业数
	private int dataNum = 0;
	public void out() {
		// 只要还有作业，继续打印
		while (dataNum > 0) {
			System.out.println("打印机打印：" + printData[0]);
			// 把作业队列整体前移一位，并将剩下的作业数减1
			System.arraycopy(printData, 1, printData, 0, --dataNum);
		}
	}
	public void getData(String msg) {
		if (dataNum >= MAX_CACHE_LINE) {
			System.out.println("输出队列已满，添加失败");
		} else {
			// 把打印数据添加到队列里，已保存数据的数量加1。
			printData[dataNum++] = msg;
		}
	}
	public int getProduceTime() {
		return 45;
	}
	public static void main(String[] args) {
		// 创建一个Printer对象，当成Output使用
		Output o = new Printer();
		o.getData("轻量级Java EE企业应用实战");
		o.getData("疯狂Java讲义");
		o.out();
		o.getData("疯狂Android讲义");
		o.getData("疯狂Ajax讲义");
		o.out();
		// 调用Output接口中定义的默认方法
		o.print("孙悟空", "猪八戒", "白骨精");
		o.test();
		// 创建一个Printer对象，当成Product使用
		Product p = new Printer();
		System.out.println(p.getProduceTime());
		// 所有接口类型的引用变量都可直接赋给Object类型的变量
		Object obj = p;
	}
}

```



### 4.7 内部类

- 在某些情况下，会**把一个类放在另一个类的内部定义**，这个定义在其他类内部的类就被称为**内部类**（有些地方也叫嵌套类），包含内部类的类也被称为外部类（有的地方也叫宿主类）。内部类有如下作用：
  - 内部类提供了更好的封装，可以把内部类隐藏在外部类之内，不允许同一个包中的其他类访问该类
  - **内部类成员可以直接访问外部类的私有数据。但外部类不能访问内部类的实现细节**，例如内部类的成员变量
  - 匿名内部类适合用于创建那些仅需要一次使用的类
- 内部类和外部类存在如下两点区别
  - 内部类比外部类可以多使用 3 个修饰符：private、protected、static —— 外部类不可以使用这三个修饰符
  - 非静态内部类不能拥有静态成员

#### 4.7.1 非静态内部类

- 定义内部类只要把一个类放在另一个类的内部定义即可。此处的 “类内部” 包括类中的任意位置，甚至在方法中也可以定义内部类（被称为局部内部类）。内部类定义语法格式如下：

```java
public class OuterClass {
    // 此处可以定义内部类
}
```

- 大部分时候，**内部类都被作为成员内部类定义**，是一种与成员变量、方法、构造器和初始化块类似的类成员；局部内部类和匿名内部类则不是类成员

```java
public class Cow {
	private double weight;
	// 外部类的两个重载的构造器
	public Cow(){}
	public Cow(double weight) {
		this.weight = weight;
	}
	// 定义一个非静态内部类
	private class CowLeg {
		// 非静态内部类的两个实例变量
		private double length;
		private String color;
		// 非静态内部类的两个重载的构造器
		public CowLeg(){}
		public CowLeg(double length, String color) {
			this.length = length;
			this.color = color;
		}
		// 下面省略length、color的setter和getter方法
		// 非静态内部类的实例方法
		public void info() {
			System.out.println("当前牛腿颜色是：" + color + ", 高：" + length);
			// 直接访问外部类的private修饰的成员变量
			System.out.println("本牛腿所在奶牛重：" + weight);   // ①
		}
	}
	public void test() {
		var cl = new CowLeg(1.12, "黑白相间");
		cl.info();
	}
}
```

- 非静态内部类里可以直接访问外部类的 private 成员，因为在非静态内部类对象里，保存了一个它所寄生的外部类对象的引用（当调用非静态内部类的实例方法时，必须有一个非静态内部类实例，非静态内部类实例必须寄生在外部类实例里）

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\非静态内部类对象中保留外部类对象的引用.png" alt="非静态内部类对象中保留外部类对象的引用内存示意图" style="zoom:80%;" />

- 当非静态内部类的方法访问某个变量时，系统查找变量的顺序为：**该方法内的局部变量 —> 该方法所在内部类的成员变量 —> 该内部类所在外部类的成员变量**；如果外部类成员变量、内部类成员变量与内部类方法的局部变量同名，则可以通过使用 **this、外部类类名.this** 作为限定区分
- 非静态内部类里不能有静态方法、静态成员变量、静态初始化块，但可以包含普通初始化块

#### 4.7.2 静态内部类

- 如果使用 **static 修饰一个内部类**，则这个**内部类就属于外部类本身**，而不属于外部类的某个对象。因此使用 static 修饰的内部类称为**类内部类**，也称为**静态内部类**
- 静态内部类可以包含静态成员，也可以包含非静态成员。静态内部类不能访问外部类的实例成员，只能访问外部类的类成员。即使是静态内部类的实例方法也不能访问外部类的实例成员，只能访问外部类的静态成员
- 外部类不能直接访问静态内部类的成员，但可以使用**静态内部类的类名作为调用者**来访问，也可以使用静态内部类对象作为调用者
- Java 还允许在接口里定义内部类，默认**使用 public static 修饰**，即**接口内部类只能是静态内部类**

#### 4.7.3 使用内部类

##### 1. 在外部类内部使用内部类

- 可以直接通过内部类类名定义变量，通过 new 调用内部类构造器来创建实例
- 不要再外部类的静态成员中使用非静态内部类

##### 2. 在外部类以外使用非静态内部类

- 在外部类以外的地方定义内部类（包括静态和非静态两种）变量的语法格式如下：

```java
OuterClass.InnerClass varName
```

- 由于非静态内部类的对象必须寄生在外部类的对象里，因此**创建非静态内部类之前，==必须先创建其外部类对象==**。在外部类以外的地方创建非静态内部类实例的语法格式如下：

```java
outerInstance.new InnerConstructor()
```

```java
class Out {
	// 定义一个内部类，不使用访问控制符，
	// 即只有同一个包中其他类可访问该内部类
	class In {
		public In(String msg) {
			System.out.println(msg);
		}
	}
}
public class CreateInnerInstance {
	public static void main(String[] args) {
		Out.In in = new Out().new In("测试信息");
		/*
		上面代码可改为如下三行代码：
		使用OuterClass.InnerClass的形式定义内部类变量
		Out.In in;
		创建外部类实例，非静态内部类实例将寄存在该实例中
		Out out = new Out();
		通过外部类实例和new来调用内部类构造器创建非静态内部类实例
		in = out.new In("测试信息");
		*/
	}
}
```

- **==注意：非静态内部类的构造器必须通过其外部类对象调用==**
- 在创建非静态内部类的子类时，必须保证让子类构造器可以调用非静态内部类的构造器，调用非静态内部类的构造器时，必须存在一个外部类对象

```java
public class SubClass extends Out.In {
	//显示定义SubClass的构造器
	public SubClass(Out out) {
		//通过传入的Out对象显式调用In的构造器
		out.super("hello");
	}
}
```

##### 3. 在外部类以外使用静态内部类

- 因为静态内部类是外部类类相关的，因此创建静态内部类对象时无须创建外部类对象。在外部类以外的地方创建静态内部类实例的语法如下：

```java
new OuterClass.InnerConstructor()
```

```java
class StaticOut {
	// 定义一个静态内部类，不使用访问控制符，
	// 即同一个包中其他类可访问该内部类
	static class StaticIn {
		public StaticIn() {
			System.out.println("静态内部类的构造器");
		}
	}
}
public class CreateStaticInnerInstance {
	public static void main(String[] args) {
		StaticOut.StaticIn in = new StaticOut.StaticIn();
		/*
		上面代码可改为如下两行代码：
		使用OuterClass.InnerClass的形式定义内部类变量
		StaticOut.StaticIn in;
		通过new来调用内部类构造器创建静态内部类实例
		in = new StaticOut.StaticIn();
		*/
	}
}
```

#### 4.7.4 局部内部类

- 如果把一个内部类放在方法里定义，则这个内部类就是一个局部内部类，局部内部类尽在方法里有效。由于局部内部类不能在外部类的方法以外的地方使用，因此**==不能==使用访问控制符和 static 修饰符修饰**
- 如果需要用局部内部类定义变量、创建实例或派生子类，那么就只能在局部内部类所在的方法内进行

```java
public class LocalInnerClass {
	public static void main(String[] args) {
		// 定义局部内部类
		class InnerBase
		{
			int a;
		}
		// 定义局部内部类的子类
		class InnerSub extends InnerBase {
			int b;
		}
		// 创建局部内部类的对象
		var is = new InnerSub();
		is.a = 5;
		is.b = 8;
		System.out.println("InnerSub对象的a和b实例变量是：" + is.a + "," + is.b);
	}
}
```

#### 4.7.5 匿名内部类

- **匿名内部类适合创建那种只需要一次使用的类**，创建匿名内部类时会立即创建一个该类的实例，这个类定义立即消失，**匿名内部类不能重复使用**

```java
new 实现接口() | 父类构造器(实参列表) {
    // 匿名内部类类体部分
}
```

- **匿名内部类必须继承一个父类，或实现一个接口**。匿名内部类还有如下两条规则：
  - **匿名内部类不能是抽象类**，因为系统在创建匿名内部类时，会立即创建匿名内部类的对象。
  - **匿名内部类不能定义构造器**。由于匿名内部类没有类名，所以无法定义构造器，但匿名内部类可以定义初始化块，可以通过实例初始化块来完成构造器需要完成的事情

```java
interface Product {
	double getPrice();
	String getName();
}
public class AnonymousTest {
	public void test(Product p) {
		System.out.println("购买了一个" + p.getName() + "，花掉了" + p.getPrice());
	}
	public static void main(String[] args) {
		var ta = new AnonymousTest();
		// 调用test()方法时，需要传入一个Product参数，
		// 此处传入其匿名实现类的实例
		ta.test(new Product() {
			public double getPrice() {
				return 567.8;
			}
			public String getName() {
				return "AGP显卡";
			}
		});
	}
}
```

- 创建匿名内部类时，必须实现接口或抽象父类里的所有抽象方法，如果需要也可以重写父类中的普通方法

- Java 8 以后的 JDK 版本中，被局部内部类、匿名内部类访问的局部变量，可以使用 final 修饰，可以不使用 final 修饰，但必须按照有 final 修饰的方式来使用 —— 一次赋值后，不能重新赋值



### 4.8 Java 11 增强的 Lambda 表达式

#### 4.8.1 Lambda 表达式入门

- Lambda 表达式的语法格式：

```java
(形参列表) -> {
    // 要实现的代码
}
```

- Lambda 表达式的主要作用就是代替匿名内部类繁琐的语法。它由三部分组成：
  - **形参列表**：允许省略形参类型。如果形参列表中只有一个参数，形参列表的圆括号也可以省略
  - **箭头（ -> ）**：必须通过英文中画线和大于符号组成
  - **代码块**：如果代码块只包含一条语句，允许省略代码块的花括号。如果代码块只有一条 return 语句，可以省略 return 关键字。

```java
interface Eatable {
	void taste();
}
interface Flyable {
	void fly(String weather);
}
interface Addable {
	int add(int a, int b);
}
public class LambdaQs {
	// 调用该方法需要Eatable对象
	public void eat(Eatable e) {
		System.out.println(e);
		e.taste();
	}
	// 调用该方法需要Flyable对象
	public void drive(Flyable f) {
		System.out.println("我正在驾驶：" + f);
		f.fly("【碧空如洗的晴日】");
	}
	// 调用该方法需要Addable对象
	public void test(Addable add) {
		System.out.println("5与3的和为：" + add.add(5, 3));
	}
	public static void main(String[] args) {
		var lq = new LambdaQs();
		// Lambda表达式的代码块只有一条语句，可以省略花括号。
		lq.eat(() -> System.out.println("苹果的味道不错！"));
		// Lambda表达式的形参列表只有一个形参，省略圆括号
		lq.drive(weather -> {
			System.out.println("今天天气是：" + weather);
			System.out.println("直升机飞行平稳");
		});
		// Lambda表达式的代码块只有一条语句，省略花括号
		// 代码块中只有一条语句，即使该表达式需要返回值，也可以省略return关键字。
		lq.test((a, b) -> a + b);
	}
}
```

#### 4.8.2 Lambda 表达式与函数式接口

- Lambda 表达式的类型，也被称为 “目标类型”，Lambda 表达式的目标类型必须是 “函数式接口（functional interface）”。**函数式接口代表只包含一个抽象方法的接口。函数式接口**可以包含多个默认方法、类方法，但**只能声明一个抽象方法**
- Lambda 表达式实现的是匿名方法 —— 因此它只能实现特定函数式接口中的唯一方法。这意味着 Lambda 表达式有如下两个限制：
  - Lambda 表达式的**目标类型必须是明确的函数式接口**
  - Lambda 表达式**只能为函数式接口创建对象**。Lambda 表达式只能实现一个方法，因此他只能为只有一个抽象方法的接口（函数式接口）创建对象
- 为保证 Lambda 表达式的目标类型是一个明确的函数式接口，可以有如下三种常见方式：
  - 将 Lambda 表达式赋值给函数式接口类型的变量
  - 将 Lambda 表达式作为函数式接口类型的参数传给某个方法
  - 使用函数式接口对 Lambda 表达式进行强制类型转换

```java
// Runnable接口中只包含一个无参数的方法
// Lambda表达式代表的匿名方法实现了Runnable接口中唯一的、无参数的方法
// 因此下面的Lambda表达式创建了一个Runnable对象
Runnable r = () -> {
    for (var i = 0; i < 100; i++)
    {
        System.out.println(i);
    }
};
```

- Java 8 在 java.util.function 包下预定义了大量函数式接口，典型的包含如下 4 类接口
  - ==**XxxFunction**==：通常包含一个 **==apply()== 抽象方法**，该方法**对参数进行处理、转换，然后返回一个新的值**。该函数式接口通常用于对指定数据进行转换处理
  - ==**XxxConsumer**==：通常包含一个 **==accept()== 抽象方法**，该方法与 XxxFunction 接口中的 apply() 方法类似，只是**不返回处理结果**
  - ==**XxxPredicate**==：通常包含一个 **==test()== 抽象方法**，该方法通常用来**对参数进行某种判断**，然后返回一个 boolean 值。该接口通常用于判断参数是否满足特定条件，经常用于进行筛选数据
  - ==**XxxSupplier**==：通常包含一个 **==getAsXxx()== 抽象方法**， 该方法不需要传入参数，会**按照某种逻辑返回一个数据**

#### 4.8.3 在 Lambda 中使用 var

- 对于 var 声明的变量，程序可以使用 Lambda 表达式进行赋值。但由于 var 代表需要由编译器推断的类型，因此使用 Lambda 表达式对 var 定义的变量赋值时，必须明确指定 Lambda 表达式的目标类型

```java
// 使用Lambda表达式对var变量赋值
// 必须显式指定Lambda表达式的目标类型
var run = (Runnable)() -> {
	for (var i = 0; i < 100; i++) {
		System.out.println();
	}
};
```

- 如果程序需要对 Lambda 表达式的形参添加注解，此时不能省略 Lambda 表达式的形参类型 —— 因为注解只能被放在形参类型之前

```java
@interface NotNull{}
interface Predator {
	void prey(@NotNull String animal);
}
// 使用var声明Lambda表达式的形参类型，
// 这样即可为Lambda表达式的形参添加@NotNull注解
Predator predator = (@NotNull var animal) -> {
	System.out.println("老鹰正在猎捕" + animal);
};
predator.prey("兔子");
```

#### 4.8.4 方法引用与构造器引用

- 如果 Lambda 表达式的代码块只有一条代码，还可以在代码块中使用方法引用和构造器引用

<center>Lambda 表达式支持的方法引用和构造器引用</center>

| 种类                   | 示例               | 说明                                                         | 对应的 Lambda 表达式                    |
| :--------------------- | :----------------- | :----------------------------------------------------------- | :-------------------------------------- |
| 引用类方法             | 类名::类方法       | 函数式接口中被实现方法的全部参数传给该类方法作为参数         | (a,b,...) -> 类名.类方法(a,b,...)       |
| 引用特定对象的实例方法 | 特定对象::实例方法 | 函数式接口中被实现方法的全部参数传给该方法作为参数           | (a,b,...) -> 特定对象.实例方法(a,b,...) |
| 引用某类对象的实例方法 | 类名::实例方法     | 函数式接口中被实现方法的第一个参数作为调用者，后面的参数全部传给该方法作为参数 | (a,b,...) -> a.实例方法(b,...)          |
| 引用构造器             | 类名::new          | 函数式接口中被实现方法的全部参数传给该构造器作为参数         | (a,b,...) -> new 类名(a,b,...)          |

##### 1. 引用类方法

```java
@FunctionalInterface
interface Converter {
	Integer convert(String from);
}
// 下面代码使用Lambda表达式创建Converter对象
Converter converter1 = from -> Integer.valueOf(from);
// 方法引用代替Lambda表达式：引用类方法。
// 函数式接口中被实现方法的全部参数传给该类方法作为参数。
Converter converter1 = Integer::valueOf;
```

##### 2. 引用特定对象的实例方法

```java
// 下面代码使用Lambda表达式创建Converter对象
Converter converter2 = from -> "fkit.org".indexOf(from);
// 方法引用代替Lambda表达式：引用特定对象的实例方法。
// 函数式接口中被实现方法的全部参数传给该方法作为参数。
Converter converter2 = "fkit.org"::indexOf;
```

##### 3. 引用某类对象的实例方法

```java
@FunctionalInterface
interface MyTest {
	String test(String a, int b, int c);
}
// 下面代码使用Lambda表达式创建MyTest对象
MyTest mt = (a, b, c) -> a.substring(b, c);
// 方法引用代替Lambda表达式：引用某类对象的实例方法。
// 函数式接口中被实现方法的第一个参数作为调用者，
// 后面的参数全部传给该方法作为参数。
MyTest mt = String::substring;
```

##### 4. 引用构造器

```java
@FunctionalInterface
interface YourTest {
	JFrame win(String title);
}
// 下面代码使用Lambda表达式创建YourTest对象
YourTest yt = a -> new JFrame(a);
// 构造器引用代替Lambda表达式。
// 函数式接口中被实现方法的全部参数传给该构造器作为参数。
YourTest yt = JFrame::new;
```

#### 4.8.5 Lambda 表达式与匿名内部类的联系与区别

- Lambda 表达式与匿名内部类存在如下相同点：
  - 都可以直接访问 "effectively final" 局部变量，以及外部类的成员变量（包括实例变量和类变量）
  - 都可以直接调用从接口中继承的默认方法
- Lambda 表达式与匿名内部类存在如下区别：
  - 匿名内部类可以为任意接口创建实例 —— 不管接口包含多少个抽象方法，只要匿名内部类实现所有抽象方法即可；但 Lambda 表达式只能为函数式接口创建实例
  - 匿名内部类可以为抽象类甚至普通类创建实例；但 Lambda 表达式只能为函数式接口创建实例
  - 匿名内部类实现的抽象方法的方法体允许调用接口中定义的默认方法；但 Lambda 表达式的代码块不允许调用



### 4.9 枚举类

#### 4.9.1 JDK 1.5 以前手动实现枚举类

```java
public class Season {
	// 把Season类定义成不可变的，将其成员变量也定义成final的
	private final String name;
	private final String desc;
	public static final Season SPRING = new Season("春天", "趁春踏青");
	public static final Season SUMMER = new Season("夏天", "夏日炎炎");
	public static final Season FALL = new Season("秋天", "秋高气爽");
	public static final Season WINTER = new Season("冬天", "围炉赏雪");
	public static Season getSeason(int seasonNum) {
		switch (seasonNum) {
			case 1 :
				return SPRING;
			case 2 :
				return SUMMER;
			case 3 :
				return FALL;
			case 4 :
				return WINTER;
			default :
				return null;
		}
	}
	// 将构造器定义成private访问权限
	private Season(String name, String desc) {
		this.name = name;
		this.desc = desc;
	}
	// 只为name和desc提供getter方法
	public String getName() {
		return this.name;
	}
	public String getDesc() {
		return this.desc;
	}
}
```

#### 4.9.2 枚举类入门

- Java 5 新增了一个 **enum 关键字**（它与 class、interface 关键字的地位相同），用以定义枚举类。枚举类是一种特殊的类，它也可以有自己的成员变量、方法，可以实现一个或多个接口，也可以定义自己的构造器。它与普通类有如下区别：
  - 枚举类可以实现一个或多个接口，使用 enum 定义的枚举类**默认继承了 java.lang.Enum 类**，而不是默认继承 Object 类，因此枚举类不能显式继承其他父类。其中 java.lang.Enum 类**实现了 java.lang.Serializable 和 java.lang.Comparable 两个接口**
  - 使用 enum 定义、非抽象的枚举类**默认会使用 final 修饰**
  - 枚举类的**构造器只能且默认使用 private 修饰**。枚举类**不能派生子类**
  - **枚举类的所有实例必须在枚举类的第一行显式的列出**，否则这个枚举类永远都不能产生实例。列出这些实例时，系统会**自动添加 public static final 修饰**，无须程序员显式添加
- 枚举类提供了一个 ==**values()**== 方法，可以方便的遍历所有的枚举值

```java
public enum SeasonEnum {
	// 在第一行列出4个枚举实例
	SPRING, SUMMER, FALL, WINTER;
}
public class EnumTest {
	public void judge(SeasonEnum s) {
		// switch语句里的表达式可以是枚举值
		switch (s) {
			case SPRING:
				System.out.println("春暖花开，正好踏青");
				break;
			case SUMMER:
				System.out.println("夏日炎炎，适合游泳");
				break;
			case FALL:
				System.out.println("秋高气爽，进补及时");
				break;
			case WINTER:
				System.out.println("冬日雪飘，围炉赏雪");
				break;
		}
	}
	public static void main(String[] args) {
		// 枚举类默认有一个values方法，返回该枚举类的所有实例
		for (var s : SeasonEnum.values()) {
			System.out.println(s);
		}
		// 使用枚举实例时，可通过EnumClass.variable形式来访问
		new EnumTest().judge(SeasonEnum.SPRING);
	}
}
```

#### 4.9.3 枚举类的成员变量、方法和构造器

- 枚举类也是一种类，只是它是一种比较特殊的类，一样可以定义成员变量、方法和构造器

```java
public enum Gender {
	// 此处的枚举值必须调用对应构造器来创建
	MALE("男"), FEMALE("女");
	private final String name;
	// 枚举类的构造器只能使用private修饰
	private Gender(String name) {
		this.name = name;
	}
	public String getName() {
		return this.name;
	}
}
```

#### 4.9.4 实现接口的枚举类

- 枚举类也可以实现一个或多个接口，也需要实现该接口所包含的方法

```java
public interface GenderDesc {
	void info();
}
public enum Gender implements GenderDesc {
	// 此处的枚举值必须调用对应构造器来创建
    // 花括号部分实际上是一个类体部分
	MALE("男") {
		public void info() {
			System.out.println("这个枚举值代表男性");
		}
	},
	FEMALE("女") {
		public void info() {
			System.out.println("这个枚举值代表女性");
		}
	};
	// 其他部分与上述类完全相同
//	// 增加下面的info()方法，实现GenderDesc接口必须实现的方法
//	public void info()
//	{
//		System.out.println(
//			"这是一个用于用于定义性别的枚举类");
//	}
}
```

#### 4.9.5 包含抽象方法的枚举类

- **枚举类里定义抽象方法**时不能使用 abstract 关键字将枚举类定义成抽象类（因为系统将自动为它添加 abstract 关键字），但因为枚举类需要显式创建枚举值，而不是作为父类，所以**定义每个枚举值时必须为抽象方法提供实现**

```java
public enum Operation {
	PLUS {
		public double eval(double x, double y) {
			return x + y;
		}
	},
	MINUS {
		public double eval(double x, double y) {
			return x - y;
		}
	},
	TIMES {
		public double eval(double x, double y) {
			return x * y;
		}
	},
	DIVIDE {
		public double eval(double x, double y) {
			return x / y;
		}
	};
	// 为枚举类定义一个抽象方法
	// 这个抽象方法由不同的枚举值提供不同的实现
	public abstract double eval(double x, double y);
	public static void main(String[] args) {
		System.out.println(Operation.PLUS.eval(3, 4));
		System.out.println(Operation.MINUS.eval(5, 4));
		System.out.println(Operation.TIMES.eval(5, 4));
		System.out.println(Operation.DIVIDE.eval(5, 4));
	}
}
```



### 4.10  修饰符的适用范围

|              | 外部类/接口 | 成员属性 | 方法 | 构造器 | 初始化块 | 成员内部类 | 局部成员 |
| ------------ | :---------: | :------: | :--: | :----: | :------: | :--------: | :------: |
| public       |      √      |    √     |  √   |   √    |          |     √      |          |
| protected    |             |    √     |  √   |   √    |          |     √      |          |
| 包访问控制符 |      √      |    √     |  √   |   √    |    〇    |     √      |    〇    |
| private      |             |    √     |  √   |   √    |          |     √      |          |
| abstract     |      √      |          |  √   |        |          |     √      |          |
| final        |      √      |    √     |  √   |        |          |     √      |    √     |
| static       |             |    √     |  √   |        |    √     |     √      |          |
| strictfp     |      √      |          |  √   |        |          |     √      |          |
| synchronized |             |          |  √   |        |          |            |          |
| native       |             |          |  √   |        |          |            |          |
| transient    |             |    √     |      |        |          |            |          |
| volatile     |             |    √     |      |        |          |            |          |
| default      |             |          |  √   |        |          |            |          |



## 第5章  Java基础类库

### 5.1 与用户的互动

#### 使用 Scanner 获取键盘输入

- **Scanner 是一个基于正则表达式的文本扫描器，它可以从文件、输入流、字符串中解析出基本类型和值和字符串值**。Scanner 主要提供了两个方法来扫描输入：
  - ==**boolean hasNextXxx()**==：是否还有下一个输入项，其中 Xxx 可以是 Int、Long 等代表基本数据类型的字符串。如果只是判断是否包含下一个字符串，则直接使用 hasNext()
  - ==**xxx nextXxx()**==：获取下一个输入项，Xxx 的含义与前一个方法中的 Xxx 相同
  - ==**boolean hasNextLine()**==：返回输入源中是否还有下一行
  - ==**String nextLine()**==：返回输入源中下一行的字符串
- 在默认情况下，Scanner 使用空白（包括空格、Tab空白、回车）作为多个输入项之间的分隔符

```java
    // System.in代表标准输入，就是键盘输入
    var sc = new Scanner(System.in);
    // 增加下面一行将只把回车作为分隔符
    // sc.useDelimiter("\n");
    // 判断是否还有下一个输入项
    while (sc.hasNext()) {
        // 输出输入项
        System.out.println("键盘输入的内容是：" + sc.next());
    }
```

- Scanner 的读取操作可能会被阻塞（当前执行顺序流暂停）来等待信息输入。如果输入源没有结束，Scanner 又读不到更多输入项时，Scanner 的 hasNext() 和 next() 方法都有可能阻塞

- 为 Scanner 设置分隔符使用 ==**useDelimiter(String pattern)**== 方法即可，该方法的**参数应该是一个正则表达式**

- Scanner 还可读取文件输入

```java
    // 将一个File对象作为Scanner的构造器参数，Scanner读取文件内容
    var sc = new Scanner(new File("ScannerFileTest.java"));
    System.out.println("ScannerFileTest.java文件内容如下：");
    // 判断是否还有下一行
    while (sc.hasNextLine()) {
        // 输出文件中的下一行
        System.out.println(sc.nextLine());
    }
```



### 5.2 系统相关

#### 5.2.1 System 类

- **System 类代表当前 Java 程序运行的平台**，程序**不能创建 System 类的对象**，System 类提供了一些类变量和类方法，允许直接通过 **System 类来调用这些类变量和类方法**
- System 类提供了**标准输入、标准输出和错误输出的类变量**，并提供了一些静态方法用于**访问环境变量、系统属性的方法**，还提供了**加载文件和动态链接库的方法**

```java
	// 获取系统所有的环境变量
    Map<String, String> env = System.getenv();
    for (var name : env.keySet()) {
        System.out.println(name + " ---> " + env.get(name));
    }
    // 获取指定环境变量的值
    System.out.println(System.getenv("JAVA_HOME"));
    // 获取所有的系统属性
    Properties props = System.getProperties();
    // 将所有系统属性保存到props.txt文件中
    props.store(new FileOutputStream("props.txt"), "System Properties");
    // 输出特定的系统属性
    System.out.println(System.getProperty("os.name"));
```

- System 类还有两个获取当前系统时间的方法：==**currentTimeMillis() 和 nanoTime()**==，他们都返回一个 long 型整数。实际上它们都返回当前时间与 UTC 1970年1月1日午夜的时间差，前者以毫秒作为单位，后者以纳秒作为单位。必须指出的是，这两个方法返回的时间粒度取决于底层操作系统，可能所造的操作系统根本不支持以毫秒、纳秒作为计时单位
- System 类的 **in、out 和 err 分别代表系统的标准输入（通常是键盘）、标准输出（通常是显示器）和错误输出流**，并提供了 ==**setIn()、setOut() 和 setErr()**== 方法来改变系统的标准输入、标准输出和标准错误输出流

- System 类还提供了一个 ==**identityHashCode(Object x)**== 方法返回指定对象的**精确 hashCode 值**，也就是根据**对象的地址计算得到的 hashCode 值**。当某个类的 hashCode() 方法被重写后，该类实例的 hashCode() 方法就不能唯一地标识该对象；但通过 identityHashCode(Object x) 方法返回的 hashCode 值，依然是根据该对象的地址计算得到的 hashCode 值

#### 5.2.2 Runtime 类与 Java 9 的 ProcessHandle

- **Runtime 类代表 Java 程序的运行时环境，可以访问 JVM 的相关信息**，每个 Java 程序都有一个与之对应的 Runtime 实例，应用程序通过该对象与其运行时环境相连。应用程序**不能创建自己的 Runtime 实例**，但可以通过 ==**getRuntime()**== 方法获取与之关联的 Runtime 对象
- Runtime 类也提供了 **gc() 方法和 runFinalization() 方法**来通知系统进行垃圾回收，清理系统资源，并提供 **load(String filename) 和 loadLibrary(String libname) 方法**来**加载文件和动态链接库**

```java
    // 获取Java程序关联的运行时对象
    var rt = Runtime.getRuntime();
    System.out.println("处理器数量：" + rt.availableProcessors());
    System.out.println("空闲内存数：" + rt.freeMemory());
    System.out.println("总内存数：" + rt.totalMemory());
    System.out.println("可用最大内存数：" + rt.maxMemory());
```

- Runtime 类还可以直接**单独启动一个进程来运行操作系统的命令**

```java
	var rt = Runtime.getRuntime();
	// 运行记事本程序
	rt.exec("notepad.exe");
```

- Java 9 新增了一个 ProcessHandle 接口，可以获取**进程的 ID、父进程和后代进程**；通过该接口的 **onExit() 方法**可以在进程结束时完成某些行为。ProcessHandle 还提供了一个 **ProcessHandle.Info 类**，用于获取**进程的命令、参数、启动时间、累计运行时间、用户**等信息

```java
    var rt = Runtime.getRuntime();
    // 运行记事本程序
    Process p = rt.exec("notepad.exe");
    ProcessHandle ph = p.toHandle();
    System.out.println("进程是否运行: " + ph.isAlive());
    System.out.println("进程ID: " + ph.pid());
    System.out.println("父进程: " + ph.parent());
    // 获取ProcessHandle.Info信息
    ProcessHandle.Info info = ph.info();
    // 通过ProcessHandle.Info信息获取进程相关信息
    System.out.println("进程命令: " + info.command());
    System.out.println("进程参数: " + info.arguments());
    System.out.println("进程启动时间: " + info.startInstant());
    System.out.println("进程累计运行时间: " + info.totalCpuDuration());
    // 通过CompletableFuture在进程结束时运行某个任务
    CompletableFuture<ProcessHandle> cf = ph.onExit();
    cf.thenRunAsync(()->{
        System.out.println("程序退出");
    });
    Thread.sleep(5000);
```



### 5.3 常用类

#### 5.3.1 Object 类

- **Object 类是所有类、数组、枚举类的父类**，也就是说，Java 允许把任何类型的对象赋给 Object 类型的变量。当定义一个类时没有使用 extends 关键字显式指定父类，则该类默认继承 Object 类。Object 类提供了如下几个常用的方法：
  - ==**boolean equals(Object obj)**==：判断指定对象与该对象是否相等，此处相等的标准是，两个对象是同一个对象
  - ==**protected void finalize()**==：当系统中没有引用变量引用到该对象时，垃圾回收去调用此方法来清理该对象的资源
  - ==**Class<?> getClass()**==：返回该对象的运行时类
  - ==**int hashCode()**==：返回该对象的 hashCode 值。默认情况下，根据该对象的地址来计算，但很多类都重写了该方法
  - ==**String toString()**==：返回该对象的字符串表示，“**运行时类名@十六进制 hashCode 值**” 格式的字符串，但很多类都重写了该方法，用于返回可表述该对象形象的字符串
- 此外，Object 类还提供了 **wait()、notify()、notfiyAll()** 方法，用于控制线程的暂停和运行
- Java 还提供了一个 **protected 修饰的 ==clone()== 方法**，用于帮助其他对象实现 **“自我克隆”**，就是**得到一个当前对象的副本**，而且二者之间**完全隔离**。该方法只能被子类重写或调用。自定义实现 “克隆” 的步骤如下。
  1. 自定义类**实现 Cloneable() 接口**。这是一个标记性接口，实现该接口的对象可以实现 “自我克隆”，接口里没有定义任何方法
  2. 自定义类实现自己的 clone() 方法
  3. 实现 clone() 方法时**通过 super.clone()；**调用 Object 实现的 clone() 方法来得到该对象的副本，并返回该副本

```java
![非静态内部类对象中保留外部类对象的引用](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\非静态内部类对象中保留外部类对象的引用.png)class Address {
	String detail;
	public Address(String detail) {
		this.detail = detail;
	}
}
// 实现Cloneable接口
class User implements Cloneable {
	int age;
	Address address;
	public User(int age) {
		this.age = age;
		address = new Address("广州天河");
	}
	// 通过调用super.clone()来实现clone()方法
	public User clone() throws CloneNotSupportedException {
		return (User) super.clone();
	}
}
public class CloneTest {
	public static void main(String[] args) throws CloneNotSupportedException {
		var u1 = new User(29);
		// clone得到u1对象的副本。
		var u2 = u1.clone();
		// 判断u1、u2是否相同
		System.out.println(u1 == u2);      // ①
		// 判断u1、u2的address是否相同
		System.out.println(u1.address == u2.address);     // ②
	}
}
```

- Object 类提供的 Clone 机制只对**对象里各实例变量进行 “简单复制”**，如果实例变量的类型也是引用类型，Object 的 Clone 机制也只是简单地复制这个引用变量，这样原有对象的引用类型的实例变量与克隆对象的引用类型的实例变量**依然指向内存中同一个实例**

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\克隆机制.png" alt="Object类提供的克隆机制" style="zoom:80%;" />

- 操作对象的 Objects 工具类：java 7 新增了一个 Objects 工具类，它提供了一些方法来操作对象，这些方法大多是 “空指针” 安全的

#### 5.3.2 Java 9 改进的 String、StringBuffer 和 StringBuilder 类

- 字符串就是一连串的字符序列，Java 提供了 String、StringBuffer 和 StringBuilder 三个类用来封装字符串，并提供一系列方法来操作字符串对象。*这三个类都实现了 CharSequence 接口，因此 CharSequence 可以认为是一个字符串的协议接口*
- **String 类是不可变类**，即一旦一个 String 对象被创建以后，包含在这个对象中的**字符序列是不可改变**的，直至这个对象被销毁
- **StringBuffer 和 StringBuilder 对象则代表一个字符序列可变的字符串**，当一个 StringBuffer 或 StringBuilder 被创建后，通过 ==**append()、insert()、reverse()、setCharAt()、setLength()**== **等方法可以**改变这个字符串对象的字符序列。可以通过 **==toString()== 方法**将其转换为 String 对象。**StringBuffer 是线程安全的，而 StringBuilder 是线程不安全的，所以性能略高**
- Java 9 以前字符串采用 **char[] 数组**来保存字符，因此字符串的**每个字符占 2 字节**；Java 9 以后的字符串采用 **byte[] 数组加一个 encoding-flag字段**来保存字符串，因此字符串的**每个字符占 1 字节**
- String 类提供了大量方法来操作字符串对象：
  - ==**int length()**==：返回当前字符串的长度
  - ==**char charAt(int index)**==： 返回 index 索引处的字符
  - ==**boolean isEmpty()**==：判断当前字符串是否是空字符串
  - ==**String toLowerCase()**==：使用默认语言环境，将 String 中的所字符转换为小写
  - ==**String toUpperCase()**==：使用默认语言环境，将 String 中的所字符转换为大写
  - ==**String trim()**==：返回字符串的副本，忽略前导空白和尾部空白
  - ==**boolean equals(Object obj)**==：将字符串与指定对象比较，如果二者包含的字符序列相等，则返回 true；否则返回 false
  - ==**boolean equalsIgnoreCase(String anotherString)**==：与equals方法类似，只是忽略字符串大小写
  - ==**String concat(String str)**==：将 str 字符串连接到此字符串的结尾。 等价于用“+”
  - ==**int compareTo(String anotherString)**==：比较两个字符串的大小，如果两个字符串序列相等，则返回 0；不相等时，从两个字符串第 0 个字符开始比较，返回第一个不相等的字符差。另一种情况，较长字符串的前面部分恰巧是较短字符串，则返回它们的长度差
  - ==**String substring(int beginIndex)**==：获取从 beginIndex 位置开始到结束的子字符串。
  - ==**String substring(int beginIndex, int endIndex)**==：获取从 beginIndex 开始到 endIndex(不包含) 位置的子字符串。
  - ==**boolean endsWith(String suffix)**==：测试此字符串是否以 suffix 后缀结束
  - ==**boolean startsWith(String prefix)**==：测试此字符串是否以 prefix 前缀开始
  - ==**boolean startsWith(String prefix, int toffset)**==：测试此字符串从 toffset 位置算起，是否以 prefix 前缀开始
  - ==**boolean contains(CharSequence s)**==：当且仅当此字符串包含指定的 char 值序列时，返回 true
  - ==**int indexOf(String str)**==：返回 str 子字符串在此字符串中第一次出现处的索引
  - ==**int indexOf(String str, int fromIndex)**==：返回 str 子字符串从 fromIndex 开始后第一次出现处的索引
  - ==**int lastIndexOf(String str)**==：返回 str 子字符串在此字符串中最后一次出现处的索引
  - ==**int lastIndexOf(String str, int fromIndex)**==：返回 str 子字符串从 fromIndex 开始后最后一次出现处的索引
  - ==**String replace(char oldChar, char newChar)**==：将字符串中第一个 oldChar 替换成 newChar
  - ==**String replace(CharSequence target, CharSequence replacement)**==：使用 replacement 值替换序列替换此字符串所匹配字面值目标序列的子字符串。
  - ==**String replaceAll(String regex, String replacement)**==：使用给定的 replacement 替换此字符串所匹配给定的正则表达式的子字符串。
  - ==**String replaceFirst(String regex, String replacement)**==：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
  - ==**boolean matches(String regex)**==：返回此字符串是否匹配给定的正则表达式。
  - ==**String[] split(String regex)**==：根据给定正则表达式的匹配拆分此字符串。
  - ==**String[] split(String regex, int limit)**==：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。

- StringBuffer 和 StringBuilder 有两个属性：**length 和 capacity**，其中 length 表示包含字符的字符序列的长度，是可以改变的，可以通过 **length()、setLength(int len) 方法**来访问和修改其字符序列的长度。capacity 表示 StringBuilder 的容量。

```java
    var sb = new StringBuilder();
    // 追加字符串
    sb.append("java");//sb = "java"
    // 插入
    sb.insert(0, "hello "); // sb="hello java"
    // 替换
    sb.replace(5, 6, ","); // sb="hello,java"
    // 删除
    sb.delete(5, 6); // sb="hellojava"
    System.out.println(sb);
    // 反转
    sb.reverse(); // sb="avajolleh"
    System.out.println(sb);
    System.out.println(sb.length()); // 输出9
    System.out.println(sb.capacity()); // 输出16
    // 改变StringBuilder的长度，将只保留前面部分
    sb.setLength(5); // sb="avajo"
    System.out.println(sb);
```



#### 5.3.3 Math 类

- Java 提供了 **Math 工具类**来完成像三角函数、对数运算、指数运算这些复杂的运算。**Math 类的所有方法都是类方法，可以直接通过类名来调用**它们，还提供了**两个类变量：PI 和 E**，它们的值分别等于 Π 和 e

```java
    /*---------下面是三角运算---------*/
    // 将弧度转换角度
    System.out.println("Math.toDegrees(1.57)：" + Math.toDegrees(1.57));
    // 将角度转换为弧度
    System.out.println("Math.toRadians(90)：" + Math.toRadians(90));
    // 计算反余弦，返回的角度范围在 0.0 到 pi 之间。
    System.out.println("Math.acos(1.2)：" + Math.acos(1.2));
    // 计算反正弦；返回的角度范围在 -pi/2 到 pi/2 之间。
    System.out.println("Math.asin(0.8)：" + Math.asin(0.8));
    // 计算反正切；返回的角度范围在 -pi/2 到 pi/2 之间。
    System.out.println("Math.atan(2.3)：" + Math.atan(2.3));
    // 计算三角余弦。
    System.out.println("Math.cos(1.57)：" + Math.cos(1.57));
    // 计算值的双曲余弦。
    System.out.println("Math.cosh(1.2 )：" + Math.cosh(1.2 ));
    // 计算正弦
    System.out.println("Math.sin(1.57 )：" + Math.sin(1.57 ));
    // 计算双曲正弦
    System.out.println("Math.sinh(1.2 )：" + Math.sinh(1.2 ));
    // 计算三角正切
    System.out.println("Math.tan(0.8 )：" + Math.tan(0.8 ));
    // 计算双曲正切
    System.out.println("Math.tanh(2.1 )：" + Math.tanh(2.1));
    // 将矩形坐标 (x, y) 转换成极坐标 (r, thet));
    System.out.println("Math.atan2(0.1, 0.2)：" + Math.atan2(0.1, 0.2));
    /*---------下面是取整运算---------*/
    // 取整，返回小于目标数的最大整数。
    System.out.println("Math.floor(-1.2 )：" + Math.floor(-1.2 ));
    // 取整，返回大于目标数的最小整数。
    System.out.println("Math.ceil(1.2)：" + Math.ceil(1.2));
    // 四舍五入取整
    System.out.println("Math.round(2.3 )：" + Math.round(2.3 ));
    /*---------下面是乘方、开方、指数运算---------*/
    // 计算平方根。
    System.out.println("Math.sqrt(2.3 )：" + Math.sqrt(2.3 ));
    // 计算立方根。
    System.out.println("Math.cbrt(9)：" + Math.cbrt(9));
    // 返回欧拉数 e 的n次幂。
    System.out.println("Math.exp(2)：" + Math.exp(2));
    // 返回 sqrt(x2 +y2)
    System.out.println("Math.hypot(4, 4)：" + Math.hypot(4, 4));
    // 按照 IEEE 754 标准的规定，对两个参数进行余数运算。
    System.out.println("Math.IEEEremainder(5, 2)：" + Math.IEEEremainder(5, 2));
    // 计算乘方
    System.out.println("Math.pow(3, 2)：" + Math.pow(3, 2));
    // 计算自然对数
    System.out.println("Math.log(12)：" + Math.log(12));
    // 计算底数为 10 的对数。
    System.out.println("Math.log10(9)：" + Math.log10(9));
    // 返回参数与 1 之和的自然对数。
    System.out.println("Math.log1p(9)：" + Math.log1p(9));
    /*---------下面是符号相关的运算---------*/
    // 计算绝对值。
    System.out.println("Math.abs(-4.5)：" + Math.abs(-4.5));
    // 符号赋值，返回带有第二个浮点数符号的第一个浮点参数。
    System.out.println("Math.copySign(1.2, -1.0)：" + Math.copySign(1.2, -1.0));
    // 符号函数；如果参数为 0，则返回 0；如果参数大于 0，则返回 1.0；如果参数小于 0，则返回 -1.0。
    System.out.println("Math.signum(2.3)：" + Math.signum(2.3));
    /*---------下面是大小相关的运算---------*/
    // 找出最大值
    System.out.println("Math.max(2.3, 4.5)：" + Math.max(2.3, 4.5));
    // 计算最小值
    System.out.println("Math.min(1.2, 3.4)：" + Math.min(1.2, 3.4));
    // 返回第一个参数和第二个参数之间与第一个参数相邻的浮点数。
    System.out.println("Math.nextAfter(1.2, 1.0)：" + Math.nextAfter(1.2, 1.0));
    // 返回比目标数略大的浮点数
    System.out.println("Math.nextUp(1.2 )：" + Math.nextUp(1.2 ));
    // 返回一个伪随机数，该值大于等于 0.0 且小于 1.0。
    System.out.println("Math.random()：" + Math.random());
```



#### 5.3.4 ThreadLocalRandom 与 Random

- **Random 类专门用于生成一个伪随机数**，它有两个构造器：一个构造器使用默认的种子（以当前时间作为种子），另一个构造器需要显式传入一个 long 型整数的种子

```java
    var rand = new Random();
    System.out.println("rand.nextBoolean()：" + rand.nextBoolean());
    var buffer = new byte[16];
    rand.nextBytes(buffer);
    System.out.println(Arrays.toString(buffer));
    // 生成0.0~1.0之间的伪随机double数
    System.out.println("rand.nextDouble()：" + rand.nextDouble());
    // 生成0.0~1.0之间的伪随机float数
    System.out.println("rand.nextFloat()：" + rand.nextFloat());
    // 生成平均值是 0.0，标准差是 1.0的伪高斯数
    System.out.println("rand.nextGaussian()：" + rand.nextGaussian());
    // 生成一个处于int整数取值范围的伪随机整数
    System.out.println("rand.nextInt()：" + rand.nextInt());
    // 生成0~26之间的伪随机整数
    System.out.println("rand.nextInt(26)：" + rand.nextInt(26));
    // 生成一个处于long整数取值范围的伪随机整数
    System.out.println("rand.nextLong()：" + rand.nextLong());
```

- **Random 使用一个 48 位的种子，如果这个类的两个实例是用同一个种子创建的，对它们以同样的顺序调用方法，则它们会产生相同的数字序列**。**当使用默认的种子构造 Random 对象时，它们属于同一个种子**
- 为了避免两个 Random 对象产生相同的数字序列，通常推荐使用当前时间作为 Random 对象的种子

```java
Random rand = new Random(System.currentTimeMillis());
```

- ThreadLocalRandom 类是 Java 7 新增的一个类，它是 Random 的增强版。在并发访问的环境下，使用 ThreadLocalRandom 来代替 Random 可以减少多线程资源竞争，最终保证系统具有更好的线程安全性

- ThreadLocalRandom 类的用法与 Random 类的用法相似，它提供了一个**静态的 ==current()== 方法**来获取 ThreadLocalRandom 对象，之后即可调用各种 **==nextXxx()==方法**来获取伪随机数

```java
ThreadLocalRandom rand = ThreadLocalRandom.current();
// 生成一个4~20之间的伪随机数
int vall = rand.nextInt(4, 20);
```



#### 5.3.5 BigDecimal 类

- float、double 两种基本浮点类型容易引起精度丢失。**为了能精确表示、计算浮点数，Java 提供了 BigDecimal 类**，该类提供了大量的构造器用于创建对象
- **创建 BigDecimal 对象时，==不要==直接使用 double 浮点数作为构造器参数来调用 BigDecimal 构造器**，否则同样会发生精度丢失问题，应该***通过 BigDecimal.valueOf(double value) 静态方法来创建对象***。***通常建议优先使用基于 String 的构造器***
- BigDecimal 类提供了 **==add()、subtract()、multiply()、divide()、pow()== 等方法**对精确浮点数进行常规算术运算

- 以 BigDecimal 为基础定义一个 Arith 工具类，封装烦琐的转换运算过程

```java
public class Arith {
	// 默认除法运算精度
	private static final int DEF_DIV_SCALE = 10;
	// 构造器私有，让这个类不能实例化
	private Arith()	{}
	// 提供精确的加法运算。
	public static double add(double v1, double v2) {
		var b1 = BigDecimal.valueOf(v1);
		var b2 = BigDecimal.valueOf(v2);
		return b1.add(b2).doubleValue();
	}
	// 提供精确的减法运算。
	public static double sub(double v1, double v2) {
		var b1 = BigDecimal.valueOf(v1);
		var b2 = BigDecimal.valueOf(v2);
		return b1.subtract(b2).doubleValue();
	}
	// 提供精确的乘法运算。
	public static double mul(double v1, double v2) {
		var b1 = BigDecimal.valueOf(v1);
		var b2 = BigDecimal.valueOf(v2);
		return b1.multiply(b2).doubleValue();
	}
	// 提供（相对）精确的除法运算，当发生除不尽的情况时.
	// 精确到小数点以后10位的数字四舍五入。
	public static double div(double v1, double v2) {
		var b1 = BigDecimal.valueOf(v1);
		var b2 = BigDecimal.valueOf(v2);
		return b1.divide(b2, DEF_DIV_SCALE,
			RoundingMode.HALF_UP).doubleValue();
	}
}
```



### 5.4 Java 8 的日期、时间类

#### 5.4.1 Date 类

- **Java 提供了 Date 类来处理日期、时间（此处的 Date 是指 java.util 包下的 Date 类）**，它的大部分构造器、方法已经过时，不再推荐使用。
- 未过时的构造器：
  - **==Date()==**：生成一个代表当前日期时间的 Date 对象。该构造其在底层调用System.currentTimeMillis()获得long整数作为日期参数
  - **==Date(long date)==**：根据指定的 long 型整数来生成一个 Date 对象。该构造器的参数表示创建的 Date 对象和 GMT 1970 年 1 月 1 日 00:00:00 之间的时间差，以毫秒作为计时单位
- 未过时的方法：
  - **==boolean after(Date when)==**：测试该日期是否在指定日期 when 之后
  - **==boolean before(Date when)==**：测试该日期是否在指定日期 when 之前
  - **==long getTime()==**：返回该时间对应的 long 型整数，即从 GMT 1970 年 1 月 1 日 00:00:00 到该 Date 对象之间的时间差
  - **==void setTime(long time)==**：设置该 Date 对象的时间

```java
    var d1 = new Date();
    // 获取当前时间之后100ms的时间
    var d2 = new Date(System.currentTimeMillis() + 100);
    System.out.println(d2);
    System.out.println(d1.compareTo(d2));
    System.out.println(d1.before(d2));
```

#### 5.4.2 Calendar 类

- **Java 提供了 Calendar 类来更好的处理日期和时间**。**Calendar 是一个抽象类**，它用于表示日历。不能使用构造器来创建 Calendar 对象，但它提供了几个**静态 ==getInstance()== 方法来获取 Calendar 对象**，这些方法根据 TimeZone、Locale 类来获取特定的 Calendar，如果不指定，则使用默认的 TimeZone、Locale 来创建 Calendar
- Calendar 与 Date 都是表示日期的工具类，它们可以直接自由转换

```java
// 创建一个默认的 Calendar 对象
var calendar = Calendar.getInstance();
// 从 Calendar 对象中取出 Date 对象
var date = calendar.getTime();
// 通过 Date 对象获得对应的 Calendar 对象
// 因为 Calendar 没有构造函数可以接收 Date 对象，所以必须先获得一个 Calendar 实例，然后调用其 setTime() 方法
var calendar2 = Calendar.getInstance();
calendar2.setTime(date);
```

- Calendar 提供了大量访问、修改日期的方法，常用方法如下：

  - **==void add(int field, int amount)==**：根据日历的规则，为给定的日历字段添加或减去指定的时间量
  - **==int get(int field)==**：返回指定日历字段的值
  - **==int getActualMaximum(int field)==**：返回指定日历字段可能拥有的最大值。例如月，最大值为 11
  - **==int getActualMinimum(int field)==**：返回指定日历字段可能拥有的最小值。例如月，最小值为 0
  - **==void roll(int field, int amount)==**：与 add() 方法类似，区别在于加上 amount 后超过了该字段所能表示的最大范围时，也不会向上一个字段进位
  - **==void set(int field, int value)==**：将给定的日历字段设置为给定值
  - **==void set(int year, int month, int date)==**：设置 Calendar 对象的年、月、日三个字段的值
  - **==void set(int year, int month, int date, int hourOfDay, int minute, int second)==**：设置 Calendar 对象的年、月、日、时、分、秒 6  个字段的值

  ```java
      var c = Calendar.getInstance();
      // 取出年
      System.out.println(c.get(Calendar.YEAR));
      // 取出月份
      System.out.println(c.get(Calendar.MONTH));
      // 取出日
      System.out.println(c.get(Calendar.DATE));
      // 分别设置年、月、日、小时、分钟、秒
      c.set(2003, 10, 23, 12, 32, 23); //2003-11-23 12:32:23
      // 将Calendar的年前推1年
      c.add(Calendar.YEAR, -1); //2002-11-23 12:32:23
      // 将Calendar的月前推8个月
      c.roll(Calendar.MONTH, -8); //2002-03-23 12:32:23
  ```

- Calendar 类还有如下几个注意点：

  1. add 与 roll 的区别

     add(int field, int amount) 有如下两条规则：

     - **当被修改的字段超出它允许的范围时，会发生进位，即上一级字段也会增大**

     ```java
         var cal1 = Calendar.getInstance();
         cal1.set(2003, 7, 23, 0, 0, 0); // 2003-8-23
         cal1.add(MONTH, 6); //2003-8-23 => 2004-2-23
     ```

     - **如果下一级字段也需要改变，那么该字段会修正到变化最小的值**

     ```java
         var cal2 = Calendar.getInstance();
         cal2.set(2003, 7, 31, 0, 0, 0); // 2003-8-31
         // 因为进位到后月份改为2月，2月没有31日，自动变成29日
         cal2.add(MONTH, 6); // 2003-8-31 => 2004-2-29
     ```

     roll(int field, int amount) 的规则：

     - **当被修改的字段超出它允许的范围时，上一级字段不会增大**

     ```java
         var cal3 = Calendar.getInstance();
         cal3.set(2003, 7, 23, 0, 0, 0); //2003-8-23
         // MONTH字段“进位”，但YEAR字段并不增加
         cal3.roll(MONTH, 6); //2003-8-23 => 2003-2-23
     ```

     - 下一级字段的处理规则与 add() 相似

  2. 设置 Calendar 的容错性

     - Calendar 提供了一个 **==setLenient()== 用于设置它的容错性**，Calendar **默认支持较好的容错性**，通过 setLenient(false) 可以关闭 Calendar 的容错性，让它进行严格的参数检查
     - Calendar 有两个解释日历字段的模式：**lenient 模式和 non-lenient 模式**。当 Calendar 处于 **lenient 模式**时，**每个时间字段都可以接受超出它允许范围的值**；当处于 **non-lenient 模式**时，如果为**某个时间字段设置的值超出了它允许的取值范围，程序将会抛出异常**

  3. set() 方法延迟修改

     - set(f, value) 方法将日历字段 f 更改为 value，此外它还设置了一个内部成员变量，以指示日历字段 f 已经被更改。尽管日历字段 f 是立即更改的，但 Calendar 所代表的时间却不会立即更改，直到下次调用 get()、getTime()、getTimeInMillis()、add() 或 roll() 时才会重新计算日历的时间。这被称为 set() 方法的延迟修改，采用延迟修改的优势是多次调用 set() 不会触发多次不必要的计算（需要计算出一个代表实际时间的 long 型整数）

#### 5.4.3 新的日期、时间包

- Java 8 专门新增了一个 java.time 包，该包下包含了如下常用的类
  - **Clock**：该类用于获取指定时区的当前日期、时间。可以取代 System 类的 currentTimeMillis() 方法，而且提供了更多方法来获取当前时间、日期。该类提供了大量静态方法来获取 Clock 对象
  - **Duration**：该类代表持续时间。该类可以非常方便地获取一段时间
  - **Instant**：代表一个具体的时刻，可以精确到纳秒。
  - **LocalDate**：该类代表不带时区的日期，例如 2007-12-03
  - **LocalTime**：该类代表不带时区的时间，例如 10:15:30
  - **LocalDateTime**：该类代表不带时区的日期、时间，例如 2007-12-03T10:15:30
  - **MonthDay**：该类仅代表月日，例如 04-12
  - **Year**：该类仅代表年，例如 2014
  - **YearMonth**：该类仅代表年月，例如 2014-04
  - **ZonedDateTime**：该类代表一个时区化的日期、时间
  - **ZoneId**：该类代表一个时区
  - **DayOfWeek**：这是一个枚举类，定义了周日到周六的枚举值
  - **Month**：这是一个枚举类，定义了一月到十二月的枚举值

```java
    // -----下面是关于Clock的用法-----
    // 获取当前Clock
    var clock = Clock.systemUTC();
    // 通过Clock获取当前时刻
    System.out.println("当前时刻为：" + clock.instant());
    // 获取clock对应的毫秒数，与System.currentTimeMillis()输出相同
    System.out.println(clock.millis());
    System.out.println(System.currentTimeMillis());
    // -----下面是关于Duration的用法-----
    var d = Duration.ofSeconds(6000);
    System.out.println("6000秒相当于" + d.toMinutes() + "分");
    System.out.println("6000秒相当于" + d.toHours() + "小时");
    System.out.println("6000秒相当于" + d.toDays() + "天");
    // 在clock基础上增加6000秒，返回新的Clock
    var clock2 = Clock.offset(clock, d);
    // 可以看到clock2与clock1相差1小时40分
    System.out.println("当前时刻加6000秒为：" +clock2.instant());
    // -----下面是关于Instant的用法-----
    // 获取当前时间
    var instant = Instant.now();
    System.out.println(instant);
    // instant添加6000秒（即100分钟），返回新的Instant
    var instant2 = instant.plusSeconds(6000);
    System.out.println(instant2);
    // 根据字符串解析Instant对象
    var instant3 = Instant.parse("2014-02-23T10:12:35.342Z");
    System.out.println(instant3);
    // 在instant3的基础上添加5小时4分钟
    var instant4 = instant3.plus(Duration.ofHours(5).plusMinutes(4));
    System.out.println(instant4);
    // 获取instant4的5天以前的时刻
    var instant5 = instant4.minus(Duration.ofDays(5));
    System.out.println(instant5);
    // -----下面是关于LocalDate的用法-----
    var localDate = LocalDate.now();
    System.out.println(localDate);
    // 获得2014年的第146天
    localDate = LocalDate.ofYearDay(2014, 146);
    System.out.println(localDate); // 2014-05-26
    // 设置为2014年5月21日
    localDate = LocalDate.of(2014, Month.MAY, 21);
    System.out.println(localDate); // 2014-05-21
    // -----下面是关于LocalTime的用法-----
    // 获取当前时间
    var localTime = LocalTime.now();
    // 设置为22点33分
    localTime = LocalTime.of(22, 33);
    System.out.println(localTime); // 22:33
    // 返回一天中的第5503秒
    localTime = LocalTime.ofSecondOfDay(5503);
    System.out.println(localTime); // 01:31:43
    // -----下面是关于localDateTime的用法-----
    // 获取当前日期、时间
    var localDateTime = LocalDateTime.now();
    // 当前日期、时间加上25小时３分钟
    var future = localDateTime.plusHours(25).plusMinutes(3);
    System.out.println("当前日期、时间的25小时3分之后：" + future);
    // -----下面是关于Year、YearMonth、MonthDay的用法示例-----
    var year = Year.now(); // 获取当前的年份
    System.out.println("当前年份：" + year); // 输出当前年份
    year = year.plusYears(5); // 当前年份再加5年
    System.out.println("当前年份再过5年：" + year);
    // 根据指定月份获取YearMonth
    var ym = year.atMonth(10);
    System.out.println("year年10月：" + ym); // 输出XXXX-10，XXXX代表当前年份
    // 当前年月再加5年、减3个月
    ym = ym.plusYears(5).minusMonths(3);
    System.out.println("year年10月再加5年、减3个月：" + ym);
    var md = MonthDay.now();
    System.out.println("当前月日：" + md); // 输出--XX-XX，代表几月几日
    // 设置为5月23日
    var md2 = md.with(Month.MAY).withDayOfMonth(23);
    System.out.println("5月23日为：" + md2); // 输出--05-23
```



### 5.5 正则表达式

> 正则表达式是一个强大的字符串处理工具，可以对字符串进行查找、提取、分割、替换等操作

#### 5.5.1 创建正则表达式

- 正则表达式就是一个用于匹配字符串的模板，可以匹配一批字符串，所以创建正则表达式就是创建一个特殊的字符串

<center>正则表达式所支持的合法字符</center>

| 字符   | 解释                                                         |
| ------ | ------------------------------------------------------------ |
| x      | 字符 x（ x 可以代表任何合法字符）                            |
| \0mnn  | 八进制数 0mnn 所表示的字符                                   |
| \xhh   | 十六进制值 0xhh 所表示的字符                                 |
| \uhhhh | 十六进制值 0xhhhh 所表示的 Unicode 字符                      |
| \t     | 制表符（‘\u0009’）                                           |
| \n     | 新行（换行）符（'\u000A'）                                   |
| \r     | 回车符（'\u000D'）                                           |
| \f     | 换页符（'\u000C'）                                           |
| \a     | 报警（bell）符（'\u0007'）                                   |
| \e     | Escape 符（'\u001B'）                                        |
| \cx    | x 对应的控制符。例如，\cM 匹配 Ctrl - M。x 值必须为 A ~ Z 或 a ~ z 之一 |

- 正则表达式中有一些**特殊字符**，这些特殊字符在正则表达式中有其特殊用途

<center>正则表达式中的特殊字符</center>

| 特殊字符 | 说明                                           |
| -------- | ---------------------------------------------- |
| $        | 匹配一行的结尾                                 |
| ^        | 匹配一行的开头                                 |
| ( )      | 标记子表达式的开始和结束的位置                 |
| [ ]      | 用于确定中括号表达式的开始和结束位置           |
| { }      | 用于标记前面子表达式的出现频度                 |
| *        | 指定前面子表达式可以出现零次或多次             |
| +        | 指定前面子表达式可以出现一次或多次             |
| ?        | 指定前面子表达式可以出现零次或一次             |
| .        | 匹配除换行符 \n 之外的任何单字符               |
| \        | 用于转义下一个字符，或指定八进制、十六进制字符 |
| \|       | 指定两项之间任选一项                           |

- ”通配符“ 是可以匹配多个字符的特殊字符。正则表达式中的 ”通配符“ 远远超出了普通通配符的功能，它被称为**预定义字符**

<center>预定义字符</center>

| 预定义字符 | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| .          | 可以匹配任何字符                                             |
| \d         | 可以匹配 0 ~ 9 的所有数字                                    |
| \D         | 匹配的非数字                                                 |
| \s         | 匹配所有的空白字符，包括空格、制表符、回车符、换页符、换行符等 |
| \S         | 匹配所有的非空白字符                                         |
| \w         | 匹配所有的单词字符，包括 0 ~ 9 所有数字、26 个英文字母和下划线（_） |
| \W         | 匹配所有的非单词字符                                         |

- **在一些特殊情况下**，只想匹配 a ~ f 的字母，或者匹配除 ab 之外的所有小写字母，或者匹配中文字符，就需要使用**方括号表达式**

<center>方括号表达式</center>

| 方括号表达式       | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| 表示枚举           | 例如 [abc]，表示 a、b、c 其中任意一个字符                    |
| 表示范围：-        | 例如 [a-f]，表示 a~f 范围内的任意字符。范围和枚举可以组合使用，如 [a-cx-z]，表示 a\~c、x\~z 范围内的任意字符 |
| 表示求否：^        | 例如 [\^abc]，表示非 a、b、c 的任意字符                      |
| 表示 ”与“ 运算：&& | 例如 [a-z&&[def]]，求 a~z 和 [def] 的交集，表示 d、e 或 f    |
| 表示 ”并“ 运算     | 并运算与前面的枚举类似。例如 [a-d[m-p]]，表示[a-dm-p]        |

- **正则表达式还支持圆括号表达式**，用于**将多个表达式组成一个子表达式**，圆括号中可以使用或运算符（|）。例如，正则表达式 ”((public)|(protected)|(private))“ 用于匹配 Java 三个访问控制符其中一个
-  Java 还支持几个**边界匹配符**

<center>边界匹配符</center>

| 边界匹配符 | 说明                           |
| ---------- | ------------------------------ |
| ^          | 行的开头                       |
| $          | 行的结尾                       |
| \b         | 单词的边界                     |
| \B         | 非单词的边界                   |
| \A         | 输入的开头                     |
| \G         | 前一个匹配的结尾               |
| \Z         | 输入的结尾，仅用于最后的结束符 |
| \z         | 输入的结尾                     |

- 分组

| 常用分组构造形式 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| (p)              | 非命名捕获。捕获匹配的字符串。编号为 0 的第一个捕获是由整个正则表达式模式匹配的文本，其他捕获结果则根据左括号的顺序从 1 开始自动编号 |
| (?<name>p)       | 命名捕获。将匹配的字符串捕获到一个组名称或编号名称中。用于 name 的字符串不能包含任何标点符号，并且不能以数字开头，可以使用单引号代替尖括号 |
| (?:p)            | 非捕获匹配，不存储供以后使用的匹配。这对应 or 字符（\|）组合模式部件的情况很有用。例如，‘industr(?:y\|ise)’ 是比 ‘industry\|industries’ 更经济的表达 |
| (?=p)            | 非捕获匹配。例如，‘Windows (?=95\|98\|NT\|2000)’ 匹配 "Windows 2000" 中的 "Windows"，但不匹配 "Windows 3.1" 中的 "Windows" |
| (?!p)            | 非捕获匹配。例如，‘Windows (?!95\|98\|NT\|2000)' 匹配 "Windows 3.1" 中的 "Windows"，但不匹配 "Windows 2000" 中的 "Windows" |

- 正则表达式还提供了**数量标识符**，正则表达式支持的数量标识符有如下几种模式
  - **Greedy（贪婪模式）**：数量标识符默认采用贪婪模式。贪婪模式的表达式会一直匹配下去，直到无法匹配为止。
  - **Reluctant（勉强模式）**：用问号后缀（?）表示，它只会匹配最少的字符。也成为最小匹配模式
  - **Possessive（占有模式）**：用加号后缀（+）表示，目前只有 Java 支持占有模式，通常比较少用

<center>三种模式的数量表示符</center>

| 贪婪模式 | 勉强模式 | 占用模式 | 说明                                 |
| -------- | -------- | -------- | ------------------------------------ |
| X?       | X??      | X?+      | X 表达式出现一次或零次               |
| X*       | X*?      | X*+      | X 表达式出现零次或多次               |
| X+       | X+?      | X++      | X 表达式出现一次或多次               |
| X{n}     | X{n}?    | X{n}+    | X 表达式出现 n 次                    |
| X{n,}    | X{n,}?   | X{n,}+   | X 表达式最少出现 n 次                |
| X{n,m}   | X{n,m}?  | X{n,m}+  | X 表达式最少出现 n 次，最多出现 m 次 |

#### 5.5.2 使用正则表达式

- 一旦程序中定义了正则表达式，就可以使用 **Pattern 和 Matcher** 来使用正则表达式
- **Pattern 对象是正则表达式编译后再内存中的表示形式**，因此，**正则表达式字符串必须先被编译为 Pattern 对象，然后再利用该 Pattern 对象创建对应的 Matcher 对象**。执行匹配所涉及的状态保留在 Matcher 对象中，**多个 Matcher 对象可以共享同一个 Pattern 对象**
- Pattern 是不可变类，可供多个并发线程安全使用
- Matcher 类提供了如下几个常用方法
  - **==find()==**：返回目标字符串中是否包含与 Pattern 匹配的子串
  - **==group()==**：返回上一次与 Pattern 匹配的子串
  - **==start()==**：返回上一次与 Pattern 匹配的子串在目标字符串中的**开始位置**
  - **==end()==**：返回上一次与 Pattern 匹配的子串在目标字符串中的**结束位置加1**
  - **==lookingAt()==**：返回目标字符串前面部分与 Pattern 是否匹配
  - **==matches()==**：返回整个目标字符串与 Pattern 是否匹配
  - **==reset()==**：将现有的 Matcher 对象应用于一个新的字符序列

```java
    // 使用字符串模拟从网络上得到的网页源码
    var str = "我想求购一本《疯狂Java讲义》，尽快联系我13500006666" + "交朋友，电话号码是13611125565"
        + "出售二手电脑，联系方式15899903312";
    // 创建一个Pattern对象，并用它建立一个Matcher对象
    // 该正则表达式只抓取13X和15X段的手机号，
    // 实际要抓取哪些电话号码，只要修改正则表达式即可。
    Matcher m = Pattern.compile("((13\\d)|(15\\d))\\d{8}").matcher(str);
    // 将所有符合正则表达式的子串（电话号码）全部输出
    while (m.find()){
        System.out.println(m.group());
    }

    // 创建一个Pattern对象，并用它建立一个Matcher对象
    var regStr = "Java is very easy!";
    System.out.println("目标字符串是：" + regStr);
    Matcher m = Pattern.compile("\\w+").matcher(regStr);
    while (m.find()) {
        System.out.println(m.group() + "子串的起始位置：" + m.start() + "，其结束位置：" + m.end());
    }

    String[] mails = {
        "kongyeeku@163.com",
        "kongyeeku@gmail.com",
        "ligang@crazyit.org",
        "wawa@abc.xx"
    };
    var mailRegEx = "\\w{3,20}@\\w+\\.(com|org|cn|net|gov)";
    var mailPattern = Pattern.compile(mailRegEx);
    Matcher matcher = null;
    for (var mail : mails) {
        if (matcher == null) {
            matcher = mailPattern.matcher(mail);
        } else {
            matcher.reset(mail);
        }
        String result = mail + (matcher.matches() ? "是" : "不是") + "一个有效的邮件地址！";
        System.out.println(result);
    }

    String[] msgs = {
        "Java has regular expressions in 1.4",
        "regular expressions now expressing in Java",
        "Java represses oracular expressions"
    };
    var p = Pattern.compile("re\\w*");
    Matcher matcher = null;
    for (var i = 0; i < msgs.length; i++) {
        if (matcher == null) {
            matcher = p.matcher(msgs[i]);
        } else {
            matcher.reset(msgs[i]);
        }
        System.out.println(matcher.replaceAll("哈哈:)"));
    }
```



### 5.6 变量处理和方法处理

#### 5.6.1 Java 9 增强的 MethodHandle

- **MethodHandle 为 Java 提供了方法引用的功能**，方法引用的概念有点类似于 C 的 “函数指针”。这种方法引用是一种轻量级的引用方式，它不会检查方法的访问权限，也不管方法所属的类、实例方法或静态方法，MethodHandle 类就是简单代表特定的方法，并可通过 MethodHandle 来调用。为了使用 MethodHandle 还涉及如下几个类
  - **MethodHandles**：MethodHandle 的工厂类，它提供了一系列静态方法用于获取 MethodHandle
  - **MethodHandles.Lookup**：Lookup 静态内部类也是 MethodHandle、VarHandle 的工厂类，专门用于获取 MethodHandle、VarHandle 
  - **MethodType**：代表一个方法类型。MethodType 根据方法的形参、返回值类型来确定方法类型

```java
	// 定义一个private的类方法
	private static void hello() {
		System.out.println("Hello world!");
	}
	// 定义一个private的实例方法
	private String hello(String name) {
		System.out.println("执行带参数的hello" + name);
		return name + ",您好";
	}
	public static void main(String[] args) throws Throwable {
		// 定义一个返回值为void、不带形参的方法类型
		var type = MethodType.methodType(void.class);
		// 使用MethodHandles.Lookup的findStatic获取类方法
		var mtd = MethodHandles.lookup().findStatic(MethodHandleTest.class, "hello", type);
		// 通过MethodHandle执行方法
		mtd.invoke();
		// 使用MethodHandles.Lookup的findVirtual获取实例方法
		var mtd2 = MethodHandles.lookup().findVirtual(MethodHandleTest.class, "hello",
			// 指定获取返回值为String, 形参为String的方法类型
            MethodType.methodType(String.class, String.class));
		// 通过MethodHandle执行方法，传入主调对象和参数
		System.out.println(mtd2.invoke(new MethodHandleTest(), "孙悟空"));
	}
```



#### 5.6.2 Java 9 增加的 VarHandle

- **VarHandle 主要用于动态操作数组的元素或对象的成员变量**。VarHandle 也需要通过 MethodHandles 来获取实例，接下来调用 VarHandle 的方法即可动态操作指定数组的元素或指定对象的成员变量

```java
class User {
	String name;
	static int MAX_AGE;
}
public class VarHandleTest {
	public static void main(String[] args) throws Throwable {
        var sa = new String[] {"Java", "Kotlin", "Go"};
        // 获取一个String[]数组的VarHandle对象
        var avh = MethodHandles.arrayElementVarHandle(String[].class);
        // 比较并设置：如果第三个元素是Go，则该元素被设为Lua
        var r = avh.compareAndSet(sa, 2, "Go", "Lua");
        // 输出比较结果
        System.out.println(r); // 输出true
        // 看到第三个元素被替换成Lua
        System.out.println(Arrays.toString(sa));
        // 获取sa数组的第二个元素
        System.out.println(avh.get(sa, 1)); // 输出Kotlin
        // 获取并设置：返回第三个元素，并将第三个元素设为Swift
        System.out.println(avh.getAndSet(sa, 2, "Swift"));
        // 看到第三个元素被替换成Swift
        System.out.println(Arrays.toString(sa));

        // 用findVarHandle方法获取User类中名为name，
        // 类型为String的实例变量
        var vh1 = MethodHandles.lookup().findVarHandle(User.class,
                                                       "name", String.class);
        var user = new User();
        // 通过VarHandle获取实例变量的值，需要传入对象作为调用者
        System.out.println(vh1.get(user)); // 输出null
        // 通过VarHandle设置指定实例变量的值
        vh1.set(user, "孙悟空");
        // 输出user的name实例变量的值
        System.out.println(user.name); // 输出孙悟空
        // 用findVarHandle方法获取User类中名为MAX_AGE，
        // 类型为Integer的类变量
        var vh2 = MethodHandles.lookup().findStaticVarHandle(User.class,
                                                             "MAX_AGE", int.class);
        // 通过VarHandle获取指定类变量的值
        System.out.println(vh2.get()); // 输出0
        // 通过VarHandle设置指定类变量的值
        vh2.set(100);
        // 输出User的MAX_AGE类变量
        System.out.println(User.MAX_AGE); // 输出100
    }
}
```



### 5.7 Java 8 新增的日期时间格式器

- java.time.format 包下提供了一个 **DateTimeFormatter** 格式器。为了使用 DateTimeFormatter 进行格式化或解析，必须先获取 DateTimeFormatter 对象，有如下三种方式：
  - **直接使用静态变量创建 DateTimeFormatter 格式器。**DateTimeFormatter 类中包含了大量形如 ISO_LOCAL_DATE、ISO_LOCAL_TIME、ISO_LOCAL_DATE_TIME 等静态常量，这些静态常量本身就是 DateTimeFormatter 实例
  - **使用不同风格的枚举值来创建 DateTimeFormatter 格式器。**在 FormatStyle 枚举类中定义了 FULL、LONG、MEDIUM、SHORT 四个枚举值，它们代表日期时间的不同风格
  - **根据模式字符串创建 DateTimeFormatter 格式器。**

#### 5.7.1 使用 DateTimeFormatter 完成格式化

- 使用 DateTimeFormatter 将日期、时间（LocalDate、LocalTime、LocalDateTime 等实例）格式化为字符串，可通过如下两种方式
  - **调用 DateTimeFormatter 的 format(TemporalAccessor temporal) 方法执行格式化**，其中 LocalDate、LocalTime、LocalDateTime 等类都是 TemporalAccessor 接口的实现类
  - **调用 LocalDate、LocalTime、LocalDateTime 等日期、时间对象的 ==format(DateTimeFormatter formatter)== 方法执行格式化**

```java
    var formatters = new DateTimeFormatter[] {
        // 直接使用常量创建DateTimeFormatter格式器
        DateTimeFormatter.ISO_LOCAL_DATE,
        DateTimeFormatter.ISO_LOCAL_TIME,
        DateTimeFormatter.ISO_LOCAL_DATE_TIME,
        // 使用本地化的不同风格来创建DateTimeFormatter格式器
        DateTimeFormatter.ofLocalizedDateTime(FormatStyle.FULL, FormatStyle.MEDIUM),
        DateTimeFormatter.ofLocalizedDate(FormatStyle.LONG),
        // 根据模式字符串来创建DateTimeFormatter格式器
        DateTimeFormatter.ofPattern("Gyyyy%%MMM%%dd HH:mm:ss")
    };
    var date = LocalDateTime.now();
    // 依次使用不同的格式器对LocalDateTime进行格式化
    for (var i = 0; i < formatters.length; i++) {
        // 下面两行代码的作用相同
        System.out.println(date.format(formatters[i]));
        System.out.println(formatters[i].format(date));
    }
```

- 有时候可能需要使用到传统的 DateFormat 类，DateTimeFormatter 则提供了一个 toFormat() 方法，该方法可以获取 DateTimeFormatter 对应的 Format 对象

#### 5.7.2 使用DateTimeFormatter 解析字符串

- **使用 DateTimeFormatter 将指定格式的字符串解析成日期、时间对象（LocalDate、LocalTime、LocalDateTime 等实例），可通过日期、时间对象提供的 ==parse(CharSequence text, DateTimeFormatter formatter)== 方法进行解析**

```java
    // 定义一个任意格式的日期时间字符串
    var str1 = "2014==04==12 01时06分09秒";
    // 根据需要解析的日期、时间字符串定义解析所用的格式器
    var fomatter1 = DateTimeFormatter.ofPattern("yyyy==MM==dd HH时mm分ss秒");
    // 执行解析
    var dt1 = LocalDateTime.parse(str1, fomatter1);
    System.out.println(dt1); // 输出 2014-04-12T01:06:09
    // ---下面代码再次解析另一个字符串---
    var str2 = "2014$$$4月$$$13 20小时";
    var fomatter2 = DateTimeFormatter.ofPattern("yyy$$$MMM$$$dd HH小时");
    var dt2 = LocalDateTime.parse(str2, fomatter2);
    System.out.println(dt2); // 输出 2014-04-13T20:00
```



## 第6章  Java集合

### 6.1 Java 集合概述

- **为了保存数量不确定的数据，以及保存具有映射关系的数据（也被称为关联数组），Java 提供了集合类。**主要负责保存、盛装其他数据，因此集合类也被称为**容器类**。
- 集合类和数组不一样，数组元素既可以是基本类型的值，也可以十对象；而集合只能保存对象
- Java 的集合主要由两个接口派生而出：Collection 和 Map，Collection 和 Map 是 Java 集合框架的根接口，这两个接口又包含了一些子接口或实现类

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\Collection集合体系的继承树.png" alt="Collection集合体系的继承树" style="zoom:100%;" />

<center>Collection 集合体系的继承树 </center>



![Map体系的继承树](E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\Map体系的继承树.png)

<center>Map 体系的继承树</center>

<img src="E:\ProgrammingStudyMaterials\Java后端\Java核心基础\Java核心基础.assets\三种集合示意图.png" alt="三种集合示意图" style="zoom:70%;" />

### 6.2 Java 11 增强的 Collection 和 Iterator 接口

- Collection 接口是 List、Set 和 Queue 接口的父接口，该接口中定义的方法既可用于操作 Set 集合，也可用于操作 List 和 Queue 集合。Collection 接口中定义了如下操作集合元素的方法
  - **==boolean add(Object o)==**：用于向集合中添加一个元素。如果集合对象被添加操作改变了，则返回 true
  - **==boolean addAll(Collection c)==**：把集合 c 里的所有元素添加到指定集合里。如果集合对象被添加操作改变了，则返回 true
  - **==void clear()==**：清除集合里的所有元素，将集合长度变为 0
  - **==boolean contains(Object o)==**：返回集合里是否包含指定元素
  - **==boolean containsAll(Collection c)==**：返回集合里是否包含集合 c 里的所有元素
  - **==boolean isEmpty()==**：返回集合是否为空。当集合长度为 0 时返回 true，否则返回 false
  - **==Iterator iterator()==**：返回一个 Iterator 对象，用于遍历集合里的元素
  - **==boolean remove(Object o)==**：删除集合中指定元素 o，当集合中包含了一个或多个元素 o 时，该方法只删除第一个符合条件的元素，该方法将返回 true
  - **==boolean removeAll(Collection c)==**：从集合中删除集合 c 里包含的所有元素（相当于调用该方法的集合减集合 c），如果删除了一个或一个以上的元素，则该方法返回 true
  - **==boolean retainAll(Collection c)==**：从集合中删除集合 c 里不包含的元素（相当于把调用该方法的集合变成该集合和集合 c 的交集），如果该操作改变了调用该方法的集合，则该方法返回 true
  - **==int size()==**：该方法返回集合里元素的个数
  - **==Object[] toArray()==**：该方法把集合转换成一个数组，所有的集合元素变成对应的数组元素

```java
    var c = new ArrayList();
    // 添加元素
    c.add("孙悟空");
    // 虽然集合里不能放基本类型的值，但Java支持自动装箱
    c.add(6);
    System.out.println("c集合的元素个数为:" + c.size()); // 输出2
    // 删除指定元素
    c.remove(6);
    System.out.println("c集合的元素个数为:" + c.size()); // 输出1
    // 判断是否包含指定字符串
    System.out.println("c集合的是否包含\"孙悟空\"字符串:" + c.contains("孙悟空")); // 输出true
    c.add("轻量级Java EE企业应用实战");
    System.out.println("c集合的元素：" + c);

    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    System.out.println("c集合是否完全包含books集合？" + c.containsAll(books)); // 输出false
    // 用c集合减去books集合里的元素
    c.removeAll(books);
    System.out.println("c集合的元素：" + c);
    // 删除c集合里所有元素
    c.clear();
    System.out.println("c集合的元素：" + c);
    // 控制books集合里只剩下c集合里也包含的元素
    books.retainAll(c);
    System.out.println("books集合的元素:" + books);
```



#### 6.2.1 使用 Lambda 表达式遍历集合

- Java 8 为 Iterable 接口新增了一个 **==forEach(Consumer action)==** 默认方法，该方法所需参数的类型是一个函数式接口
- 当程序调用 Iterable 接口的 forEach(Consumer action) 遍历集合元素时，程序会依次将集合元素传给 Consumer 的 accept(T t) 方法。正因为 Consumer 是函数式接口，因此可以使用 Lambda 表达式来遍历集合元素

```java
    // 创建一个集合
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂Android讲义");
    // 调用forEach()方法遍历集合
    books.forEach(obj -> System.out.println("迭代集合元素：" + obj));
```



#### 6.2.2 使用 Iterator 遍历集合元素

- Iterator 接口也是 Java 集合框架的成员，**主要用于遍历（即迭代访问）Collection 集合中的元素**，Iterator 对象也被称为**迭代器**
- Iterator 接口隐藏了各种 Collection 实现类的底层细节，向应用程序提供了遍历 Collection 集合元素的统一编程接口。Iterator 接口里定义了如下 4 个方法
  - **==boolean hasNext()==**：如果被迭代的集合元素还没有遍历完，则返回 true
  - **==Object next()==**：返回结合里的下一个元素
  - **==void remove()==**：删除集合里上一次 next 方法返回的元素
  - **==void forEachRemaining(Consumer action)==**：这是 Java 8 为 Iterator 新增的默认方法，该方法可以使用 Lambda 表达式来遍历集合元素

```java
    // 创建集合、添加元素的代码与前一个程序相同
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂Android讲义");
    // 获取books集合对应的迭代器
    var it = books.iterator();
    while (it.hasNext()) {
        // it.next()方法返回的数据类型是Object类型，因此需要强制类型转换
        var book = (String) it.next();
        System.out.println(book);
        if (book.equals("疯狂Java讲义")) {
            // 从集合中删除上一次next方法返回的元素
            it.remove();
        }
        // 对book变量赋值，不会改变集合元素本身
        book = "测试字符串";   // ①
    }
    System.out.println(books);
```

- 当使用 Iterator 对集合元素进行迭代时，Iterator 并不是把集合元素本身传给了迭代变量，而是**把集合元素的值传给了迭代变量**，所以**修改迭代变量的值对集合元素本身没有任何影响**
- **当使用 Iterator 迭代访问 Collection 集合元素时，Collection 集合里的元不能被改变**，只有通过 Iterator 的 remove() 方法删除上一次 next() 方法返回的集合元素才可以；否则将会引发 java.util.ConcurrentModificationException 异常
- Iterator 迭代器采用的是快速失败（fail-fast）机制，一旦在迭代过程中检测到该集合已经被修改（通常是程序中的其他线程修改），程序会立即引发 ConcurrentModificationException 异常，而不是显式修改后的结果，这样可以避免共享资源而引发的潜在问题

- 使用 Iterator 的 forEachRemaining(Consumer action) 遍历集合元素

```java
    // 创建集合、添加元素的代码与前一个程序相同
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂Android讲义");
    // 获取books集合对应的迭代器
    var it = books.iterator();
    // 使用Lambda表达式（目标类型是Comsumer）来遍历集合元素
    it.forEachRemaining(obj -> System.out.println("迭代集合元素：" + obj));
```



#### 6.2.3 使用 foreach 循环遍历集合元素

- 除可使用 Iterator 接口迭代访问 Collection 集合里的元素之外，使用 Java 5 提供的 foreach 循环迭代访问集合元素更加便捷

```java
    // 创建集合、添加元素的代码与前一个程序相同
    var books = new HashSet();
    books.add(new String("轻量级Java EE企业应用实战"));
    books.add(new String("疯狂Java讲义"));
    books.add(new String("疯狂Android讲义"));
    for (var obj : books) {
        // 此处的book变量也不是集合元素本身
        var book = (String) obj;
        System.out.println(book);
        if (book.equals("疯狂Android讲义")) {
            // 下面代码会引发ConcurrentModificationException异常
            books.remove(book);     // ①
        }
    }
    System.out.println(books);
```

- 与使用 Iterator 接口迭代访问集合元素类似，**foreach 循环中的迭代变量也不是集合元素本身，系统只是依次把集合元素的值赋给迭代变量**，因此在 foreach 循环中修改迭代变量的值也没有任何意义；同样该集合也不能被改变，否则将引发异常

#### 6.2.4 使用 Predicate 操作集合

- Java 8 为 Collection 集合新增了一个 **==removeIf(Predicate filter)==** 方法，该方法将会批量删除符合 filter 条件的所有元素。该方法需要一个 Predicate （谓语）对象作为参数，Predicate 也是函数式接口，因此可以使用 Lambda 表达式作为参数

```java
    // 创建一个集合
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂iOS讲义");
    books.add("疯狂Ajax讲义");
    books.add("疯狂Android讲义");
    // 使用Lambda表达式（目标类型是Predicate）过滤集合
    books.removeIf(ele -> ((String) ele).length() < 10);
    System.out.println(books);
```

- 使用 Predicate 可以充分简化集合的运算

```java
public static void main(String[] args) {
    // 创建books集合、为books集合添加元素的代码与前一个程序相同。
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂iOS讲义");
    books.add("疯狂Ajax讲义");
    books.add("疯狂Android讲义");
    // 统计书名包含“疯狂”子串的图书数量
    System.out.println(calAll(books, ele->((String) ele).contains("疯狂")));
    // 统计书名包含“Java”子串的图书数量
    System.out.println(calAll(books, ele->((String) ele).contains("Java")));
    // 统计书名字符串长度大于10的图书数量
    System.out.println(calAll(books, ele->((String) ele).length() > 10));
}
public static int calAll(Collection books, Predicate p) {
    int total = 0;
    for (var obj : books) {
        // 使用Predicate的test()方法判断该对象是否满足Predicate指定的条件
        if (p.test(obj)) {
            total++;
        }
    }
    return total;
}
```



#### 6.2.5 使用 Stream 操作集合

- Java 8 还新增了 **Stream、IntStream、LongStream、DoubleStream 等流式 API**，这些 API 代表多个支持串行和并行聚集操作的元素。还提供了**对应的 Builder，例如 Stream.Builder**，开发者可以通过这些 Builder 来创建对应的流。
- 独立使用 Stream 的步骤如下：
  1. 使用 **Stream 或 XxxStream 的 ==builder()== 类方法创建该 Stream 对应的 Builder**
  2. 重复调用 **Builder 的 ==add()== 方法向该流中添加多个元素**
  3. 调用 **Builder 的 ==build()== 方法获取对应的 Stream**
  4. 调用 **Stream 的聚集方法**

```java
    var is = IntStream.builder().add(20).add(13).add(-2).add(18).build();
    // 下面调用聚集方法的代码每次只能执行一个
    System.out.println("is所有元素的最大值：" + is.max().getAsInt());
    System.out.println("is所有元素的最小值：" + is.min().getAsInt());
    System.out.println("is所有元素的总和：" + is.sum());
    System.out.println("is所有元素的总数：" + is.count());
    System.out.println("is所有元素的平均值：" + is.average());
    System.out.println("is所有元素的平方是否都大于20:" + is.allMatch(ele -> ele * ele > 20));
    System.out.println("is是否包含任何元素的平方大于20:" + is.anyMatch(ele -> ele * ele > 20));
    // 将is映射成一个新Stream，新Stream的每个元素是原Stream元素的2倍+1
    var newIs = is.map(ele -> ele * 2 + 1);
    // 使用方法引用的方式来遍历集合元素
    newIs.forEach(System.out::println); // 输出41 27 -3 37
```

- Stream 提供了大量的方法进行聚集操作，这些方法既可以是 **“中间的”（intermediate）**，也可以是 **“末端的”（terminal）**
  - **中间方法**：中间操作允许流保持打开状态，并允许直接调用后续方法。中间方法的返回值是另外一个流
  - **末端方法**：末端方法是对流的最终操作。当对某个 Stream 执行末端方法后，该流将会被 “消耗” 且不可再用
- 除此之外，关于流的方法还有如下两个特征：
  - **有状态的方法**：这种方法会给流增加一些新的属性，比如元素的唯一性、元素的最大数量、保证元素以排序的方式被处理等。有状态的方法往往需要更大的性能开销
  - **短路方法**：短路方法可以尽早结束对流的操作，不必检查所有的元素
- Stream 常用的中间方法：
  - **==filter(Predicate predicate)==**：过滤 Stream 中所有不符合 predicate 的元素
  - **==mapToXxx(ToXxxFunction mapper)==**：使用 ToXxxFunction 对流中的元素执行一对一的转换，该方法返回的新流中包含了 ToXxxFunction 转换生成的所有元素
  - **==peek(Consumer action)==**：依次对每个元素执行一些操作，该方法返回的流与原有流包含相同的元素。该方法主要用于调试
  - **==distinct()==**：该方法用于排序流中所有重复的元素（判断重复的标准是使用 equals() 比较返回 true）。这是一个有状态的方法
  - **==sorted()==**：该方法用于保证流中的元素在后续的访问中处于有序状态。这是一个有状态的方法
  - **==limit(long maxSize)==**：该方法用于保证对该流的后续访问中最大允许访问的元素个数。这是一个有状态的、短路方法
- Stream 常用的末端方法：
  - **==forEach(Consumer action)==**：遍历流中的所有元素，对每个元素执行 action
  - **==toArray()==**：将流中所有元素转换成一个数组
  - **==reduce()==**：该方法有三个重载的版本，都用于通过某种操作来合并流中的元素
  - **==min()==**：返回流中所有元素的最小值
  - **==max()==**：返回流中所有元素的最大值
  - **==count()==**：返回流中所有元素的数量
  - **==anyMatch(Predicate predicate)==**：判断流中是否至少包含一个元素符合 Predicate 条件
  - **==allMatch(Predicate predicate)==**：判断流中是否每个元素都符合 Predicate 条件
  - **==noneMatch(Predicate predicate)==**：判断流中是否所有元素都不符合 Predicate 条件
  - **==findFirst()==**：返回流中的第一个元素
  - **==findAny()==**：返回流中的任意一个元素
- Java 8 允许使用流式 API 来操作集合，**Collection 接口提供了一个 ==stream()== 默认方法**，该方法可返回该集合对应的流，接下来即可通过流式 API 来操作集合元素。由于 Stream 可以对集合元素进行整体的聚集操作，因此 Stream 极大地丰富了集合的功能

```java
    // 创建books集合、为books集合添加元素的代码与8.2.5小节的程序相同。
    var books = new HashSet();
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂iOS讲义");
    books.add("疯狂Ajax讲义");
    books.add("疯狂Android讲义");
    // 统计书名包含“疯狂”子串的图书数量
    System.out.println(books.stream().filter(ele->((String) ele).contains("疯狂")).count()); // 输出4
    // 统计书名包含“Java”子串的图书数量
    System.out.println(books.stream().filter(ele->((String) ele).contains("Java") ).count()); // 输出2
    // 统计书名字符串长度大于10的图书数量
    System.out.println(books.stream().filter(ele->((String) ele).length() > 10).count()); // 输出2
    // 先调用Collection对象的stream()方法将集合转换为Stream,
    // 再调用Stream的mapToInt()方法获取原有的Stream对应的IntStream
    // 调用forEach()方法遍历IntStream中每个元素，输出8 11 16 7 8
    books.stream().mapToInt(ele -> ((String) ele).length()).forEach(System.out::println);
```



### 6.3 Set 集合

> Set 集合与 Collection 基本相同，没有提供任何额外的方法。**<u>Set 集合中添加的元素是无序的，且不允许包含相同的元素</u>**，如果试图把相同的元素加入同一个 Set 集合中，则添加操作失败，add() 方法返回 false，且新元素不会被加入。

#### 6.3.1 HashSet 类

- HashSet 是 Set 接口的典型实现，大多时候使用 Set 集合时就是使用这个实现类。**HashSet 按 Hash 算法来存储集合中的元素，因此具有很好的存储和查找性能。**HashSet 具有以下特点：
  - 不能保证元素的排列顺序，顺序可能与添加顺序不同，顺序也有可能发生变化
  - HashSet 是不同步的，如果多个线程同时访问一个 HashSet，假如有两个或两个以上线程同时修改了 HashSet 集合时，则必须通过代码来保证其同步
  - 集合元素值可以是 null
- 当向 HashSet 集合中存入一个元素时，**HashSet 会调用该对象的 hashCode() 方法来得到该对象的 hashCode 值，然后根据该 hashCode 值决定该对象在 HashSet 中的存储位置。**如果两个元素通过 **equals() 方法比较返回 true，但他们的 hashCode() 方法返回值不相等，HashSet 会把它们存储在不同的位置**，依然可以添加成功
- **==HashSet 集合判断两个元素相等的标准是两个对象通过 equals() 方法比较相等，并且两个对象的 hashCode() 方法返回值也相等==**
- 当把一个对象放入 HashSet 中时，如果需要重写该对象对应类的 equals() 方法，则也应该重写其 hashCode() 方法。**规则是：如果两个对象通过 equals() 方法比较返回 true，这两个对象的 hashCode 值也应该相同**

---

- 重写 hashCode() 方法的**基本规则：**

  - 在程序运行过程中，同一个对象多次调用 hashCode() 方法应该返回相同的值
  - 当两个对象通过 equals() 方法比较返回 true 时，这两个对象的 hashCode() 方法应返回相等的值
  - 对象中用作 equals() 方法比较标准的实例变量，都应该用于计算 hashCode() 值

- 重写 hashCode() 方法的**一般步骤：**

  1. 把对象内每个有意义的实例变量（即每个参与 equals() 方法比较标准的实例变量）计算出一个 int 类型的 hashCode 值。

     | 实例变量类型                       | 计算方式                                                     |
     | ---------------------------------- | ------------------------------------------------------------ |
     | boolean                            | hashCode = (f ? 0 : 1);                                      |
     | 整数类型（byte、short、char、int） | hashCode = (int) f;                                          |
     | long                               | hashCode = (int)(f ^ (f >>> 32));                            |
     | float                              | hashCode = Float.floatToIntBits(f)                           |
     | double                             | long l = Double.doubleToLongBits(f);                                                                      hashCode = (int)(l ^ (l >>> 32)); |
     | 引用类型                           | hashCode = f.hashCode();                                     |
     
  2. 用第 1 步计算出来的多个 hashCode 值组合计算出一个 hashCode 值返回。为了避免直接相加产生的偶然相等，可以通过为实例变量的 hashCode 值乘以任意一个质数后再相加
  
     `return f1.hashCode() * 19 + (int)f2 * 31;`
  
- 当程序把对象添加到 HashSet 中之后，**不要再去修改该集合中参与计算 hashCode()、equals() 的实例变量，**否则将会导致 HashSet 无法正确操作这些元素

#### 6.3.2 LinkedHashSet 类

- LinkedHashSet 集合也是**根据元素的 hashCode 值来决定元素的存储位置**，但它**同时使用链表来维护元素的次序**，这使得元素看起来是以插入的顺序保存的，当遍历时，会按元素的添加顺序来访问集合中的元素
- 虽然 LinkedHashSet 使用了链表记录集合元素的添加顺序，但 LinkedHashSet 依然是 HashSet，因此它**不允许集合元素重复**

#### 6.3.3 TreeSet 类

- TreeSet 是 SortedSet 接口的实现类，TreeSet 可以确保元素处于排序状态。与 HashSet 集合相比，TreeSet 提供了以下几个额外的方法：
  - **==Comparator comparator()==**：如果 TreeSet 采用了定制排序，则该方法返回定制排序所使用的 Comparator；如果 TreeSet 采用了自然排序，则返回 null。
  - **==Object first()==**：返回集合中的第一个元素
  - **==Object last()==**：返回集合中的最后一个元素
  - **==Object lower(Object e)==**：返回集合中位于指定元素之前的元素（即小于指定元素的最大元素，参考元素不需要是 TreeSet 集合中的元素）。
  - **==Object higher(Object e)==**：返回集合中位于指定元素之后的元素（即大于指定元素的最小元素，参考元素不需要是 TreeSet 集合中的元素）。
  - **==SortedSet subSet(Object fromElement, Object toElement)==**：返回此 Set 的子集合，范围从 fromElement（包含）到 toElement（不包含）。
  - **==SortedSet headSet(Object toElement)==**：返回此 Set 的子集，由小于 toElement 的元素组成
  - **==SortedSet tailSet(Object fromElement)==**：返回此 Set 的子集，由大于或等于 fromElement 的元素组成

```java
    var nums = new TreeSet();
    // 向TreeSet中添加四个Integer对象
    nums.add(5);
    nums.add(2);
    nums.add(10);
    nums.add(-9);
    // 输出集合元素，看到集合元素已经处于排序状态
    System.out.println(nums);
    // 输出集合里的第一个元素
    System.out.println(nums.first()); // 输出-9
    // 输出集合里的最后一个元素
    System.out.println(nums.last());  // 输出10
    // 返回小于4的子集，不包含4
    System.out.println(nums.headSet(4)); // 输出[-9, 2]
    // 返回大于5的子集，如果Set中包含5，子集中还包含5
    System.out.println(nums.tailSet(5)); // 输出 [5, 10]
    // 返回大于等于-3，小于4的子集。
    System.out.println(nums.subSet(-3, 4)); // 输出[2]
```

- 与 HashSet 集合采用的 hash 算法来决定元素的存储位置不同，TreeSet 采用**红黑树的数据结构**来存储集合元素。TreeSet 支持两种排序方法：**自然排序和定制排序**。在默认情况下，TreeSet 采用自然排序。

  ###### 1.自然排序

  - TreeSet 会调用集合元素的 **==compareTo(Object obj)==** 方法来比较元素之间的大小关系，然后**将集合元素按升序排列**，这种方式就是自然排序
  - 如果试图**将一个对象添加到 TreeSet 时**，则**该对象的类必须实现 Comparable 接口**，否则程序将会抛出异常
  - Java 的一些常用类已经实现了 Comparable 接口，并提供了比较大小的标准。下面是实现了 Comparable 接口的常用类：
    - **BigDecimal、BigInteger 以及所有的数值型对应的包装类：**按它们对应的数值大小进行比较
    - **Character：**按字符的 Unicode 值进行比较
    - **Boolean：** true 对应的包装类实例大于 false 对应的包装类实例
    - **String：**依次比较字符串中每个字符的 Unicode 值
    - **Date、Time：**后面的时间、日期比前面的时间、日期大

  - 对于 TreeSet 集合而言，它**判断两个对象是否相等的唯一标准是：两个对象通过 compareTo(Object obj) 方法比较是否返回 0** —— 如果通过 compareTo(Object obj) 方法比较返回 0，TreeSet 会认为它们相等；否则认为它们不相等

  - 当要把一个对象放入 TreeSet 中，重写该对象对应类的 equals() 方法时，应保证该方法与 compareTo(Object obj) 方法有一致的结果，其**规则是：如果两个对象通过 equals() 方法比较返回 true 时，这两个对象通过 compareTo(Object obj) 方法比教应返回 0**

  ###### 2.定制排序

  - TreeSet 的自然排序是根据集合元素的大小，TreeSet 将它们以升序排列。如果需要实现定制排序，例如以降序排列，则可以通过 Comparator 接口。该接口里包含了一个 **==int compare(T o1, T o2)==** 方法，用于比较 o1 和 o2 的大小
  - 如果需要实现定制排序，则需要在创建 TreeSet 集合对象时，提供一个 Comparator 对象与该 TreeSet 集合关联，由该 Comparator 对象负责集合元素的排序逻辑。由于 Comparator 是一个函数式接口，因此可使用 Lambda 表达式来代替 Comparator 对象

  ```java
  class M {
  	int age;
  	public M(int age) {
  		this.age = age;
  	}
  	public String toString() {
  		return "M [age:" + age + "]";
  	}
  }
  public class TreeSetTest4 {
  	public static void main(String[] args) {
  		// 此处Lambda表达式的目标类型是Comparator
  		var ts = new TreeSet((o1, o2) -> {
  			var m1 = (M) o1;
  			var m2 = (M) o2;
  			// 根据M对象的age属性来决定大小，age越大，M对象反而越小
  			return m1.age > m2.age ? -1 : m1.age < m2.age ? 1 : 0;
  		});
  		ts.add(new M(5));
  		ts.add(new M(-3));
  		ts.add(new M(9));
  		System.out.println(ts);
  	}
  }
  ```

#### 6.3.4 EnumSet 类

- EnumSet 是一个专门为枚举类设计的集合类，**EnumSet 中的所有元素都是必须是指定枚举类型的枚举值**，该枚举类型在创建 EnumSet 时显式或隐式地指定。EnumSet 的集合元素也是有序的，**以枚举值在 Enum 类内的定义顺序来决定集合元素的顺序**。
- EnumSet 在内部**以向量的形式存储**，这种存储形式非常紧凑、高效，因此 EnumSet 对象内存占用很小，而且运行效率很好。尤其是进行批量操作（如调用 containsAll() 和 retainAll() 方法）时，如果其参数也是 EnumSet 集合，则该批量操作的执行速度也非常快。
- EnumSet 集合不允许加入 null 元素，否则将抛出 NullPointerException 异常。
- EnumSet 类没有暴露任何构造器来创建该类的实例，通过它提供的方法来创建 EnumSet 对象：
  - **==EnumSet allOf(Class elementType)==**：创建一个包含指定枚举类里所有枚举值的 EnumSet 集合。
  - **==EnumSet complementOf(EnumSet s)==**：创建一个其元素类型与指定 EnumSet 里元素类型相同的 EnumSet 集合，新 EnumSet 集合包含原 EnumSet 集合所不包含的、此枚举类剩下的枚举值（即新 EnumSet 集合和原 EnumSet 集合的集合元素加起来就是该枚举类的所有枚举值）。
  - **==EnumSet copyOf(Collection c)==**：使用一个普通的集合来创建 EnumSet 集合。
  - **==EnumSet copyOf(EnumSet s)==**：创建一个与指定 EnumSet 具有相同元素类型、相同集合元素的 EnumSet 集合。
  - **==EnumSet noneOf(Class elementType)==**：创建一个元素类型为指定枚举类型的空 EnumSet。
  - **==EnumSet of(E first, E... rest)==**：创建一个包含一个或多个枚举值的 EnumSet 集合，传入的多个枚举值必须属于同一个枚举类。
  - **==EnumSet range(E from, E to)==**：创建一个包含从 from 枚举值到 to 枚举值范围内所有枚举值的 EnumSet 集合

```java
enum Season {
	SPRING,SUMMER,FALL,WINTER
}
public class EnumSetTest {
	public static void main(String[] args) {
		// 创建一个EnumSet集合，集合元素就是Season枚举类的全部枚举值
		var es1 = EnumSet.allOf(Season.class);
		System.out.println(es1); // 输出[SPRING, SUMMER, FALL, WINTER]
		// 创建一个EnumSet空集合，指定其集合元素是Season类的枚举值。
		var es2 = EnumSet.noneOf(Season.class);
		System.out.println(es2); // 输出[]
		// 手动添加两个元素
		es2.add(Season.WINTER);
		es2.add(Season.SPRING);
		System.out.println(es2); // 输出[SPRING, WINTER]
		// 以指定枚举值创建EnumSet集合
		var es3 = EnumSet.of(Season.SUMMER, Season.WINTER);
		System.out.println(es3); // 输出[SUMMER, WINTER]
		var es4 = EnumSet.range(Season.SUMMER, Season.WINTER);
		System.out.println(es4); // 输出[SUMMER, FALL, WINTER]
		// 新创建的EnumSet集合的元素和es4集合的元素有相同类型，
		// es5的集合元素 + es4集合元素 = Season枚举类的全部枚举值
		var es5 = EnumSet.complementOf(es4);
		System.out.println(es5); // 输出[SPRING]
        
        var c = new HashSet();
		c.clear();
		c.add(Season.FALL);
		c.add(Season.SPRING);
		// 复制Collection集合中所有元素来创建EnumSet集合
		var enumSet = EnumSet.copyOf(c);   // ①
		System.out.println(enumSet); // 输出[SPRING, FALL]
		c.add("疯狂Java讲义");
		c.add("轻量级Java EE企业应用实战");
		// 下面代码出现异常：因为c集合里的元素不是全部都为枚举值
		enumSet = EnumSet.copyOf(c);  // ②
	}
}
```

- 当试图复制一个 Collection 集合里的元素来创建 EnumSet 集合时，必须保证 **Collection 集合里的所有元素都是同一个枚举类的枚举值。**



### 6.4 List 集合

> **<u>List 集合代表一个元素有序、可重复的集合，集合中的每个元素都有其对应的顺序索引。</u>**List 集合允许使用重复元素，可以通过索引来访问指定位置的集合元素。List 集合默认按元素的添加顺序设置元素的索引。

#### 6.4.1 改进的 List 接口和 ListIterator 接口

- 由于 List 是有序集合，因此 List 集合里增加了一些根据索引来操作集合元素的方法：
  - **==void add(int index, Object element)==**：将元素 element 插入到 List 集合的 index 处。
  - **==boolean addAll(int index, Collection c)==**：将集合 c 所包含的所有元素都插入到 List 集合的 index 处。
  - **==Object get(int index)==**：返回集合 index 索引处的元素
  - **==int indexOf(Object o)==**：返回对象 o 在 List 集合中第一次出现的位置索引
  - **==int lastIndexOf(Object o)==**：返回对象 o 在 List 集合中最后一次出现的位置索引
  - **==Object remove(int index)==**：删除并返回 index 索引处的元素
  - **==Object set(int index, Object element)==**：将 index 索引处的元素替换成 element 对象，返回被替换的旧元素
  - **==List subList(int fromIndex, int toIndex)==**：返回从索引 fromIndex（包含）到索引 toIndex（不包含）处所有集合元素组成的子集合

```java
    var books = new ArrayList();
    // 向books集合中添加三个元素
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂Android讲义");
    System.out.println(books);
    // 将新字符串对象插入在第二个位置
    books.add(1, new String("疯狂Ajax讲义"));
    for (var i = 0; i < books.size(); i++) {
        System.out.println(books.get(i));
    }
    // 删除第三个元素
    books.remove(2);
    System.out.println(books);
    // 判断指定元素在List集合中的位置：输出1，表明位于第二位
    System.out.println(books.indexOf(new String("疯狂Ajax讲义"))); // ①
    //将第二个元素替换成新的字符串对象
    books.set(1, "疯狂Java讲义");
    System.out.println(books);
    // 将books集合的第二个元素（包括）到第三个元素（不包括）截取成子集合
    System.out.println(books.subList(1, 2));
```

- Java 8 还为 List 接口添加了如下两个默认方法：
  - **==void replaceAll(UnaryOperator operator)==**：根据 operator 指定的计算规则重新设置 List 集合的所有元素
  - **==void sort(Comparator c)==**：根据 Comparator 参数对 List 集合的元素排序

```java
    var books = new ArrayList();
    // 向books集合中添加4个元素
    books.add("轻量级Java EE企业应用实战");
    books.add("疯狂Java讲义");
    books.add("疯狂Android讲义");
    books.add("疯狂iOS讲义");
    // 使用目标类型为Comparator的Lambda表达式对List集合排序
    books.sort((o1, o2) -> ((String) o1).length() - ((String) o2).length());
    System.out.println(books);
    // 使用目标类型为UnaryOperator的Lambda表达式来替换集合中所有元素
    // 该Lambda表达式控制使用每个字符串的长度作为新的集合元素
    books.replaceAll(ele -> ((String) ele).length());
    System.out.println(books); // 输出[7, 8, 11, 16]
```

- List 还额外提供了一个 **==listIterator()==** 方法，该方法返回一个 ListIterator 对象，ListIterator 接口继承了 Iterator 接口，提供了专门操作 List 的方法，在 Iterator 接口的基础上增加了如下方法：
  - **==boolean hasPrevious()==**：返回该迭代器关联的集合是否还有上一个元素
  - **==Object previous()==**：返回该迭代器的上一个元素
  - **==void add(Object o)==**：在指定位置插入一个元素

```java
    String[] books = {
        "疯狂Java讲义", "疯狂iOS讲义",
        "轻量级Java EE企业应用实战"
    };
    var bookList = new ArrayList();
    for (var i = 0; i < books.length; i++) {
        bookList.add(books[i]);
    }
    var lit = bookList.listIterator();
    // 从前向后遍历
    while (lit.hasNext()) {
        System.out.println(lit.next());
        lit.add("-------分隔符-------");
    }
    System.out.println("=======下面开始反向迭代=======");
    // 从后向前遍历
    while (lit.hasPrevious()) {
        System.out.println(lit.previous());
    }
```

#### 6.4.2 ArrayList 和 Vector 实现类

- ArrayList 和 Vector 类都是基于数组实现的 List 类，所以 **ArrayList 和 Vector 类封装了一个动态的、允许再分配的 Object[] 数组。**ArrayList 或 Vector 对象使用 initialCapacity 参数来设置该数组的长度，当向 **ArrayList 或 Vector 中添加元素超出了该数组的长度时，它们的 initialCapacity 会自动增加**
- 如果向 ArrayList 或 Vector 集合中添加大量元素时，可使用 ensureCapacity(int minCapacity) 方法一次性地增加 initialCapacity
- 如果开始时就知到 ArrayList 或 Vector 集合需要保存多少个元素，则可以在创建它们时就指定 initialCapacity 大小。如果创建空的 ArrayList 或 Vector 集合时不指定 initialCapacity 参数，则 **Object[] 数组的长度默认为 ==10==**
- ArrayList 和 Vector 还提供了如下两个方法来重新分配 Object[] 数组：
  - **==void ensureCapacity(int minCapacity)==**：将 ArrayList 或 Vector 集合的 Object[] 数组长度增加大于或等于 minCapacity 值
  - **==void trimToSize()==**：调整 ArrayList 或 Vector 集合的 Object[] 数组长度为当前元素的个数。调用该方法可减少 ArrayList 或 Vector 集合对象占用的存储空间
- **ArrayList 是线程不安全的**，当多个线程访问同一个 ArrayList 集合时，如果有一个线程修改了 ArrayList 集合，则程序必须手动保证该集合的同步性；**但 Vector 是线程安全的**
- Vector 还提供了一个 **Stack 子类，它用于模拟 ”栈“ 这种数据结构，”栈“ 是指 ”后进先出“（LIFO）的容器，**提供了如下几个方法：
  - **==Object peek()==**：返回 ”栈“ 的第一个元素，但并不将该元素 ”pop“ 出栈
  - **==Object pop()==**：返回 ”栈“ 的第一个元素，并将该元素 ”pop“ 出栈
  - **==void push(Object item)==**：将一个元素 ”push“ 进栈，最后一个进 ”栈“ 的元素总是位于 ”栈“ 顶

#### 6.4.3 固定长度的 List

- Arrays 工具类中提供了 **==asList(Object... a)==** 方法，该方法可以把一个数组或指定个数的对象转换成一个 List 集合，这个 List 集合既不是 ArrayList 实现类的实例，也不是 Vector 实现类的实例，而是 Arrays 的内部类 ArrayList 的实例。
- Arrays.ArrayList 是一个固定长度的 List 集合，程序只能遍历访问该集合里的元素，不可能增加、删除该集合里的元素



### 6.5 Queue 集合

- **Queue 用于模拟队列这种数据结构，队列通常是 “先进先出”（FIFO）的容器。**队列的头部保存在队列中存放是将最长的元素，队列的尾部保存在队列中存放时间最短的元素。新元素插入（offer）到队列的尾部，访问元素（poll）操作会返回队列头部的元素。通常，队列不允许随机访问队列中的元素。Queue 接口中定义了如下方法：
  - **==void add(Object e)==**：将指定元素加入此队列的尾部
  - **==Object element()==**： 获取队列头部的元素，但是不删除该元素
  - **==boolean offer(Object e)==**：将指定元素加入此队列的尾部。当使用有容量限制的队列时，此方法通常比 add(Object e) 更好
  - **==Object peek()==**：获取队列头部的元素，但是不删除该元素。如果此队列为空，则返回 null
  - **==Object poll()==**：获取队列头部的元素，并删除该元素。如果此队列为空，则返回 null
  - **==Object remove()==**：获取队列头部的元素，并删除该元素

#### 6.5.1 PriorityQueue 实现类

- PriorityQueue 保存队列元素的顺序并不是按加入队列的顺序，而是**按队列元素的大小进行重新排序**。因此当调用 peek() 方法或者 poll() 方法取出队列中的元素时，并不是取出最先进入队列的元素，而是取出队列中最小的元素。

```java
    var pq = new PriorityQueue();
    // 下面代码依次向pq中加入四个元素
    pq.offer(6);
    pq.offer(-3);
    pq.offer(20);
    pq.offer(18);
    // 输出pq队列，并不是按元素的加入顺序排列
    System.out.println(pq); // 输出[-3, 6, 20, 18]
    // 访问队列第一个元素，其实就是队列中最小的元素：-3
    System.out.println(pq.poll());
```

- PriorityQueue **不允许插入 null 元素**，它还需要对队列元素进行排序，PriorityQueue 的元素有两种排序方式：
  - **自然排序：**采用自然顺序的 PriorityQueue 集合中的元素必须实现了 Comparable 接口，而且应该是同一个类的多个实例
  - **定制排序：**创建 PriorityQueue 队列时，传入一个 Comparator 对象，该对象负责对队列中的所有元素进行排序。采用定制排序时不要求队列元素实现 Comparable 接口

#### 6.5.2 Deque 接口与 ArrayDeque 实现类

- Deque 接口是 Queue 接口的子接口，它代表一个双端队列，Deque 接口里定义了一些双端队列的方法，这些方法允许从两端来操作队列的元素：
  - **==void addFirst(Object e)==**：将指定元素插入到该双端队列的开头
  - **==void addLast(Object e)==**：将指定元素插入到该双端队列的末尾
  - **==Iterator descendingIterator()==**：返回该双端队列的迭代器，该迭代器将以逆序来迭代队列中的元素
  - **==Object getFirst()==**：获取但不删除双端队列的第一个元素
  - **==Object getLast()==**：获取但不删除双端对立的最后一个元素
  - **==boolean offerFirst(Object e)==**：将指定元素插入到该双端队列的开头
  - **==boolean offerLast(Object e)==**：将指定元素插入到该双端队列的末尾
  - **==Object peekFirst()==**：获取但不删除该双端队列的第一个元素；如果此队列为空，则返回 null
  - **==Object peekLast()==**：获取但不删除该双端队列的最后一个元素；如果此队列为空，则返回 null
  - **==Object pollFirst()==**：获取并删除该双端队列的第一个元素；如果此队列为空，则返回 null
  - **==Object pollLast()==**：获取并删除该双端队列的最后一个元素；如果此队列为空，则返回 null
  - **==Object pop()（栈方法）==**：pop 出该双端队列所表示的栈的栈顶元素。相当于 removeFirst()
  - **==void push(Object e)（栈方法）==**：将一个元素 push 进该双端队列所表示的栈的栈顶。相当于 addFirst(e)
  - **==Object removeFirst()==**：获取并删除该双端队列的第一个元素
  - **==boolean removeFirstOccurrence(Object o)==**：删除该双端队列的第一次出现的元素 o
  - **==Object removeLast()==**：获取并删除该双端队列的最后一个元素
  - **==boolean removeLastOccurrence(Object o)==**：删除该双端队列的最后一次出现的元素 o
- Deque 接口提供了一个典型的实现类：ArrayDeque 它是一个基于数组实现的双端队列，创建 Deque 时可以指定一个 numElements 参数，用于指定 Object[] 数组的长度；如果不指定 numElements 参数，Deque 底层数组长度为 16

- 将 ArrayDeque 当成 “栈” 使用：

```java
    var stack = new ArrayDeque();
    // 依次将三个元素push入"栈"
    stack.push("疯狂Java讲义");
    stack.push("轻量级Java EE企业应用实战");
    stack.push("疯狂Android讲义");
    // 输出：[疯狂Android讲义, 轻量级Java EE企业应用实战, 疯狂Java讲义]
    System.out.println(stack);
    // 访问第一个元素，但并不将其pop出"栈"，输出：疯狂Android讲义
    System.out.println(stack.peek());
    // 依然输出：[疯狂Android讲义, 疯狂Java讲义, 轻量级Java EE企业应用实战]
    System.out.println(stack);
    // pop出第一个元素，输出：疯狂Android讲义
    System.out.println(stack.pop());
    // 输出：[轻量级Java EE企业应用实战, 疯狂Java讲义]
    System.out.println(stack);
```

- 将 ArrayDeque 当成 “队列” 使用：

```java
    var queue = new ArrayDeque();
    // 依次将三个元素加入队列
    queue.offer("疯狂Java讲义");
    queue.offer("轻量级Java EE企业应用实战");
    queue.offer("疯狂Android讲义");
    // 输出：[疯狂Java讲义, 轻量级Java EE企业应用实战, 疯狂Android讲义]
    System.out.println(queue);
    // 访问队列头部的元素，但并不将其poll出队列"栈"，输出：疯狂Java讲义
    System.out.println(queue.peek());
    // 依然输出：[疯狂Java讲义, 轻量级Java EE企业应用实战, 疯狂Android讲义]
    System.out.println(queue);
    // poll出第一个元素，输出：疯狂Java讲义
    System.out.println(queue.poll());
    // 输出：[轻量级Java EE企业应用实战, 疯狂Android讲义]
    System.out.println(queue);
```

#### 6.5.3 LinkedList 实现类

- LinkedList 类是 List 接口和 Deque 接口的实现类，可以根据索引来随机访问集合中的元素，还可以被当成双端队列使用

```java
    var books = new LinkedList();
    // 将字符串元素加入队列的尾部
    books.offer("疯狂Java讲义");
    // 将一个字符串元素加入栈的顶部
    books.push("轻量级Java EE企业应用实战");
    // 将字符串元素添加到队列的头部（相当于栈的顶部）
    books.offerFirst("疯狂Android讲义");
    // 以List的方式（按索引访问的方式）来遍历集合元素
    for (var i = 0; i < books.size(); i++) {
        System.out.println("遍历中：" + books.get(i));
    }
    // 访问、并不删除栈顶的元素
    System.out.println(books.peekFirst());
    // 访问、并不删除队列的最后一个元素
    System.out.println(books.peekLast());
    // 将栈顶的元素弹出“栈”
    System.out.println(books.pop());
    // 下面输出将看到队列中第一个元素被删除
    System.out.println(books);
    // 访问、并删除队列的最后一个元素
    System.out.println(books.pollLast());
    // 下面输出：[轻量级Java EE企业应用实战]
    System.out.println(books);
```



### 6.6 增强的 Map 集合

> **<u>Map 用于保存具有映射关系的数据，因此 Map 集合里保存着两组值，一组值用于保存 Map 里的 key，另一组值用于保存 Map 里的 value，key 和 value 都可以是任何引用类型的数据。</u>**key 和 value 之间存在单向一对一关系。 **<u>Map 的 key 不允许重复，</u>**即同一个 Map 对象的任何两个 key 通过 equals 方法比较返回 false

- Map 有时也被称为字典，或关联数组。Map 接口中定义了如下常用的方法：
  - **==void clear()==**：删除该 Map 对象中的所有 key-value 对
  - **==boolean containsKey(Object key)==**：查询 Map 中是否包含指定的 key，如果包含则返回 true
  - **==boolean containsValue(Object value)==**：查询 Map 中是否包含一个或多个 value，如果包含则返回 true
  - **==Set entrySet()==**：返回 Map 中包含的 key-value 对所组成的 Set 集合，每个集合都是 Map.Entry（Entry 是 Map 的内部类） 对象
  - **==Object get(Object key)==**：返回指定 key 所对应的 value；如果此 Map 中不包含该 key，则返回 null
  - **==boolean isEmpty()==**：查询该 Map 是否为空（即不包含任何 key-value 对），如果为空则返回 true
  - **==Set keySet()==**：返回 Map 中所有 key 组成的 Set 集合
  - **==Object put(Object key, Object value)==**：添加一个 key-value 对，如果当 Map 中已有一个与该 key 相等的 key-value 对，则新的 key-value 对会覆盖原来的 key-value 对
  - **==void putAll(Map m)==**：将指定 Map 中的 key-value 对复制到本 Map 中
  - **==Object remove(Object key)==**：删除指定 key 所对应的 key-value 对，返回被删除 key 所关联的 value，如果该 key 不存在，则返回 null
  - **==boolean remove(Object key, Object value)==**：这是 Java 8 新增的方法，删除指定 key、value 所对应的 key-value 对。如果从该 Map 中成功地删除该 key-value 对，该方法返回 true，否则返回 false
  - **==int size()==**：返回该 Map 里的 key-value 对的个数
  - **==Collection values()==**：返回 Map 里所有 value 组成的 Collection
- Map 中包含一个内部类 Entry，该类封装了一个 key-value 对。Entry 包含如下三个方法：
  - **==Object getKey()==**：返回 Entry 里包含的 key 值
  - **==Object getValue()==**：返回 Entry 里包含的 value 值
  - **==Object setValue(V value)==**：设置该 Entry 里包含的 value 值，并返回新设置的 value 值

```java
    var map = new HashMap();
    // 成对放入多个key-value对
    map.put("疯狂Java讲义", 109);
    map.put("疯狂iOS讲义", 10);
    map.put("疯狂Ajax讲义", 79);
    // 多次放入的key-value对中value可以重复
    map.put("轻量级Java EE企业应用实战", 99);
    // 放入重复的key时，新的value会覆盖原有的value，如果新的value覆盖了原有的value，该方法返回被覆盖的value
    System.out.println(map.put("疯狂iOS讲义", 99)); // 输出10
    System.out.println(map); // 输出的Map集合包含4个key-value对
    // 判断是否包含指定key
    System.out.println("是否包含值为 疯狂iOS讲义 的key：" + map.containsKey("疯狂iOS讲义")); // 输出true
    // 判断是否包含指定value
    System.out.println("是否包含值为 99 的value：" + map.containsValue(99)); // 输出true
    // 获取Map集合的所有key组成的集合，通过遍历key来实现遍历所有key-value对
    for (var key : map.keySet()) {
        // map.get(key)方法获取指定key对应的value
        System.out.println(key + "-->" + map.get(key));
    }
    map.remove("疯狂Ajax讲义"); // 根据key来删除key-value对。
    System.out.println(map); // 输出结果不再包含 疯狂Ajax讲义=79 的key-value对
```

#### 6.6.1 改进的 HashMap 和 Hashtable 实现类

- Hashtable 是一个古老的 Map 实现类。Java 8 改进了 HashMap 的实现，使用 HashMap 存在 key 冲突时依然具有良好的性能。此外，Hashtable 和 HashMap 存在两点典型区别：
  - **Hashtable 是一个线程安全的 Map 实现，但 HashMap 是线程不安全的实现**
  - **Hashtable 不允许使用 null 作为 key 和 value，**如果试图把 null 值放进 Hashtable 中，将会引发 NullPointerException 异常；***但 HashMap 可以使用 null 作为 key 或 value**
- 为了成功地在 HashMap、Hashtable 中存储、获取对象，**用作 key 的对象必须实现 hashCode() 方法和 equals() 方法**
- HashMap、Hashtable 判断两个 key 相等的标准：两个 key 通过 equals() 方法比较返回 true，两个 key 的 hashCode 值也相等
- HashMap、Hashtable 判断两个 value 相等的标准：两个对象通过 equals() 方法比较返回 true
- **==注意：==**尽量不要使用可变对象作为 HashMap、Hashtable 的 key，如果确实需要使用可变对象作为 HashMap、Hashtable 的 key，则尽量不要在程序中修改作为 key 的可变对象

#### 6.6.2 LinkedHashMap 实现类

- **LinkedHashMap 也是使用双向链表来维护 key-value 对的顺序（其实只需要考虑 key 的顺序），**该链表负责维护 Map 的迭代顺序，迭代顺序与 key-value 对的插入顺序保持一致

#### 6.6.3 使用 Properties 读写属性文件

- Properties 是 Hashtable 的子类，该对象在**处理属性文件**时特别方便。Properties 类可以**把 Map 对象和属性文件关联起来**，从而**可以把 Map 对象中的 key-value 对写入属性文件中，也可以把属性文件中的 “属性名=属性值” 加载到 Map 对象中**。由于属性文件里的属性名、属性值只能是字符串类型，所以 **Properties 里的 key、value 都是字符串类型**。
- 该类提供了以下三个方法来修改 Properties 里的 key、value值：
  - **==String getProperty(String key)==**：获取 Properties 中指定属性名对应的属性值
  - **==String getProperty(String key, String defaultValue)==**：该方法与前一个方法基本类似。只是如果 Properties 中不存在指定的 key 时，则该方法返回指定默认值
  - **==Object setProperties(String key, String value)==**：设置属性值
- 它还提供了两个读写属性文件的方法：
  - **==void load(InputStream inStream)==**：从属性文件（以流输入表示）中加载 key-value 对，把加载到的 key-value 对追加到 Properties 里
  - **==void store(OutputStream out, String comments)==**：将 Properties 中的 key-value 对输出到指定的属性文件（以输出流表示）中

```java
    var props = new Properties();
    // 向Properties中增加属性
    props.setProperty("username", "yeeku");
    props.setProperty("password", "123456");
    // 将Properties中的key-value对保存到a.ini文件中
    props.store(new FileOutputStream("a.ini"), "comment line");   // ①
    // 新建一个Properties对象
    var props2 = new Properties();
    // 向Properties中增加属性
    props2.setProperty("gender", "male");
    // 将a.ini文件中的key-value对追加到props2中
    props2.load(new FileInputStream("a.ini"));   // ②
    System.out.println(props2);
```

#### 6.6.4 SortedMap 接口和 TreeMap 实现类

- **TreeMap 就是一个红黑树数据结构**，每个 key-value 对即作为红黑树的一个结点。TreeMap 存储 key-value 对（节点）时，需要根据 key 对节点进行排序。TreeMap 可以保证所有的 key-value 对处于有序状态。TreeMap 也有两种排序方式：
  - **自然排序：**TreeMap 的所有 key 必须实现 Comparable 接口，而且所有的 key 应该是同一个类的对象
  - **定制排序：**创建 TreeMap 时，传入一个 Comparator 对象，该对象负责对 TreeMap 中的所有 key 进行排序
- Tree 中判断两个 key 相等的标准是：两个 key 通过 compareTo() 方法返回 0
- 如果使用自定义类作为 TreeMap 的 key，则应重写该类的 equals() 方法和 compareTo() 方法



#### 6.6.* Java 8 为 Map 新增的方法



## 第7章  泛型





## 第8章  异常处理





## 第9章  AWT编程





## 第10章  Swing编程





## 第11章  注解





## 第12章  输入/输出





## 第13章  多线程





## 第14章  网络编程





## 第15章  类加载机制与反射





## 第16章  MySQL数据库与JDBC编程

