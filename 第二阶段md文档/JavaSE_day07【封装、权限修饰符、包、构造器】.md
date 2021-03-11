# JavaSE_day07【面向对象基础--中】
{: id="20210309181757-1vwrgyq"}

## 今日内容
{: id="20210309181757-0yqthh5"}

* {: id="20210309181757-4llkfs0"}封装
  {: id="20210309181757-1pohp8f"}
* {: id="20210309181757-1ajffzu"}权限修饰符
  {: id="20210309181757-ysgdaa5"}
* {: id="20210309181757-7pm385v"}包
  {: id="20210309181757-zzaff9m"}
* {: id="20210309181757-6jigbyt"}构造器
  {: id="20210309181757-5bm216b"}
* {: id="20210309181757-l42z0yx"}代码块
  {: id="20210309181757-gztoqty"}
{: id="20210309181757-bvzd6t3"}

## 教学目标
{: id="20210309181757-cdc57qr"}

* {: id="20210309181757-h0gtwco"}[ ] 理解封装的概念
  {: id="20210309181757-d0plmc9"}
* {: id="20210309181757-nvsjgos"}[ ] 掌握权限修饰符的使用
  {: id="20210309181757-gfsduro"}
* {: id="20210309181757-duz085n"}[ ] 掌握属性的封装
  {: id="20210309181757-aia2e08"}
* {: id="20210309181757-dy96d6z"}[ ] 理解包的作用
  {: id="20210309181757-cyut96m"}
* {: id="20210309181757-hdecy46"}[ ] 掌握包的声明与导入
  {: id="20210309181757-ijmzo2m"}
* {: id="20210309181757-jmn07xc"}[ ] 掌握构造器的声明与使用
  {: id="20210309181757-6rszbz9"}
* {: id="20210309181757-s28dn8b"}[ ] 掌握this关键字的使用
  {: id="20210309181757-qvhd3ey"}
* {: id="20210309181757-e02waek"}[ ] 会声明标准的JavaBean
  {: id="20210309181757-n9e3h13"}
{: id="20210309181757-1a4cfqf"}

# 第六章 面向对象基础--中
{: id="20210309181757-2v21tjc"}

## 6.1 封装
{: id="20210309181757-n28zbxh"}

### 6.1.1 封装概述
{: id="20210309181757-s14ax0y"}

#### 1、为什么需要封装？
{: id="20210309181757-27epbsc"}

* {: id="20210309181757-zdqz835"}我要用洗衣机，只需要按一下开关和洗涤模式就可以了。有必要了解洗衣机内部的结构吗？有必要碰电动机吗？
  {: id="20210309181757-83we49q"}
* {: id="20210309181757-35mdrh1"}我们使用的电脑，内部有CPU、硬盘、键盘、鼠标等等，每一个部件通过某种连接方式一起工作，但是各个部件之间又是独立的
  {: id="20210309181757-21fau2r"}
* {: id="20210309181757-jzjdfda"}现实生活中，每一个个体与个体之间是有边界的，每一个团体与团体之间是有边界的，而同一个个体、团体内部的信息是互通的，只是对外有所隐瞒。
  {: id="20210309181757-ftx7ekm"}
{: id="20210309181757-1giyl6f"}

面向对象编程语言是对客观世界的模拟，客观世界里每一个事物的内部信息都是隐藏在对象内部的，外界无法直接操作和修改，只能通过指定的方式进行访问和修改。封装可以被认为是一个保护屏障，防止该类的代码和数据被其他类随意访问。适当的封装可以让代码更容易理解与维护，也加强了代码的安全性。
{: id="20210309181757-t3tanz2"}

随着我们系统越来越复杂，类会越来越多，那么类之间的访问边界必须把握好，面向对象的开发原则要遵循“高内聚、低耦合”，而“高内聚，低耦合”的体现之一：
{: id="20210309181757-82gvj01"}

* {: id="20210309181757-cdu3ogb"}高内聚：类的内部数据操作细节自己完成，不允许外部干涉；
  {: id="20210309181757-9b79b7w"}
