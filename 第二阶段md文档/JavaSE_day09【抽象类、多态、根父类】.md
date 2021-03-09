# JavaSE_day09【抽象类、多态、根父类】
{: id="20210309181757-g8bsee9"}

## 今日内容
{: id="20210309181757-zi0wb9u"}

* {: id="20210309181757-khaklez"}抽象类
  {: id="20210309181757-nohudd3"}
* {: id="20210309181757-fe5dmh5"}多态
  {: id="20210309181757-wqi3827"}
* {: id="20210309181757-q72h4bk"}向上转型
  {: id="20210309181757-erdr4m7"}
* {: id="20210309181757-hliipgc"}向下转型
  {: id="20210309181757-e8be950"}
* {: id="20210309181757-hh7zjyt"}native
  {: id="20210309181757-rvvpuky"}
* {: id="20210309181757-82tpycp"}根父类
  {: id="20210309181757-xu5jdx3"}
{: id="20210309181757-nyrwujp"}

## 学习目标
{: id="20210309181757-bni6v1s"}

* {: id="20210309181757-jh5pxx8"}[ ] 能够声明抽象类
  {: id="20210309181757-j977rqb"}
* {: id="20210309181757-5q8dxdk"}[ ] 能够说出抽象类的特点
  {: id="20210309181757-x3uc8f9"}
* {: id="20210309181757-ee1hsrn"}[ ] 能够继承抽象类
  {: id="20210309181757-tcgf4jp"}
* {: id="20210309181757-36eqr8s"}[ ] 能够应用多态解决问题
  {: id="20210309181757-2bccipi"}
* {: id="20210309181757-4zzhofa"}[ ] 理解向上转型与向下转型
  {: id="20210309181757-y7qmome"}
* {: id="20210309181757-rnujrzw"}[ ] 能够使用instanceof关键字判断对象类型
  {: id="20210309181757-w9npnrl"}
* {: id="20210309181757-s8bjbbx"}[ ] 了解native关键字
  {: id="20210309181757-ai4l129"}
* {: id="20210309181757-eft42mv"}[ ] 了解Object类的常用方法
  {: id="20210309181757-770m2i5"}
* {: id="20210309181757-jhqi0v7"}[ ] 会重写Object的常用方法
  {: id="20210309181757-7c17yvx"}
{: id="20210309181757-zkfmwac"}

# 第六章 面向对象基础--中
{: id="20210309181757-3dpvyji"}

## 6.8 抽象类
{: id="20210309181757-qijyyxw"}

### 6.8.1 由来
{: id="20210309181757-n9mim7t"}

抽象：即不具体、或无法具体
{: id="20210309181757-jmqjf6v"}

例如：当我们声明一个几何图形类：圆、矩形、三角形类等，发现这些类都有共同特征：求面积、求周长、获取图形详细信息。那么这些共同特征应该抽取到一个公共父类中。但是这些方法在父类中又**无法给出具体的实现**，而是应该交给子类各自具体实现。那么父类在声明这些方法时，**就只有方法签名，没有方法体**，我们把没有方法体的方法称为**抽象方法**。Java语法规定，包含抽象方法的类必须是**抽象类**。
{: id="20210309181757-jabrut5"}

### 6.8.2 语法格式
{: id="20210309181757-sgydsom"}

* {: id="20210309181757-n2yaole"}**抽象方法** ： 没有方法体的方法。
  {: id="20210309181757-oy59hlb"}
* {: id="20210309181757-tpfhjtb"}**抽象类**：被abstract所修饰的类。
  {: id="20210309181757-y6e7c3l"}
{: id="20210309181757-l3wkpqe"}

抽象类的语法格式
{: id="20210309181757-cxz2wfo"}

```java
【权限修饰符】 abstract class 类名{
  
}
【权限修饰符】 abstract class 类名 extends 父类{
  
}
```
{: id="20210309181757-9fym2pp"}

抽象方法的语法格式
{: id="20210309181757-h4y19cj"}

```java
【其他修饰符】 abstract 返回值类型  方法名(【形参列表】);
```
{: id="20210309181757-hf5kivd"}

> 注意：抽象方法没有方法体
> {: id="20210309181757-gil99ji"}
{: id="20210309181757-apm4592"}

代码举例：
{: id="20210309181757-ggujuc6"}

```java
public abstract class Animal {
    public abstract void run()；
}
```
{: id="20210309181757-e7k1dj1"}

```java
public class Cat extends Animal {
    public void run (){
      	System.out.println("小猫在墙头走~~~")； 	 
    }
}
```
{: id="20210309181757-0i9buq6"}

```java
public class CatTest {
 	 public static void main(String[] args) {
        // 创建子类对象
        Cat c = new Cat(); 
   
        // 调用run方法
        c.run();
  	}
}
输出结果：
小猫在墙头走~~~
```
{: id="20210309181757-6a5joi2"}

此时的方法重写，是子类对父类抽象方法的完成实现，我们将这种方法重写的操作，也叫做**实现方法**。
{: id="20210309181757-i0o3jc2"}

### 6.8.3 注意事项
{: id="20210309181757-vh9n8wm"}

关于抽象类的使用，以下为语法上要注意的细节，虽然条目较多，但若理解了抽象的本质，无需死记硬背。
{: id="20210309181757-6klrx2k"}

1. {: id="20210309181757-yetaflw"}抽象类**不能创建对象**，如果创建，编译无法通过而报错。只能创建其非抽象子类的对象。
   {: id="20210309181757-ykov6wk"}

   > 理解：假设创建了抽象类的对象，调用抽象的方法，而抽象方法没有具体的方法体，没有意义。
   > {: id="20210309181757-6rb9tl1"}
   >
   {: id="20210309181757-j27vary"}
2. {: id="20210309181757-hqsbuab"}抽象类中，也有构造方法，是供子类创建对象时，初始化父类成员变量使用的。
   {: id="20210309181757-6ajxfa6"}

   > 理解：子类的构造方法中，有默认的super()或手动的super(实参列表)，需要访问父类构造方法。
   > {: id="20210309181757-9q59llc"}
   >
   {: id="20210309181757-tptmb8k"}
3. {: id="20210309181757-nglto3f"}抽象类中，不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
   {: id="20210309181757-q7xjqkp"}

   > 理解：未包含抽象方法的抽象类，目的就是不想让调用者创建该类对象，通常用于某些特殊的类结构设计。
   > {: id="20210309181757-2qoh9w2"}
   >
   {: id="20210309181757-36o5ak1"}
4. {: id="20210309181757-vwmg2nr"}抽象类的子类，必须重写抽象父类中**所有的**抽象方法，否则，编译无法通过而报错。除非该子类也是抽象类。
   {: id="20210309181757-tmelq24"}

   > 理解：假设不重写所有抽象方法，则类中可能包含抽象方法。那么创建对象后，调用抽象的方法，没有意义。
   > {: id="20210309181757-h2jf9vl"}
   >
   {: id="20210309181757-3leelt4"}
{: id="20210309181757-j65n5m6"}

### 6.8.4 练习
{: id="20210309181757-dier15d"}

#### 1、练习1
{: id="20210309181757-ziic6l4"}

定义一个几何图形父类Graphic。所有几何图形都应该具备一个计算面积的方法。但是不同的几何图形计算面积的方式完全不同。
{: id="20210309181757-sep5knq"}

```java
abstract class Graphic{
	public abstract double getArea();
}
class Circle extends Graphic{
	private double radius;

	public Circle(double radius) {
		super();
		this.radius = radius;
	}

	public Circle() {
		super();
	}

	public double getRadius() {
		return radius;
	}

	public void setRadius(double radius) {
		this.radius = radius;
	}

	@Override
	public double getArea() {
		return Math.PI * radius * radius;
	}

}
class Rectangle extends Graphic{
	private double length;
	private double width;
	public Rectangle(double length, double width) {
		super();
		this.length = length;
		this.width = width;
	}
	public Rectangle() {
		super();
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
		return length * width;
	}
}
```
{: id="20210309181757-7t7z12e"}

