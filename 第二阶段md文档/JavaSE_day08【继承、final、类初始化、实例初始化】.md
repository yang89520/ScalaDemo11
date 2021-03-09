# JavaSE_day08【继承、初始化】
{: id="20210309181757-pqf4pen"}

## 今日内容
{: id="20210309181757-tzm0nsa"}

- {: id="20210309181757-edcz4pk"}继承
  {: id="20210309181757-76jddd0"}
- {: id="20210309181757-1bpz1mm"}方法重写
  {: id="20210309181757-1lhohfa"}
- {: id="20210309181757-f4gl6x2"}this关键字
  {: id="20210309181757-rrrrjbr"}
- {: id="20210309181757-p42yto2"}super关键字
  {: id="20210309181757-c355d7i"}
- {: id="20210309181757-6c1c9i3"}final修饰符
  {: id="20210309181757-vlmmp3n"}
- {: id="20210309181757-sljd1d9"}类初始化
  {: id="20210309181757-wuannep"}
- {: id="20210309181757-pjedj26"}实例初始化
  {: id="20210309181757-e0y4i3z"}
{: id="20210309181757-9o6d1aj"}

## 学习目标
{: id="20210309181757-tihqn7p"}

- {: id="20210309181757-5kinctz"}[ ] 能够写出类的继承格式
  {: id="20210309181757-cc5agox"}
- {: id="20210309181757-z4qfhjz"}[ ] 能够说出继承的特点
  {: id="20210309181757-scwctvj"}
- {: id="20210309181757-fai2vgq"}[ ] 能够说出方法重写的概念以及和重载的区别
  {: id="20210309181757-h3j71by"}
- {: id="20210309181757-i7jlkj9"}[ ] 能够使用this关键字解决问题
  {: id="20210309181757-n70qz96"}
- {: id="20210309181757-p5q9mps"}[ ] 能够使用super关键字解决问题
  {: id="20210309181757-m4n1ws4"}
- {: id="20210309181757-jmgdl3x"}[ ] 掌握final的使用
  {: id="20210309181757-ai5ld4s"}
- {: id="20210309181757-8rvlqrc"}[ ] 能够分析类初始化过程（为面试服务）
  {: id="20210309181757-qgy0dea"}
- {: id="20210309181757-fnvdito"}[ ] 能够分析实例初始化过程（为面试服务）
  {: id="20210309181757-0867f9w"}
{: id="20210309181757-8zeykml"}

# 第六章 面向对象基础--中（续）
{: id="20210309181757-j1wdapu"}

## 6.4 继承
{: id="20210309181757-w0c2ea0"}

### 6.4.1 继承的概述
{: id="20210309181757-eum7ze6"}

#### 生活中的继承
{: id="20210309181757-snqrd5l"}

* {: id="20210309181757-d8mo9v3"}财产：富二代
  {: id="20210309181757-20xzbzi"}
* {: id="20210309181757-zawodx0"}样貌：如图所示：
  {: id="20210309181757-qvbhtnz"}
  ![](imgs8\继承1.jpg)
  {: id="20210309181757-mlic3sj"}
  ![](imgs8\继承2.jpg)
  {: id="20210309181757-o4y06ah"}
  ![](imgs8\继承3.jpg)
  {: id="20210309181757-51wpg6h"}
* {: id="20210309181757-kpz2ud0"}才华：如图所示：
  {: id="20210309181757-lnnwh5f"}
  ![](imgs8\继承4.jpg)
  {: id="20210309181757-g08p3by"}
{: id="20210309181757-0qrlfw6"}

#### 继承的由来
{: id="20210309181757-wcn3xtm"}

如图所示：
{: id="20210309181757-65833nj"}

![](imgs8/猫狗继承1.jpg)
{: id="20210309181757-f0dqb8x"}

多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，那么多个类中无需再定义这些属性和行为，只需要和抽取出来的类构成某种关系。如图所示：
{: id="20210309181757-1p6ql28"}

![](imgs8\猫狗继承2.jpg)
{: id="20210309181757-4lw7wv0"}

其中，多个类可以称为**子类**，也叫**派生类**；多个类抽取出来的这个类称为**父类**、**超类（superclass）**或者**基类**。
{: id="20210309181757-6wzq9h0"}

继承描述的是事物之间的所属关系，这种关系是：`is-a` 的关系。例如，图中猫属于动物，狗也属于动物。可见，父类更通用，子类更具体。我们通过继承，可以使多种事物之间形成一种关系体系。
{: id="20210309181757-xd7kth3"}

#### 继承的好处
{: id="20210309181757-8hkaafe"}

* {: id="20210309181757-drb93nu"}提高**代码的复用性**。
  {: id="20210309181757-dzkai9z"}
* {: id="20210309181757-o2usv5v"}提高**代码的扩展性**。
  {: id="20210309181757-khp2v8z"}
* {: id="20210309181757-hio6xwp"}类与类之间产生了关系，是学习**多态的前提**。
  {: id="20210309181757-d6zl8j0"}
{: id="20210309181757-tlp92oo"}

### 6.4.2 继承的格式
{: id="20210309181757-lppzala"}

通过 `extends` 关键字，可以声明一个子类继承另外一个父类，定义格式如下：
{: id="20210309181757-9asi068"}

```java
【修饰符】 class 父类 {
	...
}

【修饰符】 class 子类 extends 父类 {
	...
}

```
{: id="20210309181757-ogctbk1"}

继承演示，代码如下：
{: id="20210309181757-qdnn1dd"}

```java
/*
 * 定义动物类Animal，做为父类
 */
class Animal {
    // 定义name属性
	String name; 
    // 定义age属性
    int age;
	// 定义动物的吃东西方法
	public void eat() {
		System.out.println(age + "岁的" + name + "在吃东西");
	}
}

/*
 * 定义猫类Cat 继承 动物类Animal
 */
class Cat extends Animal {
	// 定义一个猫抓老鼠的方法catchMouse
	public void catchMouse() {
		System.out.println("抓老鼠");
	}
}

/*
 * 定义测试类
 */
public class ExtendDemo01 {
	public static void main(String[] args) {
        // 创建一个猫类对象
		Cat cat = new Cat()；
      
        // 为该猫类对象的name属性进行赋值
		cat.name = "Tom";
      
      	// 为该猫类对象的age属性进行赋值
		cat.age = 2;
        
        // 调用该猫的catchMouse()方法
		cat.catchMouse();
		
      	// 调用该猫继承来的eat()方法
      	cat.eat();
	}
}

演示结果：
抓老鼠
2岁的Tom在吃东西
```
{: id="20210309181757-1aqh05d"}

### 6.4.3 继承的特点一：成员变量
{: id="20210309181757-ldio6fh"}

#### 1、父类成员变量私有化（private）
{: id="20210309181757-33fj2o2"}

* {: id="20210309181757-nty244b"}父类中的成员，无论是公有(public)还是私有(private)，均会被子类继承。
  {: id="20210309181757-kjt12i9"}
* {: id="20210309181757-dsnqdjr"}子类虽会继承父类私有(private)的成员，但子类不能对继承的私有成员直接进行访问，可通过继承的get/set方法进行访问。如图所示：
  {: id="20210309181757-6hjknun"}
{: id="20210309181757-a6wiffs"}

