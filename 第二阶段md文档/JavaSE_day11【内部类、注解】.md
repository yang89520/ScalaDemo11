# JavaSE_day11【内部类、注解】
{: id="20210309181757-5j9mpt5"}

## 今日内容
{: id="20210309181757-51mcp5h"}

* {: id="20210309181757-cyx5o8p"}内部类
  {: id="20210309181757-ysu3hq4"}
* {: id="20210309181757-8mmfcgl"}注解
  {: id="20210309181757-uzcldsy"}
{: id="20210309181757-7e0zfae"}

## 学习目标
{: id="20210309181757-xuf6x7o"}

* {: id="20210309181757-7x7kjqx"}[ ] 说出内部类的几种形式
  {: id="20210309181757-u4z6ans"}
* {: id="20210309181757-dge21dm"}[ ] 能够声明静态内部类和非静态成员内部类
  {: id="20210309181757-7k0cnfn"}
* {: id="20210309181757-028jd5x"}[ ] 能够看懂和声明匿名内部类
  {: id="20210309181757-kccznzp"}
* {: id="20210309181757-woemir1"}[ ] 能够使用系统预定义的三个基本注解
  {: id="20210309181757-qnnhliu"}
* {: id="20210309181757-coygin6"}[ ] 能够编写文档注释
  {: id="20210309181757-fqb0nym"}
* {: id="20210309181757-w5jvexj"}[ ] 能够使用JUnit框架的@Test注解
  {: id="20210309181757-kriwyt5"}
* {: id="20210309181757-xdt63wn"}[ ] 能够读懂元注解
  {: id="20210309181757-aaq5op3"}
{: id="20210309181757-f9fyqxb"}

# 第七章 面向对象基础--下（续）
{: id="20210309181757-sgtsfyb"}

## 7.4 内部类
{: id="20210309181757-vajx0kc"}

### 7.4.1 概述
{: id="20210309181757-7mtshse"}

1、什么是内部类？
{: id="20210309181757-bqsw9eh"}

将一个类A定义在另一个类B里面，里面的那个类A就称为**内部类**，B则称为**外部类**。
{: id="20210309181757-q5f1rtr"}

2、**为什么要声明内部类呢？**{: style="background-color: rgb(255, 253, 56);"}
{: id="20210309181757-ahhnb10"}

当一个**事物的内部**{: style="color: rgb(252, 13, 27);"}，还有**一个部分需要一个完整的结构进行描述**{: style="color: rgb(252, 13, 27);"}，而这个**内部的完整的结构**{: style="color: rgb(252, 13, 27);"}又**只**{: style="background-color: rgb(255, 253, 56);"}为外部事物**提供服务**{: style="color: rgb(252, 13, 27);"}，**不在**{: style="background-color: rgb(255, 253, 56);"}其他地方单独使用，那么整个内部的完整结构最好使用内部类。
{: id="20210309181757-qkhulqc"}

而且内部类因为在外部类的里面，因此可以直接访问外部类的私有成员。
{: id="20210309181757-6ij6abb"}

3、内部类都有哪些形式？
{: id="20210309181757-c251qk2"}

根据内部类声明的位置（如同变量的分类），我们可以分为：
{: id="20210309181757-ugyga8h"}

（1）**成员内部类：**{: style="color: rgb(252, 13, 27);"}
{: id="20210309181757-cdowvhg"}

* {: id="20210309181757-c2cs747"}静态成员内部类
  {: id="20210309181757-4rk3zbt"}
* {: id="20210309181757-gtrjirv"}非静态成员内部类
  {: id="20210309181757-mb711rz"}
{: id="20210309181757-pxhpgqs"}

（2）**局部内部类**{: style="color: rgb(252, 13, 27);"}
{: id="20210309181757-fd4cpln"}

* {: id="20210309181757-b0c2lrf"}有名字的局部内部类
  {: id="20210309181757-1tgsu5d"}
* {: id="20210309181757-e60cjxj"}匿名的内部类
  {: id="20210309181757-uyh2xc4"}
{: id="20210309181757-mee698a"}

### 7.4.2 静态内部类
{: id="20210309181757-nd7h5ir"}

语法格式：
{: id="20210309181757-3569nbv"}

```java
【修饰符】 class 外部类{
    【其他修饰符】 static class 内部类{
    }
}
```
{: id="20210309181757-xoa4jsb"}

静态内部类的特点：
{: id="20210309181757-viadqwk"}

* {: id="20210309181757-i8vli7m"}和其他类一样，它只是定义在外部类中的另一个完整的类结构
  {: id="20210309181757-7zcgjz4"}

  * {: id="20210309181757-wqwzopd"}可以继承自己的想要继承的父类，实现自己想要实现的父接口们，和外部类的父类和父接口无关
    {: id="20210309181757-nhp65za"}
  * {: id="20210309181757-suaj8m7"}可以在静态内部类中声明属性、方法、构造器等结构，包括静态成员
    {: id="20210309181757-jrkzwlh"}
  * {: id="20210309181757-zx4z98l"}可以使用abstract修饰，因此它也可以被其他类继承
    {: id="20210309181757-7rrse5k"}
  * {: id="20210309181757-zzjufpg"}可以使用final修饰，表示不能被继承
    {: id="20210309181757-qehd1bl"}
  * {: id="20210309181757-m1yt75i"}编译后有自己的独立的字节码文件，只不过在内部类名前面冠以外部类名和$符号。
    {: id="20210309181757-aulj37y"}
  {: id="20210309181757-dvpzzgp"}
* {: id="20210309181757-jhet69d"}和外部类不同的是，它可以允许四种权限修饰符：public，protected，缺省，private
  {: id="20210309181757-3lpmh16"}

  * {: id="20210309181757-hl2i5pk"}外部类只允许public或缺省的
    {: id="20210309181757-ejs06k1"}
  {: id="20210309181757-jcfl4ji"}
* {: id="20210309181757-ui7o328"}**只**可以在静态内部类中使用**外部类**{: style="background-color: rgb(255, 253, 56);"}的**静态成员？**{: style="color: rgb(252, 13, 27); background-color: rgb(255, 253, 56);"}
  {: id="20210309181757-kvoo0cm" updated="20210310101634"}

  * {: id="20210309181757-bm6m1h9"}**随类的加载而加载,所以只能访问静态成员**{: style="color: rgb(252, 13, 27);"}
    {: id="20210310101525-thj1vp5" updated="20210310101553"}
  * {: id="20210310101525-yzmxcc3"}在静态内部类中不能使用外部类的非静态成员哦
    {: id="20210310101525-5qnwr7q" updated="20210310101525"}
  {: id="20210309181757-ao4wbq4"}
* {: id="20210309181757-4fe04ez"}在外部类的外面不需要通过外部类的对象就可以创建静态内部类的对象
  {: id="20210309181757-2laddis"}
* {: id="20210309181757-ywzs4tu"}如果在内部类中有变量与外部类的静态成员变量同名，可以使用“外部类名."进行区别
  {: id="20210309181757-w3ytfa4"}
* {: id="20210310101918-b4jbs1k"}总结:
  {: id="20210310101918-hyfy3i8" updated="20210310102005"}

  * {: id="20210310102006-pkwv2yh" updated="20210310102055"}可以把内部类当做一个成员方法看待
    {: id="20210310102159-mb7casz" updated="20210310102222"}
  * {: id="20210310102159-15ppbmv"}在外部类创建静态内部类对象，同创建普通对象一样
    {: id="20210310102159-0adse3c" updated="20210310102159"}
  * {: id="20210310102055-de2t970"}在外部类类体外使用内部类，需要使用**外部类.内部类**{: style="background-color: rgb(255, 253, 56);"}访问内部类
    {: id="20210310102055-xmf70mj" updated="20210310102136"}
  {: id="20210310102006-da4nz48"}
{: id="20210309181757-0x10vko"}

