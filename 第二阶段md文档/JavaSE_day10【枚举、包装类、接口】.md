# JavaSE_day10【枚举，包装类，接口】
{: id="20210309181757-bn26rse"}

## 今日内容
{: id="20210309181757-jtb7ak8"}

* {: id="20210309181757-twegk5n"}枚举
  {: id="20210309181757-ezji01o"}
* {: id="20210309181757-eg1drwh"}包装类
  {: id="20210309181757-2zwqfbk"}
* {: id="20210309181757-ip0l0b8"}接口
  {: id="20210309181757-zthb2yv"}
{: id="20210309181757-y4hhli9"}

## 学习目标
{: id="20210309181757-pm1zdrp"}

* {: id="20210309181757-6yd9kwz"}[ ] 认识枚举类型
  {: id="20210309181757-m0ttprc"}
* {: id="20210309181757-e0u3g7u"}[ ] 会使用枚举类型
  {: id="20210309181757-4h2c3hp"}
* {: id="20210309181757-79gdf5d"}[ ] 认识包装类
  {: id="20210309181757-8bypo34"}
* {: id="20210309181757-djiv13m"}[ ] 认识包装类
  {: id="20210309181757-dyig4cl"}
* {: id="20210309181757-19d8euz"}[ ] 掌握声明接口的格式
  {: id="20210309181757-1o3mjyk"}
* {: id="20210309181757-1l8heso"}[ ] 掌握实现接口的格式
  {: id="20210309181757-epb7yoa"}
* {: id="20210309181757-rcgmz4g"}[ ] 说出接口中成员的特点
  {: id="20210309181757-mwxzoxq"}
* {: id="20210309181757-7ltsb8g"}[ ] 说出接口的其他特点
  {: id="20210309181757-4xzjxa3"}
{: id="20210309181757-h6k2kps"}

# 第七章 面向对象基础--下（续）
{: id="20210309181757-4vr1d0o"}

## 7.1 枚举
{: id="20210309181757-5ucp4zs"}

### 7.1.1 概述
{: id="20210309181757-j8zuj4w"}

某些类型的对象是有限的几个，这样的例子举不胜举：
{: id="20210309181757-cteblxo"}

* {: id="20210309181757-e8b2ctl"}星期：Monday(星期一)......Sunday(星期天)
  {: id="20210309181757-8mgb8ug"}
* {: id="20210309181757-tt5udn6"}性别：Man(男)、Woman(女)
  {: id="20210309181757-6l4u28z"}
* {: id="20210309181757-u89s4pe"}月份：January(1月)......December(12月)
  {: id="20210309181757-51nfkdc"}
* {: id="20210309181757-x1ob0u8"}季节：Spring(春节)......Winter(冬天)
  {: id="20210309181757-vc83yp2"}
* {: id="20210309181757-ek37c08"}支付方式：Cash（现金）、WeChatPay（微信）、Alipay(支付宝)、BankCard(银行卡)、CreditCard(信用卡)
  {: id="20210309181757-mxfcwjx"}
* {: id="20210309181757-63iweny"}员工工作状态：Busy（忙）、Free（闲）、Vocation（休假）
  {: id="20210309181757-napeeh9"}
* {: id="20210309181757-w7cepoa"}订单状态：Nonpayment（未付款）、Paid（已付款）、Fulfilled（已配货）、Delivered（已发货）、Checked（已确认收货）、Return（退货）、Exchange（换货）、Cancel（取消）
  {: id="20210309181757-l37r9gp"}
{: id="20210309181757-9notvse"}

枚举类型本质上也是一种类，只不过是这个类的对象是固定的几个，而不能随意让用户创建。
{: id="20210309181757-rpq1wcc"}

在JDK1.5之前，需要程序员自己通过特殊的方式来定义枚举类型。
{: id="20210309181757-nfio93r"}

在JDK1.5之后，Java支持enum关键字来快速的定义枚举类型。
{: id="20210309181757-1z3ceh3"}

### 7.1.2 JDK1.5之前
{: id="20210309181757-nxlsi1a"}

在JDK1.5之前如何声明枚举类呢？
{: id="20210309181757-z95r5dg"}

* {: id="20210309181757-giomzyp"}构造器加private私有化
  {: id="20210309181757-8cpyc5q"}
* {: id="20210309181757-mejm3oz"}本类内部创建一组常量对象，并添加public static修饰符，对外暴露这些常量对象
  {: id="20210309181757-m1q15bx"}
{: id="20210309181757-2rxkp4w"}

示例代码：
{: id="20210309181757-0v37i6j"}

```java
public class TestEnum {
	public static void main(String[] args) {
		Season spring = Season.SPRING;
		System.out.println(spring);
	}
}
class Season{
	public static final Season SPRING = new Season();
	public static final Season SUMMER = new Season();
	public static final Season AUTUMN = new Season();
	public static final Season WINTER = new Season();

	private Season(){

	}

	public String toString(){
		if(this == SPRING){
			return "春";
		}else if(this == SUMMER){
			return "夏";
		}else if(this == AUTUMN){
			return "秋";
		}else{
			return "冬";
		}
	}
}
```
{: id="20210309181757-4cy1rz9"}

### 7.1.3 JDK1.5之后
{: id="20210309181757-4hk1ki2"}

语法格式：
{: id="20210309181757-0p9g4jd"}

```java
【修饰符】 enum 枚举类名{
    常量对象列表
}

【修饰符】 enum 枚举类名{
    常量对象列表;
  
    其他成员列表;
}
```
{: id="20210309181757-3rv7zs0"}

示例代码：
{: id="20210309181757-wrmfg0c"}

```java
public class TestEnum {
	public static void main(String[] args) {
		Season spring = Season.SPRING;
		System.out.println(spring);
	}
}
enum Season{
	SPRING,SUMMER,AUTUMN,WINTER
}
```
{: id="20210309181757-ksotmeg"}

示例代码：
{: id="20210309181757-2xeo2fi"}

