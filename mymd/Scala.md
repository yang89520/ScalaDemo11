# 1 Scala概述

1.1 什么是Scala？

1.2 为什么要学Scala？

1.3 Java和Scala关系？

# 2 Scala安装配置

1. 依赖jdk1.8

2. 安装scala2.12

   1. 解压安装包到无中文路径
   2. 配置环境变量`$SCALA_HOME`和`Path`/bin目录
   3. cmd输入scala测试

3. idea安装scala插件![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/dd87a2615fee8da9c121847d336d4290_014b60065d8c02f9d1cc19091adcc073.png)

4. 创建maven工程

5. 添加Scala框架支持![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/130ab04f05c894d57b7315949db63893_ea7288b469a8da9322660b11851c75cd.png)

   ![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/a318ae6d569453b65f29062331faa309_30e97df5ba7d0c6b8306f6b33e055fd4.png)

6. 创建scala class

   ![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/a87563c7806718d7236261bbcd4e3658_0a4e9ac8c71aab4f91d35bf9a0465ed6.png)

   ```scala
   object HelloWorld {
     def main(args : Array[String]) : Unit = {
   
       print("Hello World")
   
       System.out.println("Hello World")
     }
   }
   ```

   > ① object HelloWorld 对象 + 对象名
   >
   > ② def 定义方法defined
   >
   > ③ main()主方法
   >
   > ④ args 参数名
   >
   > ⑤ Array[String] 参数类型，String类型的数组
   >
   > ⑥ Unit 相当于Java中的void，没有返回值的意思
   >
   > ⑦ = 给这个方法赋值，赋予一个方法体，这样方法就可以修改了。
   >
   > ⑧ {} 方法体

   

   

# 3 变量-数据类型-字符串-输入输出

## 3.1注释

同java

## 3.2 变量

**①变量声明语法:**

```scala
//var | val 变量名 : 变量类型 = 变量值
​	-var name : String = “Tom”
​	-name = “Jerry”

//var可变变量 val不可变变量
​	-val name : String = “Tom”
```

**②如果变量的类型可以通过变量值推断出来，那么可以省略变量类型：**

```scala
//通过变量值可以推断出来变量的类型，就可以省略类型
​	-val gender = "M"
​	-val num = 99
```

**③变量的初始化：scala必须显示初始化（直接赋值）**

## 3.3 标识符

**①字符数字：**

Scala标识符可以使用字母或下划线开头，后面可以接字母或数字，符号$也被看所字母

$不能开头，因为Scala编译器对于一些特殊符号会编译冲突

**②符号：**

**③关键字或保留字**![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/f0aad184a9201a06c1169f45260921df_77545aa77e64b1f0a44d32fbae137685.png)

## 3.4 数据类型

1. **不存在基本数据类型**

2. **数据类型分为：**

   1. 任意对象类型:AnyVal
   2. 任意引用类型:AnyRef![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/f9d3bc88d7cb14fc76977f6f39b3e692_watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lsanBocA==,size_16,color_FFFFFF,t_70.png)

   > 1.箭头指向是父类
   >
   > 2.Unit等同于Void
   >
   > 3.Null类型是Null类型 ，是null引用对象的类型，只有一个null值。是bottom class，是所有AnyRef的子类。
   >
   > 4.Nothing也是bottom class是所有类的子类

3. **数据类型转换**

   1. 自动类型转换(y隐式转换)

   2. *AnyVal*强制类型转换 : var 变量2 : xxx类型 = 变量.toxxx

      ```scala
      // var 变量2 : xxx类型 = 变量.toxxx
          var a1 : Int = 18
          //int --> byte
          var a2 : Byte = a1.toByte
          var a3 : Double = 19.2
          //double --> int
          var a4 : Int = a3.toInt
          //double --> char
          var a5 : Char = a3.toChar
      
      // 字符串类型转换 toString 和 +“”
          var a6 : String = "Tom and Jerry"
          println(a6.toString)
          var a7 : Int = 180
          println(a7.toString)
          var a8 : String = 289+""
          println(a8)
      ```

## 3.5 字符串

同java中String一样

①字符串连接： +

②传值字符串： %占位符

③插值字符串： ${变量名}

④多行字符串： “”“

​								|

​								|“”“.stripMargin [能够完整的保留字符串的输入格式]

```scala
object TestString2 {
  def main(args : Array[String]) : Unit = {
    val name : String = "Tom"
    val age : Int = 20
    //1 字符串连接
    println("name = " + name + ", age = " + age)

    //2 传值字符串
    printf("name = %s, age = %d\n", name, age)

    //3 插值字符串
    println(s"name = ${name}, age = ${age}")

    //4 多行字符串
    println(
      """
        |select *
        |from student
        |where name like "T%"
        |""".stripMargin)
  }
}

/*
name = Tom, age = 20
name = Tom, age = 20
name = Tom, age = 20

select *
from student
where name like "T%"
*/
```

## 3.6 输入输出

