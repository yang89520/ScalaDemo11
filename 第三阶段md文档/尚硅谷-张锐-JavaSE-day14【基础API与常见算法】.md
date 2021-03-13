# JavaSE_day14【基础API与常见算法】
{: id="20210313082711-oj212xm"}

## 主要内容
{: id="20210313082711-acefjq9"}

* {: id="20210313082711-p3v9jff"}常用类
  {: id="20210313082711-qk1kxbj"}
* {: id="20210313082711-trjy03z"}基础算法
  {: id="20210313082711-za8smod"}
{: id="20210313082711-8wi10vx"}

## 学习目标
{: id="20210313082711-mntbtrx"}

* {: id="20210313082711-v6orhiw"}[ ] 了解数学相关API
  {: id="20210313082711-soxm6xi"}
* {: id="20210313082711-uoxup64"}[ ] 了解日期时间API
  {: id="20210313082711-c5nm1xd"}
* {: id="20210313082711-mheui1t"}[ ] 了解系统类API
  {: id="20210313082711-76df5di"}
* {: id="20210313082711-rsc9cj1"}[ ] 掌握数组基础算法
  {: id="20210313082711-90wkf2y"}
* {: id="20210313082711-7348hg8"}[ ] 掌握数组工具类的使用
  {: id="20210313082711-559bvn5"}
{: id="20210313082711-3y4e61m"}

# 第十章 基础API与常见算法
{: id="20210313082711-7lynynk"}

## 10.1 和数学相关的类
{: id="20210313082711-c0y27m2"}

### 10.1.1 java.lang.Math
{: id="20210313082711-zfa76co"}

`java.lang.Math` 类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。类似这样的工具类，其所有方法均为静态方法，并且不会创建对象，调用起来非常简单。
{: id="20210313082711-6lim08d"}

* {: id="20210313082711-p6m8sl9"}`public static double abs(double a) ` ：返回 double 值的绝对值。
  {: id="20210313082711-cpfw18d"}
{: id="20210313082711-dt8i0sm"}

```java
double d1 = Math.abs(-5); //d1的值为5
double d2 = Math.abs(5); //d2的值为5
```
{: id="20210313082711-mz1dybj"}

* {: id="20210313082711-w7x3vfx"}`public static double ceil(double a)` ：返回大于等于参数的最小的整数。
  {: id="20210313082711-e402ucz"}
{: id="20210313082711-1ckzm46"}

```java
double d1 = Math.ceil(3.3); //d1的值为 4.0
double d2 = Math.ceil(-3.3); //d2的值为 -3.0
double d3 = Math.ceil(5.1); //d3的值为 6.0
```
{: id="20210313082711-7kl632u"}

* {: id="20210313082711-f84looi"}`public static double floor(double a) ` ：返回小于等于参数最大的整数。
  {: id="20210313082711-6m8haq9"}
{: id="20210313082711-g41osry"}

```java
double d1 = Math.floor(3.3); //d1的值为3.0
double d2 = Math.floor(-3.3); //d2的值为-4.0
double d3 = Math.floor(5.1); //d3的值为 5.0
```
{: id="20210313082711-slbuls3"}

* {: id="20210313082711-yjylneb"}`public static long round(double a)` ：返回最接近参数的 long。(相当于四舍五入方法)
  {: id="20210313082711-q5ohq7h"}
{: id="20210313082711-uba4e0a"}

```java
long d1 = Math.round(5.5); //d1的值为6.0
long d2 = Math.round(5.4); //d2的值为5.0
```
{: id="20210313082711-m5s01t4"}

* {: id="20210313082711-ti1f10d"}public static double pow(double a,double b)：返回a的b幂次方法
  {: id="20210313082711-c34sb4h"}
* {: id="20210313082711-ujkloh2"}public static double sqrt(double a)：返回a的平方根
  {: id="20210313082711-atbmq4r"}
* {: id="20210313082711-mbp2usk"}public static double random()：返回[0,1)的随机值
  {: id="20210313082711-0wq1i99"}
* {: id="20210313082711-dt9z44s"}public static final double PI：返回圆周率
  {: id="20210313082711-geyfk4r"}
* {: id="20210313082711-isexbqt"}public static double max(double x, double y)：返回x,y中的最大值
  {: id="20210313082711-fm2nm37"}
* {: id="20210313082711-ondfhm3"}public static double min(double x, double y)：返回x,y中的最小值
  {: id="20210313082711-82qh9nv"}
{: id="20210313082711-8rtq497"}

```java
double result = Math.pow(2,31);
double sqrt = Math.sqrt(256);
double rand = Math.random();
double pi = Math.PI;
```
{: id="20210313082711-3yt5jcq"}

##### 练习
{: id="20210313082711-7hrevy8"}

请使用`Math` 相关的API，计算在 `-10.8`  到`5.9`  之间，绝对值大于`6`  或者小于`2.1` 的整数有多少个？
{: id="20210313082711-1sodgin"}

```java
public class MathTest {
  public static void main(String[] args) {
    // 定义最小值
    double min = -10.8;
    // 定义最大值
    double max = 5.9;
    // 定义变量计数
    int count = 0;
    // 范围内循环
    for (double i = Math.ceil(min); i <= max; i++) {
      // 获取绝对值并判断
      if (Math.abs(i) > 6 || Math.abs(i) < 2.1) {
        // 计数
        count++;
      }
    }
    System.out.println("个数为: " + count + " 个");
  }
}
```
{: id="20210313082711-o8z6dzc"}

### 10.1.2 java.math包
{: id="20210313082711-01mtvv5"}

#### （1）BigInteger
{: id="20210313082711-tdvl2uq"}

不可变的任意精度的整数。
{: id="20210313082711-a27in8d"}

* {: id="20210313082711-1ves361"}BigInteger(String val)
  {: id="20210313082711-piy83tj"}
* {: id="20210313082711-a4ogslm"}BigInteger add(BigInteger val)
  {: id="20210313082711-o2joerq"}
* {: id="20210313082711-xqh6g66"}BigInteger subtract(BigInteger val)
  {: id="20210313082711-uktl6y3"}
* {: id="20210313082711-06ti1bx"}BigInteger multiply(BigInteger val)
  {: id="20210313082711-q7isjt7"}
* {: id="20210313082711-xzta4em"}BigInteger divide(BigInteger val)
  {: id="20210313082711-kgkzvfi"}
* {: id="20210313082711-isvfpds"}BigInteger remainder(BigInteger val)
  {: id="20210313082711-gp2nosl"}
* {: id="20210313082711-xz5w07y"}....
  {: id="20210313082711-5k0gxrw"}
{: id="20210313082711-qxp4pe6"}

```java
	@Test
	public void test01(){
//		long bigNum = 123456789123456789123456789L;
		
		BigInteger b1 = new BigInteger("123456789123456789123456789");
		BigInteger b2 = new BigInteger("78923456789123456789123456789");
		
//		System.out.println("和：" + (b1+b2));//错误的，无法直接使用+进行求和
		
		System.out.println("和：" + b1.add(b2));
		System.out.println("减：" + b1.subtract(b2));
		System.out.println("乘：" + b1.multiply(b2));
		System.out.println("除：" + b2.divide(b1));
		System.out.println("余：" + b2.remainder(b1));
	}
```
{: id="20210313082711-n3r38bt"}