```java
public class TestEnum {
	public static void main(String[] args) {
		Season spring = Season.SPRING;
		System.out.println(spring);
	}
}
enum Season{
	SPRING("春"),SUMMER("夏"),AUTUMN("秋"),WINTER("冬");
	private final String description;

	private Season(String description){
		this.description = description;
	}

	public String toString(){//需要手动编写，无法使用Generate toString()...
		return description;
	}
}
```
{: id="20210309181757-hm0btyf"}

枚举类的要求和特点：
{: id="20210309181757-lmkt9b3"}

* {: id="20210309181757-ao6hxyq"}枚举类的常量对象列表必须在枚举类的**首行**{: style="color: rgb(252, 13, 27);"}，因为是常量，所以建议大写。
  {: id="20210309181757-h2ku4v3"}
* {: id="20210309181757-xumepoj"}如果常量对象列表后面没有其他代码，那么“；”可以省略，否则不可以省略“；”。
  {: id="20210309181757-dv4j2uj"}
* {: id="20210309181757-n7ydt1u"}编译器给枚举类默认提供的是**private的无参构造**{: style="color: rgb(252, 13, 27);"}，如果枚举类需要的是无参构造，就不需要声明，写常量对象列表时也不用加参数，
  {: id="20210309181757-xxi2s62"}
* {: id="20210309181757-3awud9z"}如果枚举类需要的是有参构造，需要手动定义private的有参构造，调用有参构造的方法就是在常量对象名后面加(实参列表)就可以。
  {: id="20210309181757-viea5za"}
* {: id="20210309181757-8jn9390"}枚举类默认继承的是java.lang.**Enum**{: style="color: rgb(252, 13, 27);"}类，因此不能再继承其他的类型。
  {: id="20210309181757-wgtbybp"}
* {: id="20210309181757-hou82en"}JDK1.5之后switch，提供支持枚举类型，**case后面可以写枚举常量名**{: style="color: rgb(252, 13, 27);"}。
  {: id="20210309181757-3hllnpo"}
* {: id="20210309181757-6cu8jlz"}枚举类型如有其它属性，建议（**不是必须**）这些属性也声明为final的，因为常量对象在逻辑意义上应该不可变。
  {: id="20210309181757-zj1ok1b"}
{: id="20210309181757-woui4cj"}

### 7.1.4 枚举类型常用方法
{: id="20210309181757-hhfd740"}

> 1.**toString()**{: style="color: rgb(252, 13, 27);"}: 默认返回的是常量名（对象名），可以继续手动重写该方法！
> 2.**name()**{: style="color: rgb(252, 13, 27);"}:返回的是常量名（对象名） 【很少使用】
> 3.**ordinal()**{: style="color: rgb(252, 13, 27);"}:返回常量的次序号，默认从0开始
> 4.**values()**{: style="color: rgb(252, 13, 27);"}:返回该枚举类的所有的常量对象，返回类型是当前枚举的数组类型，是一个静态方法
> 5.**valueOf**{: style="color: rgb(252, 13, 27);"}(String name)：根据枚举常量对象名称获取枚举对象
> {: id="20210309185717-r6yllxk"}
{: id="20210309184919-xhkvrik"}

示例代码：
{: id="20210309181757-sefoay2"}

```java
public class TestEnum {
	public static void main(String[] args) {
		Season[] values = Season.values();
		for (int i = 0; i < values.length; i++) {
			switch(values[i]){
			case SPRING:
				System.out.println(values[i]+":春暖花开，万物复苏");
				break;
			case SUMMER:
				System.out.println(values[i]+":百花争艳，郁郁葱葱");
				break;
			case AUTUMN:
				System.out.println(values[i]+":菊桂飘香，百树凋零");
				break;
			case WINTER:
				System.out.println(values[i]+":梅花独开，大地一色");
				break;
			}
		}
	}
}
enum Season{
	SPRING,SUMMER,AUTUMN,WINTER
}
```
{: id="20210309181757-dostpbr"}

### 7.1.5 练习
{: id="20210309181757-dsnff9q"}

案例：
1、声明月份枚举类Month：
{: id="20210309181757-u1x5l1r"}

（1）创建：1-12月常量对象
{: id="20210309181757-tk6zw3r"}

```java
JANUARY,FEBRUARY,MARCH,APRIL,MAY,JUNE,JULY,AUGUST,SEPTEMBER,OCTOBER,NOVEMBER,DECEMBER
```
{: id="20210309181757-5tb7mt6"}

（2）声明两个属性：value（月份值，例如：JANUARY的value为1），
description（描述，例如：JANUARY的description为1月份是一年的开始）。
{: id="20210309181757-dsu0yn6"}

（3）声明一个有参构造，创建12个对象
{: id="20210309181757-y963sco"}

（4）声明一个方法：public static Month getByValue(int value)
{: id="20210309181757-tlvu6aw"}

（5）手动重写toString()：返回对象信息，例如：1->JANUARY->1月份是一年的开始。
{: id="20210309181757-c26ddwc"}

2、在测试类中，从键盘输入1个1-12的月份值，获取对应的月份对象，并打印对象
{: id="20210309181757-ogx9c9u"}

## 7.2 包装类
{: id="20210309181757-hvxcdmy"}

### 7.2.1 包装类
{: id="20210309181757-97yybn9"}

Java提供了两个类型系统，基本类型与引用类型，使用基本类型在于效率，然而当要使用只针对对象设计的API或新特性（例如泛型），那么基本数据类型的数据就需要用包装类来包装。
{: id="20210309181757-2nvg65y"}

| 序号 | 基本数据类型 | 包装类（java.lang包） |
| ------ | -------------- | ----------------------- |
| 1    | byte         | Byte                  |
| 2    | short        | Short                 |
| 3    | int          | **Integer**           |
| 4    | long         | Long                  |
| 5    | float        | Float                 |
| 6    | double       | Double                |
| 7    | char         | **Character**         |
| 8    | boolean      | Boolean               |
| 9    | void         | Void                  |
{: id="20210309181757-g0mzas8"}