![](imgs8\继承私有成员1.jpg)
{: id="20210309181757-m17j9h0"}

代码如下：
{: id="20210309181757-aslrmcz"}

```java
/*
 * 定义动物类Animal，做为父类
 */
class Animal {
    // 定义name属性
	private String name; 
    // 定义age属性
    public int age;
	// 定义动物的吃东西方法
	public void eat() {
		System.out.println(age + "岁的" + name + "在吃东西");
	}
}

/*
 * 定义猫类Cat 继承 动物类Animal
 */
class Cat extends Animal {
	// 定义一个猫抓老鼠的方法catchMouse
	public void catchMouse() {
		System.out.println("抓老鼠");
	}
}

/*
 * 定义测试类
 */
public class ExtendDemo01 {
	public static void main(String[] args) {
        // 创建一个猫类对象
		Cat cat = new Cat()；
      
        // 为该猫类对象的name属性进行赋值
		//cat.name = "Tom";// 编译报错
      
      	// 为该猫类对象的age属性进行赋值
		cat.age = 2;
        
        // 调用该猫的catchMouse()方法
		cat.catchMouse();
		
      	// 调用该猫继承来的eat()方法
      	cat.eat();
	}
}
```
{: id="20210309181757-0fsyrtd"}

如图所示：
{: id="20210309181757-nyto8s7"}

eclipse中Debug查看对象成员变量值的情况截图如下：
{: id="20210309181757-bl8pjfc"}

![](imgs8\继承私有成员2.jpg)
{: id="20210309181757-nrdt30u"}

idea中Debug查看对象成员变量值的情况截图如下：
{: id="20210309181757-dr9fqkz"}

![1576579518956](imgs8/1576579518956.png)
{: id="20210309181757-9t6e01v"}

#### 2、父子类成员变量重名
{: id="20210309181757-tsl4qmx"}

我们说父类的所有成员变量都会继承到子类中，那么如果子类出现与父类同名的成员变量会怎么样呢？
{: id="20210309181757-0cnt2vy"}

父类代码：
{: id="20210309181757-3303ikf"}

```java
public class Father {
	public int i=1;
	private int j=1;
	public int k=1;
	public int getJ() {
		return j;
	}
	public void setJ(int j) {
		this.j = j;
	}
}
```
{: id="20210309181757-t7nixq0"}

子类代码：
{: id="20210309181757-f9gp653"}

```java
public class Son extends Father{
	public int i=2;
	private int j=2;
	public int m=2;
}	
```
{: id="20210309181757-bna2k9e"}

现在想要在子类Son中声明一个test()方法，并打印这些所有变量的值，该如何实现？
{: id="20210309181757-xcb3q87"}

```java
public class Son extends Father{
	public int i=2;
	private int j=2;
	public int m=2;
	
	public void test() {
		System.out.println("父类继承的i：" + super.i);
		System.out.println("子类的i：" +i);
//		System.out.println(super.j);
		System.out.println("父类继承的j：" +getJ());
		System.out.println("子类的j：" +j);
		System.out.println("父类继承的k：" +k);
		System.out.println("子类的m：" +m);
	}	
}	
```
{: id="20210309181757-6m1k2lh"}

结论：
{: id="20210309181757-egnyo2x"}

（1）当父类的成员变量私有化时，在子类中是无法直接访问的，所以是否重名不影响，如果想要访问父类的私有成员变量，只能通过父类的get/set方法访问；
{: id="20210309181757-au29eke"}

（2）当父类的成员变量非私有时，在子类中可以直接访问，所以如果有重名时，就需要加“super."进行区别。
{: id="20210309181757-g7okz7y"}

使用格式：
{: id="20210309181757-10enlf6"}

```java
super.父类成员变量名
```
{: id="20210309181757-cna4zxj"}

以上test()调用结果：
{: id="20210309181757-z77gt3r"}

```java
public class TestSon{
	public static void main(String[] args){
		Son s = new Son();
		s.test();
	}
}
```
{: id="20210309181757-4t8szqg"}

```java
父类继承的i：1
子类的i：2
父类继承的j：1
子类的j：2
父类继承的k：1
子类的m：2
```
{: id="20210309181757-narcnmc"}

eclipse中Debug查看对象的成员变量的值截图如下：
{: id="20210309181757-e0d209p"}

![1572422069292](imgs8/1572422069292.png)
{: id="20210309181757-swplqoc"}

idea中Debug查看对象的成员变量的值截图如下：
{: id="20210309181757-nphjfg2"}

![1576579731205](imgs8/1576579731205.png)
{: id="20210309181757-z7swnc6"}

> 说明：虽然我们可以区分父子类的重名成员变量，但是实际开发中，我们不建议这么干。
> {: id="20210309181757-cqfjjk5"}
{: id="20210309181757-o8gp3aw"}

### 6.4.4 继承的特点二：成员方法
{: id="20210309181757-olza7fn"}

我们说父类的所有方法子类都会继承，但是当某个方法被继承到子类之后，子类觉得父类原来的实现不适合于子类，该怎么办呢？我们可以进行方法重写 (Override)
{: id="20210309181757-ji9djuo"}

#### 1、方法重写
{: id="20210309181757-0e94r9a"}

比如新的手机增加来电显示头像的功能，代码如下：
{: id="20210309181757-6l52e5j"}

```java
class Phone {
	public void sendMessage(){
		System.out.println("发短信");
	}
	public void call(){
		System.out.println("打电话");
	}
	public void showNum(){
		System.out.println("来电显示号码");
	}
}

//智能手机类
class NewPhone extends Phone {
	
	//重写父类的来电显示号码功能，并增加自己的显示姓名和图片功能
	public void showNum(){
		//调用父类已经存在的功能使用super
		super.showNum();
		//增加自己特有显示姓名和图片功能
		System.out.println("显示来电姓名");
		System.out.println("显示头像");
	}
}

public class ExtendsDemo06 {
	public static void main(String[] args) {
      	// 创建子类对象
      	NewPhone np = new NewPhone()；
        
        // 调用父类继承而来的方法
        np.call();
      
      	// 调用子类重写的方法
      	np.showNum();

	}
}

```
{: id="20210309181757-ekb76fb"}

> 小贴士：这里重写时，用到super.父类成员方法，表示调用父类的成员方法。
> {: id="20210309181757-jpfll7k"}
{: id="20210309181757-0mmjrmf"}

注意事项：
{: id="20210309181757-7e162zq"}

1.@Override：写在方法上面，用来检测是不是有效的正确覆盖重写。这个注解就算不写，只要满足要求，也是正确的方法覆盖重写。建议保留
{: id="20210309181757-oe8mlch"}

2.必须保证父子类之间方法的名称相同，参数列表也相同。
3.子类方法的返回值类型必须【小于等于】父类方法的返回值类型（小于其实就是是它的子类，例如：Student < Person）。
{: id="20210309181757-hcawx3s"}

> 注意：如果返回值类型是基本数据类型和void，那么必须是相同
> {: id="20210309181757-196j6dk"}
{: id="20210309181757-nkhk0fk"}