#### （2）RoundingMode枚举类
{: id="20210313082711-l9nn5cq"}

CEILING ：向正无限大方向舍入的舍入模式。
DOWN ：向零方向舍入的舍入模式。
FLOOR：向负无限大方向舍入的舍入模式。
HALF_DOWN ：向最接近数字方向舍入的舍入模式，如果与两个相邻数字的距离相等，则向下舍入。
HALF_EVEN：向最接近数字方向舍入的舍入模式，如果与两个相邻数字的距离相等，则向相邻的偶数舍入。
HALF_UP：向最接近数字方向舍入的舍入模式，如果与两个相邻数字的距离相等，则向上舍入。
UNNECESSARY：用于断言请求的操作具有精确结果的舍入模式，因此不需要舍入。
UP：远离零方向舍入的舍入模式。
{: id="20210313082711-oorpb6p"}

#### （3）BigDecimal
{: id="20210313082711-w4tg94e"}

不可变的、任意精度的有符号十进制数。
{: id="20210313082711-p1gf4o0"}

* {: id="20210313082711-hse9gy1"}BigDecimal(String val)
  {: id="20210313082711-2t30ri9"}
* {: id="20210313082711-ycv1wfs"}BigDecimal add(BigDecimal val)
  {: id="20210313082711-as13y7q"}
* {: id="20210313082711-xp5xdko"}BigDecimal subtract(BigDecimal val)
  {: id="20210313082711-fv7bsh2"}
* {: id="20210313082711-2atrdou"}BigDecimal multiply(BigDecimal val)
  {: id="20210313082711-bcvjxvc"}
* {: id="20210313082711-dblrzw9"}BigDecimal divide(BigDecimal val)
  {: id="20210313082711-4rvohs2"}
* {: id="20210313082711-ouoau42"}BigDecimal divide(BigDecimal divisor, int roundingMode)
  {: id="20210313082711-mljt78u"}
* {: id="20210313082711-4j6wgjs"}BigDecimal divide(BigDecimal divisor, int scale, RoundingMode roundingMode)
  {: id="20210313082711-lyhdas9"}
* {: id="20210313082711-4zbsjn0"}BigDecimal remainder(BigDecimal val)
  {: id="20210313082711-6ktlg7b"}
* {: id="20210313082711-yq9xfn3"}....
  {: id="20210313082711-fuk22bk"}
{: id="20210313082711-p8rkwf0"}

```java
	@Test
	public void test02(){
		/*double big = 12.123456789123456789123456789;
		System.out.println("big = " + big);*/
		
		BigDecimal b1 = new BigDecimal("123.45678912345678912345678912345678");
		BigDecimal b2 = new BigDecimal("7.8923456789123456789123456789998898888");
		
//		System.out.println("和：" + (b1+b2));//错误的，无法直接使用+进行求和
		
		System.out.println("和：" + b1.add(b2));
		System.out.println("减：" + b1.subtract(b2));
		System.out.println("乘：" + b1.multiply(b2));
		System.out.println("除：" + b1.divide(b2,20,RoundingMode.UP));//divide(BigDecimal divisor, int scale, int roundingMode)
		System.out.println("除：" + b1.divide(b2,20,RoundingMode.DOWN));//divide(BigDecimal divisor, int scale, int roundingMode)
		System.out.println("余：" + b1.remainder(b2));
	}
```
{: id="20210313082711-4mwwk9u"}

### 10.1.3 java.util.Random
{: id="20210313082711-e0o5p4y"}

用于产生随机数
{: id="20210313082711-zyah1fc"}

* {: id="20210313082711-8omcdln"}boolean nextBoolean():返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的 boolean 值。
  {: id="20210313082711-4a20xsg"}
* {: id="20210313082711-7ttaq0t"}void nextBytes(byte[] bytes):生成随机字节并将其置于用户提供的 byte 数组中。
  {: id="20210313082711-lyg7m1n"}
* {: id="20210313082711-eqvzzag"}double nextDouble():返回下一个伪随机数，它是取自此随机数生成器序列的、在 0.0 和 1.0 之间均匀分布的 double 值。
  {: id="20210313082711-morvprg"}
* {: id="20210313082711-mqa6xum"}float nextFloat():返回下一个伪随机数，它是取自此随机数生成器序列的、在 0.0 和 1.0 之间均匀分布的 float 值。
  {: id="20210313082711-fv1i0ws"}
* {: id="20210313082711-xxk20pb"}double nextGaussian():返回下一个伪随机数，它是取自此随机数生成器序列的、呈高斯（“正态”）分布的 double 值，其平均值是 0.0，标准差是 1.0。
  {: id="20210313082711-3kxic4j"}
* {: id="20210313082711-fgcoznu"}int nextInt():返回下一个伪随机数，它是此随机数生成器的序列中均匀分布的 int 值。
  {: id="20210313082711-q5mf0k1"}
* {: id="20210313082711-t3lgyht"}int nextInt(int n):返回一个伪随机数，它是取自此随机数生成器序列的、在 0（包括）和指定值（不包括）之间均匀分布的 int 值。
  {: id="20210313082711-f36p7vk"}
* {: id="20210313082711-qq8tff6"}long nextLong():返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的 long 值。
  {: id="20210313082711-l5jq9ae"}
{: id="20210313082711-9lrmic5"}

```java
	@Test
	public void test03(){
		Random r = new Random();
		System.out.println("随机整数：" + r.nextInt());
		System.out.println("随机小数：" + r.nextDouble());
		System.out.println("随机布尔值：" + r.nextBoolean());
	}
```
{: id="20210313082711-stc93uw"}

## 10.2 日期时间API
{: id="20210313082711-apazug0"}

### 10.2.1 JDK1.8之前
{: id="20210313082711-ozlxn57"}

#### 1、java.util.Date
{: id="20210313082711-vg23na9"}

new  Date()：当前系统时间
{: id="20210313082711-fwibl1h"}

long  getTime()：返回该日期时间对象距离1970-1-1 0.0.0 0毫秒之间的毫秒值
{: id="20210313082711-hoz758n"}

new Date(long 毫秒)：把该毫秒值换算成日期时间对象
{: id="20210313082711-7j0wkcb"}

```java
	@Test
	public void test5(){
		long time = Long.MAX_VALUE;
		Date d = new Date(time);
		System.out.println(d);
	}
	
	@Test
	public void test4(){
		long time = 1559807047979L;
		Date d = new Date(time);
		System.out.println(d);
	}
	@Test
	public void test3(){
		Date d = new Date();
		long time = d.getTime();
		System.out.println(time);//1559807047979
	}
	
	@Test
	public void test2(){
		long time = System.currentTimeMillis();
		System.out.println(time);//1559806982971
		//当前系统时间距离1970-1-1 0:0:0 0毫秒的时间差，毫秒为单位
	}
	
	@Test
	public void test1(){
		Date d = new Date();
		System.out.println(d);
	}
```
{: id="20210313082711-5gwfzoj"}