#### 2、练习2
{: id="20210309181757-1vabgx4"}

1、声明抽象父类：Person，包含抽象方法：
public abstract void walk();
public abstract void eat();
{: id="20210309181757-22ds4ii"}

2、声明子类Man，继承Person
重写walk()：大步流星走路
重写eat()：狼吞虎咽吃饭
新增方法：public void smoke()实现为吞云吐雾
{: id="20210309181757-zvub3uz"}

3、声明子类Woman，继承Person
重写walk()：婀娜多姿走路
重写eat()：细嚼慢咽吃饭
新增方法：public void buy()实现为买买买...
{: id="20210309181757-0v8py7p"}

4、在测试类中创建子类对象，调用方法测试
{: id="20210309181757-tme7bu3"}

```java
public abstract class Person {
	public abstract void walk();
	public abstract void eat();
}

```
{: id="20210309181757-gbykzzh"}

```java
public class Man extends Person {

	@Override
	public void walk() {
		System.out.println("大步流星走路");
	}

	@Override
	public void eat() {
		System.out.println("狼吞虎咽吃饭");
	}

	public void smoke(){
		System.out.println("吞云吐雾");
	}
}
```
{: id="20210309181757-eeqwvm5"}

```java
public class Woman extends Person {

	@Override
	public void walk() {
		System.out.println("婀娜多姿走路");
	}

	@Override
	public void eat() {
		System.out.println("细嚼慢咽吃饭");
	}

	public void buy(){
		System.out.println("买买买...");
	}
}
```
{: id="20210309181757-okrt9ht"}

```java
public class TestExer1 {

	public static void main(String[] args) {
		Man m = new Man();
		m.eat();
		m.walk();
		m.smoke();

		System.out.println("-------------------------");

		Woman w = new Woman();
		w.eat();
		w.walk();
		w.buy();
	}

}
```
{: id="20210309181757-ptud9q3"}

## 6.9 多态
{: id="20210309181757-3ovm8kl"}

### 6.9.1 引入
{: id="20210309181757-jltiqol"}

多态是继封装、继承之后，面向对象的第三大特性。
{: id="20210309181757-964i0i0"}

生活中，比如求面积的功能，圆、矩形、三角形实现起来是不一样的。跑的动作，小猫、小狗和大象，跑起来是不一样的。再比如飞的动作，昆虫、鸟类和飞机，飞起来也是不一样的。可见，同一行为，通过不同的事物，可以体现出来的不同的形态。那么此时就会出现各种子类的类型。
{: id="20210309181757-zjwcs1i"}

但是Java是强类型静态语言，既每一个变量在使用之前必须声明它确切的类型，然后之后的赋值和运算时都是严格按照这个数据类型来处理的。例如：
{: id="20210309181757-jaeefe5"}

```java
int num = 10;
String str = "hello";
Student stu = new Student();
```
{: id="20210309181757-aegs64v"}

但是，有的时候，我们在设计一个数组、或一个方法的形参、返回值类型时，无法确定它具体的类型，只能确定它是某个系列的类型。
{: id="20210309181757-mp8i34f"}

例如：想要设计一个数组用来存储各种图形的对象，并且按照各种图形的面积进行排序，但是具体存储的对象可能有圆、矩形、三角形等，那么各种图形的求面积方式又是不同的。
{: id="20210309181757-cxx2rni"}

例如：想要设计一个方法，它的功能是比较两个图形的面积大小，返回面积较大的那个图形对象。那么此时形参和返回值类型是图形类型，但是不知道它具体是哪一种图形类型。
{: id="20210309181757-l80kgil"}

```java
Circle[] arr = new Circle[长度]; //只能装圆形对象
Rectangle[] arr = new Rectangle[长度]; //只能装矩形对象
//无法统一管理各种图形对象，例如：给各种图形对象按照面积排序


//需要重载很多个方法，增加一种具体的图形，就需要增加一个方法
public static Circle maxArea(Circle c1, Circle c2){//只能比较两个圆对象
  
}
public static Rectangle maxArea(Rectangle r1, Rectangle r2){//只能比较两个矩形对象
  
}
```
{: id="20210309181757-4q2eksa"}

这个时候，Java就引入了多态。
{: id="20210309181757-3xv6khn"}

### 6.9.2 定义
{: id="20210309181757-x7igvji"}

#### 1、格式
{: id="20210309181757-qp46v6w"}

```java
父类类型 变量名 = 子类对象；
```
{: id="20210309181757-ju6m00o"}

> 父类类型：指子类对象继承的父类类型，或者实现的父接口类型。
> {: id="20210309181757-p6p5ieq"}
{: id="20210309181757-0htxjfh"}

例如：
{: id="20210309181757-7ub0c8u"}

```java
class Person{
	private String name;
	private int age;

    Person(String name, int age){
        this.name = name;
        this.age = age;
    }
  
	public void speak(){
		System.out.println(name + "说：我今年" + age);
	}
}
class Man extends Person{
    Man(String name, int age){
        super(name,age);
    }
}
class Woman extends Person{
    Woman(String name, int age){
        super(name,age);
    }
}
```
{: id="20210309181757-hpogd0s"}

```java
class Test{
	public static void main(String[] args){
		Person[] arr = new Person[2];
		arr[0] = new Man("张三",23);
		arr[1] = new Woman("如花",18);

		for(int i=0; i<arr.length; i++){
			arr[i].speak();
		}
		System.out.println("------------------------");

		show(new Man("张三",23));
		show(new Woman("如花",18));
	}

	public static void show(Person p){
		p.speak();
	}
}
```
{: id="20210309181757-8zo0cfj"}

#### 2、编译时类型与运行时类型不一致问题
{: id="20210309181757-rp9tlbl"}

* {: id="20210309181757-wfaicgc"}**编译时，看“父类”**{: style="background-color: rgb(255, 253, 56);"}，只能调用父类声明的方法，不能调用子类扩展的方法；
  {: id="20210309181757-lsof5dw"}
* {: id="20210309181757-v4kmwqq"}**运行时，看“子类”**{: style="background-color: rgb(255, 253, 56);"}，一定是执行子类重写的方法体；
  {: id="20210309181757-ar8kiiz"}
{: id="20210309181757-haziqxe"}

代码如下：
{: id="20210309181757-hwdd47m"}

定义父类：
{: id="20210309181757-ni86jy2"}

```java
public abstract class Animal {  
    public abstract void eat();  
}  
```
{: id="20210309181757-imyrgtn"}

定义子类：
{: id="20210309181757-exe16td"}

```java
class Cat extends Animal {  
    public void eat() {  
        System.out.println("吃鱼");  
    }  
    public void catchMouse(){
        System.out.println("抓老鼠"); 
    }
}  

class Dog extends Animal {  
    public void eat() {  
        System.out.println("吃骨头");  
    }  
}
```
{: id="20210309181757-v81fgmh"}

定义测试类：
{: id="20210309181757-0brxjcg"}

```java
public class Test {
    public static void main(String[] args) {
        // 多态形式，创建对象
        Animal a1 = new Cat();  
        // 调用的是 Cat 的 eat
        a1.eat();  
        //a1.catchMouse();//错误，catchMouse()是子类扩展的方法，父类中没有
        /*
        多态引用，编译时，看“父类”，只能调用父类声明的方法；
        	    运行时，看“子类”，一定是执行子类重写的方法体；
        */

        // 多态形式，创建对象
        Animal a2 = new Dog(); 
        // 调用的是 Dog 的 eat
        a2.eat();   
    }  
}
```
{: id="20210309181757-cl903su"}