4.子类方法的权限必须【大于等于】父类方法的权限修饰符。
小扩展提示：public > protected > 缺省 > private
{: id="20210309181757-rtixebw"}

5.几种特殊的方法不能被重写
{: id="20210309181757-ji1nzei"}

* {: id="20210309181757-0dtlfgf"}静态方法不能被重写
  {: id="20210309181757-97waei2"}
* {: id="20210309181757-u0ugwi9"}私有等在子类中不可见的方法不能被重写
  {: id="20210309181757-wvp0984"}
* {: id="20210309181757-5od5nra"}final方法不能被重写
  {: id="20210309181757-jps5ezu"}
{: id="20210309181757-7vnlf2w"}

#### 2、方法的重载
{: id="20210309181757-69d9yot"}

（1）同一个类中
{: id="20210309181757-hv3msln"}

```java
class Test{
	public int max(int a, int b){
		return a > b ? a : b;
	}
	public double max(double a, double b){
		return a > b ? a : b;
	}
	public int max(int a, int b,int c){
		return max(max(a,b),c);
	}
}
```
{: id="20210309181757-oi7tfm7"}

（2）父子类中
{: id="20210309181757-jzkt7v1"}

```java
class Father{
	public void print(int i){
		System.out.println("i = " + i);
	}
}
class Son extends Father{
	public void print(int i,int j){
		System.out.println("i = " + i  ",j = " + j);
	}
}
```
{: id="20210309181757-okgimim"}

> 对于Son类，相当于有两个print方法，一个形参列表是(int i)，一个形参列表(int i, int j)
> {: id="20210309181757-9v61t51"}
{: id="20210309181757-zgbirvx"}

### 6.4.5 继承的特点三：构造方法
{: id="20210309181757-res3l1r"}

当类之间产生了关系，其中各类中的构造方法，又产生了哪些影响呢？
{: id="20210309181757-7blkpqv"}

首先我们要回忆两个事情，构造方法的定义格式和作用。
{: id="20210309181757-dy9nczo"}

1. {: id="20210309181757-9a74zjc"}构造方法的名字是与类名一致的。
   {: id="20210309181757-dvuh49a"}

   所以子类是**无法继承**父类构造方法的。
   {: id="20210309181757-nqgeiy2"}
2. {: id="20210309181757-5tmucrk"}构造方法的作用是初始化实例变量的，而子类又会从父类继承所有成员变量
   {: id="20210309181757-sj5t717"}
   所以子类的初始化过程中，**必须**先执行父类的初始化动作。子类的构造方法中默认有一个`super()` ，表示调用父类的实例初始化方法，父类成员变量初始化后，才可以给子类使用。代码如下：
   {: id="20210309181757-p5eove5"}
{: id="20210309181757-5qfdaw8"}

```java
class Fu {
  private int n;
  Fu(){
    System.out.println("Fu()");
  }
}
class Zi extends Fu {
  Zi(){
    // super（），调用父类构造方法
    super();
    System.out.println("Zi（）");
  }  
}
public class ExtendsDemo07{
  public static void main (String args[]){
    Zi zi = new Zi();
  }
}
输出结果：
Fu（）
Zi（）
```
{: id="20210309181757-8n0emwg"}

如果父类没有无参构造怎么办？
{: id="20210309181757-rri2ube"}

```java
public class Person {
	private String name;
	private int age;
	public Person(String name, int age) {
		this.name = name;
		this.age = age;
	}
	//其他成员方法省略
}
```
{: id="20210309181757-1ilj8dy"}

```java
public class Student extends Person{
	private int score;
}
```
{: id="20210309181757-xgm9dhx"}

此时子类代码报错。
{: id="20210309181757-r4hnq2b"}

解决办法：在子类构造器中，用super(实参列表)，显示调用父类的有参构造解决。
{: id="20210309181757-87qcheh"}

```java
public class Student extends Person{
	private int score;

	public Student(String name, int age) {
		super(name, age);
	}
	public Student(String name, int age, int score) {
		super(name, age);
		this.score = score;
	}
	
	//其他成员方法省略
}
```
{: id="20210309181757-rilwxbq"}

结论：
{: id="20210309181757-9ep0qxr"}

子类对象实例化过程中必须先完成从父类继承的成员变量的实例初始化，这个过程是通过调用父类的实例初始化方法来完成的。
{: id="20210309181757-x58rknh"}

* {: id="20210309181757-yz4r71k"}super()：表示调用父类的无参实例初始化方法，要求父类必须有无参构造，而且可以省略不写；
  {: id="20210309181757-tj42lzh"}
* {: id="20210309181757-3s71w6x"}super(实参列表)：表示调用父类的有参实例初始化方法，当父类没有无参构造时，子类的构造器首行必须写super(实参列表)来明确调用父类的哪个有参构造（其实是调用该构造器对应的实例初始方法）
  {: id="20210309181757-q3uygxn"}
* {: id="20210309181757-9kn4j0f"}super()和super(实参列表)都只能出现在子类构造器的首行
  {: id="20210309181757-fhh0brg"}
{: id="20210309181757-xm6ny5b"}

### 6.4.6 继承的特点四：单继承限制
{: id="20210309181757-cqzwsbl"}

1. {: id="20210309181757-q83cnto"}Java只支持单继承，不支持多继承。
   {: id="20210309181757-gkhtvxe"}
{: id="20210309181757-j49x2ch"}

```java
//一个类只能有一个父类，不可以有多个父类。
class C extends A{} 	//ok
class C extends A，B...	//error
```
{: id="20210309181757-5kybsbn"}

2. {: id="20210309181757-syxjmnc"}Java支持多层继承(继承体系)。
   {: id="20210309181757-7hp9x3f"}
{: id="20210309181757-u2e3p41"}

```java
class A{}
class B extends A{}
class C extends B{}
```
{: id="20210309181757-rxy9m7b"}

> 顶层父类是Object类。所有的类默认继承Object，作为父类。
> {: id="20210309181757-bw1gcss"}
{: id="20210309181757-skggoi8"}

3. {: id="20210309181757-cn1pasc"}子类和父类是一种相对的概念。
   {: id="20210309181757-8f558rm"}

   例如：B类对于A来说是子类，但是对于C类来说是父类
   {: id="20210309181757-4ysh5ob"}
4. {: id="20210309181757-i25yaer"}一个父类可以同时拥有多个子类
   {: id="20210309181757-8sg4ir9"}
{: id="20210309181757-fny8o5b"}

### 6.4.7 继承练习
{: id="20210309181757-67oszfw"}

#### 练习1
{: id="20210309181757-3tyblxt"}

（1）父类Graphic图形
包含属性：name（图形名），属性私有化，不提供无参构造，只提供有参构造
包含求面积getArea()：返回0.0
求周长getPerimeter()方法：返回0.0
显示信息getInfo()方法：返回图形名称、面积、周长
{: id="20210309181757-mg5opcj"}

（2）子类Circle圆继承Graphic图形
包含属性：radius
重写求面积getArea()和求周长getPerimeter()方法，显示信息getInfo()加半径信息
{: id="20210309181757-2flpcev"}

