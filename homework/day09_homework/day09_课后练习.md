# day09_课后练习
{: id="20210309203838-sd3u12q"}

# 代码阅读分析题
{: id="20210309203838-vw45v39"}

## 第1题
{: id="20210309203838-shybeq1"}

考核知识点：属性与多态无关
{: id="20210309203838-41ivat8"}

```java
package com.atguigu.test01;

public class Test01 {
	public static void main(String[] args) {
		A a = new B();
		System.out.println(a.num);
		System.out.println(((B)a).num);
		System.out.println(((A)((B)a)).num);
		System.out.println("-------------------");
		B b = new B();
		System.out.println(b.num);
		System.out.println(((A)b).num);
		System.out.println(((B)((A)b)).num);
	}
}
class A{
	int num = 1;
}
class B extends A{
	int num = 2;
}
```
{: id="20210309203838-8qyzeyr"}

## 第2题
{: id="20210309203838-n31qmpb"}

考核知识点：实例初始化方法，属性与多态无关
{: id="20210309203838-7d9zj2k"}

```java
package com.atguigu.test02;

public class Test02 {
	public static void main(String[] args) {
		Father f = new Son();
		System.out.println(f.x);
	}
}
class Father{
	int x = 10;
	public Father(){
		this.print();
		x = 20;
	}
	public void print(){
		System.out.println("Father.x = " + x);
	}
}
class Son extends Father{
	int x = 30;
	public Son(){
		this.print();
		x = 40;
	}
	public void print(){
		System.out.println("Son.x = " + x);
	}
}
```
{: id="20210309203838-0levwui"}

## 第3题
{: id="20210309203838-snxw4dq"}

考核知识点：多态，重写，实例初始化过程
{: id="20210309203838-ysk9xvu"}

```java
package com.atguigu.test03;

public class Test03 {
	public static void main(String[] args) {
		Base b1 = new Base();
		Base b2 = new Sub();
	}
}

class Base {
	Base() {
		method(100);
	}

	public void method(int i) {
		System.out.println("base : " + i);
	}
}

class Sub extends Base {
	Sub() {
		super.method(70);
	}

	public void method(int j) {
		System.out.println("sub : " + j);
	}
}
```
{: id="20210309203838-vr0qpgf"}

## 第4题
{: id="20210309203838-dbcszf8"}

考核知识点：多态、重载、重写
{: id="20210309203838-gp7fpdo"}

```java
public class Test04 {
	public static void main(String[] args) {
		A a1 = new A();
		A a2 = new B();
		B b = new B();
		C c = new C();
		D d = new D();
		System.out.println("(1)" + a1.show(b));
		System.out.println("(2)" + a2.show(d));
		System.out.println("(3)" + b.show(c));
		System.out.println("(4)" + b.show(d));
	}
}
class A{
	public String show(D obj){
		return ("A and D");
	}
	public String show(A obj){
		return "A and A";
	}
}
class B extends A{
	public String show(B obj){
		return "B and B";
	}
	public String show(A obj){
		return "B and A";
	}
}
class C extends B{
	
}
class D extends B{
	
}
```
{: id="20210309203838-v7gghis"}

## 第5题
{: id="20210309203838-6lcg0n4"}

考核知识点：多态、重载、重写
{: id="20210309203838-jak77q5"}

```java
public class Test05 {
	public static void main(String[] args) {
		A a1 = new A();
		A a2 = new B();
		B b = new B();
		C c = new C();
		D d = new D();
		System.out.println("(1)" + a1.show(b));
		System.out.println("(2)" + a2.show(d));
		System.out.println("(3)" + b.show(c));
		System.out.println("(4)" + b.show(d));
	}
}

class A {
	public String show(C obj) {
		return ("A and C");
	}

	public String show(A obj) {
		return "A and A";
	}
}

class B extends A {
	public String show(B obj) {
		return "B and B";
	}

	public String show(A obj) {
		return "B and A";
	}
}

class C extends B {

}

class D extends B {

}
```
{: id="20210309203838-fr154f7"}

## 第6题
{: id="20210309203838-tjet5l9"}

考核知识点：属性与多态无关
{: id="20210309203838-4smoeq7"}