示例代码：
{: id="20210309181757-k9x1h32"}

```java
public class TestInner{
    public static void main(String[] args){
    	Outer.Inner in= new Outer.Inner();
    	in.inMethod();
  
    	Outer.Inner.inTest();
    
        Outer.Inner.inFun(3);
    }
}

class Outer{
	private static int a = 1;
	private int b = 2;
	protected static class Inner{
		static int d = 4;//可以
		void inMethod(){
			System.out.println("out.a = " + a);
//			System.out.println("out.b = " + b);//错误的
		}
		static void inTest(){
			System.out.println("out.a = " + a);
		}
        static void inFun(int a){
			System.out.println("out.a = " + Outer.a);
            System.out.println("local.a = " + a);
		}
	}
}
```
{: id="20210309181757-uq72pkv"}

> 其实严格的讲（在James Gosling等人编著的《The Java Language Specification》）静态内部类不是内部类，而是类似于C++的嵌套类的概念，外部类仅仅是静态内部类的一种命名空间的限定名形式而已。所以接口中的内部类通常都不叫内部类，因为接口中的内部成员都是隐式是静态的（即public static)。例如：Map.Entry。
> {: id="20210309181757-zowyg8z"}
{: id="20210309181757-7b6282o"}

### 7.4.3 非静态成员内部类
{: id="20210309181757-tc00wms"}

语法格式：
{: id="20210309181757-hdmnbi2"}

```java
【修饰符】 class 外部类{
    【修饰符】 class 内部类{
    }
}
```
{: id="20210309181757-ehj9g4r"}

非静态内部类的特点：
{: id="20210309181757-cur0x00" bookmark="💡"}

* {: id="20210309181757-7kc6m68"}和其他类一样，它只是定义在外部类中的另一个完整的类结构
  {: id="20210309181757-sf8beup"}

  * {: id="20210309181757-wrls1mf"}可以继承自己的想要继承的父类，实现自己想要实现的父接口们，和外部类的父类和父接口无关
    {: id="20210309181757-o56z6mj"}
  * {: id="20210309181757-lxvi0th"}可以在非静态内部类中声明属性、方法、构造器等结构，但是**不允许声明静态成员**{: style="background-color: rgb(255, 253, 56);"}，但是可以**继承**父类的静态成员，而且**可以声明静态常量**{: style="background-color: rgb(255, 253, 56);"}。
    {: id="20210309181757-egyukhj"}
  * {: id="20210309181757-8c4jcn6"}可以使用abstract修饰，因此它也可以被其他类继承
    {: id="20210309181757-3x3zspc"}
  * {: id="20210309181757-x79vh5v"}可以使用final修饰，表示不能被继承
    {: id="20210309181757-i5daan2"}
  * {: id="20210309181757-9vz9220"}编译后有自己的独立的字节码文件，只不过在内部类名前面冠以外部类名和$符号。
    {: id="20210309181757-rr2274i"}
  {: id="20210309181757-8jhc15e"}
* {: id="20210309181757-9g1sp8j"}和外部类不同的是，它可以允许四种权限修饰符：public，protected，缺省，private
  {: id="20210309181757-kpbt61d"}

  * {: id="20210309181757-t8rew7m"}外部类只允许public或缺省的
    {: id="20210309181757-f6ea94d"}
  {: id="20210309181757-gkr58i2"}
* {: id="20210309181757-za6pg74"}还可以在非静态内部类中使用外部类的**所有成员**{: style="background-color: rgb(255, 253, 56); color: rgb(252, 13, 27);"}，哪怕是私有的
  {: id="20210309181757-5r2opzm"}
* {: id="20210309181757-3mfhqfk"}在**外部类的静态成员中不可以使用非静态内部类**{: style="background-color: rgb(255, 253, 56); color: rgb(252, 13, 27);"}哦
  {: id="20210309181757-r8zirdq"}

  * {: id="20210309181757-q7ngit4"}就如同静态方法中不能访问本类的非静态成员变量和非静态方法一样
    {: id="20210309181757-xgefnj6"}
  {: id="20210309181757-mp4h4n8"}
* {: id="20210309181757-zfmavuu"}在外部类的外面必须通过外部类的对象才能创建非静态内部类的对象
  {: id="20210309181757-pw2yms8"}

  * {: id="20210309181757-2pxj3wi"}因此在非静态内部类的方法中有两个this对象，一个是外部类的this对象，一个是内部类的this对象
    {: id="20210309181757-89t5kl0"}
  {: id="20210310104859-pq4zqe5"}
* {: id="20210310104858-oyu3ybm"}总结:
  {: id="20210310104858-6x7o8ky" updated="20210310104903"}

  * {: id="20210310104904-unuxlu2"}非静态内部类需要逐层创建对象**外部类引用名.new 内部类()**{: style="background-color: rgb(255, 253, 56); color: rgb(252, 13, 27);"};
    {: id="20210310104904-o62dnoc" updated="20210310105011"}
  * {: id="20210310184248-ykffnvn"}内部类成员变量不影响
    {: id="20210310184248-ji2rfm1" updated="20210310184339"}
  * {: id="20210310185712-co4n5u3"}属性和方法作用域![image.png](assets/image-20210310185807-t645gmh.png)
    {: id="20210310185712-kpum7a2" updated="20210310185807"}
  {: id="20210310104905-w1iddem"}
{: id="20210309181757-gcv0yxm"}

示例代码：
{: id="20210309181757-0x05iim"}

```java
public class TestInner{
    public static void main(String[] args){
    	Outer out = new Outer();
    	Outer.Inner in= out.new Inner();
    	in.inMethod();
  
    	Outer.Inner inner = out.getInner();
    	inner.inMethod();
    }
}
class Father{
	protected static int c = 3;
}
class Outer{
	private static int a = 1;
	private int b = 2;
	protected class Inner extends Father{
//		static int d = 4;//错误
		int b = 5;
		void inMethod(){
			System.out.println("out.a = " + a);
			System.out.println("out.b = " + Outer.this.b);
			System.out.println("in.b = " + b);
			System.out.println("father.c = " + c);
		}
	}

	public static void outMethod(){
//		Inner in = new Inner();//错误的
	}
	public Inner getInner(){
		return new Inner();
	}
}
```
{: id="20210309181757-e7p2k72"}

#### 练习1：语法练习题
{: id="20210309181757-pzxbv31"}

声明一个身体Body类，包含一个私有的boolean类型的属性live，初始化为true，表示活着。属性私有化，提供get/set方法。
{: id="20210309181757-gfz2at7"}

声明一个身体Body的内部类Heart，包含void beat()方法，当live为true时，打印“心脏在跳动”，否则打印“心脏停止跳动"。因为Heart只为外部类Body服务，而又具有自己的方法，属性等，而且这里应该是有Body实体存在的情况下才能有Heart实体，所以这里把Heart声明为非静态内部类。
{: id="20210309181757-ei0sjgl"}

声明一个测试类，在测试类的主方法中，创建身体和心脏的对象，调用心脏对象的beat()方法，然后调用身体对象的setLive()方法，设置为false后，再调用心脏对象的beat()方法查看结果。
{: id="20210309181757-h4le5g1"}

```java
public class Person {
    private  boolean live = true;
    class Heart {
        public void beat() {
            // 直接访问外部类成员
            if (live) {
                System.out.println("心脏在跳动");
            } else {
                System.out.println("心脏不跳了");
            }
        }
    }

    public boolean isLive() {
        return live;
    }

    public void setLive(boolean live) {
        this.live = live;
    }

}
```
{: id="20210309181757-2nhdpk9"}