### 6.9.5 多态的应用
{: id="20210309181757-ys87x0y"}

#### 1、多态参数
{: id="20210309181757-34cxjh1"}

实际开发的过程中，父类类型作为方法形式参数，传递子类对象给方法，进行方法的调用，更能体现出多态的扩展性与便利。代码如下：
{: id="20210309181757-mholz20"}

定义父类：
{: id="20210309181757-2yglmb3"}

```java
public abstract class Animal {  
    public abstract void eat();  
}  
```
{: id="20210309181757-qfs0vh2"}

定义子类：
{: id="20210309181757-a6s2af5"}

```java
class Cat extends Animal {  
    public void eat() {  
        System.out.println("吃鱼");  
    }  
}  

class Dog extends Animal {  
    public void eat() {  
        System.out.println("吃骨头");  
    }  
}
```
{: id="20210309181757-9qi5aji"}

定义测试类：
{: id="20210309181757-uxzikvc"}

```java
public class Test {
    public static void main(String[] args) {
        // 多态形式，创建对象
        Cat c = new Cat();  
        Dog d = new Dog(); 

        // 调用showCatEat 
        showCatEat(c);
        // 调用showDogEat 
        showDogEat(d); 

        /*
        以上两个方法, 均可以被showAnimalEat(Animal a)方法所替代
        而执行效果一致
        */
        showAnimalEat(c);
        showAnimalEat(d); 
    }

    public static void showCatEat (Cat c){
        c.eat(); 
    }

    public static void showDogEat (Dog d){
        d.eat();
    }

    public static void showAnimalEat (Animal a){
        a.eat();
    }
}
```
{: id="20210309181757-grjywzm"}

由于多态特性的支持，showAnimalEat方法的Animal类型，是Cat和Dog的父类类型，父类类型接收子类对象，当然可以把Cat对象和Dog对象，传递给方法。
{: id="20210309181757-jq0ww1t"}

当eat方法执行时，多态规定，执行的是子类重写的方法，那么效果自然与showCatEat、showDogEat方法一致，所以showAnimalEat完全可以替代以上两方法。
{: id="20210309181757-89ildi0"}

不仅仅是替代，在扩展性方面，无论之后再多的子类出现，我们都不需要编写showXxxEat方法了，直接使用showAnimalEat都可以完成。
{: id="20210309181757-luhfk8d"}

所以，多态的好处，体现在，可以使程序编写的更简单，并有良好的扩展。
{: id="20210309181757-gtiouqi"}

#### 2、多态数组
{: id="20210309181757-kszdadc"}

例如：家里养了两只猫，两条狗，想要统一管理他们的对象，可以使用多态数组
{: id="20210309181757-ziynzf4"}

```java
public class TestAnimal {
	public static void main(String[] args) {
		Animal[] all = new Animal[4];//可以存储各种Animal子类的对象
		all[0] = new Cat();
		all[1] = new Cat();
		all[2] = new Dog();
		all[3] = new Dog();

		for (int i = 0; i < all.length; i++) {
			all[i].eat();//all[i]编译时是Animal类型，运行时看存储的是什么对象
		}
	}
}
```
{: id="20210309181757-o03f7ik"}

### 6.9.6 多态练习
{: id="20210309181757-nx5esce"}

#### 练习1：
{: id="20210309181757-qm3u8kp"}

（1）声明抽象父类Traffic，包含抽象方法public abstract void drive()
（2）声明子类Car,Bicycle等，并重写drive方法
（3）在测试类的main中创建一个数组，有各种交通工具，遍历调用drive()方法
模拟马路上跑的各种交通工具
{: id="20210309181757-9yp0fsw"}

```java
public abstract class Traffic {
	public abstract void drive();
}
```
{: id="20210309181757-7polzoh"}

```java
public class Car extends Traffic {
	@Override
	public void drive() {
		System.out.println("滴滴滴...");
	}
}
```
{: id="20210309181757-mfhzl63"}

```java
public class Bicycle extends Traffic {
	@Override
	public void drive() {
		System.out.println("蹬蹬蹬。。。");
	}
}
```
{: id="20210309181757-10t8e7s"}

```java
public class TestExer1 {
	public static void main(String[] args) {
		//右边这些是用匿名对象，初始化数组
		Traffic[] arr = {new Car(),new Bicycle(),new Car(),new Bicycle()};
		for (int i = 0; i < arr.length; i++) {
			arr[i].drive();
		}
	}
}
```
{: id="20210309181757-c5h2t7x"}

#### 练习2：
{: id="20210309181757-bgs7r14"}

（1）声明一个抽象父类Person类，public abstract void toilet();
（2）声明一个子类Woman类，重写方法
（3）声明一个子类Man类，重写方法
（4）在测试类中声明一个方法，
public static void goToToilet(Person p){
p.toilet();
}
在main中，创建不同子类对象，调用goToToilet方法进行测试
{: id="20210309181757-9w9nuzn"}

```java
public abstract class Person {
	public abstract void toilet();
}
```
{: id="20210309181757-xmeakz2"}

```java
public class Man extends Person {
	@Override
	public void toilet() {
		System.out.println("站着..");
	}
}
```
{: id="20210309181757-xq8c9c9"}

```java
public class Woman extends Person {
	@Override
	public void toilet() {
		System.out.println("坐着..");
	}
}
```
{: id="20210309181757-383o4op"}

```java
public class TestPerson {
	public static void main(String[] args) {
		goToToilet(new Woman());//隐含了Person p = new Woman();
		goToToilet(new Man());//隐含了Person p = new Man();
	}

	public static void goToToilet(Person p){
		p.toilet();
	}
}
```
{: id="20210309181757-5ijwux9"}

#### 练习3：
{: id="20210309181757-h3el3ao"}

1、声明一个父类Employee员工类型，有属性，姓名（String）
有方法，public abstract double earning() 用于返回实发工资
public String getInfo()：显示姓名和实发工资
{: id="20210309181757-dpbnf39"}

2、声明一个子类SalaryEmployee正式工，继承父类Employee，增加属性，薪资，工作日天数，请假天数
重写方法，public double earning()返回实发工资，实发工资 = 薪资 - 薪资/工作日天数 * 请假天数，
{: id="20210309181757-lk4dfn9"}

3、声明一个子类HourEmployee小时工，继承父类Employee
有属性，工作小时数，每小时多少钱
重写方法，public double earning()返回实发工资， 实发工资 = 每小时多少钱 * 小时数
{: id="20210309181757-wiqguxv"}

4、声明一个子类Manager经理，继承SalaryEmployee，增加属性：奖金比例
重写方法，public double earning()返回实发工资，实发工资 = (薪资 - 薪资/工作日天数 * 请假天数)*(1+奖金比例)
{: id="20210309181757-kj84nu0"}

5、你现在是财务，需要查看每个人的实发工资，并查看工资总额。
声明一个员工数组，存储各种员工，并遍历显示他们的姓名和实发工资，并计算所有员工的工资总额
{: id="20210309181757-02i27q3"}

```java
public abstract class Employee {
	private String name;

	public Employee(String name) {
		super();
		this.name = name;
	}

	public Employee() {
		super();
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public abstract double earning();

	public String getInfo() {
		return "姓名：" + name + "，实发工资：" + earning();
	}
}
```
{: id="20210309181757-41j2ist"}