（3）子类矩形Rectange继承Graphic图形
包含属性：length、width
重写求面积getArea()和求周长getPerimeter()方法
{: id="20210309181757-p0mrj5l"}

```java
public class Graphic {
	private String name;

	public Graphic(String name) {
		super();
		this.name = name;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public double getArea() {
		return 0.0;
	}

	public double getPerimeter() {
		return 0.0;
	}

	/*
	 * this对象：调用当前方法的对象，如果是Graphic对象，那么就会执行Graphic的getArea()和getPerimeter()
	 * this对象：调用当前方法的对象，如果是Circle对象，那么就会执行Circle的getArea()和getPerimeter()
	 * this对象：调用当前方法的对象，如果是Rectangle对象，那么就会执行Rectangle的getArea()和getPerimeter()
	 */
	public String getInfo() {
		return "图形：" + name + "，面积：" + getArea() + ",周长：" + getPerimeter();
	}
}
```
{: id="20210309181757-oiivm09"}

```java
public class Circle extends Graphic {
	private double radius;

	public Circle(String name, double radius) {
		super(name);
		this.radius = radius;
	}

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}

	@Override//表示这个方法是重写的方法
	public double getArea() {
		return Math.PI * radius * radius;
	}

	@Override//表示这个方法是重写的方法
	public double getPerimeter() {
		return Math.PI * radius * 2;
	}

	/*@Override//表示这个方法是重写的方法
	public String getInfo() {
		return super.getInfo() + "，半径：" + radius;
	}*/
	
}

```
{: id="20210309181757-ymhxsxy"}

```java
public class Rectangle extends Graphic {
	private double length;
	private double width;
	
	public Rectangle(String name, double length, double width) {
		super(name);
		this.length = length;
		this.width = width;
	}

	public double getLength() {
		return length;
	}

	public void setLength(double length) {
		this.length = length;
	}

	public double getWidth() {
		return width;
	}

	public void setWidth(double width) {
		this.width = width;
	}

	@Override
	public double getArea() {
		return length*width;
	}

	@Override
	public double getPerimeter() {
		return 2*(length + width);
	}
}

```
{: id="20210309181757-ry191tx"}

```java
public class TestGraphicExer3 {
	public static void main(String[] args) {
		Graphic g = new Graphic("通用图形");
		System.out.println(g.getInfo());
		
		Circle c = new Circle("圆", 1.2);
		System.out.println(c.getInfo());//调用getInfo()方法的对象是c
		
		Rectangle r = new Rectangle("矩形", 3, 5);
		System.out.println(r.getInfo());
	}
}
```
{: id="20210309181757-vz43ff5"}

#### 练习2
{: id="20210309181757-6kxdvv9"}

（1）声明一个银行储蓄卡类，
{: id="20210309181757-u5d9cff"}

​	包含属性：账户，余额
{: id="20210309181757-tsvtr4a"}

​	包含取款 public void withdraw(double money)
{: id="20210309181757-qzb38qy"}

​		    存款 pubic void save(double money)
{: id="20210309181757-ze9pt1m"}

​           获取账户信息： public String getInfo() 可以返回账户和余额
{: id="20210309181757-kgxvysf"}

（2）声明一个银行信用卡类，继承储蓄卡类
{: id="20210309181757-9xp9dzv"}

​	增加属性：可透支额度，最多可透支金额
{: id="20210309181757-rqsm1on"}

​	重写存款 public void withdraw(double money)，可透支
{: id="20210309181757-ci983kp"}

​	       存款 pubic void save(double money)，需要恢复可透支额度
{: id="20210309181757-ohwz6kv"}

（3）在测试类中，分别创建两种卡对象，测试
{: id="20210309181757-54l5vl9"}

#### 练习3
{: id="20210309181757-oxehxq8"}

1、声明父类：Person类
包含属性：姓名，年龄，性别
属性私有化，get/set
包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男
{: id="20210309181757-fn1k2s8"}

2、声明子类：Student类，继承Person类
新增属性：score成绩
属性私有化，get/set
包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男，成绩：89
{: id="20210309181757-gud3eox"}

3、声明子类：Teacher类，继承Person类
新增属性：salary薪资
属性私有化，get/set
包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男，薪资：10000
{: id="20210309181757-8u0g3dd"}

```java
public class Person {
	private String name;
	private int age;
	private char gender;
	public Person(String name, int age, char gender) {
		super();
		this.name = name;
		this.age = age;
		this.gender = gender;
	}
	public Person() {
		super();
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
	public char getGender() {
		return gender;
	}
	public void setGender(char gender) {
		this.gender = gender;
	}
	
	//包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男
	public String getInfo(){
		return "姓名：" + name + "，年龄：" + age +"，性别：" + gender;
	}
}
```
{: id="20210309181757-edg5p2k"}

```java
public class Student extends Person {
	private int score;

	public Student() {
	}

	public Student(String name, int age, char gender, int score) {
		setName(name);
		setAge(age);
		setGender(gender);
		this.score = score;
	}

	public int getScore() {
		return score;
	}

	public void setScore(int score) {
		this.score = score;
	}
	//包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男，成绩：89
	public String getInfo(){
		//方式一：
//		return "姓名：" + getName() + "，年龄：" + getAge() + "，成绩：" + score;
		
		//方法二：
		return super.getInfo() + "，成绩：" + score;
	}
	
}
```
{: id="20210309181757-y3vi8lv"}

```java
public class Teacher extends Person {
	private double salary;

	public Teacher() {
	}

	public Teacher(String name, int age, char gender, double salary) {
		setName(name);
		setAge(age);
		setGender(gender);
		this.salary = salary;
	}

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}
	
	//包含getInfo()方法：例如：姓名：张三，年龄：23，性别：男，薪资：10000
	public String getInfo(){
		return super.getInfo() + "，薪资：" + salary;
	}
}

```
{: id="20210309181757-jl8xvd2"}

```java
public class TestPersonExer2 {
	public static void main(String[] args) {
		Person p = new Person("张三", 23, '男');
		System.out.println(p.getInfo());
		
		Student s = new Student("陈琦", 25, '男', 89);
		System.out.println(s.getInfo());
		
		Teacher t = new Teacher("柴林燕", 18, '女', 11111);
		System.out.println(t.getInfo());
	}
}
```
{: id="20210309181757-4einx7t"}

## 6.5 final关键字
{: id="20210309181757-51eyp7n"}

final：最终的，不可更改的，它的用法有：
{: id="20210309181757-lnobnh8"}

### 1、修饰类
{: id="20210309181757-acv2pgc"}

表示这个类不能被继承，没有子类
{: id="20210309181757-jqt5mnq"}

```java
final class Eunuch{//太监类
	
}
class Son extends Eunuch{//错误
	
}
```
{: id="20210309181757-tuuv4e4"}

### 2、修饰方法
{: id="20210309181757-5ux8u8n"}

表示这个方法不能被子类重写
{: id="20210309181757-xntdm6w"}

```java
class Father{
	public final void method(){
		System.out.println("father");
	}
}
class Son extends Father{
	public void method(){//错误
		System.out.println("son");
	}
}
```
{: id="20210309181757-mzqelzw"}