* {: id="20210309181757-asy6yii"}低耦合：仅对外暴露少量的方法用于使用
  {: id="20210309181757-n7uk4n0"}
{: id="20210309181757-wml6u9q"}

隐藏对象内部的复杂性，只对外公开简单的接口。便于外界调用，从而提高系统的可扩展性、可维护性。通俗的讲，把该隐藏的隐藏起来，该暴露的暴露出来。这就是封装性的设计思想。
{: id="20210309181757-9lu4mu3"}

#### 2、如何实现封装呢？
{: id="20210309181757-sd3hrfi"}

通俗的讲，封装就是把该隐藏的隐藏起来，该暴露的暴露出来。那么暴露的程度如何控制呢？就是依赖访问控制修饰符，也称为权限修饰符来控制。
{: id="20210309181757-gcuq6ad"}

访问控制修饰符来控制相应的可见边界，边界有如下：
{: id="20210309181757-4o0oesc"}

（1）类
{: id="20210309181757-skzhax3"}

（2）包
{: id="20210309181757-7gs57om"}

（3）子类
{: id="20210309181757-8dvdwul"}

（4）模块：Java9之后引入
{: id="20210309181757-ymvuazx"}

权限修饰符：public,protected,缺省,private
{: id="20210309181757-d6iqm56" bookmark="✨"}

| 修饰符    | 本类 | 本包 | 其他包子类 | 其他包非子类 | 其他模块                 |
| --------- | ---- | ---- | ---------- | ------------ | ------------------------ |
| private   | √   | ×   | ×         | ×           | ×                       |
| 缺省      | √   | √   | ×         | ×           | ×                       |
| protected | √   | √   | √         | ×           | ×                       |
| public    | √   | √   | √         | √           | 默认不可以，可以建立依赖 |
{: id="20210309181757-pkvjhv0"}

外部类：public和缺省
{: id="20210309181757-nodprqs"}

成员变量：public,protected,缺省,private
{: id="20210309181757-qc6m8kp"}

成员方法：public,protected,缺省,private
{: id="20210309181757-ry6iejd"}

构造器：public,protected,缺省,private
{: id="20210309181757-dyux3ej"}

### 6.1.2 成员变量/属性私有化问题
{: id="20210309181757-tbjz6po"}

**<span style="color:red">成员变量（field）私有化</span>之后，提供标准的<span style="color:red">get/set</span>方法，我们把这种成员变量也称为<span style="color:red">属性（property）</span>。**或者可以说只要能通过get/set操作的就是事物的属性，哪怕它没有对应的成员变量。
{: id="20210309181757-to4qety"}

#### 1、成员变量封装的目的
{: id="20210309181757-ap73z6v"}

* {: id="20210309181757-beft2k4"}隐藏类的实现细节
  {: id="20210309181757-st4d2lo"}
* {: id="20210309181757-ikvk7rs"}让使用者只能通过事先预定的方法来访问数据，从而可以在该方法里面加入控制逻辑，限制对成员变量的不合理访问。还可以进行数据检查，从而有利于保证对象信息的完整性。
  {: id="20210309181757-zgv05ix"}
* {: id="20210309181757-255tthj"}便于修改，提高代码的可维护性。主要说的是隐藏的部分，在内部修改了，如果其对外可以的访问方式不变的话，外部根本感觉不到它的修改。例如：Java8->Java9，String从char[]转为byte[]内部实现，而对外的方法不变，我们使用者根本感觉不到它内部的修改。
  {: id="20210309181757-okl4u7z"}
{: id="20210309181757-1wcxcak"}

#### 2、实现步骤
{: id="20210309181757-yxxbozo"}

1. {: id="20210309181757-4br0mdx"}使用 `private` 修饰成员变量
   {: id="20210309181757-bi6a43e"}
{: id="20210309181757-0s9en56"}

```java
private 数据类型 变量名 ；
```
{: id="20210309181757-5r1ptm2"}

代码如下：
{: id="20210309181757-7s3ytrg"}