```java
public class SalaryEmployee extends Employee {
	private double salary;
	private int workingDays;//工作日天数，
	private double offDays;//请假天数

	public SalaryEmployee() {
		super();
	}

	public SalaryEmployee(String name,  double salary, int workingDays, double offDays) {
		super(name);
		this.salary = salary;
		this.workingDays = workingDays;
		this.offDays = offDays;
	}

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public int getWorkingDays() {
		return workingDays;
	}

	public void setWorkingDays(int workingDays) {
		this.workingDays = workingDays;
	}

	public double getOffDays() {
		return offDays;
	}

	public void setOffDays(double offDays) {
		this.offDays = offDays;
	}

	/*
	 * 重写方法，public double earning()返回实发工资， 
		实发工资 = 薪资 - 薪资/工作日天数 * 请假天数
	 */
	@Override
	public double earning() {
		return salary - salary/workingDays * offDays;
	}

}
```
{: id="20210309181757-ul3e72e"}

```java
public class HourEmployee extends Employee {
	private double moneyPerHour;
	private double hours;

	public HourEmployee() {
		super();
	}

	public HourEmployee(String name, double moneyPerHour, double hours) {
		super(name);
		this.moneyPerHour = moneyPerHour;
		this.hours = hours;
	}

	public double getMoneyPerHour() {
		return moneyPerHour;
	}

	public void setMoneyPerHour(double moneyPerHour) {
		this.moneyPerHour = moneyPerHour;
	}

	public double getHours() {
		return hours;
	}

	public void setHours(double hours) {
		this.hours = hours;
	}

	/*
	 * 重写方法，public double earning()返回实发工资， 
		实发工资 = 每小时多少钱 * 小时数
	 */
	@Override
	public double earning() {
		return moneyPerHour * hours;
	}

}

```
{: id="20210309181757-cqiolte"}

```java
public class Manager extends SalaryEmployee {
	private double commisionPer;

	public Manager() {
		super();
	}

	public Manager(String name,  double salary, int workingDays, double offDays, double commisionPer) {
		super(name, salary, workingDays, offDays);
		this.commisionPer = commisionPer;
	}

	public double getCommisionPer() {
		return commisionPer;
	}

	public void setCommisionPer(double commisionPer) {
		this.commisionPer = commisionPer;
	}

	@Override
	public double earning() {
		return super.earning() * (1+commisionPer);
	}
}
```
{: id="20210309181757-0vpqzlq"}

```java
public class TestEmployee {
	public static void main(String[] args) {
		Employee[] all = new Employee[3];

		all[0] = new HourEmployee("张三", 50, 50);
		all[1] = new SalaryEmployee("李四", 10000, 22, 1);
		all[2] = new Manager("老王", 20000, 22, 0, 0.3);

		double sum = 0;
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i].getInfo());
			sum += all[i].earning();
		}
		System.out.println("总额：" + sum);
	}
}
```
{: id="20210309181757-d48y5tv"}

### 6.9.7 父子类之间的类型转换
{: id="20210309181757-hsbjcge"}

#### 1、向上转型
{: id="20210309181757-q8leucr"}

* {: id="20210309181757-v7yot0h"}当父类引用指向一个子类对象时，便是向上转型。这个过程是自动完成的
  {: id="20210309181757-f0s2n0a"}
{: id="20210309181757-7is5hjw"}

使用格式：
{: id="20210309181757-eojxu4u"}

```java
父类类型  变量名 = new 子类类型();
如：Animal a = new Cat();
```
{: id="20210309181757-x8vg423"}

> 注意：此时通过父类的变量就只能调用父类中有的方法，不能调用子类特有的方法了
> {: id="20210309181757-eha7hq8"}
{: id="20210309181757-a9av1sc"}

#### 2、向下转型
{: id="20210309181757-zrmzral"}

* {: id="20210309181757-kp35nmz"}**向下转型**：父类类型向子类类型向下转换的过程，这个过程是强制的。
  {: id="20210309181757-6waf9yy"}
{: id="20210309181757-crc9272"}

使用格式：
{: id="20210309181757-vo6laaa"}

```java
子类类型 变量名 = (子类类型) 父类变量名;
如:Cat c =(Cat) a;  
```
{: id="20210309181757-46gyjke"}

**为什么要向下转型？**
{: id="20210309181757-o94tmk9"}

当使用多态方式调用方法时，首先检查父类中是否有该方法，如果没有，则编译错误。也就是说，**不能调用**子类拥有，而父类没有的方法。编译都错误，更别说运行了。这也是多态给我们带来的一点"小麻烦"。所以，想要调用子类特有的方法，必须做向下转型。
{: id="20210309181757-53osicu"}

转型演示，代码如下：
{: id="20210309181757-lxk1c7e"}

定义类：
{: id="20210309181757-q5jahdk"}

```java
abstract class Animal {  
    abstract void eat();  
}  

class Cat extends Animal {  
    public void eat() {  
        System.out.println("吃鱼");  
    }  
    public void catchMouse() {  
        System.out.println("抓老鼠");  
    }  
}  

class Dog extends Animal {  
    public void eat() {  
        System.out.println("吃骨头");  
    }  
    public void watchHouse() {  
        System.out.println("看家");  
    }  
}
```
{: id="20210309181757-bbnaq17"}

定义测试类：
{: id="20210309181757-7e5gr4u"}

```java
public class Test {
    public static void main(String[] args) {
        // 向上转型  
        Animal a = new Cat();  
        a.eat(); 				// 调用的是 Cat 的 eat

        // 向下转型  
        Cat c = (Cat)a;   
        c.catchMouse(); 		// 调用的是 Cat 的 catchMouse
    }  
}
```
{: id="20210309181757-xn78cwt"}

#### 3、转型的异常：ClassCastException
{: id="20210309181757-o2rfmgt"}

转型的过程中，一不小心就会遇到这样的问题，请看如下代码：
{: id="20210309181757-xpm75ni"}

```java
public class Test {
    public static void main(String[] args) {
        // 向上转型  
        Animal a = new Cat();  
        a.eat();               // 调用的是 Cat 的 eat

        // 向下转型  
        Dog d = (Dog)a;   
        d.watchHouse();        // 调用的是 Dog 的 watchHouse 【运行报错】
    }  
}
```
{: id="20210309181757-yf5htez"}

这段代码可以通过编译，但是运行时，却报出了 `ClassCastException` ，类型转换异常！这是因为，明明创建了Cat类型对象，运行时，当然不能转换成Dog对象的。这两个类型并没有任何继承关系，不符合类型转换的定义。
{: id="20210309181757-ok2hg1r"}

> 注意：不管是向上还是向下转型都只是针对编译时类型来说的，不是真的类型转换，即运行时类型不变，一开始new的是什么类型还是什么类型。
> {: id="20210309181757-ohv01m6"}
{: id="20210309181757-1ewo9rh"}

#### 4、instanceof运算符
{: id="20210309181757-wdu6kxc"}

为了避免ClassCastException的发生，Java提供了 `instanceof` 关键字，给引用变量做类型的校验，只要用instanceof判断返回true的，那么强转为该类型就一定是安全的，不会报ClassCastException异常。
{: id="20210309181757-re938kn"}

格式如下：
{: id="20210309181757-pafvr64" updated="20210309200955"}

> 变量名/对象 instanceof 数据类型（引用）
> {: id="20210309200946-32staq2" updated="20210309201016"}
>
> 如果变量/对象属于该数据类型，返回true。
> 如果变量/对象不属于该数据类型，返回false。
> {: id="20210309181757-8mxjidt" updated="20210309200946"}
{: id="20210309200952-gfyvh1x"}

所以，转换前，我们最好先做一个判断，代码如下：
{: id="20210309181757-yxakudh"}

```java
public class Test {
    public static void main(String[] args) {
        // 向上转型  
        Animal a = new Cat();  
        a.eat();               // 调用的是 Cat 的 eat

        // 向下转型  
        if (a instanceof Cat){
            Cat c = (Cat)a;   
            c.catchMouse();        // 调用的是 Cat 的 catchMouse
        } else if (a instanceof Dog){
            Dog d = (Dog)a;   
            d.watchHouse();       // 调用的是 Dog 的 watchHouse
        }
    }  
}
```
{: id="20210309181757-vm012sr"}