### 3、声明常量
{: id="20210309181757-7rw8fz4"}

final修饰某个变量（成员变量或局部变量），表示它的值就不能被修改，即常量，常量名建议使用大写字母。
{: id="20210309181757-llgq3h2"}

> 如果某个成员变量用final修饰后，没有set方法，并且必须初始化（可以显式赋值、或在初始化块赋值、实例变量还可以在构造器中赋值）
> {: id="20210309181757-jw0vqwf"}
{: id="20210309181757-v3mqsy8"}

```java
public class Test{
    public static void main(String[] args){
    	final int MIN_SCORE = 0;
    	final int MAX_SCORE = 100;
    }
}
class Chinese{
	public static final String COUNTRY = "中华人民共和国";	
	private String name;
	public Chinese( String name) {
		super();
		this.name = name;
	}
	public Chinese() {
		super();
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	//final修饰的没有set方法
	public static String getCountry() {
		return COUNTRY;
	}
}
```
{: id="20210309181757-rhjtn62"}

## 6.6 成员变量初始化
{: id="20210309181757-etasx95"}

### 6.6.1 成员变量初始化方式
{: id="20210309181757-gr6xedt"}

#### 1、成员变量有默认值
{: id="20210309181757-b160r7n"}

| 类别     | 具体类型                       | 默认值   |
| -------- | ------------------------------ | -------- |
| 基本类型 | 整数（byte，short，int，long） | 0        |
|          | 浮点数（float，double）        | 0.0      |
|          | 字符（char）                   | '\u0000' |
|          | 布尔（boolean）                | false    |
|          | 数据类型                       | 默认值   |
| 引用类型 | 数组，类，接口                 | null     |
{: id="20210309181757-koyahpo"}

我们知道类中成员变量都有默认值，但是现在我们要为成员变量赋默认值以外的值，我们该怎么办呢？
{: id="20210309181757-ghmmdud"}

#### 2、显式赋值
{: id="20210309181757-ax6nkhj"}

```java
public class Student{
    public static final String COUNTRY = "中华人民共和国";
	private static String school = "尚硅谷";
	private String name;
	private char gender = '男';
}
```
{: id="20210309181757-prne89u"}

> 显式赋值，一般都是赋常量值
> {: id="20210309181757-k5qbku6"}
{: id="20210309181757-33jps4z"}

#### 3、代码块
{: id="20210309181757-fhoh4uw"}

如果成员变量想要初始化的值不是一个硬编码的常量值，而是需要通过复杂的计算或读取文件、或读取运行环境信息等方式才能获取的一些值，该怎么办呢？
{: id="20210309181757-8osoc6z"}

* {: id="20210309181757-crrn028"}静态初始化块：为静态变量初始化
  {: id="20210309181757-3qo2fpx"}
{: id="20210309181757-b69l1y7"}

```java
【修饰符】 class 类名{
    static{
		静态初始化
	}
}

```
{: id="20210309181757-lol6y2z"}

* {: id="20210309181757-l5lhqi2"}实例初始化：为实例变量初始化
  {: id="20210309181757-h19u14q"}
{: id="20210309181757-rkucwkj"}

```java
【修饰符】 class 类名{
    {
		实例初始化块
	}
}
```
{: id="20210309181757-pp7f6yr"}

静态初始化块：在类初始化时由类加载器调用执行，每一个类的静态初始化只会执行一次，早于实例对象的创建。
{: id="20210309181757-cot9n4z"}

实例初始化块：每次new实例对象时自动执行，每new一个对象，执行一次。
{: id="20210309181757-0xroa64"}

```java
public class Student{
	private static String school;
	private String name;
	private char gender;
	
	static{
		//获取系统属性，这里只是说明school的初始化过程可能比较复杂
		school = System.getProperty("school");
		if(school==null) {
			school = "尚硅谷";
		}
	}
	{
		String info = System.getProperty("gender");
		if(info==null) {
			gender = '男';
		}else {
			gender = info.charAt(0);
		}
	}
	public static String getSchool() {
		return school;
	}
	public static void setSchool(String school) {
		Student.school = school;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public char getGender() {
		return gender;
	}
	public void setGender(char gender) {
		this.gender = gender;
	}

}
```
{: id="20210309181757-kim4e61"}

#### 4、构造器
{: id="20210309181757-7zpq0mf"}

我们发现，显式赋值和实例初始化块为每一个实例对象的实例变量初始化的都是相同的值，那么我们如果想要不同的实例对象初始化为不同的值，怎么办呢？此时我们可以考虑使用构造器，在new对象时由对象的创建者决定为当前对象的实例变量赋什么值。
{: id="20210309181757-x31y8k1"}

> **注意：构造器只为实例变量初始化，不为静态类变量初始化**
> {: id="20210309181757-ajf5bi6"}
{: id="20210309181757-qme8d5r"}

为实例变量初始化，再new对象时由对象的创建者决定为当前对象的实例变量赋什么值。
{: id="20210309181757-6yp5wrf"}

#### 5、setter方法
{: id="20210309181757-1w68koh"}

一般用于修改成员变量的值。
{: id="20210309181757-g3hg578"}

### 6.6.2 类初始化
{: id="20210309181757-0ekel5j"}

1、类初始化的目的：为类中的静态变量进行赋值。
{: id="20210309181757-8amgd3o"}

2、实际上，类初始化的过程时在调用一个<clinit>()方法，而这个方法是编译器自动生成的。编译器会将如下两部分的**所有**代码，**按顺序**合并到类初始化<clinit>()方法体中。
{: id="20210309181757-v3yhn6z"}

（1）静态类成员变量的显式赋值语句
{: id="20210309181757-33lkcay"}

（2）静态代码块中的语句
{: id="20210309181757-5ykbnev"}

3、整个类初始化只会进行一次，如果子类初始化时，发现父类没有初始化，那么会先初始化父类。
{: id="20210309181757-5dab98s"}

#### 示例代码1：单个类
{: id="20210309181757-rlpfx8q"}

```java
public class Test{
    public static void main(String[] args){
    	Father.test();
    }
}
class Father{
	private static int a = getNumber();//这里调用方法为a变量显式赋值的目的是为了看到这个过程
	static{
		System.out.println("Father(1)");
	}
	private static int b = getNumber();
	static{
		System.out.println("Father(2)");
	}
	
	public static int getNumber(){
		System.out.println("getNumber()");
		return 1;
	}
	
	public static void test(){
		System.out.println("Father:test()");
	}
}
```
{: id="20210309181757-6v4qnmf"}

```java
运行结果：
getNumber()
Father(1)
getNumber()
Father(2)
Father:test()
```
{: id="20210309181757-85ie8dc"}

![1562070829002](imgs8/1562070829002.png)
{: id="20210309181757-0kl7lj0"}

#### 示例代码2：父子类
{: id="20210309181757-nqg6ia3"}