#### 2、java.util.TimeZone
{: id="20210313082711-byicgs1"}

通常，使用 `getDefault` 获取 `TimeZone`，`getDefault`  基于程序运行所在的时区创建 `TimeZone`。
{: id="20210313082711-40fqkt7"}

也可以用 `getTimeZone` 及时区 ID 获取 `TimeZone` 。例如美国太平洋时区的时区 ID 是  "America/Los_Angeles"。
{: id="20210313082711-8wbb09o"}

```java
	@Test
	public void test8(){
		String[] all = TimeZone.getAvailableIDs();
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i]);
		}
	}
	
	@Test
	public void test7(){
		TimeZone t = TimeZone.getTimeZone("America/Los_Angeles");
	}
```
{: id="20210313082711-95pwxqj"}

常见时区ID：
{: id="20210313082711-vbhpwrk"}

```java
Asia/Shanghai
UTC
America/New_York
```
{: id="20210313082711-tjqpehq"}

#### 3、java.util.Calendar
{: id="20210313082711-2m43fji"}

`Calendar` 类是一个抽象类，它为特定瞬间与一组诸如  `YEAR`、`MONTH`、`DAY_OF_MONTH`、`HOUR`  等 [`日历字段`](../../java/util/Calendar.html#fields)之间的转换提供了一些方法，并为操作日历字段（例如获得下星期的日期）提供了一些方法。瞬间可用毫秒值来表示，它是距*历元*（即格林威治标准时间 1970 年 1 月 1 日的 00:00:00.000，格里高利历）的偏移量。与其他语言环境敏感类一样，`Calendar` 提供了一个类方法  `getInstance`，以获得此类型的一个通用的对象。
{: id="20210313082711-w6dyxdi"}

（1）getInstance()：得到Calendar的对象
{: id="20210313082711-kldnx6e"}

（2）get(常量)
{: id="20210313082711-s13o4hw"}

```java
	@Test
	public void test6(){
		Calendar c = Calendar.getInstance();
		System.out.println(c);
		
		int year = c.get(Calendar.YEAR);
		System.out.println(year);
		
		int month = c.get(Calendar.MONTH)+1;
		System.out.println(month);
		
		//...
	}

	@Test
	public void test7(){
		TimeZone t = TimeZone.getTimeZone("America/Los_Angeles");
		
		//getInstance(TimeZone zone)
		Calendar c = Calendar.getInstance(t);
		System.out.println(c);
	}
```
{: id="20210313082711-vma3vf6"}

#### 4、java.text.SimpleDateFormat
{: id="20210313082711-eecn6mx"}

SimpleDateFormat用于日期时间的格式化。
{: id="20210313082711-h6ckxdx"}

![1572599023197](imgs14/1572599023197.png)
{: id="20210313082711-rtxd88n"}

```java
	@Test
	public void test10() throws ParseException{
		String str = "2019年06月06日 16时03分14秒 545毫秒  星期四 +0800";
		SimpleDateFormat sf = new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒 SSS毫秒  E Z");
		Date d = sf.parse(str);
		System.out.println(d);
	}
	
	@Test
	public void test9(){
		Date d = new Date();

		SimpleDateFormat sf = new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒 SSS毫秒  E Z");
		//把Date日期转成字符串，按照指定的格式转
		String str = sf.format(d);
		System.out.println(str);
	}
```
{: id="20210313082711-8l01sbt"}

### 10.2.2 JDK1.8之后
{: id="20210313082711-rdhmgd0"}

Java1.0中包含了一个Date类，但是它的大多数方法已经在Java 1.1引入Calendar类之后被弃用了。而Calendar并不比Date好多少。它们面临的问题是：
{: id="20210313082711-2wug4pk"}

* {: id="20210313082711-pzil774"}可变性：象日期和时间这样的类对象应该是不可变的。Calendar类中可以使用三种方法更改日历字段：set()、add() 和 roll()。
  {: id="20210313082711-t3a0vuf"}
* {: id="20210313082711-cy3sz2t"}偏移性：Date中的年份是从1900开始的，而月份都是从0开始的。
  {: id="20210313082711-9povomk"}
* {: id="20210313082711-od5tdqb"}格式化：格式化只对Date有用，Calendar则不行。
  {: id="20210313082711-l4s7zb1"}
* {: id="20210313082711-irb8bl6"}此外，它们也不是线程安全的，不能处理闰秒等。
  {: id="20210313082711-a42bezm"}
{: id="20210313082711-ux0jjrb"}

可以说，对日期和时间的操作一直是Java程序员最痛苦的地方之一。第三次引入的API是成功的，并且java 8中引入的java.time API 已经纠正了过去的缺陷，将来很长一段时间内它都会为我们服务。
{: id="20210313082711-0eb47ag"}

Java 8 吸收了 Joda-Time 的精华，以一个新的开始为 Java 创建优秀的 API。
{: id="20210313082711-v6ctxza"}

* {: id="20210313082711-hh8xzu0"}java.time – 包含值对象的基础包
  {: id="20210313082711-1b7r4a7"}
* {: id="20210313082711-yg5xnwe"}java.time.chrono – 提供对不同的日历系统的访问。
  {: id="20210313082711-xwshaxu"}
* {: id="20210313082711-exrzcix"}java.time.format – 格式化和解析时间和日期
  {: id="20210313082711-kv29t1e"}
* {: id="20210313082711-10tqs2y"}java.time.temporal – 包括底层框架和扩展特性
  {: id="20210313082711-4sjcncw"}
* {: id="20210313082711-pwl9tw5"}java.time.zone – 包含时区支持的类
  {: id="20210313082711-x9eo2ui"}
{: id="20210313082711-dsyoaxg"}

Java 8 吸收了 Joda-Time 的精华，以一个新的开始为 Java 创建优秀的 API。新的 java.time 中包含了所有关于时钟（Clock），本地日期（LocalDate）、本地时间（LocalTime）、本地日期时间（LocalDateTime）、时区（ZonedDateTime）和持续时间（Duration）的类。
{: id="20210313082711-kleqnc7"}

#### 1、本地日期时间：LocalDate、LocalTime、LocalDateTime
{: id="20210313082711-mbu3bug"}

| 方法                                                               | **描述**                                                     |
| ------------------------------------------------------------------ | ------------------------------------------------------------ |
| now() / now(ZoneId zone)                                           | 静态方法，根据当前时间创建对象/指定时区的对象                |
| of()                                                               | 静态方法，根据指定日期/时间创建对象                          |
| getDayOfMonth()/getDayOfYear()                                     | 获得月份天数(1-31) /获得年份天数(1-366)                      |
| getDayOfWeek()                                                     | 获得星期几(返回一个 DayOfWeek 枚举值)                        |
| getMonth()                                                         | 获得月份, 返回一个 Month 枚举值                              |
| getMonthValue() / getYear()                                        | 获得月份(1-12) /获得年份                                     |
| getHours()/getMinute()/getSecond()                                 | 获得当前对象对应的小时、分钟、秒                             |
| withDayOfMonth()/withDayOfYear()/withMonth()/withYear()            | 将月份天数、年份天数、月份、年份修改为指定的值并返回新的对象 |
| with(TemporalAdjuster  t)                                          | 将当前日期时间设置为校对器指定的日期时间                     |
| plusDays(), plusWeeks(), plusMonths(), plusYears(),plusHours()     | 向当前对象添加几天、几周、几个月、几年、几小时               |
| minusMonths() / minusWeeks()/minusDays()/minusYears()/minusHours() | 从当前对象减去几月、几周、几天、几年、几小时                 |
| plus(TemporalAmount t)/minus(TemporalAmount t)                     | 添加或减少一个 Duration 或 Period                            |
| isBefore()/isAfter()                                               | 比较两个 LocalDate                                           |
| isLeapYear()                                                       | 判断是否是闰年（在LocalDate类中声明）                        |
| format(DateTimeFormatter  t)                                       | 格式化本地日期、时间，返回一个字符串                         |
| parse(Charsequence text)                                           | 将指定格式的字符串解析为日期、时间                           |
{: id="20210313082711-rhrusnm"}

```java
	@Test
	public void test7(){
		LocalDate now = LocalDate.now();
		LocalDate before = now.minusDays(100);
		System.out.println(before);//2019-02-26
	}
	
	@Test
	public void test06(){
		LocalDate lai = LocalDate.of(2019, 5, 13);
		LocalDate go = lai.plusDays(160);
		System.out.println(go);//2019-10-20
	}
	
	@Test
	public void test05(){
		LocalDate lai = LocalDate.of(2019, 5, 13);
		System.out.println(lai.getDayOfYear());
	}
	
	
	@Test
	public void test04(){
		LocalDate lai = LocalDate.of(2019, 5, 13);
		System.out.println(lai);
	}
	
	@Test
	public void test03(){
		LocalDateTime now = LocalDateTime.now();
		System.out.println(now);
	}
	
	@Test
	public void test02(){
		LocalTime now = LocalTime.now();
		System.out.println(now);
	}
	
	@Test
	public void test01(){
		LocalDate now = LocalDate.now();
		System.out.println(now);
	}
```
{: id="20210313082711-lqtwmsr"}

#### 2、指定时区日期时间：ZonedDateTime
{: id="20210313082711-z1cekgl"}

常见时区ID：
{: id="20210313082711-89alj0a"}

```java
Asia/Shanghai
UTC
America/New_York
```
{: id="20210313082711-ewy0r1c"}

```java
import java.time.ZoneId;
import java.time.ZonedDateTime;

public class TestZonedDateTime {
	public static void main(String[] args) {
		ZonedDateTime t = ZonedDateTime.now();
		System.out.println(t);
		
		ZonedDateTime t1 = ZonedDateTime.now(ZoneId.of("America/New_York"));
		System.out.println(t1);
	}
}
```
{: id="20210313082711-qvaehai"}

#### 3、持续日期/时间：Period和Duration
{: id="20210313082711-20xjdw2"}

Period:用于计算两个“日期”间隔
{: id="20210313082711-p1pkumg"}

```java
public static void main(String[] args) {
		LocalDate t1 = LocalDate.now();
		LocalDate t2 = LocalDate.of(2018, 12, 31);
		Period between = Period.between(t1, t2);
		System.out.println(between);
		
		System.out.println("相差的年数："+between.getYears());//1年
		System.out.println("相差的月数："+between.getMonths());//又7个月
		System.out.println("相差的天数："+between.getDays());//零25天
		System.out.println("相差的总数："+between.toTotalMonths());//总共19个月
	}
```
{: id="20210313082711-9djv3zz"}

Duration:用于计算两个“时间”间隔
{: id="20210313082711-1fwcc97"}

```java
	public static void main(String[] args) {
		LocalDateTime t1 = LocalDateTime.now();
		LocalDateTime t2 = LocalDateTime.of(2017, 8, 29, 0, 0, 0, 0);
		Duration between = Duration.between(t1, t2);
		System.out.println(between);
		
		System.out.println("相差的总天数："+between.toDays());
		System.out.println("相差的总小时数："+between.toHours());
		System.out.println("相差的总分钟数："+between.toMinutes());
		System.out.println("相差的总秒数："+between.getSeconds());
		System.out.println("相差的总毫秒数："+between.toMillis());
		System.out.println("相差的总纳秒数："+between.toNanos());
		System.out.println("不够一秒的纳秒数："+between.getNano());
	}
```
{: id="20210313082711-ahixd7b"}

#### 4、DateTimeFormatter：日期时间格式化
{: id="20210313082711-8za30on"}

该类提供了三种格式化方法：
{: id="20210313082711-9u69rxz"}

预定义的标准格式。如：ISO_DATE_TIME;ISO_DATE
{: id="20210313082711-q1d34da"}

本地化相关的格式。如：ofLocalizedDate(FormatStyle.MEDIUM)
{: id="20210313082711-51xfty9"}

自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
{: id="20210313082711-jxpb73s"}

```java
	@Test
	public void test10(){
		LocalDateTime now = LocalDateTime.now();
		
//		DateTimeFormatter df = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);//2019年6月6日 下午04时40分03秒
		DateTimeFormatter df = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.SHORT);//19-6-6 下午4:40
		String str = df.format(now);
		System.out.println(str);
	}
	@Test
	public void test9(){
		LocalDateTime now = LocalDateTime.now();
		
		DateTimeFormatter df = DateTimeFormatter.ISO_DATE_TIME;//2019-06-06T16:38:23.756
		String str = df.format(now);
		System.out.println(str);
	}
	
	@Test
	public void test8(){
		LocalDateTime now = LocalDateTime.now();
		
		DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy年MM月dd日 HH时mm分ss秒  SSS毫秒  E 是这一年的D天");
		String str = df.format(now);
		System.out.println(str);
	}
```
{: id="20210313082711-00d8h83"}

## 10.3 系统相关类
{: id="20210313082711-6cw9j21"}

### 10.3.1 java.lang.System类
{: id="20210313082711-nsr6ii7"}

系统类中很多好用的方法，其中几个如下：
{: id="20210313082711-ocz2k67"}

* {: id="20210313082711-h80dydj"}static long currentTimeMillis() ：返回当前系统时间距离1970-1-1 0:0:0的毫秒值
  {: id="20210313082711-mzwj85n"}
* {: id="20210313082711-35y3u0u"}static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)：
  {: id="20210313082711-ptzjcga"}
  从指定源数组中复制一个数组，复制从指定的位置开始，到目标数组的指定位置结束。常用于数组的插入和删除
  {: id="20210313082711-1itqokc"}