### 7.2.2  装箱与拆箱
{: id="20210309181757-42gi44b"}

装箱：把基本数据类型转为包装类对象。
{: id="20210309181757-12zggce"}

> 转为包装类的对象，是为了使用专门为对象设计的API和特性
> {: id="20210309181757-l2nz5wv"}
{: id="20210309181757-4zz3tr7"}

拆箱：把包装类对象拆为基本数据类型。
{: id="20210309181757-mc366di"}

> 转为基本数据类型，一般是因为需要运算，Java中的大多数运算符是为基本数据类型设计的。比较、算术等
> {: id="20210309181757-y1khk8l"}
{: id="20210309181757-88n064t"}

基本数值---->包装对象
{: id="20210309181757-2ry7vsi"}

```java
Integer i1 = new Integer(4);//使用构造函数函数
Integer i2 = Integer.valueOf(4);//使用包装类中的valueOf方法
```
{: id="20210309181757-vqqaysh"}

包装对象---->基本数值
{: id="20210309181757-5h59mzx"}

```java
Integer i1 = new Integer(4);
int num1 = i1.intValue();
```
{: id="20210309181757-clk89kp"}

JDK1.5之后，可以自动装箱与拆箱。
{: id="20210309181757-7cpig1o"}

> 注意：只能与自己对应的类型之间才能实现自动装箱与拆箱。
> {: id="20210309181757-4xk59lc"}
{: id="20210309181757-bpnzsk1"}

```java
Integer i = 4;//自动装箱。相当于Integer i = Integer.valueOf(4);
i = i + 5;//等号右边：将i对象转成基本数值(自动拆箱) i.intValue() + 5;
//加法运算完成后，再次装箱，把基本数值转成对象。
```
{: id="20210309181757-firq50o"}

```java
Integer i = 1;
Double d = 1;//错误的，1是int类型
```
{: id="20210309181757-myryodx"}

总结：对象（引用数据类型）能用的运算符有哪些？
{: id="20210309181757-lrmhm32"}

（1）instanceof
{: id="20210309181757-faztruc"}

（2）=：赋值运算符
{: id="20210309181757-3q5jl30"}

（3）==和!=：用于比较地址，但是要求左右两边对象的类型一致或者是有父子类继承关系。
{: id="20210309181757-55zit3u"}

（4）对于字符串这一种特殊的对象，支持“+”，表示拼接。
{: id="20210309181757-qyq3xu8"}

### 7.2.3 包装类的一些API
{: id="20210309181757-mlas6g3"}

#### 1、基本数据类型和字符串之间的转换
{: id="20210309181757-oniu2rw"}

（1）把基本数据类型转为字符串
{: id="20210309181757-y818wmv"}

```java
int a = 10;
//String str = a;//错误的
//方式一：
String str = a + "";
//方式二：
String str = String.valueOf(a);
```
{: id="20210309181757-bea6t8p"}

（2）把字符串转为基本数据类型
{: id="20210309181757-572h5qs"}

String转换成对应的基本类型 ，除了Character类之外，其他所有包装类都具有parseXxx静态方法可以将字符串参数转换为对应的基本类型，例如：
{: id="20210309181757-2nhpatu"}

* {: id="20210309181757-37fszhy"}`**public static int parseInt(String s)**`：将字符串参数转换为对应的int基本类型。
  {: id="20210309181757-3wvn6on"}
* {: id="20210309181757-j58hg7t"}`**public static long parseLong(String s)**`：将字符串参数转换为对应的long基本类型。
  {: id="20210309181757-m6fm3m9"}
* {: id="20210309181757-u0i1gu7"}`**public static double parseDouble(String s)**`：将字符串参数转换为对应的double基本类型。
  {: id="20210309181757-hyo3ext"}
{: id="20210309181757-j78nxtm"}

或把字符串转为包装类，然后可以自动拆箱为基本数据类型
{: id="20210309181757-oiak27q"}

* {: id="20210309181757-3ow6893"}``**public static Integer valueOf(String s)**``：将字符串参数转换为对应的Integer包装类，然后可以自动拆箱为int基本类型
  {: id="20210309181757-eh1icmb"}
* {: id="20210309181757-hvhxqc4"}``**public static Long valueOf(String s)**``：将字符串参数转换为对应的Long包装类，然后可以自动拆箱为long基本类型
  {: id="20210309181757-t0m3ebt"}
* {: id="20210309181757-k9y1a8t"}``**public static Double valueOf(String s)**``：将字符串参数转换为对应的Double包装类，然后可以自动拆箱为double基本类型
  {: id="20210309181757-1c8fsms"}
{: id="20210309181757-rsfll5x"}

注意:如果字符串参数的内容无法正确转换为对应的基本类型，则会抛出`java.lang.NumberFormatException`异常。
{: id="20210309181757-nqkgvl1"}

```java
//字符串转包装类型
int a = Integer.parseInt("整数的字符串");
double d = Double.parseDouble("小数的字符串");
boolean b = Boolean.parseBoolean("true或false");
//包装类型转字符串
int a = Integer.valueOf("整数的字符串");
double d = Double.valueOf("小数的字符串");
boolean b = Boolean.valueOf("true或false");
```
{: id="20210309181757-95agt1a" updated="20210309185551"}

#### 2、数据类型的最大最小值
{: id="20210309181757-r1ue03f"}

```java
Integer.MAX_VALUE和Integer.MIN_VALUE
Long.MAX_VALUE和Long.MIN_VALUE
Double.MAX_VALUE和Double.MIN_VALUE
```
{: id="20210309181757-xo62m5u"}

#### 3、字符转大小写
{: id="20210309181757-zwovpph"}

```java
Character.toUpperCase('x');
Character.toLowerCase('X');
```
{: id="20210309181757-911th48"}

#### 4、整数转进制
{: id="20210309181757-h77m584"}

```java
Integer.toBinaryString(int i) 
Integer.toHexString(int i)
Integer.toOctalString(int i)
```
{: id="20210309181757-zaic1bd"}