```java
public class InnerDemo {
    public static void main(String[] args) {
        // 创建外部类对象 
        Person p  = new Person();
        // 创建内部类对象
        Heart heart = p.new Heart();

        // 调用内部类方法
        heart.beat();
        // 调用外部类方法
        p.setLive(false);
        // 调用内部类方法
        heart.beat();
    }
}
输出结果:
心脏在跳动
心脏不跳了
```
{: id="20210309181757-vem3j5l"}

或
{: id="20210309181757-dwdthob"}

```java
public class Beatable{//可跳动的
    public abstract void beat();
}
```
{: id="20210309181757-q1zw62c"}

```java
public class Person {
    private  boolean live = true;
    private  Heart heart = new Heart();
    private class Heart implements Beatable{
        public void jump() {
            // 直接访问外部类成员
            if (live) {
                System.out.println("心脏在跳动");
            } else {
                System.out.println("心脏不跳了");
            }
        }
    }

    public boolean isLive() {
        return live;
    }

    public void setLive(boolean live) {
        this.live = live;
    }

	public Beatable getHeart(){
		return heart;
	}
}
```
{: id="20210309181757-oolx9ed"}

```java
public class InnerDemo {
    public static void main(String[] args) {
        // 创建外部类对象 
        Person p  = new Person();
        // 获取内部类对象
        Beatable heart = p.getHeart();

        // 调用内部类方法
        heart.beat();
        // 调用外部类方法
        p.setLive(false);
        // 调用内部类方法
        heart.beat();
    }
}
输出结果:
心脏在跳动
心脏不跳了
```
{: id="20210309181757-9awex6a"}

#### 练习2：简单面试题
{: id="20210309181757-wxlaqat"}

判断如下代码的运行结果：
{: id="20210309181757-2l0km73"}

```java
public class Test{
	public Test(){
		Inner s1 = new Inner();
		s1.a = 10;
		Inner s2 = new Inner();
		s2.a = 20;
		Test.Inner s3 = new Test.Inner();
		System.out.println(s3.a);
	}
	class Inner{
		public int a = 5;
	}
	public static void main(String[] args) {
		Test t = new Test();
		Inner r = t.new Inner();
		System.out.println(r.a);
	}
}
```
{: id="20210309181757-0nuzkpv"}

#### 练习3：高难面试题
{: id="20210309181757-sf25p2j"}

代码填空题：
{: id="20210309181757-5lwbyl9"}

```java
public class TestInner{
    public static void main(String[] args){
    	Outer.Inner in = new Sub();
    	in.method();//输出 hello inner
    }
}

class Outer {
	abstract class Inner{
		abstract void method();
	}
}
class Sub ________（1）__________{



	______（2）多行代码_______________

}
```
{: id="20210309181757-0ftlpxu"}

参考答案：
{: id="20210309181757-j30drzv"}

```java
public class TestInner{
    public static void main(String[] args){
    	Outer.Inner in = new Sub();
    	in.method();//输出 hello inner
    }
}

class Outer {
	abstract class Inner{
		abstract void method();
	}
}
//考察抽象内部类继承的写法
//
class Sub extends Outer.Inner{
	static Outer out = new Outer();
	Sub(){
		out.super();
	}

	@Override
	void method() {
		System.out.println("hello inner");
	}

}
```
{: id="20210309181757-74vi0an" updated="20210310165055"}

### 7.4.4 局部内部类
{: id="20210309181757-t055qay"}

语法格式：
{: id="20210309181757-pyk0uen"}

```java
【修饰符】 class 外部类{
    【修饰符】 返回值类型  方法名(【形参列表】){
            【final/abstract】 class 内部类{
    	}
    }  
}
```
{: id="20210309181757-or3q7dc"}

局部内部类的特点：
{: id="20210309181757-7hmg2re"}

* {: id="20210309181757-vaq4j7k"}和外部类一样，它只是定义在外部类的某个方法中的另一个完整的类结构
  {: id="20210309181757-yzlcoz0"}

  * {: id="20210309181757-rn6svlp"}可以继承自己的想要继承的父类，实现自己想要实现的父接口们，和**外部类的父类和父接口无关**{: style="background-color: rgb(255, 253, 56);"}
    {: id="20210309181757-3cvtrnp"}
  * {: id="20210309181757-hrrbwya"}可以在局部内部类中声明**属性、方法、构造器**{: style="color: rgb(252, 13, 27);"}等结构，**但不包括静态成员，除非是从父类继承的或静态常量**{: style="background-color: rgb(255, 253, 56);"}
    {: id="20210309181757-z44axls"}
  * {: id="20210309181757-b9sspta"}可以使用**abstract**{: style="background-color: rgb(255, 253, 56);"}修饰，因此它也可以被**同一个方法**{: style="background-color: rgb(255, 253, 56);"}的**在它后面**{: style="background-color: rgb(255, 253, 56);"}的**其他内部类**{: style="background-color: rgb(255, 253, 56);"}继承
    {: id="20210309181757-rpmapym"}
  * {: id="20210310130108-psfp1x7"}**不允许定义接口**{: style="background-color: rgb(255, 253, 56);"}
    {: id="20210310130108-joykfch" updated="20210310130122"}
  * {: id="20210309181757-zz7j7x0"}可以使用**final**{: style="background-color: rgb(255, 253, 56);"}修饰，表示不能被继承
    {: id="20210309181757-qw77pka"}
  * {: id="20210309181757-pt96kns"}编译后有自己的独立的字节码文件，只不过在内部类名前面冠以外部类名、$符号、编号。
    {: id="20210309181757-bxv1i4j"}

    * {: id="20210309181757-5wli2ot"}这里有编号是因为同一个外部类中，不同的方法中存在相同名称的局部内部类
      {: id="20210309181757-malpy9t"}
    {: id="20210309181757-td3md1p"}
  {: id="20210309181757-2k230l8"}
* {: id="20210309181757-otzk3qt"}和成员内部类不同的是，它前面**不能有**{: style="background-color: rgb(255, 253, 56);"}权限修饰符等
  {: id="20210309181757-9kax3x6"}
* {: id="20210309181757-4cyc9x7"}局部内部类如同局部变量一样，有作用域，**不能外部文件申明内部类对象**{: style="background-color: rgb(255, 253, 56);"}
  {: id="20210309181757-8a3g7vn" updated="20210310113133"}
* {: id="20210309181757-v1eon36"}**局部内部类中是否能访问外部类的静态还是非静态的成员，取决于所在的方法**{: style="background-color: rgb(255, 253, 56);"}
  {: id="20210309181757-2otgsds"}
* {: id="20210309181757-rj7khl6"}局部内部类中还可以使用所在方法的局部常量，即用final声明的局部变量
  {: id="20210309181757-qqbobw6"}

  * {: id="20210309181757-4g1wgke"}JDK1.8之后，如果某个局部变量在局部内部类中被使用了，自动加final
    {: id="20210309181757-7w0h12r"}
  {: id="20210309181757-cmtkkdz"}
{: id="20210309181757-y9wa90w"}

示例代码：
{: id="20210309181757-m0s4fl5"}

```java
class Outer{
	private static int a = 1;
	private int b = 2;

	public static void outMethod(){
		final int c = 3;
		class Inner{
			public void inMethod(){
				System.out.println("out.a = " + a);
//				System.out.println("out.b = " + b);//错误的，因为outMethod是静态的
				System.out.println("out.local.c = " + c);
			}
		}

		Inner in = new Inner();
		in.inMethod();
	}

	public void outTest(){
		final int c = 3;
		class Inner{
			public void inMethod(){
				System.out.println("out.a = " + a);
				System.out.println("out.b = " + b);//可以，因为outTest是飞静态的
				System.out.println("method.c = " + c);
			}
		}

		Inner in = new Inner();
		in.inMethod();
	}

}
```
{: id="20210309181757-n79ktcc"}