* {: id="20210313082711-5gntg50"}static void exit(int status) ：退出当前系统
  {: id="20210313082711-1ivepmq"}
* {: id="20210313082711-mp724ac"}static void gc() ：运行垃圾回收器。
  {: id="20210313082711-qud6l2f"}
* {: id="20210313082711-c6qhkr7"}static String getProperty(String key)：获取某个系统属性
  {: id="20210313082711-jfljn3i"}
* {: id="20210313082711-z2fbszo"}...
  {: id="20210313082711-ddhkvhn"}
{: id="20210313082711-8mveskm"}

```java
public class Test{
    public static void main(String[] args){
    	long time = System.currentTimeMillis();
    	System.out.println("现在的系统时间距离1970年1月1日凌晨：" + time + "毫秒");
    	
    	System.exit(0);

    	System.out.println("over");//不会执行
    }
}
```
{: id="20210313082711-n5lz7ho"}

```

```
{: id="20210313082711-13fqqle"}

### 10.3.3 java.lang.Runtime类
{: id="20210313082711-xkjrqsl"}

每个 Java 应用程序都有一个 `Runtime` 类实例，使应用程序能够与其运行的环境相连接。可以通过  `getRuntime` 方法获取当前运行时。  应用程序不能创建自己的 Runtime 类实例。
{: id="20210313082711-3cc3up4"}

