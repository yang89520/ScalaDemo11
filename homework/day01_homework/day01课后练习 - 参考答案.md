# day01课后练习
{: id="20210309203838-ekqtlv3"}

# 基础题目:
{: id="20210309203838-yepwkrd"}

## 第一题
{: id="20210309203838-zhy36p2"}

* {: id="20210309203838-lu760sp"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-v98hto1"}
{: id="20210309203838-ciz9nay"}

![](img\1.jpg)
{: id="20210309203838-9gf73zr"}

* {: id="20210309203838-tm78re5"}编写步骤：
  {: id="20210309203838-q0j053n"}
{: id="20210309203838-68kx9b9"}

1. {: id="20210309203838-l3ub0fx"}定义类 Test1
   {: id="20210309203838-op955kp"}
2. {: id="20210309203838-1bbactx"}定义 main方法
   {: id="20210309203838-qpo8i7u"}
3. {: id="20210309203838-sezmdmg"}控制台输出5行字符串类型常量值
   {: id="20210309203838-23f25ki"}
4. {: id="20210309203838-q5bcvub"}控制台输出5行字符类型常量值
   {: id="20210309203838-y7il9u2"}
{: id="20210309203838-2xp7ynw"}

```java
class Test1{
    public static void main(String[] args){
        System.out.println("善学如春起之苗");
        System.out.println("不见其增，日有所长");
        System.out.println("假学如磨刀之石");
        System.out.println("不见其损，年有所亏");
        System.out.println("加油吧！少年");
        
        System.out.println("J");
        System.out.println("A");
        System.out.println("V");
        System.out.println("A");
        System.out.println("!");
    }
}
```
{: id="20210309203838-76sbgqj"}

## 第二题
{: id="20210309203838-2k7j3ek"}

* {: id="20210309203838-7m90lv5"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-3kum1b0"}

  ![](img\2.jpg)
  {: id="20210309203838-dbkp2ae"}
* {: id="20210309203838-7ffrqvj"}编写步骤：
  {: id="20210309203838-6xpy55y"}
  1. {: id="20210309203838-3e2nllg"}定义类 Test2
     {: id="20210309203838-jgzmo1m"}
  2. {: id="20210309203838-dfo0g7h"}定义 main方法
     {: id="20210309203838-f43yqzl"}
  3. {: id="20210309203838-0oq3q2t"}控制台输出5行整数类型常量值
     {: id="20210309203838-tejck42"}
  4. {: id="20210309203838-xcakz6r"}控制台输出5行小数类型常量值
     {: id="20210309203838-ui7z69a"}
  {: id="20210309203838-q24x4vd"}
{: id="20210309203838-mbfz15c"}

```java
public class Test2 {

	public static void main(String[] args) {
		System.out.println(-2147483648);
		System.out.println(-100);
		System.out.println(0);
		System.out.println(100);
		System.out.println(2147483647);
		System.out.println(-100.0);
		System.out.println(-10.0);
		System.out.println(0.0);
		System.out.println(10.9);
		System.out.println(100.9);
	}

}
```
{: id="20210309203838-7stql00"}

## 第三题
{: id="20210309203838-802lvby"}

- {: id="20210309203838-k5eg8hs"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-67cacsd"}

  ![](img\3.jpg)
  {: id="20210309203838-ulzec2x"}
- {: id="20210309203838-5aaorek"}编写步骤：
  {: id="20210309203838-bsko3jn"}
  1. {: id="20210309203838-cvaaz7z"}定义类 Test3
     {: id="20210309203838-nz4jt8i"}
  2. {: id="20210309203838-8iux8ec"}定义 main方法
     {: id="20210309203838-y8p4gsw"}
  3. {: id="20210309203838-khrovs3"}控制台输出所有布尔类型常量值
     {: id="20210309203838-tt4evx7"}
  {: id="20210309203838-3gv5ine"}
{: id="20210309203838-xc1rzjm"}

```java
public class Test3 {
	public static void main(String[] args) {
		System.out.println(true);
		System.out.println(false);
	}
}
```
{: id="20210309203838-v6pr4w4"}

## 第四题
{: id="20210309203838-ssqssqm"}

- {: id="20210309203838-pnw4opy"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-t3ewfb7"}

  ![](img\4.jpg)
  {: id="20210309203838-0z3n2jv"}
- {: id="20210309203838-znoclks"}编写步骤：
  {: id="20210309203838-1x90r3i"}
  1. {: id="20210309203838-ymkdxu5"}定义类 Test4
     {: id="20210309203838-qy9un3p"}
  2. {: id="20210309203838-q0qxhnu"}定义 main方法
     {: id="20210309203838-hvqk6dy"}
  3. {: id="20210309203838-fz7vlmw"}定义2个 byte类型变量,分别赋byte类型范围内最大值和最小值,并输出在控制台.
     {: id="20210309203838-w3j7lkm"}
  4. {: id="20210309203838-q21lnmj"}定义2个 short类型变量,分别赋short类型范围内的值,并输出在控制台.
     {: id="20210309203838-2nq26e3"}
  5. {: id="20210309203838-w2qmly1"}定义2个 int类型变量,分别赋int类型范围内的值,并输出在控制台.
     {: id="20210309203838-6rtbovh"}
  6. {: id="20210309203838-s76znfm"}定义2个 long类型变量,分别赋超过int类型范围的值,并输出在控制台.
     {: id="20210309203838-4p84cqp"}
  {: id="20210309203838-qkasdgh"}
{: id="20210309203838-nx80r4p"}

```java
public class Test4 {

	public static void main(String[] args) {
		byte minByte = -128;
		byte maxByte = 127;
		System.out.println(minByte);
		System.out.println(maxByte);
		
		short minShort = -32768;
		short maxShort = 32767;
		System.out.println(minShort);
		System.out.println(maxShort);
		
		int minInt = -2147483648;
		int maxInt = 2147483647;
		System.out.println(minInt);
		System.out.println(maxInt);
		
		long minLong = -2147483649L;
		long maxLong = 2147483648L;
		System.out.println(minLong);
		System.out.println(maxLong);
	}

}
```
{: id="20210309203838-dp56yyi"}

## 第五题
{: id="20210309203838-a9nfuwh"}

- {: id="20210309203838-r3gcixa"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-9sgm4mp"}

  ![](img\5.jpg)
  {: id="20210309203838-d1ouwe1"}
{: id="20210309203838-f9j68zk"}

* {: id="20210309203838-0x0oyaf"}编写步骤：
  {: id="20210309203838-44usqtw"}
  1. {: id="20210309203838-4yejou8"}定义类 Test5
     {: id="20210309203838-1fis95d"}
  2. {: id="20210309203838-96ec24c"}定义 main方法
     {: id="20210309203838-mr0bvs0"}
  3. {: id="20210309203838-t50pf75"}定义2个 float类型变量,分别赋值,并输出在控制台.
     {: id="20210309203838-p01l2l3"}
  4. {: id="20210309203838-bm0tk5z"}定义2个 double类型变量,分别赋值,并输出在控制台.
     {: id="20210309203838-f4uxcph"}
  {: id="20210309203838-ued7wtq"}
{: id="20210309203838-3u9630u"}

```java
public class Test5 {

	public static void main(String[] args) {
		float f1 = -3.14F;
		float f2 = 3.14F;
		System.out.println(f1);
		System.out.println(f2);
		
		double d1 = -3.4;
		double d2 = 3.4;
		System.out.println(d1);
		System.out.println(d2);
	}

}
```
{: id="20210309203838-yo0ick2"}

## 第六题
{: id="20210309203838-799hxwh"}

- {: id="20210309203838-fybxqg1"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-tnyd93y"}

  ![](img\6.jpg)
  {: id="20210309203838-syqbspk"}
- {: id="20210309203838-vzrrsnx"}编写步骤：
  {: id="20210309203838-ulbr2zk"}
{: id="20210309203838-lyga1cp"}

1. {: id="20210309203838-lkir6q2"}定义类 Test6
   {: id="20210309203838-xbc9bc1"}
2. {: id="20210309203838-h65kpr9"}定义 main方法
   {: id="20210309203838-1f9uqfi"}
3. {: id="20210309203838-ufg9cba"}定义5个 char类型变量,分别赋值,并输出在控制台.
   {: id="20210309203838-pswenw5"}
4. {: id="20210309203838-ccxecy3"}定义2个 boolean类型变量,分别赋值,并输出在控制台.
   {: id="20210309203838-jt2olqm"}
{: id="20210309203838-pnj3rl5"}

```java
public class Test6 {
	public static void main(String[] args) {
		char c1 = '9';
		//或 char c1 = 57;
		char c2 = 'J';
		char c3 = 'a';
		char c4 = ' ';
		char c5 = '@';
		System.out.println(c1);
		System.out.println(c2);
		System.out.println(c3);
		System.out.println(c4);
		System.out.println(c5);
		
		boolean yes = true;
		boolean no = false;
		System.out.println(yes);
		System.out.println(no);
	}
}
```
{: id="20210309203838-1umvow1"}

## 第七题
{: id="20210309203838-2san43k"}

- {: id="20210309203838-6fnh45c"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-snsbzdn"}

  ![1558837582892](img/7.png)
  {: id="20210309203838-b2emhiu"}
- {: id="20210309203838-placj7o"}步骤图解：
  {: id="20210309203838-vyw3ykh"}
  ![](img\71.jpg)
  {: id="20210309203838-6cym7mu"}
- {: id="20210309203838-ui7jyy1"}开发提示：定义变量不赋值的格式
  {: id="20210309203838-pg1v3mj"}
  ```java
  // 	数据类型 变量名 ；
  	int temp；
  ```
  {: id="20210309203838-sdsnoru"}
- {: id="20210309203838-hb4l9ta"}编写步骤：
  {: id="20210309203838-vdnlwns"}
  1. {: id="20210309203838-93u1zwh"}定义类 Test7
     {: id="20210309203838-t6owt5d"}
  2. {: id="20210309203838-ymxmt1z"}定义 main方法
     {: id="20210309203838-f4l5j7e"}
  3. {: id="20210309203838-i91geqm"}定义两个整数变量a，b并赋值
     {: id="20210309203838-n49ydmb"}
  4. {: id="20210309203838-ye0a5lq"}控制台输出变量a，b互换前的值
     {: id="20210309203838-2fb21rq"}
  5. {: id="20210309203838-8xf7lld"}定义一个第三方变量temp，使a，b的值互换
     {: id="20210309203838-qo07hvn"}
  6. {: id="20210309203838-x9vnlzl"}控制台输出变量a，b互换后的值
     {: id="20210309203838-hgqb82t"}
  {: id="20210309203838-p2ob45r"}
{: id="20210309203838-iv7f8iv"}

```java
public class Test7 {

	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		System.out.println("互换前：");
		System.out.println("a = " + a);
		System.out.println("b = " + b);
		
		int temp = a;
		a = b;
		b = temp;
		System.out.println("互换后：");
		System.out.println("a = " + a);
		System.out.println("b = " + b);
	}

}
```
{: id="20210309203838-qte03k1"}

# 扩展题目:
{: id="20210309203838-abaoco8"}

## 第八题
{: id="20210309203838-d2dhcpd"}

- {: id="20210309203838-4vgtoji"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-hh9kugg"}
{: id="20210309203838-i02ak0h"}

![1558837813998](img/8.png)
{: id="20210309203838-p13h75v"}

* {: id="20210309203838-n6i9ag2"}开发提示：四则运算的符号
  {: id="20210309203838-b6e13dh"}

  ```java
  加: +
  减: -
  乘: *
  除: /
  ```
  {: id="20210309203838-ioopymg"}
* {: id="20210309203838-rgcwmg6"}编写步骤：
  {: id="20210309203838-ovcwh1z"}
  1. {: id="20210309203838-l1ze4sk"}定义类 Test8
     {: id="20210309203838-khbsko0"}
  2. {: id="20210309203838-ljgjud8"}定义 main方法
     {: id="20210309203838-v1926ue"}
  3. {: id="20210309203838-cg830ig"}定义2个int类型变量x、y，x赋值为100，y赋值为200
     {: id="20210309203838-4zmqqlf"}
  4. {: id="20210309203838-ds5xqpw"}定义新变量add，保存变量x，y的和并打印到控制台
     {: id="20210309203838-7wsy0fz"}
  5. {: id="20210309203838-44beh3w"}定义新变量sub，保存变量x，y的差并打印到控制台
     {: id="20210309203838-d3h6vyv"}
  6. {: id="20210309203838-o6ics25"}定义新变量mul，保存变量x，y的积并打印到控制台
     {: id="20210309203838-uxi9ti2"}
  7. {: id="20210309203838-hnspi02"}定义新变量div，保存变量x，y的商并打印到控制台
     {: id="20210309203838-z2c3vi8"}
  {: id="20210309203838-a2iawhb"}
{: id="20210309203838-k2d9b9x"}

```java
public class Test8 {

	public static void main(String[] args) {
		int x = 100;
		int y = 200;
		System.out.println("x,y的和为：" + (x+y));
		System.out.println("x,y的差为：" + (x-y));
		System.out.println("x,y的积为：" + (x*y));
		System.out.println("x,y的商为：" + (x/y));
	}

}
```
{: id="20210309203838-c0nk0su"}

## 第九题
{: id="20210309203838-vijgu5p"}

- {: id="20210309203838-xwmkc5l"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-txjdxp7"}

  ![1558838062315](img/9.png)
  {: id="20210309203838-rxw5gwq"}
- {: id="20210309203838-wdly98s"}开发提示：观察小数类型数值运算后的结果.
  {: id="20210309203838-zx6nl02"}
  ```java
   小数运算经常出现精度丢失的问题,不建议使用基本类型运算.
  ```
  {: id="20210309203838-1bj5fg1"}
- {: id="20210309203838-tyg3ja8"}编写步骤：
  {: id="20210309203838-1yud30q"}
  1. {: id="20210309203838-aezv0a2"}定义类 Test9
     {: id="20210309203838-eyfm1ks"}
  2. {: id="20210309203838-3xo1u6x"}定义 main方法
     {: id="20210309203838-cggfu4d"}
  3. {: id="20210309203838-da2zzch"}定义2个double类型变量x、y，x赋值为100.8，y赋值为20.6
     {: id="20210309203838-0bv5wf5"}
  4. {: id="20210309203838-rqmdqrb"}定义新变量add，保存变量x，y的和并打印到控制台
     {: id="20210309203838-d90g9k0"}
  5. {: id="20210309203838-ix9ylod"}定义新变量sub，保存变量x，y的差并打印到控制台
     {: id="20210309203838-q370lc6"}
  6. {: id="20210309203838-ohug7e1"}定义新变量mul，保存变量x，y的积并打印到控制台
     {: id="20210309203838-5wa97ob"}
  7. {: id="20210309203838-ydveig0"}定义新变量div，保存变量x，y的商并打印到控制台
     {: id="20210309203838-3bp06rq"}
  {: id="20210309203838-i04b9u7"}
{: id="20210309203838-v4blfhf"}

* {: id="20210309203838-4hybxan"}提示：
  {: id="20210309203838-33suqzz"}
  1. {: id="20210309203838-mfotlkt"}加法：+
     {: id="20210309203838-vr69umc"}
  2. {: id="20210309203838-7samhcd"}减法：-
     {: id="20210309203838-quilauw"}
  3. {: id="20210309203838-x18oclp"}乘法：*
     {: id="20210309203838-6zvac1c"}
  4. {: id="20210309203838-htduedx"}除法：/
     {: id="20210309203838-qutakkw"}
  {: id="20210309203838-h68cgrj"}
{: id="20210309203838-a1w7d6d"}

```java
public class Test9 {

	public static void main(String[] args) {
		double x = 100.8;
		double y = 20.6;
		
		double add = x + y;
		System.out.println("x,y的和为：" + add);
		
		double sub = x - y;
		System.out.println("x,y的差为：" + sub);
		
		double mul = x * y;
		System.out.println("x,y的积为：" + mul);
		
		double div = x / y;
		System.out.println("x,y的商为：" + div);
	}

}
```
{: id="20210309203838-dnqrsdz"}

## 第十题
{: id="20210309203838-fryt9mb"}

- {: id="20210309203838-g1ubd61"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-luf21is"}

  ![](img\10.jpg)
  {: id="20210309203838-4j8bjkt"}
- {: id="20210309203838-1iqyr16"}开发提示：不换行的输出
  {: id="20210309203838-qgxyyhc"}
  ```java
  System.out.print("整数类型-byte:"); // 去掉ln ,输出内容后,没有换行
  System.out.println(10);// 带有ln,输出内容后,带有换行
  ```
  {: id="20210309203838-d1tdmnv"}
- {: id="20210309203838-6iw8mwe"}编写步骤：
  {: id="20210309203838-igxy47e"}
  1. {: id="20210309203838-eyraxe4"}定义类 Test10
     {: id="20210309203838-qtmlg87"}
  2. {: id="20210309203838-btc4ioy"}定义 main方法
     {: id="20210309203838-alb6y4y"}
  3. {: id="20210309203838-1hiaxdg"}定义byte类型变量，并赋值为10，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-jvvhava"}
  4. {: id="20210309203838-q26jtj2"}定义short类型变量，并赋值为100，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-8e8xmg3"}
  5. {: id="20210309203838-kxzrs2b"}定义int类型变量，并赋值为1000，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-h0k5sqh"}
  6. {: id="20210309203838-dhkacxr"}定义long类型变量，并赋值为10000，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-3wy4dbj"}
  7. {: id="20210309203838-xlz272t"}定义float类型变量，并赋值为100000.0，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-q3e2mxf"}
  8. {: id="20210309203838-hktyoqr"}定义double类型变量，并赋值为1000000.0，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-jswvae4"}
  9. {: id="20210309203838-vvll75w"}定义char类型变量，并赋值为'Z'，不换行输出类型说明，换行输出变量值。
     {: id="20210309203838-v5lv2a3"}
  10. {: id="20210309203838-m9saw8r"}定义boolean类型变量，并赋值为false，不换行输出类型说明，换行输出变量值。
      {: id="20210309203838-1stwnef"}
  {: id="20210309203838-0zg06xu"}
{: id="20210309203838-7e0bn9a"}

```java
public class Test10 {
	public static void main(String[] args) {
		byte b = 10;
		System.out.print("整数类型-byte：");
		System.out.println(b);
		
		short s = 100;
		System.out.print("整数类型-short：");
		System.out.println(s);
		
		int i = 1000;
		System.out.print("整数类型-int：");
		System.out.println(i);
		
		long l = 10000L;
		System.out.print("整数类型-long：");
		System.out.println(l);
		
		float f = 100000.0F;
		System.out.print("小数类型-float：");
		System.out.println(f);
		
		double d = 1000000.0;
		System.out.print("小数类型-double：");
		System.out.println(d);
		
		char c = 'Z';
		System.out.print("字符类型-char：");
		System.out.println(c);
		
		boolean no = false;
		System.out.print("布尔类型-boolean：");
		System.out.println(no);
	}
}
```
{: id="20210309203838-s5n041v"}

# 简答题
{: id="20210309203838-xd38bw3"}

1、Java的基本数据类型有哪些？String是基本数据类型吗？
{: id="20210309203838-o1mgpy6"}

```java
Java的基本数据类型有：byte,short,int,long,float,double,char,boolean
String不是基本数据类型
```
{: id="20210309203838-ht20p1t"}

2、float f=3.4;是否正确，表达式15/2*2的值是多少
{: id="20210309203838-jwmiugj"}

```java
float f=3.4; //错误，因为3.4默认是double类型
System.out.println(15/2*2); //14，因为15/2结果是7
```
{: id="20210309203838-stlnly9"}

3、char型变量中是否可以存储一个汉字？
{: id="20210309203838-xdg59be"}

```
可以
```
{: id="20210309203838-b1x1j0b"}

4、如何用最有效的的方法计算2乘以8
{: id="20210309203838-3go7845"}

```java
2<<3
```
{: id="20210309203838-lordlsl"}


{: id="20210309203838-zrdlufj" type="doc"}