#### 思考
{: id="20210309181757-sft4bhl"}

为什么在局部内部类中使用外部类方法的局部变量要加final呢？
{: id="20210309181757-es9b0ha"}

```java
public class TestInner{
	public static void main(String[] args) {
		A obj = Outer.method();
		//因为如果c不是final的，那么method方法执行完，
		//method的栈空间就释放了，那么c也就消失了
		obj.a();//这里打印c就没有中可取了，所以把c声明为常量，存储在方法区中
	}
}

interface A{
	void a();
}
class Outer{
	public static A method(){
		final int c = 3;
		class Sub implements A{
			@Override
			public void a() {
				System.out.println("method.c = " + c);
			}
		}
		return new Sub();
	}
}
```
{: id="20210309181757-yn1hg64" updated="20210310164556"}

### 7.4.5  匿名内部类
{: id="20210309181757-9tin4xe"}

> 应用场景：
> {: id="20210310113657-vl3edkq" updated="20210310113713"}
>
> 因为接口和抽象类不能直接实例化
> {: id="20210310113713-4d3qpxw" updated="20210310113728"}
{: id="20210310113701-qo7veud"}

#### 1、引入
{: id="20210309181757-dlvse9n"}

当我们在开发过程中，需要用到一个抽象类的子类的对象或一个接口的实现类的对象，而且只创建一个对象，而且逻辑代码也不复杂。那么我们原先怎么做的呢？
{: id="20210309181757-8lj0d1i"}

（1）编写类，继承这个父类或实现这个接口
{: id="20210309181757-leumnst"}

（2）重写父类或父接口的方法
{: id="20210309181757-eunowcv"}

（3）创建这个子类或实现类的对象
{: id="20210309181757-qt0ao3u"}

例如：
{: id="20210309181757-41ts1bt"}

```java
public interface Runnable{
    public abstract void run();
}
```
{: id="20210309181757-daaxqgf"}

```java
//声明接口实现类
public class MyRunnable implements Runnable{
    public void run(){
        while(true){
            System.out.println("大家注意安全");
            try
            	Thread.sleep(1000);
            }catch(Exception e){            
            }
        }
    }
}
```
{: id="20210309181757-vgi7wed"}

```java
public class Test{
    public static void main(String[] args){
        //如果MyRunnable类只是在这里使用一次，并且只创建它的一个对象
        //分开两个.java源文件，反而不好维护
        Runnable target = new MyRunnable();
        Thread t = new Thread("安全提示线程",target);
        t.start();
    }
}
```
{: id="20210309181757-e6wvx7t"}

这里，因为考虑到这个子类或实现类是一次性的，那么我们“费尽心机”的给它取名字，就显得多余。那么我们完全可以使用匿名内部类的方式来实现，避免给类命名的问题。
{: id="20210309181757-obt1pbb"}

可以修改为如下形式：
{: id="20210309181757-v904hyp"}

```java
public class Test{
    public static void main(String[] args){
        //MyRunnable类只是在这里使用一次，并且只创建它的一个对象，那么这些写代码更紧凑，更好维护
        Runnable target = new Runnable(){
            public void run(){
                while(true){
                    System.out.println("大家注意安全");
                    try
                        Thread.sleep(1000);
                    }catch(Exception e){            
                    }
                }
            }
        };
        Thread t = new Thread("安全提示线程",target);
        t.start();
    }
}
```
{: id="20210309181757-uq29m08"}

#### 2、语法格式
{: id="20210309181757-4xnp0jy"}

```java
new 父类(【实参列表】){
    重写方法...
}
//()中是否需要【实参列表】，看你想要让这个匿名内部类调用父类的哪个构造器，如果调用父类的无参构造，那么()中就不用写参数，如果调用父类的有参构造，那么()中需要传入实参
```
{: id="20210309181757-94oe9ws"}

```java
new 父接口(){
    重写方法...
}
//()中没有参数，因为此时匿名内部类的父类是Object类，它只有一个无参构造
```
{: id="20210309181757-ty5goom"}

> 匿名内部类是没有名字的类，因此在声明类的同时就创建好了唯一的对象。
> {: id="20210309181757-5p2qo4v"}
{: id="20210309181757-cjr0fds"}

注意：
{: id="20210309181757-ahai36a"}

匿名内部类是一种特殊的局部内部类，只不过没有名称而已。所有局部内部类的限制都适用于匿名内部类。例如：
{: id="20210309181757-k3rqtyi"}

* {: id="20210309181757-78051qi"}在匿名内部类中是否可以使用外部类的非静态成员变量，看所在方法是否静态
  {: id="20210309181757-gqw2z7x"}
* {: id="20210309181757-19fscep"}在匿名内部类中如果需要访问当前方法的局部变量，该局部变量需要加final
  {: id="20210309181757-o4qku3s"}
{: id="20210309181757-sapwytb"}

思考：这个对象能做什么呢？
{: id="20210309181757-pwq0g54"}

答：（1）调用某个方法（2）赋值给父类/父接口的变量，通过多态引用使用这个对象（3）作为某个方法调用的实参
{: id="20210309181757-r3wv2jg"}

#### 3、使用方式一：匿名内部类的对象直接调用方法
{: id="20210309181757-qyzld38"}

```java
interface A{
	void a();
}
public class Test{
    public static void main(String[] args){
    	new A(){
			@Override
			public void a() {
				System.out.println("aaaa");
			}
    	}.a();
    }
}
```
{: id="20210309181757-hvuyhv1"}

```java
class B{
	public void b(){
		System.out.println("bbbb");
	}
}
public class Test{
    public static void main(String[] args){
    	new B(){
    		public void b(){
    			System.out.println("ccccc");
    		}
    	}.b();
  
    }
}
```
{: id="20210309181757-igxh8d0"}

#### 4、使用方式二：通过父类或父接口的变量多态引用匿名内部类的对象
{: id="20210309181757-e5klsrt"}

```java
interface A{
	void a();
}
public class Test{
    public static void main(String[] args){
    	A obj = new A(){
			@Override
			public void a() {
				System.out.println("aaaa");
			}
    	};
    	obj.a();
    }
}
```
{: id="20210309181757-1gmcaji"}

```java
class B{
	public void b(){
		System.out.println("bbbb");
	}
}
public class Test{
    public static void main(String[] args){
    	B obj = new B(){
    		public void b(){
    			System.out.println("ccccc");
    		}
    	};
    	obj.b();
    }
}
```
{: id="20210309181757-5pu91u9"}

#### 5、使用方式三：匿名内部类的对象作为实参
{: id="20210309181757-jzpjzm2"}

```java
interface A{
	void method();
}
public class Test{
    public static void test(A a){
    	a.method();
    }
  
    public static void main(String[] args){
    	test(new A(){

			@Override
			public void method() {
				System.out.println("aaaa");
			}
  
    	});
    }   
}
```
{: id="20210309181757-u5qco0q"}

#### 6、练习
{: id="20210309181757-osf5u8n"}

##### 练习1
{: id="20210309181757-qhsfyw3"}

声明一个Employee员工类，包含编号、姓名、薪资，
{: id="20210309181757-g1o96ur"}

声明一个测试类，在main中，创建Employee[]数组，长度为5，显示原来顺序结果
{: id="20210309181757-inbnr9h"}