public static Runtime getRuntime()： 返回与当前 Java 应用程序相关的运行时对象。
{: id="20210313082711-of8a4mi"}

public long totalMemory()：返回 Java 虚拟机中的内存总量。此方法返回的值可能随时间的推移而变化，这取决于主机环境。
{: id="20210313082711-h7yfsiv"}

public long freeMemory()：回 Java 虚拟机中的空闲内存量。调用 gc 方法可能导致 freeMemory 返回值的增加。
{: id="20210313082711-anaa3v6"}

```

```
{: id="20210313082711-6u9s8g3"}

## 10.4 数组的算法升华
{: id="20210313082711-r5uzr0m"}

### 10.4.1 数组的算法升华
{: id="20210313082711-ksmb5ry"}

#### 1、数组的反转
{: id="20210313082711-332mm5g"}

方法有两种：
{: id="20210313082711-j8vseyb"}

1、借助一个新数组
{: id="20210313082711-r454fkl"}

2、首尾对应位置交换
{: id="20210313082711-wmsv71n"}

第一种方式示例代码：
{: id="20210313082711-fy182a1"}

![1572828418996](imgs14/1572828418996.png)
{: id="20210313082711-2k1bgyn"}

```java
int[] arr = {1,2,3,4,5,6,7,8,9};

//(1)先创建一个新数组
int[] newArr = new int[arr.length];

//(2)复制元素
int len = arr.length;
for(int i=0; i<newArr.length; i++){
    newArr[i] = arr[len -1 - i];
}

//(3)舍弃旧的，让arr指向新数组
arr = newArr;//这里把新数组的首地址赋值给了arr

//(4)遍历显示
for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}

```
{: id="20210313082711-jghp8vs"}

> 缺点：需要借助一个数组，浪费额外空间，原数组需要垃圾回收
> {: id="20210313082711-fh41z5z"}
{: id="20210313082711-zvvln7y"}

第二种方式示例代码：
{: id="20210313082711-scswq0v"}

**实现思想：**数组对称位置的元素互换。
{: id="20210313082711-1lxj34w"}

![1561469467316](imgs14/1561469467316.png)
{: id="20210313082711-m5b9q9x"}

```java
int[] arr = {1,2,3,4,5,6,7,8,9};

//(1)计算要交换的次数：  次数 = arr.length/2
//(2)首尾对称位置交换
for(int i=0; i<arr.length/2; i++){//循环的次数就是交换的次数
    int temp = arr[i];
    arr[i] = arr[arr.length-1-i];
	arr[arr.length-1-i] = temp;
}

//（3）遍历显示
for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}
```
{: id="20210313082711-1943ft9"}

或
{: id="20210313082711-xwi1flu"}

![1561469087319](imgs14/1561469087319.png)
{: id="20210313082711-vy8iir0"}

```java
	public static void main(String[] args){
		int[] arr = {1,2,3,4,5,6,7,8,9};

		//左右对称位置交换
		for(int left=0,right=arr.length-1; left<right; left++,right--){
		    //首  与  尾交换
		    int temp = arr[left];
		    arr[left] = arr[right];
			arr[right] = temp;
		}

		//（3）遍历显示
		for(int i=0; i<arr.length; i++){
		    System.out.println(arr[i]);
		}
	}
```
{: id="20210313082711-c3oybaf"}

#### 2、数组的扩容
{: id="20210313082711-lju6h4w"}

示例：当原来的数组长度不够了需要扩容，例如需要新增位置来存储10
{: id="20210313082711-o2j6p3a"}

```java
int[] arr = {1,2,3,4,5,6,7,8,9};

//如果要把arr数组扩容，增加1个位置
//(1)先创建一个新数组，它的长度 = 旧数组的长度+1，或者也可以扩大为原来数组长度的1.5倍，2倍等
int[] newArr = new int[arr.length + 1];

//(2)复制元素
//注意：i<arr.length   因位arr比newArr短，避免下标越界
for(int i=0; i<arr.length; i++){
    newArr[i] = arr[i];
}

//(3)把新元素添加到newArr的最后
newArr[newArr.length-1] = 10;

//(4)如果下面继续使用arr，可以让arr指向新数组
arr = newArr;

//(4)遍历显示
for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}
```
{: id="20210313082711-s8n8h1o"}

> （1）至于新数组的长度定义多少合适，看实际情况，如果新增的元素个数确定，那么可以增加指定长度，如果新增元素个数不确定，那么可以扩容为原来的1.5倍、2倍等
> {: id="20210313082711-3z2z9r9"}
>
> （2）数组扩容太多会造成浪费，太少会导致频繁扩容，效率低下
> {: id="20210313082711-vhibi3c"}
{: id="20210313082711-4txmchj"}

#### 3、数组元素的插入
{: id="20210313082711-jugr5xg"}

示例：在原数组的某个[index]插入一个元素
{: id="20210313082711-z2k8k2n"}

情形一：原数组未满
{: id="20210313082711-kmwuxao"}

```java
String[] arr = new String[5];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

那么目前数组的长度是5，而数组的实际元素个数是3，如果此时需要在“张三”和“李四”之间插入一个“赵六”，即在[index=1]的位置插入“赵六”，需要怎么做呢？
```
{: id="20210313082711-kvjqa5h"}

```java
String[] arr = new String[5];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

//（1）移动2个元素，需要移动的起始元素下标是[1]，它需要移动到[2]，一共一共2个
System.arraycopy(arr,1,arr,2,2);
//（2）插入新元素
arr[1]="赵六";

//(3)遍历显示
for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}
```
{: id="20210313082711-k87u8or"}

情形二：原数组已满
{: id="20210313082711-j86pznn"}

```java
String[] arr = new String[3];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

那么目前数组的长度是3，而数组的实际元素个数是3，如果此时需要在“张三”和“李四”之间插入一个“赵六”，即在[index=1]的位置插入“赵六”，需要怎么做呢？
```
{: id="20210313082711-frtdioz"}

```java
String[] arr = new String[3];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

//（1）先扩容
String[] newArr = new String[4];
for(int i=0; i<arr.length; i++){
	newArr[i] = arr[i];
}
arr=newArr;

//（2）移动2个元素，需要移动的起始元素下标是[1]，它需要移动到[2]，一共一共2个
System.arraycopy(arr,1,arr,2,2);
//（3）插入新元素
arr[1]="赵六";

//(4)遍历显示
for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}
```
{: id="20210313082711-pfpibf7"}