- 控制台输入
- 文件获取输入
- 输出到文件
- 网络传输 socket
  - 普通字符传输 
  - 序列化：对象传输

```scala
/* 控制台获取输入*/
	scala.io.StdIn.readLine()


/* 文件获取输入*/
	val source = scala.io.Source.fromFile(new File("input/word.txt"))
    //变量生成的快捷键加.var
    val strings = source.getLines()
    //获取迭代器
    while (strings.hasNext) {
      println(strings.next())
    }


/* 输出到文件*/
  def main(args: Array[String]): Unit = {
    val writer = new PrintWriter(new File("output/word.txt"))
    writer.write(
      """
        |Hello
        |World
        |Spark
        |""".stripMargin)

    writer.println("Scala")
    writer.flush()
    writer.close()
  }
```

```scala
# 网络传输

// 字符传输
object TestClient {
  def main(args: Array[String]): Unit = {

    val client = new Socket("localhost", 9090)
    val writer = new PrintWriter(new OutputStreamWriter(client.getOutputStream))

    while (true){
      println("输入对server的内容：")
      val str = scala.io.StdIn.readLine()
      writer.println(str)
      writer.flush()

    }
  }
}


object TestServer {
  def main(args: Array[String]): Unit = {
    val server = new ServerSocket(9090)
    while (true) {
      val socket = server.accept()
      val reader = new BufferedReader(new InputStreamReader(socket.getInputStream))
      var s: String = ""
      var flag = true
      while (flag) {
        s = reader.readLine()
        if (s != null) {
          println(s)
        } else {
          flag = false
        }
      }
    }
  }
}
```

```scala
# 网络传输

// 对象传输
object TestServer {
  def main(args: Array[String]): Unit = {
    val server = new ServerSocket(9090)

      val socket = server.accept()
      val stream = new ObjectInputStream(socket.getInputStream)
      val value = stream.readObject()
      println("接收对象："+ value)
      socket.close()
      server.close()
  }
}

object TestClient {
  def main(args: Array[String]): Unit = {
    val client = new Socket("localhost", 9090)

    val outputStream = new ObjectOutputStream(client.getOutputStream)
    outputStream.writeObject(new Student())
    outputStream.close()
    client.close()
  }
}

public class Student implements Serializable {
    private String name = "Tom";
    private int age = 10;

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

# 4 导包

Scala可以在任何位置导包, `import` 语句用于导入其他包中的成员（类，特质，函数等）。

```scala
import users._  // 导入包 users 中的所有成员
import users.User  // 导入类 User
import users.{User, UserPreferences}  // 仅导入选择的成员
import users.{UserPreferences => UPrefs}  // 导入类并且设置别名
```



# 5 运算符

- scala中没有运算符，实际上是方法的重载，如：

  ​	1 + 2实际上就是1.+(2)

  ​	我们可以将之视为运算符，是因为在Scala中，如果方法的参数小于等于1个的话，那	么“.”和括号就都是可选的。

- 没有++ --,后续通过+1 -1 += -=实现++ --的功能
- 不支持三元运算，用if-else实现三元运算符的作用
- == equal() eq() 

```scala
val a1="abc"
val a2="abc"
print(a1==a2) //true 等价于java加了非空判断的equals
val a3=new String("abc")
val a4=new String("abc")
print(a3=a4) //true
print(a3.equals(a4)) //true 等价于java equals
print(a3.eq(a4)) //false 内存比较等价于java==
```

运算符优先级

```scala
// 优先级由高到低
-()[]
-单元运算 !~
-算术运算
-移位运算
-比较运算
-位运算
-逻辑运算
-赋值运算
- ，
```

# 6 流程控制

- 所有的语句都有返回值 默认返回值是unit
- 返回值为语句最后一行的值
- 若没指定数据类型 返回值是所有返回值类型的父类

## if ..else if..else

```scala
// 无三元运算使用if语句替换
// 使用同java
```

## switch

- scala没有switch结构，使用模式匹配完成

# 7 循环控制

## for

- scala新特性`for推导式`

  ```scala
  /*
  	for语句的i默认是val
  */
  
  // 双闭区间
  	for (i <- 1 to 10){}
  // 左闭右开
  	for (i <- 1 until 10){}
  // 循环条件式(循环守卫) 类似continue
  	for (i <- 1 to 10 if i != 6){}
  // 引入变量
  	for (1 <- 1 to 3; j=4-i){}
  // 单行嵌套循环 相当于简单双层循环
  	for (i <- 1 to 3; j <- 1 to 3){}
  // 循环返回值
  	// 对i遍历1-10
  	// yied 将迭代器元素放到vector集合中 返回给res
  	// yield后可以进行二次处理
  	val res = for (i <- 1 to 10) yield i
  	val res = for (i <- 1 to 10) yield {
          if (i%2==0) i else "不是偶数"
      }
  // 遍历集合
  	for (i <- List集合){}
  
  // ()和{}的等价替换 ;可以省略 标准格式分行
  	for (i <- 1 to 10;j <- 1 to 10){}
  	for {
          i <- 1 to 10
          j <- 1 to 10
      }{}
  // for Range使用 左闭右开
  	// 控制步长 
  	for （i 《- Range(1,10,2)）
  	// 守卫实现控制步长
  	for (i <- 1 until 10 if 1%2==1)
  
  ```

## while

**while**

- 为什么说不建议使用while？

  while需要使用外部变量控制while流程 ，而scala设计理念是使函数体在内部完成生命周期(递归实现方法体内部的定义变量自己变化) ，所以不推荐使用while

- 使用方法同java
- 因为使用同java，所以无返回值

**do while**

- 同java，也无返回值

## Break

如何使用break退出循环？

- 和java不同的是scala没有break和continue关键字
- 使用Break()方法结束循环并且抛出异常
- 外层嵌套breakable方法接收抛出的异常，并在这个方法的源码里try catch了。保证循环体之后的代码正常执行

```scala
var n:int=0
breakable(
	while (n<=20){
        if (n==18) Break()
        n+=1
        print(n)   
    }
    print("ok~")
)
```

```scala
// 使用守卫实现break效果
var loop:Boolean=true
for (i <- 1 to 100 if loop){
    if (i==20) loop=false
    print("这是"+i)
}
```



## Continue

scala没有这种写法

```scala
// 循环条件式(循环守卫) 类似continue
	for (i <- 1 to 10 if i != 6){}