```java
public class Test{
    public static void main(String[] args){
    	Son.test();
        System.out.println("-----------------------------");
        Son.test();
    }
}
class Father{
	private static int a = getNumber();
	static{
		System.out.println("Father(1)");
	}
	private static int b = getNumber();
	static{
		System.out.println("Father(2)");
	}
	
	public static int getNumber(){
		System.out.println("Father:getNumber()");
		return 1;
	}
}
class Son extends Father{
	private static int a = getNumber();
	static{
		System.out.println("Son(1)");
	}
	private static int b = getNumber();
	static{
		System.out.println("Son(2)");
	}
	
	public static int getNumber(){
		System.out.println("Son:getNumber()");
		return 1;
	}
	
	public static void test(){
		System.out.println("Son:test()");
	}	
}
```
{: id="20210309181757-6hm3t4p"}

```java
运行结果：
Father:getNumber()
Father(1)
Father:getNumber()
Father(2)
Son:getNumber()
Son(1)
Son:getNumber()
Son(2)
Son:test()
-----------------------------
Son:test()
```
{: id="20210309181757-i9n6fsg"}

结论：
{: id="20210309181757-mdl5tvv"}

每一个类都有一个类初始化方法<clinit>()方法，然后子类初始化时，如果发现父类加载和没有初始化，会先加载和初始化父类，然后再加载和初始化子类。一个类，只会初始化一次。
{: id="20210309181757-j7pz9sg"}

### 6.6.3 实例初始化
{: id="20210309181757-82dlzna"}

1、实例初始化的目的：为类中非静态成员变量赋值
{: id="20210309181757-st1k542"}

2、实际上我们编写的代码在编译时，会自动处理代码，整理出一个<clinit>()的类初始化方法，还会整理出一个或多个的<init>(...)实例初始化方法。一个类有几个实例初始化方法，由这个类就有几个构造器决定。
{: id="20210309181757-9lhi2vh"}

实例初始化方法的方法体，由四部分构成：
{: id="20210309181757-bmvc868"}

（1）super()或super(实参列表)    这里选择哪个，看原来构造器首行是哪句，没写，默认就是super()
{: id="20210309181757-ympveey"}

（2）非静态实例变量的显示赋值语句
{: id="20210309181757-pn1e3mc"}

（3）非静态代码块
{: id="20210309181757-bvkjtni"}

（4）对应构造器中的代码
{: id="20210309181757-kju8xlq"}

特别说明：其中（2）和（3）是按顺序合并的，（1）一定在最前面（4）一定在最后面
{: id="20210309181757-4oywsdf"}

3、执行特点：
{: id="20210309181757-srhtvu9"}

* {: id="20210309181757-gzz79nw"}创建对象时，才会执行，
  {: id="20210309181757-zjlckmp"}
* {: id="20210309181757-tz93hnj"}调用哪个构造器，就是指定它对应的实例初始化方法
  {: id="20210309181757-rvefd00"}
* {: id="20210309181757-13iy7jk"}创建子类对象时，父类对应的实例初始化会被先执行，执行父类哪个实例初始化方法，看用super()还是super(实参列表)
  {: id="20210309181757-c8s0mz2"}
{: id="20210309181757-tb3t2zo"}

#### 示例代码1：单个类
{: id="20210309181757-v4bf93y"}

```java
public class Test{
    public static void main(String[] args){
    	Father f1 = new Father();
    	Father f2 = new Father("atguigu");
    }
}
class Father{
	private int a = getNumber();
	private String info;
	{
		System.out.println("Father(1)");
	}
	Father(){
		System.out.println("Father()无参构造");
	}
	Father(String info){
		this.info = info;
		System.out.println("Father(info)有参构造");
	}
	private int b = getNumber();
	{
		System.out.println("Father(2)");
	}
	
	public int getNumber(){
		System.out.println("Father:getNumber()");
		return 1;
	}
}
```
{: id="20210309181757-lwpjr3a"}

```java
运行结果：
Father:getNumber()
Father(1)
Father:getNumber()
Father(2)
Father()无参构造
Father:getNumber()
Father(1)
Father:getNumber()
Father(2)
Father(info)有参构造
```
{: id="20210309181757-lb1liw5"}

![1562072678317](imgs8/1562072678317.png)
{: id="20210309181757-mupidc1"}

#### 示例代码2：父子类
{: id="20210309181757-0o5gdkp"}

```java
public class Test{
    public static void main(String[] args){
    	Son s1 = new Son();
        System.out.println("-----------------------------");
    	Son s2 = new Son("atguigu");
    }
}
class Father{
	private int a = getNumber();
	private String info;
	{
		System.out.println("Father(1)");
	}
	Father(){
		System.out.println("Father()无参构造");
	}
	Father(String info){
		this.info = info;
		System.out.println("Father(info)有参构造");
	}
	private int b = getNumber();
	{
		System.out.println("Father(2)");
	}
	
	public static int getNumber(){
		System.out.println("Father:getNumber()");
		return 1;
	}
}
class Son extends Father{
	private int a = getNumber();
	{
		System.out.println("Son(1)");
	}
	private int b = getNumber();
	{
		System.out.println("Son(2)");
	}
	public Son(){
		System.out.println("Son()：无参构造");
	}
	public Son(String info){
		super(info);
		System.out.println("Son(info)：有参构造");
	}
	public static int getNumber(){
		System.out.println("Son:getNumber()");
		return 1;
	}
}
```
{: id="20210309181757-l2hxeno"}

```java
运行结果：
Father:getNumber()
Father(1)
Father:getNumber()
Father(2)
Father()无参构造
Son:getNumber()
Son(1)
Son:getNumber()
Son(2)
Son()：无参构造
-----------------------------
Father:getNumber()
Father(1)
Father:getNumber()
Father(2)
Father(info)有参构造
Son:getNumber()
Son(1)
Son:getNumber()
Son(2)
Son(info)：有参构造
```
{: id="20210309181757-8cnk5ke"}

#### 示例代码3：父子类，方法有重写
{: id="20210309181757-6xzfsmm"}

```java
public class Test{
    public static void main(String[] args){
    	Son s1 = new Son();
    	System.out.println("-----------------------------");
    	Son s2 = new Son("atguigu");
    }
}
class Father{
	private int a = getNumber();
	private String info;
	{
		System.out.println("Father(1)");
	}
	Father(){
		System.out.println("Father()无参构造");
	}
	Father(String info){
		this.info = info;
		System.out.println("Father(info)有参构造");
	}
	private int b = getNumber();
	{
		System.out.println("Father(2)");
	}
	
	public int getNumber(){
		System.out.println("Father:getNumber()");
		return 1;
	}
}
class Son extends Father{
	private int a = getNumber();
	{
		System.out.println("Son(1)");
	}
	private int b = getNumber();
	{
		System.out.println("Son(2)");
	}
	public Son(){
		System.out.println("Son()：无参构造");
	}
	public Son(String info){
		super(info);
		System.out.println("Son(info)：有参构造");
	}
	public int getNumber(){
		System.out.println("Son:getNumber()");
		return 1;
	}
}
```
{: id="20210309181757-312jl0s"}