#### 4、数组元素的删除
{: id="20210313082711-o6d43k5"}

示例：
{: id="20210313082711-nc28ppp"}

```java
String[] arr = new String[3];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

现在需要删除“李四”，我们又不希望数组中间空着元素，该如何处理呢？
```
{: id="20210313082711-qpjn1h6"}

```java
String[] arr = new String[3];
arr[0]="张三";
arr[1]="李四";
arr[2]="王五";

//（1）移动元素，需要移动元素的起始下标[2]，该元素需要移动到[1]，一共需要移动1个元素
System.arraycopy(arr,2,arr,1,1);

//（2）因为数组元素整体往左移动，这里本质上是复制，原来最后一个元素需要置空
arr[2]=null;//使得垃圾回收尽快回收对应对象的内存
```
{: id="20210313082711-92i5fnl"}

#### 5、数组的二分查找
{: id="20210313082711-7xoct14"}

二分查找：对折对折再对折
{: id="20210313082711-bubapum"}

要求：要求数组元素必须支持比较大小，并且数组中的元素已经按大小排好序
{: id="20210313082711-0wnljsx"}

示例：
{: id="20210313082711-aij1ygh"}

```java
class Exam2{
	public static void main(String[] args){
		int[] arr = {2,5,7,8,10,15,18,20,22,25,28};//数组是有序的
		int value = 18;
		
        int index = -1;
		int left = 0;
        int right = arr.length - 1;
        int mid = (left + right)/2;
        while(left<=right){
            //找到结束
            if(value == arr[mid]){
                index = mid;
                break;
            }//没找到
            else if(value > arr[mid]){//往右继续查找
                //移动左边界，使得mid往右移动
                left = mid + 1;
            }else if(value < arr[mid]){//往左边继续查找
                right = mid - 1;
            }
            
            mid = (left + right)/2;
        }
        
        if(index==-1){
    		System.out.println(value + "不存在");
		}else{
    		System.out.println(value + "的下标是" + index);
		}
        
	}
}
```
{: id="20210313082711-da7hhhj"}

![](imgs14/1、二分查找图解(1).png)
{: id="20210313082711-leg3sqt"}

![](imgs14/2、二分查找图解(2).png)
{: id="20210313082711-l7zyehu"}

#### 6、数组的直接选择排序
{: id="20210313082711-wzmslr3"}

示例代码：简单的直接选择排序
{: id="20210313082711-u4nw5oq"}

```java
int[] arr = {49,38,65,97,76,13,27,49};

for(int i=1; i<arr.length; i++){//外循环的次数 = 轮数 = 数组的长度-1
    //（1）找出本轮未排序元素中的最值
    /*
    未排序元素：
    第1轮：i=1,未排序，[0,7]，本轮未排序元素第一个元素是[0]
    第2轮：i=2,未排序，[1,7]，本轮未排序元素第一个元素是[1]
    ...
    第7轮：i=7,未排序，[6,7]，本轮未排序元素第一个元素是[6]
    
    每一轮未排序元素的起始下标：0,1,2,3,4,5,6，正好是i-1的
    未排序的后面的元素依次：
    第1轮：[1,7]  j=1,2,3,4,5,6,7
    第2轮：[2,4]  j=2,3,4,5,6,7
    。。。。
    第7轮：[7]    j=7
    j的起点是i，终点都是7
    */
    int max = arr[i-1];
    int index = i-1;
    for(int j=i; j<arr.length; j++){
        if(arr[j] > max){
            max = arr[j];
            index = j;
        }
    }
    
    //（2）如果这个最值没有在它应该在的位置，就与这个位置的元素交换
    /*
    第1轮，最大值应该在[0]
    第2轮，最大值应该在[1]
    ....
    第7轮，最大值应该在[6]
    正好是i-1的值
    */
    if(index != i-1){
        //交换arr[i-1]与arr[index]
        int temp = arr[i-1];
        arr[i-1] = arr[index];
        arr[index] = temp;
    }
}

//显示结果
for(int i=0; i<arr.length; i++){
	System.out.print(arr[i]);
}
```
{: id="20210313082711-y61v3km"}

![1561513135868](imgs14/1561513135868.png)
{: id="20210313082711-aj02l86"}

### 10.4.2 数组工具类
{: id="20210313082711-8jvrbzr"}

java.util.Arrays数组工具类，提供了很多静态方法来对数组进行操作，而且如下每一个方法都有各种重载形式，以下只列出int[]类型的，其他类型的数组类推：
{: id="20210313082711-3a3mvhp"}

* {: id="20210313082711-b5pmiq9"}static int binarySearch(int[] a, int key) ：要求数组有序，在数组中查找key是否存在，如果存在返回第一次找到的下标，不存在返回负数
  {: id="20210313082711-cmugcyj"}
* {: id="20210313082711-wun8cko"}static int[] copyOf(int[] original, int newLength)  ：根据original原数组复制一个长度为newLength的新数组，并返回新数组
  {: id="20210313082711-z5vcgft"}
* {: id="20210313082711-oiudjsy"}static int[] copyOfRange(int[] original, int from, int to) ：复制original原数组的[from,to)构成新数组，并返回新数组
  {: id="20210313082711-ms47nyp"}
* {: id="20210313082711-k37qi8o"}static boolean equals(int[] a, int[] a2) ：比较两个数组的长度、元素是否完全相同
  {: id="20210313082711-4dfp68o"}
* {: id="20210313082711-c7mp5zi"}static void fill(int[] a, int val) ：用val填充整个a数组
  {: id="20210313082711-x78svpw"}
* {: id="20210313082711-l40gbl7"}static void fill(int[] a, int fromIndex, int toIndex, int val)：将a数组[fromIndex,toIndex)部分填充为val
  {: id="20210313082711-0p5p1ol"}
* {: id="20210313082711-feqsw40"}static void sort(int[] a) ：将a数组按照从小到大进行排序
  {: id="20210313082711-s8bf02l"}
* {: id="20210313082711-2x4ak8g"}static void sort(int[] a, int fromIndex, int toIndex) ：将a数组的[fromIndex, toIndex)部分按照升序排列
  {: id="20210313082711-ptxtq0n"}
* {: id="20210313082711-xiecj0x"}static String toString(int[] a) ：把a数组的元素，拼接为一个字符串，形式为：[元素1，元素2，元素3。。。]
  {: id="20210313082711-3t4jvid"}
{: id="20210313082711-zeijci1"}

示例代码：
{: id="20210313082711-iagymsa"}