哪些情况下instanceof判断返回true
{: id="20210309181757-zfx9381"}

示例代码：
{: id="20210309181757-1t11ryi"}

```java
class Person{
	//方法代码省略...
}
class Woman extends Person{
    //方法代码省略...
}
class ChineseWoman extends Woman{
	//方法代码省略...
}
```
{: id="20210309181757-y7m81qi"}

```java
 public class Test{
     public static void main(String[] args){
         Person p1 = new Person();
         Person p2 = new Woman();
         Person p3 = new ChineseWoman();
   
         if(p1 instanceof Woman){//false
   
         }
         if(p2 instanceof Woman){//true
             //p2转为Woman类型安全
         }
         if(p3 instanceof Woman){//true
             //p3转为Woman类型安全
         }
     }
 }
```
{: id="20210309181757-9rlkgz9"}

#### 5、练习
{: id="20210309181757-bqaqd1u"}

1、声明一个父类Employee员工类型，
有属性，姓名（String），出生日期（MyDate类型，也是自定义的含年，月，日属性日期类型）
有方法，public abstract double earning()
public String getInfo()：显示姓名和实发工资
{: id="20210309181757-5k6u3dp"}

2、声明一个子类SalaryEmployee正式工，继承父类Employee
增加属性，薪资，工作日天数，请假天数
重写方法，public double earning()返回实发工资， 实发工资 = 薪资 - 薪资/工作日天数 * 请假天数，
重写方法，public String getInfo()：显示姓名和实发工资，月薪，工作日天数，请假天数
{: id="20210309181757-s9kis9c"}

3、声明一个子类HourEmployee小时工，继承父类Employee
有属性，工作小时数，每小时多少钱
重写方法，public double earning()返回实发工资， 实发工资 = 每小时多少钱 * 小时数
重写方法，public String getInfo()：显示姓名和实发工资，时薪，工作小时数
增加方法，public void leave()：打印查看使用工具是否损坏，需要赔偿
{: id="20210309181757-wik8io0"}

4、声明一个子类Manager经理，继承SalaryEmployee
增加属性：奖金，奖金比例
重写方法，public double earning()返回实发工资， 实发工资 = (薪资 - 薪资/工作日天数 * 请假天数)*(1+奖金比例)
重写方法，public String getInfo()：显示姓名和实发工资，月薪，工作日天数，请假天数，奖金比例
{: id="20210309181757-ucvrnpg"}

5、声明一个员工数组，存储各种员工，
你现在是人事，从键盘输入当前的月份，需要查看每个人的详细信息。
如果他是正式工（包括SalaryEmployee和Manager），并且是本月生日的，祝福生日快乐，通知领取生日礼物。如果是HourEmployee显示小时工，就进行完工检查，即调用leave方法
{: id="20210309181757-mfitq88"}

```java
public abstract class Employee {
	private String name;
	private MyDate birthday;
	public Employee(String name, MyDate birthday) {
		super();
		this.name = name;
		this.birthday = birthday;
	}
	public Employee(String name, int year, int month, int day) {
		super();
		this.name = name;
		this.birthday = new MyDate(year, month, day);
	}
	public Employee() {
		super();
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public MyDate getBirthday() {
		return birthday;
	}
	public void setBirthday(MyDate birthday) {
		this.birthday = birthday;
	}

	public abstract double earning();

	public String getInfo(){
		return "姓名：" + name + "，生日：" + birthday.getInfo() +"，实发工资：" + earning();
	}
}
```
{: id="20210309181757-jhym0le"}

```java
public class SalaryEmployee extends Employee {
	private double salary;
	private int workingDays;//工作日天数，
	private double offDays;//请假天数

	public SalaryEmployee() {
		super();
	}

	public SalaryEmployee(String name, int year, int month, int day, double salary, int workingDays, double offDays) {
		super(name, year, month, day);
		this.salary = salary;
		this.workingDays = workingDays;
		this.offDays = offDays;
	}

	public SalaryEmployee(String name, MyDate birthday, double salary, int workingDays, double offDays) {
		super(name, birthday);
		this.salary = salary;
		this.workingDays = workingDays;
		this.offDays = offDays;
	}

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public int getWorkingDays() {
		return workingDays;
	}

	public void setWorkingDays(int workingDays) {
		this.workingDays = workingDays;
	}

	public double getOffDays() {
		return offDays;
	}

	public void setOffDays(double offDays) {
		this.offDays = offDays;
	}

	/*
	 * 重写方法，public double earning()返回实发工资， 
		实发工资 = 薪资 - 薪资/工作日天数 * 请假天数
	 */
	@Override
	public double earning() {
		return salary - salary/workingDays * offDays;
	}

	@Override
	public String getInfo() {
		return super.getInfo() + "，月薪：" + salary + "，工作日：" + workingDays +"，请假天数：" + offDays;
	}
}
```
{: id="20210309181757-ivfwe6t"}

```java
public class HourEmployee extends Employee {
	private double moneyPerHour;
	private double hours;

	public HourEmployee() {
		super();
	}

	public HourEmployee(String name, int year, int month, int day, double moneyPerHour, double hours) {
		super(name, year, month, day);
		this.moneyPerHour = moneyPerHour;
		this.hours = hours;
	}

	public HourEmployee(String name, MyDate birthday, double moneyPerHour, double hours) {
		super(name, birthday);
		this.moneyPerHour = moneyPerHour;
		this.hours = hours;
	}

	public double getMoneyPerHour() {
		return moneyPerHour;
	}

	public void setMoneyPerHour(double moneyPerHour) {
		this.moneyPerHour = moneyPerHour;
	}

	public double getHours() {
		return hours;
	}

	public void setHours(double hours) {
		this.hours = hours;
	}

	/*
	 * 重写方法，public double earning()返回实发工资， 
		实发工资 = 每小时多少钱 * 小时数
	 */
	@Override
	public double earning() {
		return moneyPerHour * hours;
	}

	@Override
	public String getInfo() {
		return super.getInfo() + "，时薪：" + moneyPerHour + "，小时数：" + hours;
	}

	public void leave(){
		System.out.println("小时工，查看使用工具是否损坏，需要赔偿，然后拿钱走人");
	}
}

```
{: id="20210309181757-pe19stl"}

```java
public class Manager extends SalaryEmployee {
	private double commisionPer;

	public Manager() {
		super();
	}

	public Manager(String name, int year, int month, int day, double salary, int workingDays, double offDays,
			double commisionPer) {
		super(name, year, month, day, salary, workingDays, offDays);
		this.commisionPer = commisionPer;
	}

	public Manager(String name, MyDate birthday, double salary, int workingDays, double offDays, double commisionPer) {
		super(name, birthday, salary, workingDays, offDays);
		this.commisionPer = commisionPer;
	}

	public double getCommisionPer() {
		return commisionPer;
	}

	public void setCommisionPer(double commisionPer) {
		this.commisionPer = commisionPer;
	}

	@Override
	public double earning() {
		return super.earning() * (1+commisionPer);
	}
	@Override
	public String getInfo() {
		return super.getInfo() + "，奖金比例：" + commisionPer;
	}
}

```
{: id="20210309181757-7cje7bo"}