```java
运行结果：
Son:getNumber()  //子类重写getNumber()方法，那么创建子类的对象，就是调用子类的getNumber()方法，因为当前对象this是子类的对象。
Father(1)
Son:getNumber()
Father(2)
Father()无参构造
Son:getNumber()
Son(1)
Son:getNumber()
Son(2)
Son()：无参构造
-----------------------------
Son:getNumber()
Father(1)
Son:getNumber()
Father(2)
Father(info)有参构造
Son:getNumber()
Son(1)
Son:getNumber()
Son(2)
Son(info)：有参构造
```
{: id="20210309181757-7f3s5mb"}

### 6.6.4 类初始化与实例初始化
{: id="20210309181757-k1ovjrd"}

类初始化肯定优先于实例初始化。
{: id="20210309181757-0lverqp"}

类初始化只做一次。
{: id="20210309181757-exjbrl0"}

实例初始化是每次创建对象都要进行。
{: id="20210309181757-aaf3ffh"}

```java
public class Test{
    public static void main(String[] args){
    	Son s1 = new Son();
    	System.out.println("----------------------------");
    	Son s2 = new Son();
    }
}
class Father{
	static{
		System.out.println("Father:static");
	}
	{
		System.out.println("Father:not_static");
	}
	Father(){
		System.out.println("Father()无参构造");
	}
}
class Son extends Father{
	static{
		System.out.println("Son:static");
	}
	{
		System.out.println("Son:not_static");
	}
	Son(){
		System.out.println("Son()无参构造");
	}
}
```
{: id="20210309181757-btz3e25"}

```java
运行结果：
Father:static
Son:static
Father:not_static
Father()无参构造
Son:not_static
Son()无参构造
----------------------------
Father:not_static
Father()无参构造
Son:not_static
Son()无参构造
```
{: id="20210309181757-628mui3"}

## 6.7 this和super关键字
{: id="20210309181757-6oaypja"}

### 6.7.1 this关键字
{: id="20210309181757-u9snnxm"}

#### 1、this的含义
{: id="20210309181757-sadc1o6"}

this代表当前对象
{: id="20210309181757-f2yfjk3"}

#### 2、this使用位置
{: id="20210309181757-picslkj"}

* {: id="20210309181757-up07xnn"}this在实例初始化相关的代码块和构造器中：表示正在创建的那个实例对象，即正在new谁，this就代表谁
  {: id="20210309181757-juxrq3g"}
* {: id="20210309181757-yvqs5x5"}this在非静态实例方法中：表示调用该方法的对象，即谁在调用，this就代表谁。
  {: id="20210309181757-acl47j8"}
* {: id="20210309181757-n65nvce"}this不能出现在静态代码块和静态方法中
  {: id="20210309181757-2rivcl5"}
{: id="20210309181757-6szgp3q"}

#### 3、this使用格式
{: id="20210309181757-57obl1s"}

（1）this.成员变量名
{: id="20210309181757-fs7a0ve"}

* {: id="20210309181757-zaejbp3"}当方法的局部变量与当前对象的成员变量重名时，就可以在成员变量前面加this.，如果没有重名问题，就可以省略this.
  {: id="20210309181757-oit16vu"}
* {: id="20210309181757-59q176m"}this.成员变量会先从本类声明的成员变量列表中查找，如果未找到，会去从父类继承的在子类中仍然可见的成员变量列表中查找
  {: id="20210309181757-o76y0b6"}
{: id="20210309181757-w1bquxa"}

（2）this.成员方法
{: id="20210309181757-f7erc7c"}

* {: id="20210309181757-3s5sd0u"}调用当前对象的成员方法时，都可以加"this."，也可以省略，实际开发中都省略
  {: id="20210309181757-h6fcw3x"}
* {: id="20210309181757-wzay4nm"}当前对象的成员方法，先从本类声明的成员方法列表中查找，如果未找到，会去从父类继承的在子类中仍然可见的成员方法列表中查找
  {: id="20210309181757-1uwu539"}
{: id="20210309181757-bu7zptf"}

（3）this()或this(实参列表)
{: id="20210309181757-hr58q1w"}

* {: id="20210309181757-bmtfq2g"}只能调用本类的其他构造器
  {: id="20210309181757-vdcz9h7"}
* {: id="20210309181757-9mvccx1"}必须在构造器的首行
  {: id="20210309181757-4gdfyuu"}
* {: id="20210309181757-uqw6lbd"}如果一个类中声明了n个构造器，则最多有 n - 1个构造器中使用了"this(【实参列表】)"，否则会发生递归调用死循环
  {: id="20210309181757-2oabrqx"}
{: id="20210309181757-l46t6gb"}

### 6.7.2  super关键字
{: id="20210309181757-b520595"}

#### 1、super的含义
{: id="20210309181757-gkz4t24"}

super代表当前对象中从父类的引用的
{: id="20210309181757-453i8yh"}

#### 2、super使用的前提
{: id="20210309181757-1lg6a6i"}

* {: id="20210309181757-wv3is6x"}通过super引用父类的xx，都是在子类中仍然可见的
  {: id="20210309181757-wym645e"}
* {: id="20210309181757-6ehc6cn"}不能在静态代码块和静态方法中使用super
  {: id="20210309181757-te9avs6"}
{: id="20210309181757-vhbc0b3"}

#### 3、super的使用格式
{: id="20210309181757-5x7p8hi"}

（1）super.成员变量
{: id="20210309181757-06zoji7"}

在子类中访问父类的成员变量，特别是当子类的成员变量与父类的成员变量重名时。
{: id="20210309181757-rfgmacz"}

```java
public class Person {
	private String name;
	private int age;
	//其他代码省略
}
public class Student extends Person{
	private int score;
	//其他成员方法省略
}
public class Test{
    public static void main(String[] args){
    	Student stu = new Student();
    }
}
```
{: id="20210309181757-iwost1l"}

![1561984785190](imgs8/1561984785190.png)
{: id="20210309181757-twzai3e"}

```java
public class Test{
    public static void main(String[] args){
    	Son s = new Son();
    	s.test(30);
    }
}
class Father{
	int a = 10;
}
class Son extends Father{
	int a = 20;
	public void test(int a){
		System.out.println(super.a);//10
		System.out.println(this.a);//20
		System.out.println(a);//30
	}
}
```
{: id="20210309181757-ue93wot"}

（2）super.成员方法
{: id="20210309181757-hyte7bu"}

在子类中调用父类的成员方法，特别是当子类重写了父类的成员方法时
{: id="20210309181757-w8izvju"}

```java
public class Test{
    public static void main(String[] args){
    	Son s = new Son();
    	s.test();
    }
}
class Father{
	public void method(){
		System.out.println("aa");
	}
}
class Son extends Father{
	public void method(){
		System.out.println("bb");
	}
	public void test(){
		method();//bb
		this.method();//bb
		super.method();//aa
	}
}
```
{: id="20210309181757-cxqvqe8"}

（3）super()或super(实参列表)
{: id="20210309181757-2kdwuax"}

在子类的构造器首行，用于表示调用父类的哪个实例初始化方法
{: id="20210309181757-r8jiakg"}

> super() 和 this() 都必须是在构造方法的第一行，所以不能同时出现。
> {: id="20210309181757-p69q9z4"}
{: id="20210309181757-0g8qzvr"}

### 6.7.3  就近原则和追根溯源原则
{: id="20210309181757-14v2g5d"}