```java
public class Chinese {
    private static String country;
    private String name;
  	private int age;
    private boolean marry;
}
```
{: id="20210309181757-wlzpb2k"}

2. {: id="20210309181757-4ev9qvd"}提供 `getXxx`方法 / `setXxx` 方法，可以访问成员变量，代码如下：
   {: id="20210309181757-1nluo61"}
{: id="20210309181757-161ysin"}

```java
public class Chinese {
  	private static String country;
    private String name;
  	private int age;
    private boolean marry;
    
    public static void setCountry(String c){
        country = c;
    }
    
    public static String getCountry(){
        return country;
    }

	public void setName(String n) {
		name = n;
    }

    public String getName() {
        return name;
	}

    public void setAge(int a) {
        age = a;
    }

    public int getAge() {
        return age;
    }
    
    public void setMarry(boolean m){
        marry = m;
    }
    
    public boolean isMarry(){
        return marry;
    }
}
```
{: id="20210309181757-jccymmn"}

#### 3、如何解决局部变量与成员变量同名问题
{: id="20210309181757-ezz6df4"}

当局部变量与类变量（静态成员变量）同名时，在类变量前面加“类名."；
{: id="20210309181757-i62hkru"}

当局部变量与实例变量（非静态成员变量）同名时，在实例变量前面加“this.”
{: id="20210309181757-3vaxc3p"}

```java
public class Chinese {
  	private static String country;
    private String name;
  	private int age;
    
    public static void setCountry(String country){
        Chinese.country = country;
    }
    
    public static String getCountry(){
        return country;
    }

	public void setName(String name) {
		this.name = name;
    }

    public String getName() {
        return name;
	}

    public void setAge(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }
}
```
{: id="20210309181757-j61g3l7"}

#### 4、 练习
{: id="20210309181757-ymm0x7s"}

（1）定义矩形类Rectangle，
{: id="20210309181757-9cud18c"}

​	声明静态变量sides，初始化为4，表示矩形边长的总数量；
{: id="20210309181757-75luk3r"}

​	声明实例变量长和宽
{: id="20210309181757-7hzse2h"}

​	全部私有化，并提供相应的get/set方法
{: id="20210309181757-97a6nmw"}

（2）在测试类中创建Rectangle对象，并调用相应的方法测试
{: id="20210309181757-oxo9pnj"}

（2）测试类ObjectArrayTest的main中创建一个可以装3个学生对象的数组，并且按照学生成绩排序，显示学生信息
{: id="20210309181757-he82f04"}

### 6.1.3 包（Package）
{: id="20210309181757-ab1wv2u"}

#### 1、包的作用
{: id="20210309181757-2i0gtzs"}

（1）可以避免类重名：有了包之后，类的全名称就变为：包.类名
{: id="20210309181757-t30tjav"}

（2）分类组织管理众多的类
{: id="20210309181757-7elvxr4"}

例如：
{: id="20210309181757-cw1sdlx"}

* {: id="20210309181757-s58m3yx"}java.lang----包含一些Java语言的核心类，如String、Math、Integer、 System和Thread等，提供常用功能
  {: id="20210309181757-4pvs273"}
* {: id="20210309181757-3pyueeh"}java.net----包含执行与网络相关的操作的类和接口。
  {: id="20210309181757-bme4r3t"}
* {: id="20210309181757-uwothzi"}java.io ----包含能提供多种输入/输出功能的类。
  {: id="20210309181757-jp3qtsx"}
* {: id="20210309181757-1rr49lp"}java.util----包含一些实用工具类，如集合框架类、日期时间、数组工具类Arrays，文本扫描仪Scanner，随机值产生工具Random。
  {: id="20210309181757-a2udb2k"}
* {: id="20210309181757-19adu53"}java.text----包含了一些java格式化相关的类
  {: id="20210309181757-dpi9tr0"}
* {: id="20210309181757-61t72kk"}java.sql和javax.sql----包含了java进行JDBC数据库编程的相关类/接口
  {: id="20210309181757-tvzl7ne"}