```java
public class TestEmployee {
	public static void main(String[] args) {
		Employee[] all = new Employee[3];
		/*all[0] = new HourEmployee("张三", new MyDate(1990, 5, 1), 50, 50);
		all[1] = new SalaryEmployee("李四", new MyDate(1991, 1, 1), 10000, 22, 1);
		all[2] = new Manager("老王", new MyDate(1987, 12, 8), 20000, 22, 0, 0.3);*/

		all[0] = new HourEmployee("张三", 1990, 5, 1, 50, 50);
		all[1] = new SalaryEmployee("李四", 1991, 1, 1, 10000, 22, 1);
		all[2] = new Manager("老王", 1987, 12, 8, 20000, 22, 0, 0.3);

		//从键盘输入当前的月份
		Scanner input = new Scanner(System.in);
		System.out.print("请输入当前月份：");
		int month;
		while(true){
			month = input.nextInt();
			if(month>=1 && month<=12){
				break;
			}
		}
		input.close();

		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i].getInfo());
			if(all[i] instanceof SalaryEmployee){
				if(month == all[i].getBirthday().getMonth()){
					System.out.println(all[i].getName() +"生日快乐，领取生日补助购物卡");
				}
			}else{
				HourEmployee he = (HourEmployee) all[i];
				he.leave();
			}
		}
	}
}
```
{: id="20210309181757-tnjphfq"}

### 6.9.8 多态引用时关于成员变量与成员方法引用的原则
{: id="20210309181757-x5a5w3w"}

#### 1、**成员变量**{: style="background-color: rgb(255, 253, 56);"}：只看编译时类型
{: id="20210309181757-uumhtka" updated="20210309201520"}

如果直接访问成员变量，那么只看编译时类型
{: id="20210309181757-08g7gr3"}

```java
public class TestField {
	public static void main(String[] args) {
		Father f = new Son();
		System.out.println(f.x);//只看编译时类型
	}
}
class Father{
	int x = 1;
}
class Son extends Father{
	int x = 2;
}

1
```
{: id="20210309181757-20zn36g" updated="20210309201337"}

#### 2、**非虚方法**{: style="background-color: rgb(255, 253, 56);"}：只看编译时类型
{: id="20210309181757-nw2lc0b"}

如果方法在编译期就确定了具体的调用版本，这个版本在运行时是不可变的，这样的方法称为非虚方法。其他方法称为虚方法。
{: id="20210309181757-61lyiz5"}

* {: id="20210309181757-yqjzppi"}静态方法、私有方法、final方法、实例构造器、通过super调用的父类方法都是非虚方法。
  {: id="20210309181757-albnvec"}

  * {: id="20210309181757-p1awvt1"}静态方法与类型直接关联
    {: id="20210309181757-hdaiafm"}
  * {: id="20210309181757-pskxqf6"}私有方法在外部不可访问
    {: id="20210309181757-gpo4yfu"}
  * {: id="20210309181757-grkl6ul"}final不可被继承
    {: id="20210309181757-4si6gis"}
  {: id="20210309181757-g9mfu20"}
{: id="20210309181757-de51rxy"}

```java
public class TestField {
	public static void main(String[] args) {
		Father f = new Son();
		f.test();//只看编译时类型
	}
}
class Father{
	public static void test(){
		System.out.println("father");
	}
}
class Son extends Father{
	public static void test(){
		System.out.println("son");
	}
}
```
{: id="20210309181757-chcwb6r"}

> 小贴士：
> {: id="20210309181757-n8ann96"}
>
> 静态方法不能被重写
> {: id="20210309181757-hqg5qvu"}
>
> 调用静态方法最好使用“类名.”
> {: id="20210309181757-czu6u79"}
{: id="20210309181757-mtna7d7"}

#### 3、**虚方法**{: style="background-color: rgb(255, 253, 56);"}：静态分派与动态绑定
{: id="20210309181757-y1ubgmu"}

**引用为静态，作为形参传递时，优先引用类型就近匹配原则。**{: style="color: rgb(252, 13, 27);"}
{: id="20210309201618-6r82jqf" updated="20210309201811"}

**实际调用方法向下层搜索在递归回查到父类搜索方法，调用第一次找到的方法**{: style="color: rgb(252, 13, 27);"}
{: id="20210309201812-7u34ndb" updated="20210309201812"}

##### （1）示例一：重写
{: id="20210309181757-r3zp7vs"}

```java
abstract class Animal {  
    public abstract void eat();  
}  
class Cat extends Animal {  
    public void eat() {  
        System.out.println("吃鱼");  
    }  
}  

class Dog extends Animal {  
    public void eat() {  
        System.out.println("吃骨头");  
    }  
}

public class Test{
    public static void main(String[] args){
        Animal a = new Cat();
        a.eat();
    }
}
```
{: id="20210309181757-l6fyvcs"}

如上代码在编译期间先进行静态分派：即确定是调用Animal类中的public void eat()方法，如果Animal类或它的父类中没有这个方法，将会报错。
{: id="20210309181757-dfrrlya"}

而在运行期间动态的在进行动态分派：即确定执行的是Cat类中的public void eat()方法，因为子类重写了eat()方法，如果没有重写，那么还是执行Animal类在的eat()方法
{: id="20210309181757-71hh1f5"}

##### （2）示例二：重载
{: id="20210309181757-5p9hyv4"}

```java
class MyClass{
	public void method(Father f) {
		System.out.println("father");
	}
	public void method(Son s) {
		System.out.println("son");
	}
	public void method(Daughter f) {
		System.out.println("daughter");
	}
}
class Father{

}
class Son extends Father{

}
class Daughter extends Father{

}
```
{: id="20210309181757-uzytc7t"}

```java
public class TestOverload {
	public static void main(String[] args) {
		MyClass my = new MyClass();
		Father f = new Father();
		Father s = new Son();
		Father d = new Daughter();
  
		my.method(f);//father
		my.method(s);//father
		my.method(d);//father
	}
}
```
{: id="20210309181757-fsiexwt"}

如上代码在编译期间先进行静态分派：即确定是调用MyClass类中的method(Father f)方法，如果Animal类或它的父类中没有这个方法，将会报错。
{: id="20210309181757-mur602f"}

而在运行期间动态的在进行动态分派：即确定执行的是MyClass类中的method(Father f)方法，因为my对象的运行时类型还是MyClass类型。
{: id="20210309181757-dp2r00w"}

**有些同学会疑问，不是应该分别执行method(Father f)、method(Son s)、method(Daughter d)吗？**
{: id="20210309181757-i5gfcvy"}

**因为此时f,s,d编译时类型都是Father类型，因此method(Father f)是最合适的。**
{: id="20210309181757-0cudspo"}

##### （3）示例三：重载
{: id="20210309181757-pvzbxg5"}

```
class MyClass{
	public void method(Father f) {
		System.out.println("father");
	}
	public void method(Son s) {
		System.out.println("son");
	}
}
class Father{

}
class Son extends Father{

}
class Daughter extends Father{

}
```
{: id="20210309181757-a2qbrlm"}

```java
public class TestOverload {
	public static void main(String[] args) {
		MyClass my = new MyClass();
		Father f = new Father();
		Son s = new Son();
		Daughter d = new Daughter();
		my.method(f);//father
		my.method(s);//son
		my.method(d);//father
	}
}
```
{: id="20210309181757-qm6mhqo"}

如上代码在编译期间先进行静态分派：即确定是分别调用MyClass类中的method(Father f)，method(Son s)，method(Father f)方法。
{: id="20210309181757-ayge8fq"}

而在运行期间动态的在进行动态分派：即确定执行的是MyClass类中的method(Father f)，method(Son s)，method(Father f)方法，因为my对象的运行时类型还是MyClass类型。
{: id="20210309181757-0qvuwe1"}

**有些同学会疑问，这次为什么分别执行method(Father f)、method(Son s)？**
{: id="20210309181757-8qb3aw5"}

**因为此时f,s,d编译时类型分别是Father、Son、Daughter，而Daughter只能与Father参数类型匹配**
{: id="20210309181757-84oed64"}

##### （4）示例四：重载与重写
{: id="20210309181757-yjz2cv1"}