```java
import java.util.Arrays;
import java.util.Random;

public class Test{
    public static void main(String[] args){
    	int[] arr = new int[5];
        // 打印数组,输出地址值
  		System.out.println(arr); // [I@2ac1fdc4
  		// 数组内容转为字符串
    	System.out.println("arr数组初始状态："+ Arrays.toString(arr));
    	
    	Arrays.fill(arr, 3);
    	System.out.println("arr数组现在状态："+ Arrays.toString(arr));
    	
    	Random rand = new Random();
    	for (int i = 0; i < arr.length; i++) {
			arr[i] = rand.nextInt(100);//赋值为100以内的随机整数
		}
    	System.out.println("arr数组现在状态："+ Arrays.toString(arr));
    	
    	int[] arr2 = Arrays.copyOf(arr, 10);
    	System.out.println("新数组：" + Arrays.toString(arr2));
    	
    	System.out.println("两个数组的比较结果：" + Arrays.equals(arr, arr2));
    	
    	Arrays.sort(arr);
    	System.out.println("arr数组现在状态："+ Arrays.toString(arr));
    }
}
```
{: id="20210313082711-7c0lair"}

### 10.4.3 数组面试题
{: id="20210313082711-s36wrpz"}

#### 1、编程题1
{: id="20210313082711-cbo5vjc"}

找出数组中一个值，使其左侧值的加和等于右侧值的加和，
{: id="20210313082711-fuevbt7"}

​	例如：[1,2,5,3,2,4,2]，结果为：第4个值3
{: id="20210313082711-3cfc1eu"}

​			    [9, 6, 8, 8, 7, 6, 9, 5, 2, 5]，结果是没有
{: id="20210313082711-7swywks"}

```java
	public static void main(String[] args) {
		int[] arr = {1,2,5,3,2,4,2};
			
		int index = leftSumEqualsRightSum(arr);
		if(index!=-1) {
			System.out.println(arr[index]);
		}else {
			System.out.println("没有");
		}
	}
	
	public static int leftSumEqualsRightSum(int[] arr) {
		for (int mid = 0; mid < arr.length; mid++) {
			int leftSum = 0;
			int rightSum = 0;
			for (int i = 0; i <mid; i++) {
				leftSum += arr[i];
			}
			for (int i = mid+1; i < arr.length; i++) {
				rightSum += arr[i];
			}
			if(leftSum==rightSum) {
				return mid;
			}
		}
		return -1;
	}
```
{: id="20210313082711-zdgz8b8"}

#### 2、编程题2
{: id="20210313082711-onft1l9"}

- {: id="20210313082711-25hv9k5"}左奇右偶
  {: id="20210313082711-c42lwj2"}

  - {: id="20210313082711-moz43qf"}10个整数的数组{26,67,49,38,52,66,7,71,56,87}。
    {: id="20210313082711-aqcewcv"}
  - {: id="20210313082711-xztj85n"}元素重新排列，所有的奇数保存到数组左边，所有的偶数保存到数组右边。
    {: id="20210313082711-qlg4jlo"}
  {: id="20210313082711-vofe9t0"}
- {: id="20210313082711-7md6562"}代码实现，效果如图所示：
  {: id="20210313082711-fy1tioe"}
  ![](imgs14/9.jpg)
  {: id="20210313082711-8ixgyeu"}
- {: id="20210313082711-10xe7wz"}开发提示：
  {: id="20210313082711-8h45qio"}
  - {: id="20210313082711-mf4s1ud"}左边的偶数与右边的奇数换位置：
    {: id="20210313082711-c6he8bh"}
  - {: id="20210313082711-rhxg33r"}定义两个变量left和right，从左边开始查找偶数的位置，找到后用left记录，从右边开始找奇数的位置，找到后用right记录，如果left<right，那么就交换，然后在上一次的基础上继续查找，直到left与right擦肩。
    {: id="20210313082711-xtl8sus"}
  {: id="20210313082711-urn3u4r"}
{: id="20210313082711-mnwxrg5"}

```java
    //效率最高
    public void order2(int[] arr){
        for (int left = 0,right = arr.length-1; left < right; ){
            //left代表左边需要交换的数的下标，偶数的下标
            //如果arr[left]此时是奇数，说明此时left不是我们要找的下标，left++往后移动
            while(arr[left]%2!=0){//当arr[left]是偶数时，结束while循环
                left++;
            }
            //如果arr[right]此时是偶数，说明此时right不是我们要找的下标，right--往前移动
            while(arr[right]%2==0){//当arr[right]是奇数时，结束while循环
                right--;
            }
            if(left < right){
                int temp = arr[left];
                arr[left] = arr[right];
                arr[right]= temp;
            }
        }
    }
```
{: id="20210313082711-50k5wpc"}

```java
public void order3(int[] arr){
        int len = arr.length;
        while (len>0) {
            for (int j=0; j<len-1; j++){
                //左边的元素是偶数，就和它相邻的元素交换
                if (arr[j]%2==0) {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
            len--;
        }
    }
```
{: id="20210313082711-6acecd4"}

```java
public void order(int[] arr){
        //从左边往右边找偶数，记录下标，evenIndex，这个是错误的数字的下标
        //从右边往左边找奇数，记录下标，oddIndex，这个是错误的数字的下标
        //交换arr[oddIndex]与arr[evenIndex]，调整之后就可以了
        int evenIndex = 0;
        int oddIndex = arr.length-1;
        while(evenIndex < oddIndex){
            for (int i=0; i<arr.length; i++){
                if(arr[i]%2==0){
                    evenIndex = i;
                    break;
                }
            }

            for(int i=arr.length-1; i>=0; i--){
                if(arr[i]%2!=0){
                    oddIndex = i;
                    break;
                }
            }

            if(evenIndex < oddIndex) {
                int temp = arr[evenIndex];
                arr[evenIndex] = arr[oddIndex];
                arr[oddIndex] = temp;
            }
        }
    }
```
{: id="20210313082711-b5vw6aw"}

#### 3、编程题3
{: id="20210313082711-zs77w69"}

* {: id="20210313082711-8xtbr2g"}数组去重
  {: id="20210313082711-3rz3okg"}

  * {: id="20210313082711-pt4xyg9"}10个整数{9,10,6,6,1,9,3,5,6,4}，范围1-10，保存到数组中。
    {: id="20210313082711-8iuy5gm"}
  * {: id="20210313082711-foovk5e"}去除数组中重复的内容，只保留唯一的元素。
    {: id="20210313082711-of0d88o"}
  {: id="20210313082711-r0aoh5r"}
* {: id="20210313082711-vfk5cn2"}按步骤编写代码，效果如图所示：
  {: id="20210313082711-rfd11ra"}
  ![](imgs14/10.jpg)
  {: id="20210313082711-ly7rzoh"}
* {: id="20210313082711-0aekadr"}开发提示：
  {: id="20210313082711-1o01xcn"}
  - {: id="20210313082711-kruopva"}定义一个变量count，初始化为数组的长度
    {: id="20210313082711-2zch0dd"}
  - {: id="20210313082711-vpis206"}遍历每一个元素，如果该元素与前面的某个元素相等，那么通过移动数组，把该元素覆盖掉，并修改count--。
    {: id="20210313082711-4l08mh7"}
  - {: id="20210313082711-h41fusb"}最后创建一个新数组，长度为count，并从原数组把前count个元素复制过来
    {: id="20210313082711-8qbdexs"}
  {: id="20210313082711-hmqhfli"}
{: id="20210313082711-85xodb4"}