* {: id="20210309181757-wbyczpa"}java.awt和java.swing----包含了构成抽象窗口工具集（abstract window toolkits）的多个类，这些类被用来构建和管理应用程序的图形用户界面(GUI)。
  {: id="20210309181757-b3pzjkv"}
{: id="20210309181757-judz1k2"}

（3）可以控制某些类型或成员的可见范围
{: id="20210309181757-xkzamfr"}

如果某个类型或者成员的权限修饰缺省的话，那么就仅限于本包使用
{: id="20210309181757-sy4iayx"}

#### 2、声明包的语法格式
{: id="20210309181757-4ti2t0p"}

```java
package 包名;
```
{: id="20210309181757-8trkdma"}

> 注意：
> {: id="20210309181757-j803fvi"}
>
> (1)必须在源文件的代码首行
> {: id="20210309181757-4hyc05d"}
>
> (2)一个源文件只能有一个声明包的语句
> {: id="20210309181757-hduefh8"}
{: id="20210309181757-40rkfps"}

包的命名规范和习惯：
（1）所有单词都小写，每一个单词之间使用.分割
（2）习惯用公司的域名倒置
{: id="20210309181757-nay7mq3"}

例如：com.atguigu.xxx;
{: id="20210309181757-pmh9x45"}

> 建议大家取包名时不要使用“java.xx"包
> {: id="20210309181757-q3l5hmb"}
{: id="20210309181757-qngerix"}

#### 3、如何在命令行编译和运行声明包的Java文件（了解）
{: id="20210309181757-giehrp9"}

编译格式：
{: id="20210309181757-kr6ci7p"}

```
javac -d class文件存放路径 源文件路径名.java
```
{: id="20210309181757-04wpl4r"}

例如：
{: id="20210309181757-fzf363u"}

```java
package com.atguigu.demo;

public class TestPackage {
	public static void main(String[] args) {
		System.out.println("hello package");
	}
}
```
{: id="20210309181757-bwxawnb"}

编译：
{: id="20210309181757-l0bnb0b"}

```java
javac -d . TestPackage.java
```
{: id="20210309181757-rqv1sfn"}

> 其中 . 表示在当前目录生成包目录
> {: id="20210309181757-i4t2j25"}
{: id="20210309181757-jf987gd"}

运行：
{: id="20210309181757-6v3ir1y"}

```java
java com.atguigu.demo.TestPackage
```
{: id="20210309181757-1inzjae"}

> 定位到com目录的外面才能正确找到这个类
> {: id="20210309181757-wmg5v2d"}
>
> 使用类的全名称才能正确运行这个类
> {: id="20210309181757-jjihwsw"}
{: id="20210309181757-dmrppdi"}

![1561887467445](imgs7/1561887467445.png)
{: id="20210309181757-vs2pcou"}

#### 4、如何跨包使用类
{: id="20210309181757-6w4rmjl"}

前提：被使用的类或成员的权限修饰符是>缺省的，即可见的
{: id="20210309181757-skdispo"}

（1）使用类型的全名称
{: id="20210309181757-u0u2pdg"}

例如：java.util.Scanner input = new java.util.Scanner(System.in);
{: id="20210309181757-4t27t0e"}

（2）使用import 语句之后，代码中使用简名称
{: id="20210309181757-xavx4x0"}

import语句告诉编译器到哪里去寻找类。
{: id="20210309181757-o0pltme"}

import语句的语法格式：
{: id="20210309181757-cx6olmd"}

```java
import 包.类名;
import 包.*;
import static 包.类名.静态成员;
```
{: id="20210309181757-dx1whef"}

> 注意：
> {: id="20210309181757-4kmrc9q"}
>
> 使用java.lang包下的类，不需要import语句，就直接可以使用简名称
> {: id="20210309181757-zif90l1"}
>
> import语句必须在package下面，class的上面
> {: id="20210309181757-tzmtvyy"}
>
> 当使用两个不同包的同名类时，例如：java.util.Date和java.sql.Date。一个使用全名称，一个使用简名称
> {: id="20210309181757-z31ae4j"}
{: id="20210309181757-uj6dudy"}