```java
class MyClass{
	public void method(Father f) {
		System.out.println("father");
	}
	public void method(Son s) {
		System.out.println("son");
	}
}
class MySub extends MyClass{
	public void method(Daughter d) {
		System.out.println("daughter");
	}
}
class Father{

}
class Son extends Father{

}
class Daughter extends Father{

}
```
{: id="20210309181757-grbxshp"}

```java
public class TestOverload {
	public static void main(String[] args) {
		MyClass my = new MySub();
		Father f = new Father();
		Son s = new Son();
		Daughter d = new Daughter();
		my.method(f);//father
		my.method(s);//son
		my.method(d);//father
	}
}
```
{: id="20210309181757-9k81xy1"}

如上代码在编译期间先进行静态分派：即确定是分别调用MyClass类中的method(Father f)，method(Son s)，method(Father f)方法。
{: id="20210309181757-bt6pire"}

而在运行期间动态的在进行动态分派：即确定执行的是MyClass类中的method(Father f)，method(Son s)，method(Father f)方法。
{: id="20210309181757-ck54dho"}

**有些同学会疑问，my对象不是MySub类型吗，而MySub类型中有method(Daughter d)方法，那么my.method(d)语句应该执行MySub类型中的method(Daughter d)方法？**
{: id="20210309181757-sc1ae5b"}

* {: id="20210309181757-96lc0bl"}my变量在编译时类型是MyClass类型，那么在MyClass类中，只有method(Father f)，method(Son s)方法，
  {: id="20210309181757-lpfst45"}
* {: id="20210309181757-0acyl24"}f,s,d变量编译时类型分别是Father、Son、Daughter，而Daughter只能与Father参数类型匹配
  {: id="20210309181757-w5m93n4"}
* {: id="20210309181757-zziemj3"}而在MySub类中并没有重写method(Father f)方法，所以仍然执行MyClass类中的method(Father f)方法
  {: id="20210309181757-ylfalex"}
{: id="20210309181757-0b6c5b7"}

##### （5）结论
{: id="20210309181757-rn25xyj"}

方法的分派有两个需要考虑的因素：
{: id="20210309181757-w6tw8rx"}

* {: id="20210309181757-ljr0mv7"}方法的参数：在编译期间确定，根据编译器时类型，找最匹配的
  {: id="20210309181757-zpw2rsh"}
* {: id="20210309181757-xruzl3w"}方法的所有者：
  {: id="20210309181757-lyyvk37"}

  * {: id="20210309181757-yx3q5t7"}如果没有重写，就按照编译时类型处理
    {: id="20210309181757-8xx1r76"}
  * {: id="20210309181757-e6f3n82"}如果有重写，就按照运行时类型处理
    {: id="20210309181757-isny34g"}
  {: id="20210309181757-8tscc1o"}
{: id="20210309181757-u28i2ij"}

## 6.10 native关键字
{: id="20210309181757-cop8r6y"}

native：本地的，原生的
用法：
{: id="20210309181757-nrc4z44"}

```
只能修饰方法
```
{: id="20210309181757-7hhu63w"}

```
表示这个方法的方法体代码不是用Java语言实现的，而是由C/C++语言编写的。
```
{: id="20210309181757-5kwwk9w"}

```
但是对于Java程序员来说，可以当做Java的方法一样去正常调用它，或者子类重写它。
```
{: id="20210309181757-wtwsvz5"}

JVM内存的管理：
{: id="20210309181757-adue4s3"}

![](imgs9/1561465258546.png)
{: id="20210309181757-p7a312l"}

| 区域名称   | 作用                                                                                                                             |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| 程序计数器 | 程序计数器是CPU中的寄存器，它包含每一个线程下一条要执行的指令的地址                                                              |
| 本地方法栈 | 当程序中调用了native的本地方法时，本地方法执行期间的内存区域                                                                     |
| 方法区     | 存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。                                                       |
| 堆内存     | 存储对象（包括数组对象），new来创建的，都存储在堆内存。                                                                          |
| 虚拟机栈   | 用于存储正在执行的每个Java方法的局部变量表等。局部变量表存放了编译期可知长度的各种基本数据类型、对象引用，方法执行完，自动释放。 |
{: id="20210309181757-i34v6j9"}

### 修饰符一起使用问题？
{: id="20210309181757-p7hd2l4"}

|           | 外部类 | 成员变量 | 代码块 | 构造器 | 方法 | 局部变量 |
| ----------- | -------- | ---------- | -------- | -------- | ------ | ---------- |
| public    | √     | √       | ×     | √     | √   | ×       |
| protected | ×     | √       | ×     | √     | √   | ×       |
| private   | ×     | √       | ×     | √     | √   | ×       |
| static    | ×     | √       | √     | ×     | √   | ×       |
| final     | √     | √       | ×     | ×     | √   | √       |
| abstract  | √     | ×       | ×     | ×     | √   | ×       |
| native    | ×     | ×       | ×     | ×     | √   | ×       |
{: id="20210309181757-8f4lune"}

不能和abstract一起使用的修饰符？
{: id="20210309181757-oornnwm"}

（1）abstract和**final**不能一起修饰**方法和类**
{: id="20210309181757-ygu4x2z"}

（2）abstract和**static**不能一起修饰**方法**
{: id="20210309181757-2272eti"}

（3）abstract和**native**不能一起修饰**方法**
{: id="20210309181757-0m94ll4"}

（4）abstract和**private**不能一起修饰**方法**
{: id="20210309181757-vgw88ui"}

static和final一起使用：
{: id="20210309181757-dsyer9a"}

（1）修饰方法：可以，因为都不能被重写
{: id="20210309181757-7c755s0"}

（2）修饰成员变量：可以，表示静态常量
{: id="20210309181757-gppd5lb"}

（3）修饰局部变量：不可以，static不能修饰局部变量
{: id="20210309181757-455snll"}

（4）修饰代码块：不可以，final不能修改代码块
{: id="20210309181757-zhs7yli"}

（5）修饰内部类：可以一起修饰成员内部类，不能一起修饰局部内部类（后面讲）
{: id="20210309181757-1ivbl6m"}

## 6.11  Object根父类
{: id="20210309181757-aul7rci"}

### 6.11.1 如何理解根父类
{: id="20210309181757-x7u5ct0"}

类 `java.lang.Object`是类层次结构的根类，即所有类的父类。每个类都使用 `Object` 作为超类。
{: id="20210309181757-m5hkdx1"}

* {: id="20210309181757-mo7p756"}Object类型的变量与除Object以外的任意引用数据类型的对象都多态引用
  {: id="20210309181757-nidy41q"}
* {: id="20210309181757-4ivqgwa"}所有对象（包括数组）都实现这个类的方法。
  {: id="20210309181757-eue5lxx"}
* {: id="20210309181757-evck22w"}如果一个类没有特别指定父类，那么默认则继承自Object类。例如：
  {: id="20210309181757-pv2a4lu"}
{: id="20210309181757-lh44lt3"}

```java
public class MyClass /*extends Object*/ {
  	// ...
}
```
{: id="20210309181757-ahm3dt7"}

### 6.11.2 Object类的API
{: id="20210309181757-isr5mi9"}

```

```
{: id="20210309184209-x5ysdcb"}

**API(Application Programming Interface)**，应用程序编程接口。Java API是一本程序员的`字典` ，是JDK中提供给我们使用的类的说明文档。所以我们可以通过查询API的方式，来学习Java提供的类，并得知如何使用它们。在API文档中是无法得知这些类具体是如何实现的，如果要查看具体实现代码，那么我们需要查看**src源码**。
{: id="20210309181757-61y9wb0"}

```
根据JDK源代码及Object类的API文档，Object类当中包含的方法有11个。今天我们主要学习其中的5个：
```
{: id="20210309181757-hrgnrid"}