```java
public class Test06 {
	public static void main(String[] args) {
		Base b = new Sub();
		System.out.println(b.x);
	}
}
class Base{
	int x = 1;
}
class Sub extends Base{
	int x = 2;
}
```
{: id="20210309203838-akpfx1d"}

## 第7题
{: id="20210309203838-pgzd14x"}

考核知识点：权限修饰符
{: id="20210309203838-lex2abg"}

如下代码是否可以编译通过，如果能，结果是什么，如果不能，为什么？
{: id="20210309203838-ojccrrp"}

```java
public class Father{
	private String name = "atguigu";
	int age = 0;
}
public class Child extends Father{
	public String grade;
	
	public static void main(String[] args){
		Father f = new Child();
		System.out.println(f.name);
	}
}
```
{: id="20210309203838-ce54h80"}

## 第8题
{: id="20210309203838-9tq4eh9"}

考核知识点：继承，super，static
{: id="20210309203838-1hezhmt"}

如下代码是否可以编译通过，如果能，结果是什么，如果不能，为什么？
{: id="20210309203838-x0d0q02"}

```java
public class Person{
	public Person(){
		System.out.println("this is a Person.");
	}
}
public class Teacher extends Person{
	private String name = "tom";
	public Teacher(){
		System.out.println("this is a teacher.");
		super();
	}
	public static void main(String[] args){
		Teacher tea = new Teacher();
		System.out.println(this.name);
	}
}
```
{: id="20210309203838-siiipdj"}

# 代码编程题
{: id="20210309203838-hkb5rgk"}

## 第9题
{: id="20210309203838-lk0q4an"}

* {: id="20210309203838-94gp323"}知识点：抽象类
  {: id="20210309203838-j9ntfug"}
* {: id="20210309203838-qrhum8t"}语法点：继承，抽象类
  {: id="20210309203838-8gwiiqp"}