示例代码：
{: id="20210309181757-ez5nxha"}

```java
package com.atguigu.bean;

public class Student {
	// 成员变量
	private String name;
	private int age;

	// 构造方法
	public Student() {
	}

	public Student(String name, int age) {
		this.name = name;
		this.age = age;
	}

	// 成员方法
	public void setName(String name) {
		this.name = name;
	}

	public String getName() {
		return name;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public int getAge() {
		return age;
	}
}
```
{: id="20210309181757-cauepgz"}

```java
package com.atguigu.test;

import java.util.Scanner;
import java.util.Date;
import com.atguigu.bean.Student;

public class Test{
    public static void main(String[] args){
        Scanner input = new Scanner(System.in);
        Student stu = new Student();
        String str = "hello";
        
        Date now = new Date();
        java.sql.Date d = new java.sql.Date(346724566);        
    }
}
```
{: id="20210309181757-ajf6kf4"}

## 6.2 构造器（Constructor)
{: id="20210309181757-8fphx6u"}

我们发现我们new完对象时，所有成员变量都是默认值，如果我们需要赋别的值，需要挨个为它们再赋值，太麻烦了。我们能不能在new对象时，直接为当前对象的某个或所有成员变量直接赋值呢。
{: id="20210309181757-fkztvt6"}

可以，Java给我们提供了构造器。
{: id="20210309181757-h5213o1"}

#### 1、构造器的作用
{: id="20210309181757-h04io19"}

在创建对象的时候为实例变量赋初始值。
{: id="20210309181757-xgan09y"}

> **注意：构造器只为实例变量初始化，不为静态类变量初始化**
> {: id="20210309181757-nh5rdaj"}
{: id="20210309181757-k3l81k1"}

#### 2、构造器的语法格式
{: id="20210309181757-tr3l7ka"}

构造器又称为构造方法，那是因为它长的很像方法。但是和方法还有有所区别的。
{: id="20210309181757-rl6smev"}

```java
【修饰符】 构造器名(){
    // 实例初始化代码
}
【修饰符】 构造器名(参数列表){
	// 实例初始化代码
}
```
{: id="20210309181757-lxh062g"}

代码如下：
{: id="20210309181757-bex2btf"}

```java
public class Student {
	private String name;
	private int age;
	// 无参构造
  	public Student() {} 
 	// 有参构造
  	public Student(String name,int age) {
		this.name = name;
    	this.age = age; 
	}
  	
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
}
```
{: id="20210309181757-20u8kus"}

注意事项：
{: id="20210309181757-q1qmtpj"}

1. {: id="20210309181757-0mu2cyk"}构造器名必须与它所在的类名必须相同。
   {: id="20210309181757-ilet0d5"}
2. {: id="20210309181757-efld7cq"}它没有返回值，所以不需要返回值类型，甚至不需要void
   {: id="20210309181757-cktqu25"}
3. {: id="20210309181757-v6vcsej"}如果你不提供构造器，系统会给出无参数构造器，并且该构造器的修饰符默认与类的修饰符相同
   {: id="20210309181757-ozuaut1"}
4. {: id="20210309181757-1mquzab"}如果你提供了构造器，系统将不再提供无参数构造器，除非你自己定义。
   {: id="20210309181757-x0lqkts"}
5. {: id="20210309181757-bedkx0w"}构造器是可以重载的，既可以定义参数，也可以不定义参数。
   {: id="20210309181757-d3iwqzh"}
6. {: id="20210309181757-cog15kp"}构造器的修饰符只能是权限修饰符，不能被其他任何修饰
   {: id="20210309181757-wr4i3y8"}
{: id="20210309181757-y1mwfv8"}

#### 3、练习
{: id="20210309181757-2izr6qa"}

（1）声明一个员工类，
{: id="20210309181757-s6tzg1x"}

* {: id="20210309181757-1gq6yix"}包含属性：编号、姓名、薪资、性别，要求属性私有化，提供get/set，
  {: id="20210309181757-eiy30oe"}