### 7.2.4 包装类对象的缓存问题
{: id="20210309181757-o0pjohe"}

| 包装类    | 缓存对象    |
| ----------- | ------------- |
| Byte      | -128~127    |
| Short     | -128~127    |
| Integer   | -128~127    |
| Long      | -128~127    |
| Float     | 没有        |
| Double    | 没有        |
| Character | 0~127       |
| Boolean   | true和false |
{: id="20210309181757-mv0b20a"}

```java
Integer i = 1;
Integer j = 1;
System.out.println(i == j);//true

Integer i = 128;
Integer j = 128;
System.out.println(i == j);//false

Integer i = new Integer(1);//新new的在堆中
Integer j = 1;//这个用的是缓冲的常量对象，在方法区
System.out.println(i == j);//false

Integer i = new Integer(1);//新new的在堆中
Integer j = new Integer(1);//另一个新new的在堆中
System.out.println(i == j);//false
```
{: id="20210309181757-cu2vo66"}

```java
	@Test
	public void test3(){
		Double d1 = 1.0;
		Double d2 = 1.0;
		System.out.println(d1==d2);//false 比较地址，没有缓存对象，每一个都是新new的
	}
```
{: id="20210309181757-79zheyw"}

### 7.2.5 面试题
{: id="20210309181757-0y0t8rf"}

#### 1、类型转换问题
{: id="20210309181757-zbzjci7"}

```java
	@Test
	public void test4(){
		Double d1 = 1.0;
		double d2 = 1.0;
		System.out.println(d1==d2);//true 和基本数据类型比较会自动拆箱，比较数据值
	}

	@Test
	public void test2(){
		Integer i = 1000;
		double j = 1000;
		System.out.println(i==j);//true  会先将i自动拆箱为int，然后根据基本数据类型“自动类型转换”规则，转为double比较
	}

	@Test
	public void test(){
		Integer i = 1000;
		int j = 1000;
		System.out.println(i==j);//true 会自动拆箱，按照基本数据类型进行比较
	}
```
{: id="20210309181757-m08dwef"}

#### 2、不可变对象
{: id="20210309181757-swygwbn"}

```java
public class TestExam {
	public static void main(String[] args) {
		int i = 1;
		Integer j = new Integer(2);
		Circle c = new Circle();
		change(i,j,c);
		System.out.println("i = " + i);//1
		System.out.println("j = " + j);//2
		System.out.println("c.radius = " + c.radius);//10.0
	}

	/*
	 * 方法的参数传递机制：
	 * （1）基本数据类型：形参的修改完全不影响实参
	 * （2）引用数据类型：通过形参修改对象的属性值，会影响实参的属性值
	 * 这类Integer等包装类对象是“不可变”对象，即一旦修改，就是新对象，和实参就无关了
	 */
	public static void change(int a ,Integer b,Circle c ){
		a += 10;
//		b += 10;//等价于  b = new Integer(b+10);
		c.radius += 10;
		/*c = new Circle();
		c.radius+=10;*/
	}
}
class Circle{
	double radius;
}
```
{: id="20210309181757-xvs2zfu"}

## 7.3 接口
{: id="20210309181757-398f5vc"}

### 7.3.1 概述
{: id="20210309181757-w51ngjs"}

生活中大家每天都在用USB接口，那么USB接口与我们今天要学习的接口有什么相同点呢？
{: id="20210309181757-ldwrqwz"}

```
USB是通用串行总线的英文缩写，是Intel公司开发的总线架构，使得在计算机上添加串行设备（鼠标、键盘、打印机、扫描仪、摄像头、充电器、MP3机、手机、数码相机、移动硬盘等）非常容易。只须将设备插入计算机的USB端口中，系统会自动识别和配置。 有了USB，我们电脑需要提供的各种插槽的口越来越少，而能支持的其他设备的连接却越来越多。
```
{: id="20210309181757-18obhha"}

```
那么我们平时看到的电脑上的USB插口、以及其他设备上的USB插口是什么呢？
```
{: id="20210309181757-fvbqntj"}

```
其实，不管是电脑上的USB插口，还是其他设备上的USB插口都只是遵循了USB规范的一种具体设备而已。
```
{: id="20210309181757-0pc30vi"}

```
根据时代发展，USB接口标准经历了一代USB、第二代USB 2.0和第三代USB 3.0 。
```
{: id="20210309181757-utz9m2k"}

```
USB规格第一次是于1995年，由Intel、IBM、Compaq、Microsoft、NEC、Digital、North Telecom等七家公司组成的USBIF(USB Implement Forum)共同提出，USBIF于1996年1月正式提出USB1.0规格，频宽为1.5Mbps。
```
{: id="20210309181757-c2twr7w"}

USB2.0技术规范是有由Compaq、Hewlett Packard、Intel、Lucent、Microsoft、NEC、Philips共同制定、发布的，规范把外设数据传输速度提高到了480Mbps，被称为USB 2.0的高速(High-speed)版本.
{: id="20210309181757-z7xbwer"}

USB 3.0是最新的USB规范，该规范由英特尔等公司发起,USB3.0的最大传输带宽高达5.0Gbps(640MB/s),USB3.0 引入全双工数据传输。5根线路中2根用来发送数据，另2根用来接收数据，还有1根是地线。也就是说，USB 3.0可以同步全速地进行读写操作。
{: id="20210309181757-jwwqmtn"}

| **USB版本** | **最大传输速率** | **速率称号**          | **最大输出电流** | **推出时间** |
| ------------- | ------------------ | ----------------------- | ------------------ | -------------- |
| USB1.0      | 1.5Mbps(192KB/s) | 低速(Low-Speed)       | 5V/500mA         | 1996年1月    |
| USB1.1      | 12Mbps(1.5MB/s)  | 全速(Full-Speed)      | 5V/500mA         | 1998年9月    |
| USB2.0      | 480Mbps(60MB/s)  | 高速(High-Speed)      | 5V/500mA         | 2000年4月    |
| USB3.0      | 5Gbps(500MB/s)   | 超高速(Super-Speed)   | 5V/900mA         | 2008年11月   |
| USB 3.1     | 10Gbps(1280MB/s) | 超高速+(Super-speed+) | 20V/5A           | 2013年12月   |
{: id="20210309181757-2y57nsb"}