* {: id="20210309203838-u502i67"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-1bhjulg"}
{: id="20210309203838-w3s909f"}

![1559049252810](imgs/1559049252810.png)
{: id="20210309203838-toluqm9"}

编写步骤：
{: id="20210309203838-wptovo2"}

1. {: id="20210309203838-hlvqheo"}定义抽象类A，抽象类B继承A，普通类C继承B
   {: id="20210309203838-ksw806s"}
2. {: id="20210309203838-n8txz8i"}A类中，定义成员变量numa，赋值为10，抽象showA方法。
   {: id="20210309203838-2cgmpmj"}
3. {: id="20210309203838-jztl45v"}B类中，定义成员变量numb，赋值为20，抽象showB方法。
   {: id="20210309203838-ysplt9s"}
4. {: id="20210309203838-qxtaw9n"}C类中，定义成员变量numc，赋值为30，重写showA方法，打印numa，重写showB方法，打印numb，定义showC方法，打印numc。
   {: id="20210309203838-048of3k"}
5. {: id="20210309203838-ejfuyhk"}测试类Test09中，创建C对象，调用showA方法，showB方法，showC方法。
   {: id="20210309203838-ede75y6"}
{: id="20210309203838-7t0nm7t"}

## 第10题
{: id="20210309203838-o5jb3v1"}

知识点：抽象类
{: id="20210309203838-t3qfbkj"}

案例：
{: id="20210309203838-s4qscz5"}

​	1、声明抽象父类Person，包含抽象方法public abstract void pee();
{: id="20210309203838-ctbhxcc"}

​	2、声明子类Woman，重写抽象方法，打印坐着尿
{: id="20210309203838-vs7q8ei"}

​	3、声明子类Man，重写抽象方法，打印站着上尿
{: id="20210309203838-bsvei72"}

​	4、声明测试类Test10，创建Person数组，存放Woman和Man对象，并遍历数组，调用pee()方法
{: id="20210309203838-t87y0ok"}

## 第11题
{: id="20210309203838-ies9pea"}

知识点：抽象类
{: id="20210309203838-daj5lns"}

案例：
{: id="20210309203838-t9gmuun"}

​	1、声明抽象父类Person，包含抽象方法public abstract void eat();
{: id="20210309203838-156m4r7"}

​	2、声明子类中国人Chinese，重写抽象方法，打印用筷子吃饭
{: id="20210309203838-n2cyklq"}

​	3、声明子类美国人American，重写抽象方法，打印用刀叉吃饭
{: id="20210309203838-ery5ors"}

​	4、声明子类印度人Indian，重写抽象方法，打印用手抓饭
{: id="20210309203838-sfoo5cb"}

​	5、声明测试类Test11，创建Person数组，存储各国人对象，并遍历数组，调用eat()方法
{: id="20210309203838-m0fd6pa"}

## 第12题
{: id="20210309203838-v6gd1f6"}

知识点：Object类的方法
{: id="20210309203838-covvxs5"}

案例：
{: id="20210309203838-cxkrpdq"}

​	1、声明三角形类，包含a,b,c三边
{: id="20210309203838-eo32a62"}

​	（1）属性私有化，提供无参，有参构造，提供get/set
{: id="20210309203838-42l3p3p"}

​	（2）重写：toString()
{: id="20210309203838-7o2snxp"}

​	（3）重写：hashCode和equals方法
{: id="20210309203838-jpr0afw"}

​	（4）编写  public double getArea()：求面积方法
{: id="20210309203838-uu533i2"}

​	（5）编写 public double getPiremeter()：求周长方法
{: id="20210309203838-khml02a"}

​	2、声明测试类Test12，在测试类中创建两个三角形对象，调用以上方法进行测试
{: id="20210309203838-3lenxvc"}

## 第13题
{: id="20210309203838-ke506y0"}

案例：
{: id="20210309203838-2bsqzbb"}

​	1、在com.atguigu.test13包中声明员工类、程序员类、设计师类、架构师类，
{: id="20210309203838-lkud64e"}

![1558933215448](imgs/1558933215448.png)
{: id="20210309203838-7cfhtxx"}

* {: id="20210309203838-176acnc"}员工类属性：编号、姓名、年龄、薪资
  {: id="20210309203838-rhd080d"}
* {: id="20210309203838-rs8phdj"}程序员类属性：编程语言，默认都是"java"
  {: id="20210309203838-tc15pl4"}
* {: id="20210309203838-d8w1gjo"}设计师类属性：奖金
  {: id="20210309203838-i4nwplk"}
* {: id="20210309203838-g6lece0"}架构师类属性：持有股票数量
  {: id="20210309203838-eetm58p"}
  要求：属性私有化，无参有参构造，get/set，getInfo方法（考虑重写）
  {: id="20210309203838-r1kkxd3"}
  2、在com.atguigu.test13包中声明Test13测试类
  {: id="20210309203838-4937jgi"}
  （1）在main中有一些常量和一个二维数组
  {: id="20210309203838-ywvz2zi"}
  ```java
  final int EMPLOYEE = 10;//表示普通员工
  final int PROGRAMMER = 11;//表示程序员
  final int DESIGNER = 12;//表示设计师
  final int ARCHITECT = 13;//表示架构师

  String[][] EMPLOYEES = {
          {"10", "1", "段誉", "22", "3000"},
          {"13", "2", "令狐冲", "32", "18000", "15000", "2000"},
          {"11", "3", "任我行", "23", "7000"},
          {"11", "4", "张三丰", "24", "7300"},
          {"12", "5", "周芷若", "28", "10000", "5000"},
          {"11", "6", "赵敏", "22", "6800"},
          {"12", "7", "张无忌", "29", "10800","5200"},
          {"13", "8", "韦小宝", "30", "19800", "15000", "2500"},
          {"12", "9", "杨过", "26", "9800", "5500"},
          {"11", "10", "小龙女", "21", "6600"},
          {"11", "11", "郭靖", "25", "7100"},
          {"12", "12", "黄蓉", "27", "9600", "4800"}
      };
  ```
  {: id="20210309203838-0v3jhko"}
  （2）创建一个员工数组
  {: id="20210309203838-xt17yiv"}
  （3）根据以上数据，初始化员工数组
  {: id="20210309203838-a6nit2y"}
  提示：把字符串转为int和double类型的值，可以使用如下方式：
  {: id="20210309203838-6jt8thh"}
  ```java
  String idStr = "1";
  int id = Integer.parseInt(idStr);

  String salaryStr = "7300";
  double salary = Double.parseDouble(salaryStr);
  ```
  {: id="20210309203838-qjeb2ik"}
  （4）遍历数组，使用如下格式
  {: id="20210309203838-eky7szo"}
  ```
  编号	姓名	年龄	薪资	语言	奖金	股票
  .....
  ```
  {: id="20210309203838-6xquzi0"}
{: id="20210309203838-yph2j8f"}

## 第14题
{: id="20210309203838-9gvbop6"}

案例：
{: id="20210309203838-mszrwq7"}

​	1、在com.atguigu.test14包中声明图形Graphic、圆Circle、矩形Rectangle类、三角形Triangle类
{: id="20210309203838-cqui5xi"}

​	2、图形Graphic类中有：
{: id="20210309203838-1bolsyj"}

​		①public double getArea()方法：返回面积
{: id="20210309203838-2vgltsj"}

​		②public double getPerimeter()方法：返回周长
{: id="20210309203838-6vqb150"}

​		③public String getInfo()方法：返回图形信息
{: id="20210309203838-fzpe1iu"}

​	3、圆类和矩形类重写这两个方法
{: id="20210309203838-dxoyfxj"}

​	4、在com.atguigu.test14包中声明测试类Test14_1
{: id="20210309203838-w0qotv4"}

​	(1)请设计一个方法，可以用于比较两个图形的面积是否相等
{: id="20210309203838-a2qhmt8"}

​	(2)请设计一个方法，可以用于找出两个图形中面积大的那个
{: id="20210309203838-56ky10n"}

​	(3)public static void main(String[] args){}
{: id="20210309203838-i4a13v7"}

​	在主方法中，创建1个圆、1个矩形、1个三角形对象，并分别调用(1)、(2)方法进行测试。
{: id="20210309203838-vgqxokl"}

​	5、在com.atguigu.test14包中测试类Test14_2
{: id="20210309203838-sujl47g"}

​	(1)请设计一个方法，可以用于遍历一个图形数组
{: id="20210309203838-bpts8fg"}

​	(2)请设计一个方法，可以用于给一个图形数组进行按照面积从小到大排序
{: id="20210309203838-pa96ynq"}

​	(3)public static void main(String[] args){}
{: id="20210309203838-a3pgmlt"}

​	在主方法中，创建1个圆、1个矩形、1个三角形对象，放到数组中，遍历显示，然后排序后再遍历显示。
{: id="20210309203838-mp08gir"}

## 第15题
{: id="20210309203838-40xx0c9"}

案例：
{: id="20210309203838-wfz3vc3"}

​	1、在com.atguigu.test15包中声明人Person、男人Man、女人Woman类
{: id="20210309203838-0j8sqdn"}

​	（1）在Person类中，包含
{: id="20210309203838-8v00nng"}

​		①public void eat()：打印吃饭
{: id="20210309203838-odbfdyo"}

​		②public void toilet()：打印上洗手间
{: id="20210309203838-pfceog1"}

​	（2）在Man类中，包含
{: id="20210309203838-ajpgaoz"}

​		①重写上面的方法
{: id="20210309203838-ori7or0"}

​		②增加  public void smoke()：打印抽烟
{: id="20210309203838-y2px88a"}

​	（3）在Woman类中，包含
{: id="20210309203838-ma42ik8"}

​		①重写上面的方法
{: id="20210309203838-3385ugf"}

​		②增加 public void makeup()：打印化妆
{: id="20210309203838-swi6opu"}

​	2、在com.atguigu.test15包中声明测试类Test15
{: id="20210309203838-upyndib"}

​	（1）public static void meeting(Person...  ps)
{: id="20210309203838-gwle79i"}

​		在该方法中，每一个人先吃饭，然后上洗手间，然后如果是男人，随后抽根烟，如果是女人，随后化个妆
{: id="20210309203838-efp3nyu"}

​	（2）public static void main(String[] args)
{: id="20210309203838-02a4uaw"}

​		在主方法中，创建多个男人和女人对象，并调用meeting()方法进行测试
{: id="20210309203838-hw8a0ls"}

# 关键字整理
{: id="20210309203838-ijpk94x"}

整理目前学过的关键字
{: id="20210309203838-ad0qag3"}


{: id="20210309203838-yc8yu6g" type="doc"}