调用java.util.Arrays数组工具类的排序方法public static void sort(Object[] a, Comparator c)对数组的元素进行排序，用匿名内部类的对象给c形参传入按照薪资比较大小的定制比较器对象。并显示排序后结果
{: id="20210309181757-ofj4y5g"}

调用java.util.Arrays数组工具类的排序方法public static void sort(Object[] a, Comparator c)对数组的元素进行排序，用匿名内部类的对象给c形参传入按照编号比较大小的定制比较器对象。并显示排序后结果
{: id="20210309181757-2sfqs1r"}

员工类示例代码：
{: id="20210309181757-2yblijt"}

```java
class Employee{
	private int id;
	private String name;
	private double salary;
	public Employee(int id, String name, double salary) {
		super();
		this.id = id;
		this.name = name;
		this.salary = salary;
	}
	public Employee() {
		super();
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
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
	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + ", salary=" + salary + "]";
	}
}
```
{: id="20210309181757-joki6n2"}

测试类：
{: id="20210309181757-shucj8m"}

```java
public class TestInner {
	public static void main(String[] args) {
		Employee[] arr = new Employee[5];
		arr[0] = new Employee(1,"张三",13000);
		arr[1] = new Employee(3,"王五",14000);
		arr[2] = new Employee(2,"李四",13000);
		arr[3] = new Employee(4,"赵六",7000);
		arr[4] = new Employee(5,"钱七",9000);

		//原顺序
		System.out.println("员工列表：");
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}

		Arrays.sort(arr, new Comparator() {
			@Override
			public int compare(Object o1, Object o2) {
				Employee e1 = (Employee) o1;
				Employee e2 = (Employee) o2;
				return Double.compare(e1.getSalary(), e2.getSalary());
			}
		});

		System.out.println("按照薪资排序后员工列表：");
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}

		Arrays.sort(arr, new Comparator() {
			@Override
			public int compare(Object o1, Object o2) {
				Employee e1 = (Employee) o1;
				Employee e2 = (Employee) o2;
				return e1.getId() - e2.getId();
			}
		});
		
		System.out.println("按照编号排序后员工列表：");
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
	}
}
```
{: id="20210309181757-bpju0xr"}

##### 练习2
{: id="20210309181757-u3ymp71"}

（1）声明一个抽象类Father，包含抽象方法：public abstract void method();
（2）用匿名内部类继承Father，并重写抽象方法，打印“hello baby"
并调用子类对象的method方法
{: id="20210309181757-uv2jfpg"}

```java
public abstract class Father{
	public abstract void method();
}
```
{: id="20210309181757-9t9bzwi"}

```java
public class TestExer1 {
	public static void main(String[] args) {
		new Father(){

			@Override
			public void method() {
				System.out.println("hello 孩子");
			}
	
		}.method();
	}
}
```
{: id="20210309181757-ktj3i4p"}

##### 练习3
{: id="20210309181757-70ddo67"}

（1）声明一个员工类Triangle三角形，有属性：a,b,c表示三条边
（2）在测试类中创建Triangle数组
（3）分别调用Arrays.sort(数组，Comparator)，用匿名内部类实现按照编号周长排列
（4）分别调用Arrays.sort(数组，Comparator)，用匿名内部类实现按照薪资面积排列
{: id="20210309181757-las5d8d"}

```java
public class Triangle {
	private double a;
	private double b;
	private double c;
	public Triangle(double a, double b, double c) {
		super();
		this.a = a;
		this.b = b;
		this.c = c;
	}
	public Triangle() {
		super();
	}
	public double getA() {
		return a;
	}
	public void setA(double a) {
		this.a = a;
	}
	public double getB() {
		return b;
	}
	public void setB(double b) {
		this.b = b;
	}
	public double getC() {
		return c;
	}
	public void setC(double c) {
		this.c = c;
	}
	@Override
	public String toString() {
		return "Triangle [a=" + a + ", b=" + b + ", c=" + c + "]";
	}
	public double getPerimeter(){
		return a+b+c;
	}
	public double getArea(){
		double p = getPerimeter()/2;
		return Math.sqrt(p*(p-a)*(p-b)*(p-c));
	}
}
```
{: id="20210309181757-042xgex"}

```java
public class TestExer2 {
	public static void main(String[] args) {
		Triangle[] arr = new Triangle[3];
		arr[0]  = new Triangle(6, 1, 6);
		arr[1]  = new Triangle(3, 4, 5);
		arr[2]  = new Triangle(6, 6, 6);

		System.out.println("原来的顺序：");
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
		System.out.println("--------------------");
		System.out.println("按照周长排序：");
		Arrays.sort(arr, new Comparator() {

			@Override
			public int compare(Object o1, Object o2) {
				Triangle t1 = (Triangle) o1;
				Triangle t2 = (Triangle) o2;
				return Double.compare(t1.getPerimeter(), t2.getPerimeter());
			}
		});
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
		System.out.println("--------------------");
		System.out.println("按照面积排序：");
		Arrays.sort(arr, new Comparator() {

			@Override
			public int compare(Object o1, Object o2) {
				Triangle t1 = (Triangle) o1;
				Triangle t2 = (Triangle) o2;
				return Double.compare(t1.getArea(), t2.getArea());
			}
		});
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
	}
}
```
{: id="20210309181757-ytnjiug"}

##### 练习4
{: id="20210309181757-jcf24v3"}

1、声明一个接口：Predicate接口，包含public abstract boolean test(Object obj);抽象方法
2、声明一个员工类：Employee,有属性：编号、姓名、年龄、薪资
3、声明一个员工管理类：EmployeeService，
（1）包含Employee[] arr，并在EmployeeService构造器中，创建数组，并初始化数组，例如：
arr = new Employee[5];
arr[0] = new Employee(4, "李四", 24, 24000);
arr[1] = new Employee(3, "张三", 23, 13000);
arr[2] = new Employee(5, "王五", 25, 15000);
arr[3] = new Employee(1, "赵六", 27, 17000);
arr[4] = new Employee(2, "钱七", 16, 6000);
{: id="20210309181757-vl2ukif"}