下面是USB2.0和USB3.0标准下的各类接口示意图：
{: id="20210309181757-ggb1etv"}

![](imgs10/20180627200402517.png)
{: id="20210309181757-rw0lie3"}

```
电脑边上提供了USB插槽，这个插槽遵循了USB的规范，只要其他设备也是遵循USB规范的，那么就可以互联，并正常通信。至于这个电脑、以及其他设备是哪个厂家制造的，内部是如何实现的，我们都无需关心。
```
{: id="20210309181757-38jcxft"}

```
这种设计是将规范和实现分离，这也正是Java接口的好处。Java的软件系统会有很多模块组成，那么各个模块之间也应该采用这种面相接口的低耦合，为系统提供更好的可扩展性和可维护性。
```
{: id="20210309181757-mek51iv"}

* {: id="20210309181757-jwvlq3b"}接口就是规范，定义的是一组规则，体现了现实世界中“如果你是/要...则必须能...”的思想。继承是一个"是不是"的is-a关系，而接口实现则是 "能不能"的has-a关系。
  {: id="20210309181757-8sfufk1"}

  * {: id="20210309181757-pwc6kbd"}例如：你能不能用USB进行连接，或是否具备USB通信功能，就看你是否遵循USB接口规范
    {: id="20210309181757-srz5woi"}
  * {: id="20210309181757-2yzzh4b"}例如：Java程序是否能够连接使用某种数据库产品，那么要看该数据库产品有没有实现Java设计的JDBC规范
    {: id="20210309181757-zw2nlp5"}
  {: id="20210309181757-t27uslv"}
{: id="20210309181757-xht1hbj"}

![1562216188519](imgs10/1562216188519.png)
{: id="20210309181757-c01lwec"}

![1562891521094](imgs10/1562891521094.png)
{: id="20210309181757-fhueomj"}

### 7.3.2 定义格式
{: id="20210309181757-rlboslb"}

接口的定义，它与定义类方式相似，但是使用 `interface` 关键字。它也会被编译成.class文件，但一定要明确它并不是类，而是另外一种引用数据类型。
{: id="20210309181757-muwpbc9"}

> 引用数据类型：数组，类，接口。
> {: id="20210309181757-iuavjtt"}
{: id="20210309181757-8y7dw7e"}

#### 1、接口的声明格式
{: id="20210309181757-c6ny3o8"}

```java
【修饰符】 interface 接口名{
    //接口的成员列表：
    // 静态常量
    // 抽象方法
    // 默认方法  默认就是抽象方法public abstract
    // 静态方法
    // 私有方法  1.9才有
}
```
{: id="20210309181757-bmytkm0"}

示例代码：
{: id="20210309181757-tqr982a"}

```java
interface Usb3{
    //静态常量
	long MAX_SPEED = 500*1024*1024;//500MB/s
  
    //抽象方法
	void read();
    void write();
  
    //默认方法
    public default void start(){
        System.out.println("开始");
    }
    public default void stop(){
        System.out.println("结束");
    }
  
    //静态方法
    public static void show(){
        System.out.println("USB 3.0可以同步全速地进行读写操作");
    }
}
```
{: id="20210309181757-n90rmyy"}

#### 2、接口的成员说明
{: id="20210309181757-bitbtwc"}

接口定义的是多个类共同的公共行为规范，这些行为规范是与外部交流的通道，这就意味着接口里通常是定义一组公共方法。
{: id="20210309181757-qk14hto"}

在JDK8之前，接口中只允许出现：
{: id="20210309181757-e0zqtsc"}

（1）公共的静态的常量：其中public static final可以省略
{: id="20210309181757-zez0t85"}

（2）公共的抽象的方法：其中public abstract可以省略
{: id="20210309181757-mnb3qi8"}

> 理解：接口是从多个相似类中抽象出来的规范，不需要提供具体实现
> {: id="20210309181757-rarbu58"}
{: id="20210309181757-oym2hcx"}

在JDK1.8时，接口中允许声明默认方法和静态方法：
{: id="20210309181757-lmt3h36"}

（3）公共的默认的方法：其中public 可以省略，建议保留，但是default不能省略
{: id="20210309181757-775mntt"}

（4）公共的静态的方法：其中public 可以省略，建议保留，但是static不能省略
{: id="20210309181757-gf4p4z3"}

在JDK1.9时，接口又增加了：
{: id="20210309181757-7ccl8ca"}

（5）私有方法
{: id="20210309181757-pri9fyf"}

除此之外，接口中不能有其他成员，没有构造器，没有初始化块，因为接口中没有成员变量需要初始化。
{: id="20210309181757-h8s94sh"}

#### 3、面试题拷问？
{: id="20210309181757-qb4frwa"}

1、为什么接口中只能声明公共的静态的常量？
{: id="20210309181757-a3btv8k"}

因为接口是标准规范，那么在规范中需要声明一些底线边界值，当实现者在实现这些规范时，不能去随意修改和触碰这些底线，否则就有“危险”。
{: id="20210309181757-q15g13g"}

例如：USB1.0规范中规定最大传输速率是1.5Mbps，最大输出电流是5V/500mA
{: id="20210309181757-psc7jik"}

```
USB3.0规范中规定最大传输速率是5Gbps(500MB/s)，最大输出电流是5V/900mA
```
{: id="20210309181757-9jdnejz"}

例如：尚硅谷学生行为规范中规定学员，早上8:25之前进班，晚上21:30之后离开等等。
{: id="20210309181757-1drh06s"}

2、为什么JDK1.8之后要允许接口定义静态方法和默认方法呢？因为它违反了接口作为一个抽象标准定义的概念。
{: id="20210309181757-j3jqq38"}