// if 过滤掉需要continue的条件
	for (i <- 1 to 10){
        if (i != 6){
            //这里写业务逻辑
        }
    }
```

# 8 函数式编程

## 函数式编程基础

为什么要用函数式编程?

​	同一个人在不同环境拥有不同的标签

​	同一个方法在不同场景拥有不同的标签

### 函数声明

```scala
// 直接声明函数
def sum(n1:Int,n2:Int)=>n1+n2 //一行可省略{}
def sum(n1:Int,n2:Int)=>{n1+n2}
// 方法转函数
val f1= math.sum _ //加" _"
print(f1) //<function2> //function后的2表示参数个数
print(f1(10,20)) //30

/**基本语法：
	def 函数名([参数名:数据类型][...])[ [:返回类型] =]{}
	说明：
		1. [参数名:数据类型]可不写 ...代表形参列表 可不传参数
		2. 没有return默认以【执行到】最后一行作为返回值
		3. :返回类型={} 写死返回类型
		4. ={} 推导出返回类型，由最后一行决定
		5. {} 不写等号无返回值 等价于：unit={} return不生效
*/
```

### 运行机制

```scala
// 所有的方法函数都在栈内
// 先调用main方法，压入栈，指针指向main的内存地址
// main中调用sum，将sum方法压入栈，指针指向sum
// sum执行结束后return回到main被调用点，指针指向main，sum栈就没有引用对象了，sum栈销毁
```



![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/20210405153413.png)![](https://gitee.com/Mryang_bast/typera/raw/master/scala_imgs/20210405153456.png)![image-20210405153612791](C:\Users\华为\AppData\Roaming\Typora\typora-user-images\image-20210405153612791.png)

### 递归

- 当函数每执行一次时，就开辟一个新函数栈
- 每次执行函数的局部变量互相独立，引用变量共享修改同一堆中对象
- 大问题化小，必须有一个出口
- return向上一级调用者返回，执行上一级的后续代码



### 过程

- 返回值是unit或者明确无返回值省略了:类型=的函数称作过程(procedure)

### 惰性函数和异常

- **惰性函数:**延迟运行的函数的求值，只加载不运行 类似ajex的缓冲原理
- 在java中类似懒汉加载(延时加载)声明对象时不会真正执行，调用getinstance方法才加载对象
- scala实现惰性函数

```scala
def main(args:Array[String]):unit={
    lazy sum_=sum(10,20)
    print("--------")
    print(sum_) //再次调用才执行sum函数的计算
    
}
def sum(n1:Int,n2:Int)={
    print("sum执行了")
    n1+n2
}
```





### 函数式细节和坑

```scala
// 参数列表可以是多个 没有形参可以不带小括号

// 形参和返回列表可以是任意类型

// 类型推导：根据执行最后一行自行推断数据类型

// 使用了return就，类型推导就无效，必须声明返回值类型

// 返回类型什么都没写 return语句不报错，但无效，返回()等价于 :unit={}

// 返回类型声明unit ，有无return都无效 返回()

// 如果明确无返回值或者返回不确定的类型值 ，返回类型可以省略或 Any

// 任何语法结构都可以嵌套 比如分支、循环、函数、方法嵌套

// 形参有默认初值，可以不赋值，默认使用初值 类python

// 形参赋值带默认初值的方法时，需要指定指定参数名赋值

// 形参默认是val

// 递归不能使用类型推导

// 支持可变长参 args：Int* args是集合  java ... python *args **kwargs
1到多个
def sum(a:Int,a_args:Int*)
o到多个
def sum(a_args:Int*)
//可变参数只能写在最后
```



## 函数式编程高级



# 9 面向对象编程