（2）包含public Employee[] get(Predicate p){
Employee[] result = new Employee[arr.length];
int total = 0;
for(int i=0; i<arr.length; i++){
if(p.test(arr[i]){
result[total++] = arr[i];
}
}
return Arrays.copyOf(result,total);
}
这个方法的作用，就是用于在arr数组中筛选满足件的元素
4、在测试类中，创建EmployeeService对象，调用get(Predicate p)方法，通过匿名内部类的对象给形参p赋值，
分别获取：
（1）所有员工对象
（2）所有年龄超过25的员工
（3）所有薪资高于15000的员工
（4）所有编号是偶数的员工
（5）名字是“张三”的员工
（6）年龄超过25，薪资高于15000的员工
{: id="20210309181757-vpcrpzv" updated="20210310143615"}

```java
public interface Predicate {
	public abstract boolean test(Object obj);
}
```
{: id="20210309181757-5flhnhx"}

```java
public class Employee{
	private int id;
	private String name;
	private int age;
	private double salary;
	public Employee() {
		super();
	}
	public Employee(int id, String name, int age, double salary) {
		super();
		this.id = id;
		this.name = name;
		this.age = age;
		this.salary = salary;
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
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
	public double getSalary() {
		return salary;
	}
	public void setSalary(double salary) {
		this.salary = salary;
	}
	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + ", age=" + age + ", salary=" + salary + "]";
	}
}
```
{: id="20210309181757-jajypk6"}

```java
public class EmployeeService {
	private Employee[] arr;

	public EmployeeService() {
		arr = new Employee[5];
		arr[0] = new Employee(4, "李四", 24, 24000);
		arr[1] = new Employee(3, "张三", 23, 13000);
		arr[2] = new Employee(5, "王五", 25, 15000);
		arr[3] = new Employee(1, "赵六", 27, 17000);
		arr[4] = new Employee(2, "钱七", 16, 6000);
	}
	public Employee[] get(Predicate p){
		Employee[] result = new Employee[arr.length] ;
		int total = 0;
		for (int i = 0; i < arr.length; i++) {
			if(p.test(arr[i])){
				result[total++] = arr[i];
			}
		}
		return Arrays.copyOf(result, total);
	}
}
```
{: id="20210309181757-6usmpnh"}

```java
public class TestExer5 {
	public static void main(String[] args) {
		EmployeeService es = new EmployeeService();

		//（1）所有员工对象
		Employee[] employees = es.get(new Predicate(){

			@Override
			public boolean test(Object obj) {
				return true;
			}
	
		});
		for (int i = 0; i < employees.length; i++) {
			System.out.println(employees[i]);
		}
		System.out.println("============================");
//		（2）所有年龄超过25的员工
		employees = es.get(new Predicate(){

			@Override
			public boolean test(Object obj) {
				Employee emp = (Employee) obj;
				return emp.getAge()>25;
			}
	
		});
		for (int i = 0; i < employees.length; i++) {
			System.out.println(employees[i]);
		}
        //....
	}
}
```
{: id="20210309181757-2dqbd1l"}

## 7.5 static关键字
{: id="20210309181757-7lw2t5n"}

static是一个修饰符，可以修饰：
{: id="20210309181757-s2kkj25"}

* {: id="20210309181757-8oxos7z"}成员变量，我们称为类变量，或静态变量，表示某个类的所有对象共享的数据
  {: id="20210309181757-ash083i"}
* {: id="20210309181757-dfm5p7q"}成员方法，我们称为类方法，或静态方法，表示不需要实例对象就可以调用的方法，使用“类名."进行调用
  {: id="20210309181757-ks60k09"}
* {: id="20210309181757-qs3s1p2"}代码块，我们称为静态代码块，或静态初始化块，用于为静态变量初始化，每一个类的静态代码块只会执行一次，在类第一次初始化时执行
  {: id="20210309181757-htwzfxy"}
* {: id="20210309181757-o9b374k"}成员内部类，我们称为静态成员内部类，简称静态内部类，不需要外部类实例对象就可以使用的内部类，在静态内部类中只能使用外部类的静态成员
  {: id="20210309181757-zvd5g0f"}
{: id="20210309181757-mttr1l7"}

容易错误：
{: id="20210309181757-t23g1z0"}

static修饰外部类（错误）
{: id="20210309181757-4gcnuh5"}

static的方法被重写（错误）
{: id="20210309181757-pofqjj4"}

## 7.6 注解
{: id="20210309181757-uqsn8t1"}

### 7.6.1 概述
{: id="20210309181757-6osngzk"}

注解是以“**@注释名**”在代码中存在的，还可以添加一些参数值，例如：
{: id="20210309181757-uztaiky"}

```java
@SuppressWarnings(value=”unchecked”) 抑制警告注解
@Override 检查方法重写是否正确
@Deprecated 
	标注方法已过期
	过期方法能正常使用
@Test 测试
@author 作者
@param 参数
....
```
{: id="20210309181757-ml5ggws" updated="20210310143927"}

注解Annotation是从JDK5.0开始引入。
{: id="20210309181757-1pvwvpb"}

虽然说注解也是一种注释，因为它们都不会改变程序原有的逻辑，只是对程序增加了某些注释性信息。不过它又不同于单行注释和多行注释，对于单行注释和多行注释是给程序员看的，而注解是可以被编译器或其他程序读取的一种注释，程序还可以根据注解的不同，做出相应的处理。
{: id="20210309181757-c8ga8w6"}

一个完整的注解有三个部分：
{: id="20210309181757-pu7gl67"}

* {: id="20210309181757-fdmbwei"}注解的声明：就如同类、方法、变量等一样，需要先声明后使用
  {: id="20210309181757-pjssa3x"}
* {: id="20210309181757-rl2ww0s"}注解的使用：用于注解在包、类、方法、属性、构造、局部变量等上面的10个位置中一个或多个位置
  {: id="20210309181757-wzts6um"}
* {: id="20210309181757-pusv2xw"}注解的读取：有一段专门用来读取这些使用的注解，然后根据注解信息作出相应的处理，这段程序称为注解处理流程，这也是注解区别与普通注释最大的不同。
  {: id="20210309181757-m4to00p"}
{: id="20210309181757-9j02bos"}

### 7.6.2 系统预定义的三个最基本的注解
{: id="20210309181757-1214j6e"}

#### 1、@Override
{: id="20210309181757-b74vo59"}

```
用于检测被修饰的方法为有效的重写方法，如果不是，则报编译错误!
```
{: id="20210309181757-ixbmh9y"}

```
只能标记在方法上。
```
{: id="20210309181757-cekd1ly"}

```
它会被编译器程序读取。
```
{: id="20210309181757-t5lmynl"}

#### 2、@Deprecated
{: id="20210309181757-t3ayr10"}

```
用于表示被标记的数据已经过时，不建议使用。
```
{: id="20210309181757-zuabit2"}

```
可以用于修饰 属性、方法、构造、类、包、局部变量、参数。
```
{: id="20210309181757-z80qjm7"}

```
它会被编译器程序读取。
```
{: id="20210309181757-anm8icp"}

#### 3、@SuppressWarnings
{: id="20210309181757-m3mduto"}

```
抑制编译警告。
```
{: id="20210309181757-o0qq750"}

```
可以用于修饰类、属性、方法、构造、局部变量、参数
```
{: id="20210309181757-45s1og3"}

```
它会被编译器程序读取。
```
{: id="20210309181757-90pc5ff"}

示例代码：
{: id="20210309181757-m560q92"}

```java
public class TestAnnotation {
	@SuppressWarnings({"unused","rawtypes", "unchecked"})
	public static void main(String[] args) {

		int i;

		List list = new ArrayList();
		list.add("");
		list.add(123);
		list.add("");

		Father f = new Son();
		f.show();
		f.methodOl();
	}

}


class Father{
	@Deprecated
	public void show() {

	}
	public void methodOl() {
		System.out.println("Father Method");
	}
	public void print1n(){
		System.out.println("Father Method");
	}
	public int sum(int... nums){
		int sum = 0;
		for (int i = 0; i < nums.length; i++) {
			sum += nums[i];
		}
		return sum;
	}
}

class Son extends Father{

/*	@Override
	public void method01() {
		System.out.println("Son Method");
	}

	@Override
	public void println(){
		System.out.println("Father Method");
	}

	@Override
	public long sum(int[] nums){
		int sum = 0;
		for (int i = 0; i < nums.length; i++) {
			sum += nums[i];
		}
		return sum;
	}*/
}
```
{: id="20210309181757-4ddi71e"}

### 7.6.3 文档注释
{: id="20210309181757-jxgla5s"}

* {: id="20210309181757-jgocs5k"}@author 标明开发该类模块的作者，多个作者之间使用,分割
  {: id="20210309181757-5yuowfn"}
* {: id="20210309181757-7q62bxk"}@version 标明该类模块的版本
  {: id="20210309181757-qdr3aq2"}
* {: id="20210309181757-fxicrfx"}@see 参考转向，也就是相关主题
  {: id="20210309181757-yxroen1"}
* {: id="20210309181757-0ktzt53"}@since 从哪个版本开始增加的
  {: id="20210309181757-v9my0vu"}
* {: id="20210309181757-odq3z3j"}@param 对方法中某参数的说明，如果没有参数就不能写
  {: id="20210309181757-n879d3t"}
* {: id="20210309181757-5xl7r0b"}@return 对方法返回值的说明，如果方法的返回值类型是void就不能写
  {: id="20210309181757-ecl33kx"}
* {: id="20210309181757-tp7l6gr"}@throws/@exception 对方法可能抛出的异常进行说明 ，如果方法没有用throws显式抛出的异常就不能写
  {: id="20210309181757-d0qur0o"}

  * {: id="20210309181757-2kl21fd"}其中 @param  @return 和 @exception 这三个标记都是只用于方法的。
    {: id="20210309181757-2ixa308"}
  * {: id="20210309181757-jlduvgy"}@param的格式要求：@param 形参名 形参类型  形参说明
    {: id="20210309181757-5p6jv8z"}
  * {: id="20210309181757-d0wkk0m"}@return 的格式要求：@return 返回值类型 返回值说明
    {: id="20210309181757-n4zfrik"}
  * {: id="20210309181757-3ik3l4i"}@exception 的格式要求：@exception 异常类型 异常说明
    {: id="20210309181757-pchnqfh"}
  * {: id="20210309181757-f5q7cjx"}@param和@exception可以并列多个
    {: id="20210309181757-9hi1keu"}
  {: id="20210309181757-xlz8zca"}
{: id="20210309181757-e8fq8re"}

javadoc.exe就是这些注解的信息处理流程。
{: id="20210309181757-apek00l"}

示例代码：
{: id="20210309181757-ibsbadm"}

```java
/**
 * 
 * @author Irene
 *
 */
public class TestAnnotation2 {

	/**
	 * 这是Java的主方法，是Java程序的入口
	 * @param args String[] 命令行参数，使用java命令时，在后面传入参数，例如
	 * 	java 类名   参数1  参数2 ....
	 */
	public static void main(String[] args) {

	}

	/**
	 * 这是一个求两个整数中最大值的方法
	 * @param a int 其中一个整数
	 * @param b int 另一个整数
	 * @return int 返回最大值
	 */
	public static int getMax(int a, int b){
		return a>b?a:b;
	}

	/**
	 * 这是复制一个文件的方法
	 * @param src String 源文件
	 * @param dest  String 目标文件
	 * @throws FileNotFoundException 当源文件找不到时会抛出该异常
	 */
	public static void copyFile(String src, String dest) throws FileNotFoundException{
		FileInputStream fis = new FileInputStream(src);
		//..
	}

	/**
	 * 
	 */
	public void println(){

	}
}
```
{: id="20210309181757-nrn52lg"}

> 注释与代码要一致，如果不一致，会误导别人或自己
> {: id="20210309181757-ajv2dfd"}
{: id="20210309181757-h0jjm38"}

#### eclipse中导出javadoc
{: id="20210309181757-wqemhs3"}

![1576665188851](imgs11/1576665188851.png)
{: id="20210309181757-gvb9uv3"}

![1576665298238](imgs11/1576665298238.png)
{: id="20210309181757-o1t1u5h"}

![1576665309340](imgs11/1576665309340.png)
{: id="20210309181757-mj09gpu"}

如果导出时有乱码问题，可以在上述窗口下面按next到最后一步通过增加Javadoc的额外参数选项来指定字符编码再导出：
{: id="20210309181757-hcrxb7q"}

```command
-docencoding UTF-8
-encoding UTF-8
-charset UTF-8
```
{: id="20210309181757-7azl4zr"}

![1576665525558](imgs11/1576665525558.png)
{: id="20210309181757-osv1bq6"}

![1576665321307](imgs11/1576665321307.png)
{: id="20210309181757-bj9fu76"}

![1576665331437](imgs11/1576665331437.png)
{: id="20210309181757-olxnfbz"}

#### idea中导出javadoc
{: id="20210309181757-ax8eeg6"}

![1576467074566](imgs11/1576467074566.png)
{: id="20210309181757-p4em5ll"}

![img](imgs11/javadoc2.jpg)
{: id="20210309181757-kpjigev"}

### 7.6.4 JUnit单元测试
{: id="20210309181757-bzbi123"}

JUnit是由 Erich Gamma 和 Kent Beck 编写的一个回归测试框架（regression testing framework）,供Java开发人员编写单元测试之用。多数Java的开发环境都已经集成了JUnit作为单元测试的工具。JUnit测试是程序员测试，即所谓白盒测试，因为程序员知道被测试的软件如何（How）完成功能和完成什么样（What）的功能。![image.png](assets/image-20210311093545-ebst5jt.png)
{: id="20210309181757-ccj7mbv" updated="20210311093545"}

要使用JUnit，必须在项目的编译路径中必须引入JUnit的库，即相关的.class文件组成的jar包。如何把JUnit的jar添加到编译路径如图所示：
{: id="20210309181757-8igpknw"}

#### 在eclipse中截图如下：
{: id="20210309181757-dpzomgx"}

##### 方式一：
{: id="20210309181757-eskqwfg"}

![1562474605131](imgs11/1562474605131.png)
{: id="20210309181757-ufbvxp2"}

![1562474620088](imgs11/1562474620088.png)
{: id="20210309181757-3ei4fbx"}

![1562474639231](imgs11/1562474639231.png)
{: id="20210309181757-87ofp3i"}

![1562474653799](imgs11/1562474653799.png)
{: id="20210309181757-xstnmje"}

![1562474692691](imgs11/1562474692691.png)
{: id="20210309181757-oaxn0li"}

##### 方式二：
{: id="20210309181757-zhyoxf2"}

在@Test后面按Ctrl + 1，在选择Add JUnit 4 library to the build path
{: id="20210309181757-c6g9lck"}

![1576580402867](imgs11/1576580402867.png)
{: id="20210309181757-0ig09xm"}

![1576580476913](imgs11/1576580476913.png)
{: id="20210309181757-g8iyy58"}

#### 在idea中截图如下：
{: id="20210309181757-h9184wi"}

##### 方式一：指定本地jar目录
{: id="20210309181757-on41vpo"}

单击工具栏的![1576580533760](imgs11/1576580533760.png)打开项目设置
{: id="20210309181757-6qeybov"}

![1576584674884](imgs11/1576584674884.png)
{: id="20210309181757-lvs4b9r"}

![1576584719209](imgs11/1576584719209.png)
{: id="20210309181757-m79bn5a"}

注意：如上操作需要提前下载，并将JUnit的相关jar放到当前模块的libs文件夹中。
{: id="20210309181757-9xyalgd"}

![1576584781088](imgs11/1576584781088.png)
{: id="20210309181757-fm6vlsg"}

##### 方式二：指定Marven仓库
{: id="20210309181757-teadhfd"}

在@Test后面按Alt + 回车，选择Add 'JUnit4' to classpath即可
{: id="20210309181757-ygsepq3"}

![1576580013065](imgs11/1576580013065.png)
{: id="20210309181757-vi3iall"}

![1576580073306](imgs11/1576580073306.png)
{: id="20210309181757-aw89qb1"}

**注意：如果Maven的本地仓库（例如：C:\Users\Irene\\.m2）中没有则需要联网从Maven的中央仓库中下载。**
{: id="20210309181757-lbpqsn0"}

![1576580095402](imgs11/1576580095402.png)
{: id="20210309181757-jpm8jak"}

* {: id="20210309181757-mc81k68"}首先使用JUnit测试的类必须是public的。需要测试的方法都必须是public，无参，无返回值。
  {: id="20210309181757-lr0z4vk"}
* {: id="20210309181757-mjvhqh5"}@Test：标记在非静态的测试方法上。只有标记@Test的方法才能被作为一个测试方法单独测试。一个类中可以有多个@Test标记的方法。运行时如果只想运行其中一个@Test标记的方法，那么选择这个方法名，然后单独运行，否则整个类的所有标记了@Test的方法都会被执行，**而且执行顺序不可控**。
  {: id="20210309181757-7v8022w"}
* {: id="20210309181757-2irnogt"}@BeforeClass：标记在静态方法上。因为这个方法只执行一次。在所有方法@Test方法之前执行。
  {: id="20210309181757-5c7erp0"}
* {: id="20210309181757-aoxcn2y"}@AfterClass：标记在静态方法上。因为这个方法只执行一次。在所有方法@Test方法完成后执行。
  {: id="20210309181757-gsfogj1"}
* {: id="20210309181757-voyv3nv"}@Before：标记在非静态方法上。在@Test方法前面执行，而且是在每一个@Test方法前面都执行
  {: id="20210309181757-jglonrm"}
* {: id="20210309181757-o6wsxwr"}@After：标记在非静态方法上。在@Test方法后面执行，而且是在每一个@Test方法后面都执行
  {: id="20210309181757-pfhgc8k"}
* {: id="20210309181757-gvztus1"}@BeforeClass、@AfterClass、@Before、@After都是配合@Test使用的，单独使用没有意义。
  {: id="20210309181757-h0n16mq"}
{: id="20210309181757-zkftdoh"}

这些注解会被JUnit框架读取，并处理。
{: id="20210309181757-1s9jdao"}

示例代码：
{: id="20210309181757-0pptdbg"}

```java
package com.atguigu.annotation;

import java.util.Arrays;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class TestJUnit {
	private static Object[] array;
	private static int total;

	@BeforeClass
	public static void init(){
		System.out.println("初始化数组");
		array = new Object[5];
		//默认添加一个元素
		array[total++] = "atguigu";
	}

	@Before
	public void before(){
		System.out.println("调用之前total=" + total);
		System.out.println("调用之前array=" + Arrays.toString(array));
	}
	@Test
	public void delete(){
		//从数组中删除一个元素
		System.out.println("delete");
		System.arraycopy(array, 1, array, 0, 2);
		array[--total]=null;
	}
	@Test
	public void tadd(){
		//往数组中存储三个元素
		System.out.println("add");
		array[total++] = "hello";
		array[total++] = "world";
		array[total++] = "java";
	}

	@After
	public void after(){
		System.out.println("调用之后total=" + total);
		System.out.println("调用之后array=" + Arrays.toString(array));
	}

	@AfterClass
	public static void destroy(){
		array = null;
		System.out.println("销毁数组");
	}
}
```
{: id="20210309181757-8mfgsnq"}

### 7.6.5 自定义注解
{: id="20210309181757-47v2865"}

#### 1、元注解
{: id="20210309181757-atiow9b"}

JDK1.5在java.lang.annotation包定义了4个标准的meta-annotation类型，它们被用来提供对其它 annotation类型作说明。
{: id="20210309181757-4m847s9"}

（1）**@Target**{: style="color: rgb(252, 13, 27);"}：用于描述注解的使用范围
{: id="20210309181757-j4ukjwj"}

* {: id="20210309181757-htiydpp"}可以通过枚举类型ElementType的10个常量对象来指定
  {: id="20210309181757-obb20es"}
* {: id="20210309181757-t7pnyge"}TYPE，METHOD，CONSTRUCTOR，PACKAGE.....
  {: id="20210309181757-m8f898b"}
{: id="20210309181757-v2norjh"}

（2）**@Retention**{: style="color: rgb(252, 13, 27);"}：用于描述注解的生命周期
{: id="20210309181757-kjgcm0y"}

* {: id="20210309181757-ekmq5sn"}可以通过枚举类型RetentionPolicy的3个常量对象来指定
  {: id="20210309181757-n8ifjzr"}
* {: id="20210309181757-clpqywy"}**SOURCE**{: style="background-color: rgb(255, 253, 56);"}（源代码）、**CLASS**{: style="background-color: rgb(255, 253, 56);"}（字节码）、**RUNTIME**{: style="background-color: rgb(255, 253, 56);"}（运行时）
  {: id="20210309181757-hp65ver"}
* {: id="20210309181757-gfcigcr"}**唯有RUNTIME阶段才能被反射读取到**{: style="background-color: rgb(255, 253, 56);"}。
  {: id="20210309181757-bky7cas"}
{: id="20210309181757-9pwyi8h"}

（3）@Documented：表明这个注解应该被 javadoc工具记录。
{: id="20210309181757-9nelsnf"}

（4）@Inherited：允许子类继承父类中的注解
{: id="20210309181757-j9b63xs"}

示例代码：
{: id="20210309181757-brtk4i4"}

```java
package java.lang;

import java.lang.annotation.*;

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.SOURCE)
public @interface Override {
}
```
{: id="20210309181757-t0x8xqm"}

```java
package java.lang;

import java.lang.annotation.*;
import static java.lang.annotation.ElementType.*;

@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
@Retention(RetentionPolicy.SOURCE)
public @interface SuppressWarnings {
    String[] value();
}
```
{: id="20210309181757-8w190ys"}

```java
package java.lang;

import java.lang.annotation.*;
import static java.lang.annotation.ElementType.*;

@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, PARAMETER, TYPE})
public @interface Deprecated {
}
```
{: id="20210309181757-c1eut8u"}

```java
@Target() //元注解 注解作用域
@Retention() //源注解 注解生命周期
public @interface MyAnno{
	public String name(); //注意这是个属性
}
```
{: id="20210309181757-6brmfkw" updated="20210310162539"}

#### 2、语法格式
{: id="20210310161519-84budmu" updated="20210310161519"}

```java
【@元注解】
【修饰符】 @interface 注解名{
    【配置参数列表;】
}
```
{: id="20210309181757-nmcg01d"}

* {: id="20210309181757-7azvsii"}Annotation 的成员变量在 Annotation 定义中以无参数方法的形式来声明。 其方法名和返回值定义了该成员的名字和类型. 我们称为配置参数。类型只能是八种基本数据类型、String类型、Class类型、enum类型、Annotation类型、以上所有类型的数组
  {: id="20210309181757-xhbotdf"}
* {: id="20210309181757-bgdi93p"}可以在定义 Annotation 的成员变量时为其指定初始值, 指定成员变量的初始值可使用 default 关键字
  {: id="20210309181757-5jgei9b"}
* {: id="20210309181757-ih8cpli"}如果只有一个参数成员，建议使用参数名为value
  {: id="20210309181757-wgbo8vm"}
* {: id="20210309181757-8ps5wmv"}如果定义的注解含有配置参数，那么使用时必须指定参数值，除非它有默认值。格式是“参数名 = 参数值”，如果只有一个参数成员需要赋值，且名称为value，可以省略“value=”
  {: id="20210309181757-7bctdor"}
* {: id="20210309181757-u0apncm"}自定义注解必须配上注解的信息处理流程才有意义。
  {: id="20210309181757-qh6f4yt"}
{: id="20210309181757-r6zrd5g"}

示例代码：
{: id="20210309181757-aquttfp"}

```java
package com.atguigu.annotation;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

public class TestDefineAnnotation {
	public static void main(String[] args) {
		//读取注解信息
		MyAnnotation my = MyClass.class.getAnnotation(MyAnnotation.class);
		System.out.println(my.value());
	}
}

@MyAnnotation("尚硅谷")
class MyClass{

}

@Documented
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@interface MyAnnotation{
	String value() default "atguigu";
}
```
{: id="20210309181757-76wyxlf"}


{: id="20210309181757-fu2uzza" type="doc"}