**静态方法**：因为之前的标准类库设计中，有很多Collection/Colletions或者Path/Paths这样成对的接口和类，后面的类中都是静态方法，而这些静态方法都是为前面的接口服务的，那么这样设计一对API，不如把静态方法直接定义到接口中使用和维护更方便。
{: id="20210309181757-soobmyw"}

**默认方法**：（1）我们要在已有的老版接口中提供新方法时，如果添加抽象方法，就会涉及到原来使用这些接口的类就会有问题，那么为了保持与旧版本代码的兼容性，只能允许在接口中定义默认方法实现。比如：Java8中对Collection、List、Comparator等接口提供了丰富的默认方法。（2）当我们接口的某个抽象方法，在很多实现类中的实现代码是一样的，此时将这个抽象方法设计为默认方法更为合适，那么实现类就可以选择重写，也可以选择不重写。
{: id="20210309181757-gfy60oj"}

3、为什么JDK1.9要允许接口定义私有方法呢？因为我们说接口是规范，规范时需要公开让大家遵守的
{: id="20210309181757-zyv64r4"}

**私有方法**：因为有了默认方法和静态方法这样具有具体实现的方法，那么就可能出现多个方法由共同的代码可以抽取，而这些共同的代码抽取出来的方法又只希望在接口内部使用，所以就增加了私有方法。
{: id="20210309181757-s23emej"}

### 7.3.3 实现接口
{: id="20210309181757-urwmw4a"}

接口的使用，它**不能创建对象**，但是可以被实现（`implements` ，类似于被继承）。
{: id="20210309181757-9abh9zf"}

类与接口的关系为实现关系，即**类实现接口**，该类可以称为接口的实现类，也可以称为接口的子类。实现的动作类似继承，格式相仿，只是关键字不同，实现使用 ` implements`关键字。
{: id="20210309181757-h3gcvat"}

#### 1、实现接口语法格式
{: id="20210309181757-j51yh5m"}

```java
【修饰符】 class 实现类  implements 接口{
	// 重写接口中抽象方法【必须】，当然如果实现类是抽象类，那么可以不重写
  	// 重写接口中默认方法【可选】
}

【修饰符】 class 实现类 extends 父类 implements 接口{
    // 重写接口中抽象方法【必须】，当然如果实现类是抽象类，那么可以不重写
  	// 重写接口中默认方法【可选】
}
```
{: id="20210309181757-0821102"}

**注意：**{: style="color: rgb(252, 13, 27);"}
{: id="20210309181757-k7xhun6" updated="20210309190428"}

1. {: id="20210309181757-drvimd2"}如果接口的实现类是非抽象类，那么必须重写接口中**所有**{: style="color: rgb(252, 13, 27);"}抽象方法。
   {: id="20210309181757-pfe85ee"}
2. {: id="20210309181757-ip2dag2"}默认方法**可以选择保留，也可以重写**{: style="color: rgb(252, 13, 27);"}。
   {: id="20210309181757-n894op5"}

   > **重写时**{: style="color: rgb(252, 13, 27);"}，**default单词就不要再写了**{: style="color: rgb(252, 13, 27);"}，它只用于在接口中表示默认方法，到类中就没有默认方法的概念了
   > {: id="20210309181757-dofjj7i"}
   >
   {: id="20210309181757-dbgpbv3"}
3. {: id="20210309181757-k8y3k19"}**不能重写静态方法**{: style="color: rgb(252, 13, 27);"}
   {: id="20210309181757-twfbj6r"}
{: id="20210309181757-mcue9bx"}

示例代码：
{: id="20210309181757-gdq4777"}

```java
class MobileHDD implements Usb3{

	//重写/实现接口的抽象方法，【必选】
	public void read() {
		System.out.println("读数据");
	}
    public void write(){
        System.out.println("写数据");
    }

	//重写接口的默认方法，【可选】
	//重写默认方法时，default单词去掉
	public void end(){
        System.out.println("清理硬盘中的隐藏回收站中的东西，再结束");
    }
}
```
{: id="20210309181757-lfu1pl1"}

#### 2、如何调用对应的方法
{: id="20210309181757-fjlt6q1"}

* {: id="20210309181757-fr8b68u"}对于接口的静态方法，直接使用“接口名.”进行调用即可
  {: id="20210309181757-062v88z"}

  * {: id="20210309181757-k58lw50"}也只能使用“接口名."进行调用，**不能**{: style="color: rgb(252, 13, 27);"}通过实现类的**对象进行调用**{: style="color: rgb(252, 13, 27);"}
    {: id="20210309181757-kz5tzwj"}
  {: id="20210309181757-f6yyu94"}
* {: id="20210309181757-frgqa8i"}对于接口的抽象方法、默认方法，只能通过实现类对象才可以调用
  {: id="20210309181757-zv4ybob"}

  * {: id="20210309181757-2bphjfb"}接口不能直接创建对象，只能创建实现类的对象
    {: id="20210309181757-j9f58sl"}
  {: id="20210309181757-jj1h4s5"}
{: id="20210309181757-qnboba8"}

```java
public class TestInteface {
	public static void main(String[] args) {
		//创建实现类对象
		MobileHDD b = new MobileHDD();

		//通过实现类对象调用重写的抽象方法，以及接口的默认方法，如果实现类重写了就执行重写的默认方法，如果没有重写，就执行接口中的默认方法
		b.start();
		b.read();
		b.stop();

		//通过接口名调用接口的静态方法
		MobileHDD.show();
	}
}
```
{: id="20210309181757-jy51btm"}

#### 3、练习
{: id="20210309181757-wqx3r7z"}

1、声明一个LiveAble接口
{: id="20210309181757-w5jdpbp"}

* {: id="20210309181757-kccwi1l"}包含两个抽象方法：
  {: id="20210309181757-icdmbbv"}

  * {: id="20210309181757-gsxqy9p"}void eat();
    {: id="20210309181757-xu2cw1c"}
  * {: id="20210309181757-ytndaa9"}void breathe();
    {: id="20210309181757-gde2t1r"}
  {: id="20210309181757-6gxerzm"}