#### （1）toString()
{: id="20210309181757-6m0h5ft"}

public String toString()
{: id="20210309181757-ayvroi4"}

①默认情况下，toString()返回的是“对象的运行时类型 @ 对象的hashCode值的十六进制形式"
{: id="20210309181757-sdgt7jw"}

②通常是建议重写，如果在eclipse中，可以用Alt +Shift + S-->Generate toString()
{: id="20210309181757-rcktdve"}

③如果我们直接System.out.println(对象)，默认会自动调用这个对象的toString()
{: id="20210309181757-dmm8ifr"}

> 因为Java的引用数据类型的变量中存储的实际上时对象的内存地址，但是Java对程序员隐藏内存地址信息，所以不能直接将内存地址显示出来，所以当你打印对象时，JVM帮你调用了对象的toString()。
> {: id="20210309181757-9wboy8k"}
{: id="20210309181757-gofr8ky"}

例如自定义的Person类：
{: id="20210309181757-7wmbg7a"}

```java
public class Person {  
    private String name;
    private int age;

    @Override
    public String toString() {
        return "Person{" + "name='" + name + '\'' + ", age=" + age + '}';
    }

    // 省略构造器与Getter Setter
}
```
{: id="20210309181757-54yo1ak"}

#### （2）getClass()
{: id="20210309181757-jm23wa0"}

public final Class<?> getClass()：获取对象的运行时类型
{: id="20210309181757-msw2cgs"}

> 因为Java有多态现象，所以一个引用数据类型的变量的编译时类型与运行时类型可能不一致，因此如果需要查看这个变量实际指向的对象的类型，需要用getClass()方法
> {: id="20210309181757-zqgnnvq"}
{: id="20210309181757-bolegu4"}

```java
	public static void main(String[] args) {
		Object obj = new String();
		System.out.println(obj.getClass());//运行时类型
	}
```
{: id="20210309181757-79b0iuk"}

#### （3）finalize()
{: id="20210309181757-c32fkd8"}

protected void finalize()：用于最终清理内存的方法
{: id="20210309181757-6lacf90"}

```java
public class TestFinalize {
	public static void main(String[] args) {
		for (int i = 0; i < 10; i++) {
			MyData my = new MyData();
		}

		System.gc();//通知垃圾回收器来回收垃圾

		try {
			Thread.sleep(2000);//等待2秒再结束main，为了看效果
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	}
}
class MyData{

	@Override
	protected void finalize() throws Throwable {
		System.out.println("轻轻的我走了...");
	}

}
```
{: id="20210309181757-ubl7fq3"}

面试题：对finalize()的理解？
{: id="20210309181757-o1b1mku"}

* {: id="20210309181757-g5eztp8"}当对象被GC确定为要被回收的垃圾，在回收之前由GC帮你调用这个方法，不是由程序员手动调用。
  {: id="20210309181757-sxk4d5v"}
* {: id="20210309181757-ymaxatp"}这个方法与C语言的析构函数不同，C语言的析构函数被调用，那么对象一定被销毁，内存被回收，而finalize方法的调用不一定会销毁当前对象，因为可能在finalize()中出现了让当前对象“复活”的代码
  {: id="20210309181757-5qun3o9"}
* {: id="20210309181757-7bbryv6"}每一个对象的finalize方法只会被调用一次。
  {: id="20210309181757-de7c88p"}
* {: id="20210309181757-s7zdb4i"}子类可以选择重写，一般用于彻底释放一些资源对象，而且这些资源对象往往时通过C/C++等代码申请的资源内存
  {: id="20210309181757-lf6zml5"}
{: id="20210309181757-zxgghk9"}

#### （4）hashCode()
{: id="20210309181757-7kv7zcq"}

public int hashCode()：返回每个对象的hash值。
{: id="20210309181757-497apqa"}

hashCode 的常规协定：
{: id="20210309181757-c99e7el"}

* {: id="20210309181757-h1axult"}①如果两个对象的hash值是不同的，那么这两个对象一定不相等；
  {: id="20210309181757-9z218ux"}
* {: id="20210309181757-gnk8ycr"}②如果两个对象的hash值是相同的，那么这两个对象不一定相等。
  {: id="20210309181757-wfotfj1"}
{: id="20210309181757-guyfkoy"}

主要用于后面当对象存储到哈希表等容器中时，为了提高存储和查询性能用的。
{: id="20210309181757-irdk69m"}

```java
	public static void main(String[] args) {
		System.out.println("Aa".hashCode());//2112
		System.out.println("BB".hashCode());//2112
	}
```
{: id="20210309181757-rm57ox9"}

#### （5）equals()
{: id="20210309181757-2i1gyqv"}

public boolean equals(Object obj)：用于判断当前对象this与指定对象obj是否“相等”
{: id="20210309181757-zb1vyhf"}

①默认情况下，equals方法的实现等价于与“==”，比较的是对象的地址值
{: id="20210309181757-0fsahot"}

②我们可以选择重写，重写有些要求：
{: id="20210309181757-aw5ucjb"}

A：如果重写equals，那么一定要一起重写hashCode()方法，因为规定：
{: id="20210309181757-ba2qp7h"}

```
a：如果两个对象调用equals返回true，那么要求这两个对象的hashCode值一定是相等的；
```
{: id="20210309181757-ccuiwnj"}

```
b：如果两个对象的hashCode值不同的，那么要求这个两个对象调用equals方法一定是false；
```
{: id="20210309181757-b9ga4yx"}

```
c：如果两个对象的hashCode值相同的，那么这个两个对象调用equals可能是true，也可能是false
```
{: id="20210309181757-ieeu7x4"}

B：如果重写equals，那么一定要遵循如下几个原则：
{: id="20210309181757-kt4mwxs"}

```
a：自反性：x.equals(x)返回true
```
{: id="20210309181757-mtjo9le"}

```
b：传递性：x.equals(y)为true, y.equals(z)为true，然后x.equals(z)也应该为true
```
{: id="20210309181757-37k0m1y"}

```
c：一致性：只要参与equals比较的属性值没有修改，那么无论何时调用结果应该一致
```
{: id="20210309181757-jco4v2w"}

```
d：对称性：x.equals(y)与y.equals(x)结果应该一样
```
{: id="20210309181757-aoxpvrm"}

```
e：非空对象与null的equals一定是false
```
{: id="20210309181757-26e2jm9"}

```java
class User{
	private String host;
	private String username;
	private String password;
	public User(String host, String username, String password) {
		super();
		this.host = host;
		this.username = username;
		this.password = password;
	}
	public User() {
		super();
	}
	public String getHost() {
		return host;
	}
	public void setHost(String host) {
		this.host = host;
	}
	public String getUsername() {
		return username;
	}
	public void setUsername(String username) {
		this.username = username;
	}
	public String getPassword() {
		return password;
	}
	public void setPassword(String password) {
		this.password = password;
	}
	@Override
	public String toString() {
		return "User [host=" + host + ", username=" + username + ", password=" + password + "]";
	}
	@Override
	public int hashCode() {
		final int prime = 31;
		int result = 1;
		result = prime * result + ((host == null) ? 0 : host.hashCode());
		result = prime * result + ((password == null) ? 0 : password.hashCode());
		result = prime * result + ((username == null) ? 0 : username.hashCode());
		return result;
	}
	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		User other = (User) obj;
		if (host == null) {
			if (other.host != null)
				return false;
		} else if (!host.equals(other.host))
			return false;
		if (password == null) {
			if (other.password != null)
				return false;
		} else if (!password.equals(other.password))
			return false;
		if (username == null) {
			if (other.username != null)
				return false;
		} else if (!username.equals(other.username))
			return false;
		return true;
	}

}
```
{: id="20210309181757-mc4h9cc"}


{: id="20210309181757-zgp3pnu" type="doc"}