#### 4、编程题4
{: id="20210313082711-zna1i87"}

![1573715386032](imgs14/1573715386032.png)
{: id="20210313082711-r5bqelb"}

```java
import java.util.Arrays;

public class TestExer4 {
	public static void main(String[] args) {
		
		double[] arr = new double[10];
		for (int i = 0; i < arr.length-1; i++) {
			arr[i] = Math.random() * 100;//[0,100)之间的小数
		}
		arr[arr.length-1] = 0;
		System.out.println("直线上每一个点距离下一个点的距离："+Arrays.toString(arr));
		
		double length = 150.5;
		
		int count = 0;
		double sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum += arr[i];
			if(sum<=length) {
				count++;
			}else {
				break;
			}
		}
		System.out.println("长度为：" + length + "的绳子最多能覆盖" +count+"个点");
	}
}
```
{: id="20210313082711-y09el0w"}

#### 5、编程题5
{: id="20210313082711-1wc5o0m"}

![1573715429966](imgs14/1573715429966.png)
{: id="20210313082711-um9wcbm"}

冒泡排序：
{: id="20210313082711-u22vewy"}

```java
public static void bubbleSort(int[] arr) {
		for (int i = 1; i < arr.length; i++) {
			for (int j = 0; j < arr.length-i; j++) {
				if(arr[j] > arr[j+1]) {
					int temp = arr[j];
					arr[j] = arr[j+1];
					arr[j+1] = temp;
				}
			}
		}
	}
```
{: id="20210313082711-6ltpv6f"}

直接选择排序：
{: id="20210313082711-42j6vvc"}

```java
public static void selectSort(int[] arr) {
		for (int i = 0; i < arr.length-1; i++) {
			int minIndex = i;
			for (int j = i+1; j < arr.length; j++) {
				if(arr[minIndex] > arr[j]) {
					minIndex = j;
				}
			}
			if(minIndex!=i) {
				int temp = arr[minIndex];
				arr[minIndex] = arr[i];
				arr[i] = temp;
			}
		}
	}
```
{: id="20210313082711-1k49rgo"}

### 10.4.4 附加
{: id="20210313082711-1wxyich"}

#### 1、折半插入排序
{: id="20210313082711-kanauqg"}

例如：数组{12,2,6,1,5}
{: id="20210313082711-djv21k7"}

第一次：在[0,1)之间找插入2的位置==>left = [0] ==> {2,12,6,1,5}
{: id="20210313082711-fm3pma5"}

第二次：在[0,2)之间找插入6的位置==>left = [1] ==> {2,6,12,1,5}
{: id="20210313082711-0gk96c8"}

第三次：在[0,3)之间找插入1的位置==>left = [0] ==>{1,2,6,12,5}
{: id="20210313082711-odevov8"}

第四次：在[0,4)之间找插入5的位置==>left = [2] ==>{1,2,5,6,12}
{: id="20210313082711-yskoemw"}

```java
    @Test
    public void test(){
        int[] arr = {12,2,6,1,5};
        sort(arr);
        System.out.println(Arrays.toString(arr));
    }

    public void sort(int[] arr){
        for (int i=1; i<arr.length; i++){
            //找到[0,i)之间插入arr[i]的位置
            //使用二分查找法
            int left = 0;
            int right=i-1;
            while (left<=right){
                int mid = (left + right)/2;
                if(arr[i]<=arr[mid]){
                    right = mid - 1;
                }else{
                    left = mid + 1;
                }
            }
 
            //在[0,i)插入arr[i]
            if(left < i){
                int temp = arr[i];
                System.arraycopy(arr,left,arr,left+1,i-left);
                arr[left] = temp;
            }
        }
    }
```
{: id="20210313082711-djs7pax"}

![](imgs14/折半插入排序过程分析.png)
{: id="20210313082711-qdcmvzr"}

#### 2、快速排序
{: id="20210313082711-b20hcow"}

例如：数组{5, 2, 6, 12, 1,7,9}
{: id="20210313082711-iekge93"}

```java
    @Test
    public void test(){
        int[] arr = {5, 2, 6, 12, 1,7,9};
        sort(arr,0, arr.length-1);
        System.out.println(Arrays.toString(arr));
    }

    //将[start+1,end]之间的元素分为两拨，左边的所有元素比arr[start]小，右边的所有元素比arr[start]大
    public void sort(int[] arr,int start, int end){
        if(start < end){
            int left = start+1;
            int right = end;
            while(left<right){
                //从左往右，从[start+1]开始找比arr[start]大的数arr[left]，让它与arr[right]交换
                //当arr[left]大于arr[start]就停止循环，因为此时找到了比arr[start]大的数arr[left]
                while(arr[left]<=arr[start] && left<end){
                    left++;
                }
                
                //从右往左，从[end]开始找比比arr[start]小的数arr[right]，让它与arr[left]交换
               //当arr[right]小于arr[start]就停止循环，因为此时找到了比arr[start]小的数arr[right]
                while(arr[right]>=arr[start] && right>start){
                    right--;
                }
                
                
                if(left < right){
                    int temp = arr[left];
                    arr[left] = arr[right];
                    arr[right] = temp;
                }
            }
            
            //经过上面的while，//如果right>start+1，那么说明在[start+1,end]之间的数分为两拨
            //[start+1,right]之间的是比arr[start]小的数
            //[right,end]之间的是比arr[start]大的数
            //交换arr[start]与arr[right]
            if(right > start + 1){
                int temp = arr[start];
                arr[start] = arr[right];
                arr[right] = temp;
            }
            //此时[start,right-1]之间都是比arr[start]小的数据了，但是它们还未排序
            //此时[right+1,end]之间都是比arr[start]大的数据了，但是它们还未排序
            //所以需要分别对[start,right-1]、[right+1,end]之间元素重复上面的操作继续排序
            sort(arr,start,right-1);
            sort(arr,right+1,end);
        }

    }
```
{: id="20210313082711-scmirt5"}

第1次调用sort(arr,0,6)
交换arr[left=2]与arr[right=4]：[5, 2, 1, 12, 6, 7, 9]
交换基准位置的元素与分界位置的元素：arr[start=0]与arr[right=2]：[1, 2, 5, 12, 6, 7, 9]
第2次调用sort(arr,0,1)
第3次调用sort(arr,0,0)
第4次调用sort(arr,2,1)
第5次调用sort(arr,3,6)
交换基准位置的元素与分界位置的元素：arr[start=3]与arr[right=6]：[1, 2, 5, 9, 6, 7, 12]
第6次调用sort(arr,3,5)
交换基准位置的元素与分界位置的元素：arr[start=3]与arr[right=5]：[1, 2, 5, 7, 6, 9, 12]
第7次调用sort(arr,3,4)
第8次调用sort(arr,3,3)
第9次调用sort(arr,5,4)
第10次调用sort(arr,6,5)
第11次调用sort(arr,7,6)
{: id="20210313082711-p1n8lhz"}

![](imgs14/快速排序过程分析.png)
{: id="20210313082711-hdu3iae"}


{: id="20210313082711-84tt40y" type="doc"}