* {: id="20210309181757-3z2t4wt"}包含默认方法  default void sleep()，实现为打印“静止不动”
  {: id="20210309181757-plsl7mi"}
* {: id="20210309181757-aqikt4g"}包含静态方法 static void drink()，实现为“喝水”
  {: id="20210309181757-ueeodll"}
{: id="20210309181757-xekcovu"}

2、声明动物Animal类，实现LiveAble接口。
{: id="20210309181757-7r28zte"}

* {: id="20210309181757-sfl25ph"}void eat();实现为“吃东西”，
  {: id="20210309181757-rg609fb"}
* {: id="20210309181757-zifoln8"}void breathe();实现为"吸入氧气呼出二氧化碳"
  {: id="20210309181757-flkebqb"}
* {: id="20210309181757-fzodxy8"}void sleep()重写为”闭上眼睛睡觉"
  {: id="20210309181757-aw6e1tl"}
{: id="20210309181757-zy322sn"}

3、声明植物Plant类，实现LiveAble接口。
{: id="20210309181757-hep5tij"}

* {: id="20210309181757-ggd5tmt"}void eat();实现为“吸收营养”
  {: id="20210309181757-j69vn73"}
* {: id="20210309181757-4ic3q1u"}void breathe();实现为"吸入二氧化碳呼出氧气"
  {: id="20210309181757-9d9vb4s"}
{: id="20210309181757-uwugufi"}

4、在测试类中，分别创建两个实现类的对象，调用对应的方法。通过接口名，调用静态方法
{: id="20210309181757-l5iwckw"}

定义接口：
{: id="20210309181757-lmdibyr"}

```java
public interface LiveAble {
    // 定义抽象方法
    public abstract void eat();
    public abstract void breathe();
    //定义默认方法
    public default void sleep(){
    	System.out.println("静止不动");
    }
    //定义静态方法
    public static void drink(){
    	System.out.println("喝水");
    }
}
```
{: id="20210309181757-vlvk26p"}

定义实现类：
{: id="20210309181757-mfh1g4s"}

```java
public Animal implements LiveAble {
	//重写/实现接口的抽象方法
    @Override
    public void eat() {
        System.out.println("吃东西");
    }
  
    //重写/实现接口的抽象方法
    @Override
    public void breathe(){
        System.out.println("吸入氧气呼出二氧化碳");
    }
  
    //重写接口的默认方法
    @Override
    public void sleep() {
        System.out.println("闭上眼睛睡觉");
    }
}
```
{: id="20210309181757-doizj5b"}

```java
public class Plant implements LiveAble {
	//重写/实现接口的抽象方法
    @Override
    public void eat() {
        System.out.println("吸收营养");
    }
    //重写/实现接口的抽象方法
    @Override
    public void breathe(){
        System.out.println("吸入二氧化碳呼出氧气");
    }
}
```
{: id="20210309181757-fiit47i"}

定义测试类：
{: id="20210309181757-yjhsact"}

```java
public class InterfaceDemo {
    public static void main(String[] args) {
        // 创建实现类（子类）对象  
        Animal a = new Animal();
        // 调用实现后的方法
        a.eat();
        a.sleep();
        a.breathe();
  
        //创建实现类（子类）对象
        Plant p = new Plant();
        p.eat();
        p.sleep();
        p.breathe();
  
        //通过接口调用静态方法
        LiveAble.drink();
    }
}
输出结果：
吃东西
闭上眼睛睡觉
吸入氧气呼出二氧化碳
吸收营养
静止不动
吸入二氧化碳呼出氧气
喝水
```
{: id="20210309181757-wjo7kul"}

### 7.3.4 接口的多实现
{: id="20210309181757-ip1ub6r"}

之前学过，在继承体系中，一个类只能继承一个父类。而对于接口而言，一个类是可以实现多个接口的，这叫做接口的**多实现**。并且，一个类能继承一个父类，同时实现多个接口。
{: id="20210309181757-6gdml49"}

实现格式：
{: id="20210309181757-m9djvxa"}

```java
【修饰符】 class 实现类  implements 接口1，接口2，接口3。。。{
	// 重写接口中所有抽象方法【必须】，当然如果实现类是抽象类，那么可以不重写
  	// 重写接口中默认方法【可选】
}

【修饰符】 class 实现类 extends 父类 implements 接口1，接口2，接口3。。。{
    // 重写接口中所有抽象方法【必须】，当然如果实现类是抽象类，那么可以不重写
  	// 重写接口中默认方法【可选】
}
```
{: id="20210309181757-ts5wk37"}

> 接口中，有多个抽象方法时，实现类必须重写所有抽象方法。**如果抽象方法有重名的，只需要重写一次**。
> {: id="20210309181757-a8qg170"}
{: id="20210309181757-7uoyovo"}

定义多个接口：
{: id="20210309181757-ikl7a0k"}

```java
interface A {
    public abstract void showA();
    public abstract void show();
}

interface B {
    public abstract void showB();
    public abstract void show();
}
```
{: id="20210309181757-hmz1989"}

定义实现类：
{: id="20210309181757-y387jl4"}

```java
public class C implements A,B{
    @Override
    public void showA() {
        System.out.println("showA");
    }

    @Override
    public void showB() {
        System.out.println("showB");
    }

    @Override
    public void show() {
        System.out.println("show");
    }
}
```
{: id="20210309181757-zhuya67"}

#### 练习
{: id="20210309181757-wnac3ux"}

1、声明第一个接口Runner，包含抽象方法：void run()
{: id="20210309181757-8spyyc2"}

2、声明第二个接口Swimming，包含抽象方法：void swim()
{: id="20210309181757-1e39cmm"}

3、声明兔子类，实现Runner接口
{: id="20210309181757-389sgp8"}

4、声明乌龟类，实现Runner接口和Swimming接口
{: id="20210309181757-v72z7sz"}

```java
interface Runner{
	void run();
}
```
{: id="20210309181757-587b200"}

```java
interface Swimming{
	void swim();
}
```
{: id="20210309181757-o9x5uh0"}

