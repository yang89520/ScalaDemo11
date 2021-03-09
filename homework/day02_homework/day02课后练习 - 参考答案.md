# day02课后练习
{: id="20210309203838-m9yp19c"}

# 基础题目:
{: id="20210309203838-wfrsqlz"}

## 第一题
{: id="20210309203838-mxe5uk3"}

* {: id="20210309203838-w9p3rwl"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-5gal006"}
{: id="20210309203838-5wosfbw"}

![](img\1.jpg)
{: id="20210309203838-t6j28pn"}

* {: id="20210309203838-z3d4n5l"}编写步骤：
  {: id="20210309203838-2h1uuux"}
{: id="20210309203838-ayidkgt"}

1. {: id="20210309203838-dfue32z"}定义类 Test1
   {: id="20210309203838-re7i81t"}
2. {: id="20210309203838-l630vfj"}定义 main方法
   {: id="20210309203838-2gi4dfj"}
3. {: id="20210309203838-zr7mhl9"}定义两个byte类型变量b1,b2,并分别赋值为10和20.
   {: id="20210309203838-i602pxm"}
4. {: id="20210309203838-mm9cnbr"}定义变量b3,保存b1和b2的和,并输出.
   {: id="20210309203838-mxzo5mt"}
5. {: id="20210309203838-ayp53dc"}定义两个short类型变量s1,s2,并分别赋值为1000和2000.
   {: id="20210309203838-4rngk2a"}
6. {: id="20210309203838-q93x5p4"}定义变量s3,保存s1和s2的和,并输出.
   {: id="20210309203838-ueq41si"}
7. {: id="20210309203838-5q0tuk0"}定义一个char类型变量ch1赋值为'a',一个int类型变量i1赋值为30.
   {: id="20210309203838-7paup5v"}
8. {: id="20210309203838-1tti6cy"}定义变量ch3,保存c1和i1的差,并输出.
   {: id="20210309203838-e92iyvv"}
{: id="20210309203838-fr6n2ul"}

```java
public class Test01 {

	public static void main(String[] args) {
		byte b1 = 10;
		byte b2 = 20;
		byte b3 = (byte)(b1 + b2);
		System.out.println("byte类型的b1和b2的和为：");
		System.out.println(b3);
		
		short s1 = 1000;
		short s2 = 2000;
		short s3 = (short)(s1 + s2);
		System.out.println("short类型的s1和s2的和为：");
		System.out.println(s3);
		
		char c1 = 'a';
		int i1 = 30;
		int ch3 = c1 - i1;
		System.out.println("char类型的ch1和int类型的i1的差：");
		System.out.println(ch3);
	}
}
```
{: id="20210309203838-wd56uve"}

## 第二题
{: id="20210309203838-v9z52pk"}

* {: id="20210309203838-58foliw"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-texxd1o"}

  ![](img\2.jpg)
  {: id="20210309203838-ao4g8c2"}
* {: id="20210309203838-ohjeaiu"}编写步骤：
  {: id="20210309203838-scnzc9u"}
  1. {: id="20210309203838-l7ggusf"}定义类 Test2
     {: id="20210309203838-x0ycycc"}
  2. {: id="20210309203838-2qnx76q"}定义 main方法
     {: id="20210309203838-sodrmci"}
  3. {: id="20210309203838-nl1l2ts"}定义 int类型变量i1 和 long类型变量l1
     {: id="20210309203838-mqywuha"}
  4. {: id="20210309203838-h4gmpsu"}定义变量add,保存i1和l1的和,并输出.
     {: id="20210309203838-chwfs6p"}
  5. {: id="20210309203838-k973yev"}定义 long类型变量l2 和 float类型变量f2
     {: id="20210309203838-hhgzvun"}
  6. {: id="20210309203838-gcrewlj"}定义变量add2,保存l2和f2的和,并输出.
     {: id="20210309203838-1tav595"}
  7. {: id="20210309203838-3crlfeb"}定义 int类型变量i3 和 double类型变量d3
     {: id="20210309203838-mz9zx5o"}
  8. {: id="20210309203838-frjx1bf"}定义变量add3,保存i3和d3的和,并输出.
     {: id="20210309203838-ivabx8k"}
  9. {: id="20210309203838-rq14mno"}定义 float类型变量f4 和 double类型变量d4
     {: id="20210309203838-nzijg98"}
  10. {: id="20210309203838-7c04tf3"}定义变量add4,保存f4和d4的和,并输出.
      {: id="20210309203838-reiq2a0"}
  {: id="20210309203838-w4v3klb"}
{: id="20210309203838-pw7gq97"}

```java
public class Test2 {
	public static void main(String[] args) {
		int i1 = 100;
		long l1 = 200;
		long add = i1 + l1;
		System.out.println("add的值：" + add);
		
		long l2 = 1000000L;
		float f2 = 0.44F;
		float add2 = l2 + f2;
		System.out.println("add2的值：" + add2);
		
		int i3 = 100000;
		double d3 = 0.45;
		double add3 = i3 + d3;
		System.out.println("add3的值：" + add3);
		
		float f4 = 1000000;
		double d4 = 1.2625;
		double add4 = f4 + d4;
		System.out.println("add4的值：" + add4);
	}
}

```
{: id="20210309203838-g7aruyg"}

## 第三题
{: id="20210309203838-0xgaqrr"}

- {: id="20210309203838-p2r0y0y"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-khsh3hz"}

  ![](img\3.jpg)
  {: id="20210309203838-8dsiad7"}
- {: id="20210309203838-rqx8b4s"}编写步骤：
  {: id="20210309203838-tn3am8x"}
  1. {: id="20210309203838-aowmkin"}定义类 Test3
     {: id="20210309203838-0ba7zvn"}
  2. {: id="20210309203838-fkpcepp"}定义 main方法
     {: id="20210309203838-hxoodod"}
  3. {: id="20210309203838-vw6nnmi"}定义char类型变量ch,赋值为'J'
     {: id="20210309203838-ppls7xk"}
  4. {: id="20210309203838-w60e4g4"}使用强制转换的方式,将变量ch转换为小写'j',并输出
     {: id="20210309203838-6ksingc"}
  5. {: id="20210309203838-c942hn2"}定义char类型变量ch2,赋值为'a'
     {: id="20210309203838-n20t3s5"}
  6. {: id="20210309203838-t5awq9j"}使用+=的方式,将变量ch2转换为大写'A',并输出
     {: id="20210309203838-ukca5nn"}
  7. {: id="20210309203838-7syx14e"}定义double类型变量d3,int类型变量i3
     {: id="20210309203838-j73t7nq"}
  8. {: id="20210309203838-0rpyukm"}定义double变量sum3,保存d3与i3的和,输出sum3的值和sum3去除小数部分的值
     {: id="20210309203838-mx4e4ju"}
  9. {: id="20210309203838-ysn7f5l"}定义double类型变量d4,int类型变量i4
     {: id="20210309203838-a7po7z1"}
  10. {: id="20210309203838-t5zmngg"}定义int变量mul4,保存d4和i4乘积的整数部分,并输出
      {: id="20210309203838-hvao1vw"}
  {: id="20210309203838-0f4oc2d"}
{: id="20210309203838-rnuppwl"}

```java

public class Test03 {

	public static void main(String[] args){
		char ch = 'J';
		char ch1 = (char)(ch + 32);
		System.out.println(ch1);
		
		char ch2 = 'a';
		ch2 -= 32;
		System.out.println(ch2);
		
		double d3 = 100.5;
		int i3 = 3;
		double sum3 = d3 + i3;
		int sum4 = (int)sum3;
		System.out.println("sum3的值：" + sum3);
		System.out.println("sum3的整数部分的值：" + sum4);
		
		double d4 = 4.0;
		int i4 = 435;
		int mul4 = (int)(d4 * i4);
		System.out.println("mul4的整数部分的值：" + mul4);
	}

}
```
{: id="20210309203838-s4oxehx"}

## 第四题
{: id="20210309203838-61xms6b"}

- {: id="20210309203838-myrikqk"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-3eq58rj"}

  ![](img\4.jpg)
  {: id="20210309203838-2igrmw4"}
- {: id="20210309203838-z90f6fl"}编写步骤：
  {: id="20210309203838-wppf86c"}
  1. {: id="20210309203838-ot8wep5"}定义类 Test4
     {: id="20210309203838-0ee8pqr"}
  2. {: id="20210309203838-d07ot6s"}定义 main方法
     {: id="20210309203838-rnuyfry"}
  3. {: id="20210309203838-xub6voj"}定义两个int类型变量a1和a2,分别赋值10,11,判断变量是否为偶数,拼接输出结果
     {: id="20210309203838-0k0id95"}
  4. {: id="20210309203838-86sodtn"}定义两个int类型变量a3和a4,分别赋值12,13,判断变量是否为奇数,拼接输出结果
     {: id="20210309203838-ieclqbu"}
  {: id="20210309203838-8zsl5o4"}
{: id="20210309203838-a3nnfzz"}

```java
public class Test04 {
	public static void main(String[] args) {
		int a1 = 10;
		int a2 = 11;
		int a3 = 12;
		int a4 = 13;
		System.out.println("10是偶数？" + (a1 % 2 == 0));
		System.out.println("11是偶数？" + (a2 % 2 == 0));
		System.out.println("12是奇数？" + (a3 % 2 != 0));
		System.out.println("13是奇数？" + (a4 % 2 != 0));
	}
}
```
{: id="20210309203838-rmdt61g"}

## 第五题
{: id="20210309203838-shsmi8o"}

- {: id="20210309203838-hah8yuu"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-594zwbf"}

  ![](img\5.jpg)
  {: id="20210309203838-i7fypgw"}
{: id="20210309203838-sbgvr7r"}

* {: id="20210309203838-nzya7ze"}编写步骤：
  {: id="20210309203838-p8cmpn7"}
  1. {: id="20210309203838-svxa76g"}定义类 Test5
     {: id="20210309203838-bpwovy1"}
  2. {: id="20210309203838-q778qbf"}定义 main方法
     {: id="20210309203838-vwj8mmf"}
  3. {: id="20210309203838-kemuap7"}定义一个int类型变量a,变量b,都赋值为20.
     {: id="20210309203838-kub65j7"}
  4. {: id="20210309203838-6rd2k10"}定义boolean类型变量bo , 判断++a 是否被3整除,并且a++ 是否被7整除,将结果赋值给bo
     {: id="20210309203838-xvub7ub"}
  5. {: id="20210309203838-r877ipo"}输出a的值,bo的值.
     {: id="20210309203838-8la0p5b"}
  6. {: id="20210309203838-1jmycat"}定义boolean类型变量bo2 , 判断b++ 是否被3整除,并且++b 是否被7整除,将结果赋值给bo2
     {: id="20210309203838-lysvn8k"}
  7. {: id="20210309203838-m62d49k"}输出b的值,bo2的值.
     {: id="20210309203838-5w1xygl"}
  {: id="20210309203838-6xecwso"}
{: id="20210309203838-nf9kk5n"}

```java
public class Test05 {
	public static void main(String[] args){
		int a = 20;
		int b = 20;
		boolean bo = ((++a % 3) == 0) && ((a++ % 7) == 0);
		boolean bo2 = ((b++ % 3) == 0) && ((++b % 7) == 0);
		
		System.out.println("bo的值：" + bo);
		System.out.println("a的值：" + a);
		System.out.println("----------------------------");
		System.out.println("bo2的值：" + bo2);
		System.out.println("b的值：" + b);
	}
}
```
{: id="20210309203838-3ocyq0k"}

## 第六题
{: id="20210309203838-f6kapjs"}

案例：为抵抗洪水，战士连续作战89小时，编程计算共多少天零多少小时？
{: id="20210309203838-c64pms3"}

- {: id="20210309203838-2f5dq66"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-lyllehg"}

  ![1557879127503](img/6.png)
  {: id="20210309203838-panttmb"}
{: id="20210309203838-qqe8eu5"}

* {: id="20210309203838-wxhjo3y"}编写步骤：
  {: id="20210309203838-4e2n6lo"}
  1. {: id="20210309203838-cuh01t3"}定义类Test6
     {: id="20210309203838-5q98lf6"}
  2. {: id="20210309203838-trsjkf6"}定义main方法
     {: id="20210309203838-qcwt7mz"}
  3. {: id="20210309203838-7kghzjj"}定义一个int类型变量hours，赋值为89
     {: id="20210309203838-splfdr5"}
  4. {: id="20210309203838-5dwk30h"}定义一个int类型变量day，用来保存89小时中天数的结果
     {: id="20210309203838-lrvyuqj"}
  5. {: id="20210309203838-yuqjqsn"}定义一个int类型变量hour，用来保存89小时中不够一天的剩余小时数的结果
     {: id="20210309203838-73af0tk"}
  6. {: id="20210309203838-0a6ipkd"}输出结果
     {: id="20210309203838-7sod4qn"}
  {: id="20210309203838-2bbcvvm"}
{: id="20210309203838-rlf17fa"}

```java
public class Test06 {
	public static void main(String[] args){
		int hours = 89;
		int day = hours / 24;
		int hour = hours % 24;
		System.out.println("为抵抗洪水，战士连续作战89小时：");
		System.out.println(hours + "是" + day + "天" + hour +"小时");
	}
}
```
{: id="20210309203838-kw12804"}

## 第七题
{: id="20210309203838-shgr8z6"}

案例：今天是周2，100天以后是周几？
{: id="20210309203838-9i1ra21"}

* {: id="20210309203838-v3tlejo"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-m8rt4xb"}
{: id="20210309203838-8iigk3h"}

![1557879464870](img/7.png)
{: id="20210309203838-o9hdyz3"}

* {: id="20210309203838-pepqoje"}编写步骤：
  {: id="20210309203838-pzbudkm"}
  1. {: id="20210309203838-lsnkm9w"}定义类Test7
     {: id="20210309203838-8g5rfyv"}
  2. {: id="20210309203838-9dlsgl8"}定义main方法
     {: id="20210309203838-thnxjt4"}
  3. {: id="20210309203838-ber26ac"}定义一个int类型变量week，赋值为2
     {: id="20210309203838-kk4wsav"}
  4. {: id="20210309203838-zkjq5be"}修改week的值，在原值基础上加上100
     {: id="20210309203838-hlok0wv"}
  5. {: id="20210309203838-7xzwzf8"}因为week的值加上100后超过了星期的范围，重写修改week的值
     {: id="20210309203838-oioe0vz"}
  6. {: id="20210309203838-w9occzg"}输出结果，在输出结果的时候考虑特殊值，例如周日
     {: id="20210309203838-l260x58"}
  {: id="20210309203838-ckndrve"}
{: id="20210309203838-xgp1r32"}

```java
public class Test07 {

	public static void main(String[] args){
		int week = 2;
		week += 100;
		week %= 7;
		System.out.println("今天是周2,100天以后是周" + (week==0?"日":week));
	}

}
```
{: id="20210309203838-dwwd3o1"}

## 第八题
{: id="20210309203838-14tf4q7"}

案例：求三个整数x,y,z中的最大值
{: id="20210309203838-pfenfkb"}

* {: id="20210309203838-56uhcxf"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-ocfpoh1"}
{: id="20210309203838-gpa0np6"}

![1557879847378](img/8.png)
{: id="20210309203838-0t6dfns"}

* {: id="20210309203838-kq1rbzz"}编写步骤：
  {: id="20210309203838-8kbs2g7"}

  1. {: id="20210309203838-53ssfxb"}定义类Test8
     {: id="20210309203838-4aodmsq"}
  2. {: id="20210309203838-ofgjtd6"}定义main方法
     {: id="20210309203838-eco538e"}
  3. {: id="20210309203838-jhg8nfz"}定义三个int类型变量,x,y,z，随意赋值整数值
     {: id="20210309203838-sor3x68"}
  4. {: id="20210309203838-k9x9c0t"}定义一个int类型变量max，先存储x与y中的最大值（使用三元运算符）
     {: id="20210309203838-fglntsa"}
  5. {: id="20210309203838-8bdrf6s"}再次对max赋值，让它等于上面max与z中的最大值（使用三元运算符）
     {: id="20210309203838-tudl4oe"}
  6. {: id="20210309203838-wa34w7s"}输出结果
     {: id="20210309203838-588x0dz"}
  {: id="20210309203838-r1mys7l"}
{: id="20210309203838-x7bnp7y"}

```java
public class Test08 {
	public static void main(String[] args) {
		int x = 3;
		int y = 4;
		int z = 1;
		int max = x > y ? x : y;
		max = max > z ? max : z;
		System.out.println(x + "," + y + "," + z + "中的最大值是：" + max);
	}
}
```
{: id="20210309203838-ymby4cn"}

## 第九题
{: id="20210309203838-ouy9hwb"}

案例：给定一个年份，判断是否是闰年
{: id="20210309203838-ly5kka6"}

闰年的判断标准是：
{: id="20210309203838-3zarizj"}

​       1）可以被4整除，但不可被100整除
{: id="20210309203838-kcpsbdk"}

​       2）可以被400整除
{: id="20210309203838-3jo7gy7"}

* {: id="20210309203838-6gnp39d"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-1hduk80"}
{: id="20210309203838-14l0oem"}

![1557902649882](img/9.png)
{: id="20210309203838-yblgenx"}

* {: id="20210309203838-xmvtraw"}编写步骤：
  {: id="20210309203838-j1pa3kh"}
  1. {: id="20210309203838-igqytd6"}定义类Test9
     {: id="20210309203838-i1vahw4"}
  2. {: id="20210309203838-6oih4ks"}定义main方法
     {: id="20210309203838-hsm3oyo"}
  3. {: id="20210309203838-8u4l80s"}定义一个int类型变量year，随意赋值一个年份
     {: id="20210309203838-j3vi6mp"}
  4. {: id="20210309203838-msvo2q4"}定一个一个boolean类型变量，用来保存这个年份是否是闰年的结果
     {: id="20210309203838-yaxme2c"}
  5. {: id="20210309203838-8wokupa"}输出结果
     {: id="20210309203838-k3wight"}
  {: id="20210309203838-riw43rz"}
{: id="20210309203838-j5epbuc"}

```java
public class Test09 {

	public static void main(String[] args) {
		int year = 2018;
		boolean result = year%4==0 && year%100!=0 || year%400==0;
		System.out.println(year + (result ? "是闰年" : "不是闰年"));
	}

}
```
{: id="20210309203838-zcma8w7"}

## 第十题
{: id="20210309203838-1arhl8f"}

案例：小明要到美国旅游，可是那里的温度是以华氏度为单位记录的。它需要一个程序将华氏温度（80度）转换为摄氏度，并以华氏度和摄氏度为单位分别显示该温度。
{: id="20210309203838-qdmv91c"}

![1557903785834](img/1557903785834.png)
{: id="20210309203838-7hxj3da"}

* {: id="20210309203838-88a6b3x"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-muz8u1j"}

  ![1557903814057](img/1557903814057.png)
  {: id="20210309203838-5glhf21"}
* {: id="20210309203838-ns11tcj"}编写步骤：
  {: id="20210309203838-d01b8es"}
  1. {: id="20210309203838-loll9a4"}定义类Test10
     {: id="20210309203838-sqv5g2o"}
  2. {: id="20210309203838-k00oyvo"}定义main方法
     {: id="20210309203838-ko6st8t"}
  3. {: id="20210309203838-tcxaqru"}定义一个double类型变量hua，存储华氏温度80
     {: id="20210309203838-64nn303"}
  4. {: id="20210309203838-2cavwaf"}定义一个double类型变量she，存储摄氏温度，根据公式求值
     {: id="20210309203838-nv3bxi7"}
  5. {: id="20210309203838-y0fvgtu"}输出结果
     {: id="20210309203838-8xxpbvv"}
  {: id="20210309203838-7scu0fb"}
{: id="20210309203838-w63xivl"}

```java
public class Test10 {
	public static void main(String[] args) {
		double hua = 80;
		double she = (hua-32)/1.8;
		System.out.println("华氏度" + hua+"℉转为摄氏度是" +she+"℃");
	}
}
```
{: id="20210309203838-u86ypat"}

# 阅读代码题：
{: id="20210309203838-7swtmnk"}

## 第一题
{: id="20210309203838-m2kr0pu"}

```java
如下代码的计算结果是：
int i = 1;
i *= 0.2;  
i++;
System.out.println("i=" + i);//i=1
```
{: id="20210309203838-zfa3iaa"}

## 第二题
{: id="20210309203838-f3ss57v"}

```java
如下代码的运算结果是：
int i = 2;
i *= i++;

int j = 2;
j *= j+1; 

int k = 2;
k *= ++k;

System.out.println("i=" + i);//i=4
System.out.println("j=" + j);//i=6
System.out.println("k=" + k);//i=6
```
{: id="20210309203838-pud0yib"}

## 第三题
{: id="20210309203838-brpvhrg"}

```java
	public static void main(String[] args) {
		int a = 3;
		int b = 1;
		if(a = b){//编译报错
			System.out.println("Equal");
		}else{
			System.out.println("Not Equal");
		}
	}
```
{: id="20210309203838-pa5i1sq"}

## 第四题
{: id="20210309203838-esqumos"}

```java
	public static void main(String[] args) {
		int a = 8, b = 3;
		System.out.println(a>>>b);//1
		System.out.println(a>>>b | 2);//2
	}
```
{: id="20210309203838-ngco8sx"}


{: id="20210309203838-i8vczp7" type="doc"}