#### 1、找变量
{: id="20210309181757-bfttudz"}

* {: id="20210309181757-pl5w4i7"}**没有super和this**
  {: id="20210309181757-0dy88ec"}

  * {: id="20210309181757-s6m5o8j"}在构造器、代码块、方法中如果出现使用某个变量，先查看是否是当前块声明的局部变量，
    {: id="20210309181757-0sbqide"}
  * {: id="20210309181757-vzft8if"}如果不是局部变量，先从当前执行代码的本类去找成员变量
    {: id="20210309181757-ao02ltp"}
  * {: id="20210309181757-pbrqo3f"}如果从当前执行代码的本类中没有找到，会往上找父类的（非private，跨包还不能是缺省的）
    {: id="20210309181757-4699do1"}
  {: id="20210309181757-38huvjx"}
* {: id="20210309181757-i176iwk"}**this** ：代表当前对象
  {: id="20210309181757-zw5bxpa"}
  * {: id="20210309181757-ktnroga"}通过this找成员变量时，先从当前执行代码的本类中找，没有的会往上找父类的（非private，跨包还不能是缺省的）。
    {: id="20210309181757-s0dl7fc"}
  {: id="20210309181757-ajey98t"}
* {: id="20210309181757-3907e14"}**super** ：代表父类的
  {: id="20210309181757-57tycmj"}
  * {: id="20210309181757-kljbpr6"}通过super找成员变量，直接从当前执行代码所在类的父类找
    {: id="20210309181757-wkwtc22"}
  * {: id="20210309181757-e8wturk"}super()或super(实参列表)只能从直接父类找
    {: id="20210309181757-k3amrjg"}
  * {: id="20210309181757-gjlsd8o"}通过super只能访问父类在子类中可见的（非private，跨包还不能是缺省的）
    {: id="20210309181757-deinegn"}
  {: id="20210309181757-82zdhta"}
{: id="20210309181757-u5zsez5"}

> 注意：super和this都不能出现在静态方法和静态代码块中，因为super和this都是存在与**对象**中的
> {: id="20210309181757-6jbrwi6"}
{: id="20210309181757-il41giz"}

#### 2、找方法
{: id="20210309181757-iqufgmq"}

* {: id="20210309181757-1wozw32"}没有super和this
  {: id="20210309181757-qujxisd"}

  * {: id="20210309181757-zjzc220"}先从当前对象（调用方法的对象）的本类找，如果没有，再从直接父类找，再没有，继续往上追溯
    {: id="20210309181757-q8zqw4z"}
  {: id="20210309181757-547a48b"}
* {: id="20210309181757-x1kcad4"}this
  {: id="20210309181757-3gdxgal"}
  * {: id="20210309181757-45s49mx"}先从当前对象（调用方法的对象）的本类找，如果没有，再从父类继承的可见的方法列表中查找
    {: id="20210309181757-kxznbq8"}
  {: id="20210309181757-6xuviao"}
* {: id="20210309181757-1qkvkuj"}super
  {: id="20210309181757-9jbgz0h"}
  * {: id="20210309181757-ux4z727"}直接从当前对象（调用方法的对象）的父类继承的可见的方法列表中查找
    {: id="20210309181757-9kgwy41"}
  {: id="20210309181757-idbub41"}
{: id="20210309181757-j9bt8qr"}

#### 3、找构造器
{: id="20210309181757-y6llut3"}

* {: id="20210309181757-9o9k020"}this()或this(实参列表)：只从本类中，不会再往上追溯
  {: id="20210309181757-p2t6oeo"}
* {: id="20210309181757-2opw7e2"}super()或super(实参列表)：只从直接父类找，不会再往上追溯
  {: id="20210309181757-dld42n2"}
{: id="20210309181757-18ocuff"}

#### 4、练习
{: id="20210309181757-jvndphw"}

##### （1）情形1
{: id="20210309181757-5o16bqb"}

```java
class Father{
	int a = 10;
	int b = 11;
}
class Son extends Father{
	int a = 20;
	
	public void test(){
		//子类与父类的属性同名，子类对象中就有两个a
		System.out.println("父类的a：" + super.a);//10    直接从父类局部变量找
		System.out.println("子类的a：" + this.a);//20   先从本类成员变量找
		System.out.println("子类的a：" + a);//20  先找局部变量找，没有再从本类成员变量找
		
		//子类与父类的属性不同名，是同一个b
		System.out.println("b = " + b);//11  先找局部变量找，没有再从本类成员变量找，没有再从父类找
		System.out.println("b = " + this.b);//11   先从本类成员变量找，没有再从父类找
		System.out.println("b = " + super.b);//11  直接从父类局部变量找
	}
	
	public void method(int a){
		//子类与父类的属性同名，子类对象中就有两个成员变量a，此时方法中还有一个局部变量a
		System.out.println("父类的a：" + super.a);//10  直接从父类局部变量找
		System.out.println("子类的a：" + this.a);//20  先从本类成员变量找
		System.out.println("局部变量的a：" + a);//30  先找局部变量
	}
    
    public void fun(int b){
        System.out.println("b = " + b);//13  先找局部变量
		System.out.println("b = " + this.b);//11  先从本类成员变量找
		System.out.println("b = " + super.b);//11  直接从父类局部变量找
    }
}
public class TestInherite2 {
	public static void main(String[] args) {
		Son son = new Son();
		System.out.println(son.a);//20
		System.out.println(son.b);//11
		
		son.test();
		
		son.method(30);
        
        son.fun(13);
	}
}
```
{: id="20210309181757-s5w873o"}

##### （2）情形2
{: id="20210309181757-0xb8ti1"}

```java
public class Test{
    public static void main(String[] args){
    	Son s = new Son();
    	System.out.println(s.getNum());//10   没重写，先找本类，没有，找父类
    	
    	Daughter d = new Daughter();
    	System.out.println(d.getNum());//20  重写了，先找本类
    }
}
class Father{
	protected int num = 10;
	public int getNum(){
		return num;
	}
}
class Son extends Father{
	private int num = 20;
}
class Daughter extends Father{
	private int num = 20;
	public int getNum(){
		return num;
	}
}
```
{: id="20210309181757-tyk216j"}

##### （3）情形3
{: id="20210309181757-ksz7d5v"}

```java
public class Test{
    public static void main(String[] args){
    	Son s = new Son();
    	s.test();
    	
    	Daughter d = new Daughter();
    	d.test();
    }
}
class Father{
	protected int num = 10;
	public int getNum(){
		return num;
	}
}
class Son extends Father{
	private int num = 20;
	public void test(){
		System.out.println(getNum());//10  本类没有找父类
		System.out.println(this.getNum());//10  本类没有找父类
		System.out.println(super.getNum());//10  本类没有找父类
	}
}
class Daughter extends Father{
	private int num = 20;
	public int getNum(){
		return num;
	}
	public void test(){
		System.out.println(getNum());//20  先找本类
		System.out.println(this.getNum());//20  先找本类
		System.out.println(super.getNum());//10  直接找父类
	}
}
```
{: id="20210309181757-3pdivag"}


{: id="20210309181757-3w3bvrj" type="doc"}