```java
class Rabbit implements Runner{

	@Override
	public void run() {
		System.out.println("兔子跑得快");
	}

}
```
{: id="20210309181757-cmwt2bz"}

```java
class Tortoise implements Runner,Swimming{

	@Override
	public void swim() {
		System.out.println("乌龟游得快");
	}

	@Override
	public void run() {
		System.out.println("乌龟跑的慢");
	}

}
```
{: id="20210309181757-enz1ag0"}

### 7.3.5 默认方法冲突问题
{: id="20210309181757-s51lwj7"}

#### 1、亲爹优先原则
{: id="20210309181757-mmsglxu"}

当一个类，既继承一个父类，又实现若干个接口时，父类中的成员方法与接口中的抽象方法重名，子类就近选择执行父类的成员方法。代码如下：
{: id="20210309181757-u8myqzz"}

定义接口：
{: id="20210309181757-24g8y00"}

```java
interface A {
    public default void methodA(){
        System.out.println("AAAAAAAAAAAA");
    }
}
```
{: id="20210309181757-aedsb6q"}

定义父类：
{: id="20210309181757-ts4jpvt"}

```java
class D {
    public void methodA(){
        System.out.println("DDDDDDDDDDDD");
    }
}
```
{: id="20210309181757-4lq2xda"}

定义子类：
{: id="20210309181757-9chxoqm"}

```java
class C extends D implements A {
  	// 未重写methodA方法
}
class B extends D implements A{
    //当然也可以选择重写
    public void methodA(){
        System.out.println("BBBBBBBBBBBB");
    }
}
```
{: id="20210309181757-rz6suyd"}

定义测试类：
{: id="20210309181757-cgfflwa"}

```java
public class Test {
    public static void main(String[] args) {
        C c = new C();
        c.methodA(); 
  
        B b = new B();
        b.methodA();
    }
}
输出结果:
DDDDDDDDDDDD
BBBBBBBBBBBB
```
{: id="20210309181757-ed1o9n1"}

#### 2、必须做出选择
{: id="20210309181757-rqz3mj1"}

当一个类同时实现了多个接口，而多个接口中包含方法签名相同的默认方法时，怎么办呢？
{: id="20210309181757-oynmirz"}

![](imgs10/选择困难.jpg)
{: id="20210309181757-ju4utnk"}

无论你多难抉择，最终都是要做出选择的。代码如下：
{: id="20210309181757-k2ceg53"}

声明接口：
{: id="20210309181757-0gu6jqd"}

```java
interface A{
	public default void d(){
		System.out.println("今晚7点-8点陪我吃饭看电影");
	}
}
interface B{
	public default void d(){
		System.out.println("今晚7点-8点陪我逛街吃饭");
	}
}
```
{: id="20210309181757-119dsaz"}

选择保留其中一个，通过“接口名.super.方法名"的方法选择保留哪个接口的默认方法。
{: id="20210309181757-1ucbzpb"}

```java
class C implements A,B{

	@Override
	public void d() {
		A.super.d();
	}

}
```
{: id="20210309181757-8o9xzda"}

选择自己完全重写：
{: id="20210309181757-jcq2092"}

```java
class D implements A,B{
	@Override
	public void d() {
		System.out.println("自己待着");
	}
}
```
{: id="20210309181757-0dhzwel"}

### 7.3.6 接口的多继承
{: id="20210309181757-dyf34d5"}

一个接口能继承另一个或者多个接口，接口的继承也使用 `extends` 关键字，子接口继承父接口的方法。
{: id="20210309181757-dd0eon8"}

定义父接口：
{: id="20210309181757-l0wnde5"}

```java
interface A {
    void a();
    public default void methodA(){
        System.out.println("AAAAAAAAAAAAAAAAAAA");
    }
}

interface B {
    void b();
    public default void methodB(){
        System.out.println("BBBBBBBBBBBBBBBBBBB");
    }
}
```
{: id="20210309181757-a18b0or"}

定义子接口：
{: id="20210309181757-bc5i435"}

```java
interface C extends A,B{
    @Override
    public default void methodB() {
        System.out.println("CCCCCCCCCCCCCCCCCCCC");
    }
}
```
{: id="20210309181757-mywreey"}

> 小贴士：
> {: id="20210309181757-4j9st4y"}
>
> 子接口重写默认方法时，default关键字可以保留。
> {: id="20210309181757-563vjp9"}
>
> 子类重写默认方法时，default关键字不可以保留。
> {: id="20210309181757-i4kolh1"}
{: id="20210309181757-xweh5bq"}

```java
class D implements C{

	@Override
	public void a() {
		System.out.println("xxxxx");
	}

	@Override
	public void b() {
		System.out.println("yyyyy");
	}

}
```
{: id="20210309181757-532vcn7"}

```java
class E implements A,B,C{//效果和上面的D是等价的

	@Override
	public void b() {
		System.out.println("xxxxx");
	}

	@Override
	public void a() {
		System.out.println("yyyyy");
	}

}
```
{: id="20210309181757-1lzljsv"}

### 7.3.7 接口与实现类对象的多态引用
{: id="20210309181757-v7l8nl1"}

实现类实现接口，类似于子类继承父类，因此，接口类型的变量与实现类的对象之间，也可以构成多态引用。通过接口类型的变量调用方法，最终执行的是你new的实现类对象实现的方法体。
{: id="20210309181757-x1kg6zb"}

```java
public class TestInterface {
	public static void main(String[] args) {
		Flyable b = new Bird();
		b.fly();

		Flyable k = new Kite();
		k.fly();
	}
}
interface Flyable{
    //抽象方法
	void fly();
}
class Bird implements Flyable{

	@Override
	public void fly() {
		System.out.println("展翅高飞");
	}

}
class Kite implements Flyable{

	@Override
	public void fly() {
		System.out.println("别拽我，我要飞");
	}

}
```
{: id="20210309181757-ea69slc"}


{: id="20210309181757-heyp0ed" type="doc"}