* {: id="20210309181757-34bmf96"}提供无参构造器和有参构造器
  {: id="20210309181757-lq1ga5q"}
* {: id="20210309181757-40dp4ti"}提供getInfo()
  {: id="20210309181757-uj1hsbs"}
{: id="20210309181757-vf4ysy7"}

（2）在测试类的main中分别用无参构造和有参构造创建员工类对象，调用getInfo
{: id="20210309181757-vec1qxm"}

```java
public class TestEmployee {
	public static void main(String[] args){
		//分别用无参构造和有参构造创建对象，调用getInfo
		Employee e1 = new Employee();
		System.out.println(e1.getInfo());
		
		Employee e2 = new Employee("1001","张三",110000,'男');
		System.out.println(e2.getInfo());
		
		e2.setSalary(120000);
		System.out.println(e2.getInfo());
		
		System.out.println("e1薪资：" + e1.getSalary());
	}
}
class Employee{
	private String id;
	private String name;
	private double salary;
	private char gender;
	
	//提供无参构造器和有参构造器
	public Employee(){
		
	}
	public Employee(String id, String name){
		this.id = id;
		this.name = name;
	}
	public Employee(String id, String name, double salary, char gender){
		this.id = id;
		this.name = name;
		this.salary = salary;
		this.gender = gender;
	}
	
	public String getId() {
		return id;
	}
	public void setId(String id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public double getSalary() {
		return salary;
	}
	public void setSalary(double salary) {
		this.salary = salary;
	}
	public char getGender() {
		return gender;
	}
	public void setGender(char gender) {
		this.gender = gender;
	}
	
	//提供getInfo()
	public String getInfo(){
		return "编号：" + id + "，姓名：" + name + "，薪资：" + salary + "，性别：" +gender;
	}
}
```
{: id="20210309181757-nsz5ccx"}

## 6.3 标准JavaBean
{: id="20210309181757-5d2yw1i"}

`JavaBean` 是 Java语言编写类的一种标准规范。符合`JavaBean` 的类，要求：
{: id="20210309181757-7wmiati"}

（1）类必须是具体的和公共的，
{: id="20210309181757-r56mcuw"}

（2）并且具有无参数的构造方法，
{: id="20210309181757-15rmv5m"}

（3）成员变量私有化，并提供用来操作成员变量的`set` 和`get` 方法。
{: id="20210309181757-urlgv80"}

```java
public class ClassName{
  //成员变量
    
  //构造方法
  	//无参构造方法【必须】
  	//有参构造方法【建议】
  	
  //getXxx()
  //setXxx()
  //其他成员方法
}
```
{: id="20210309181757-p1pplj6"}

编写符合`JavaBean` 规范的类，以学生类为例，标准代码如下：
{: id="20210309181757-41qa5gl"}

```java
public class Student {
	// 成员变量
	private String name;
	private int age;

	// 构造方法
	public Student() {
	}

	public Student(String name, int age) {
		this.name = name;
		this.age = age;
	}

	// get/set成员方法
	public void setName(String name) {
		this.name = name;
	}

	public String getName() {
		return name;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public int getAge() {
		return age;
	}
    
    //其他成员方法列表
    public String getInfo(){
        return "姓名：" + name + "，年龄：" + age;
    }
}
```
{: id="20210309181757-61412dk"}

测试类，代码如下：
{: id="20210309181757-ipcxqcq"}

```java
public class TestStudent {
	public static void main(String[] args) {
		// 无参构造使用
		Student s = new Student();
		s.setName("柳岩");
		s.setAge(18);
		System.out.println(s.getName() + "---" + s.getAge());
        System.out.println(s.getInfo());

		// 带参构造使用
		Student s2 = new Student("赵丽颖", 18);
		System.out.println(s2.getName() + "---" + s2.getAge());
        System.out.println(s2.getInfo());
	}
}
```
{: id="20210309181757-d83ryys"}


{: id="20210309181757-fncjro5" type="doc"}
