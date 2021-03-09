# day03_课后练习
{: id="20210309203838-s9373b0"}

# 编程题
{: id="20210309203838-j24ss42"}

## 第一题
{: id="20210309203838-zdvuf1r"}

语法点：变量，运算符，if...else
{: id="20210309203838-cw280sw"}

案例：从键盘输入一个整数，判断它是奇数还是偶数（这里把0归为偶数）
{: id="20210309203838-97tx9z2"}

![1557990838327](imgs/1557990838327.png)
{: id="20210309203838-va1w3s4"}

开发提示：
{: id="20210309203838-bu5cs0p"}

​	键盘输入需要用到Scanner类。
{: id="20210309203838-p27w6yt"}

```java
java.util.Scanner input = new java.util.Scanner(System.in);//准备从键盘输入的扫描仪
int num = input.nextInt();//输入整数
```
{: id="20210309203838-ijoqc22"}

​	能够被2整除的是偶数，不能被2整除的是奇数
{: id="20210309203838-2c2v519"}

```java
public class Test01{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入一个整数：");
		int num = input.nextInt();
		if(num % 2 == 0){
			System.out.println(num + "是偶数");
		}else{
			System.out.println(num + "是奇数");
		}
	}
}

```
{: id="20210309203838-z0zbyrp"}

## 第二题
{: id="20210309203838-792ap71"}

语法点：变量，运算符，if...else
{: id="20210309203838-14cp0ki"}

案例：从键盘输入一个字符，判断它是字母还是数字，还是其他字符
{: id="20210309203838-845chsd"}

![1557991405648](imgs/1557991405648.png)
{: id="20210309203838-8xpo3q9"}

开发提示：
{: id="20210309203838-d8ozuop"}

​	键盘输入需要用到Scanner类。
{: id="20210309203838-xe4ng45"}

```java
java.util.Scanner input = new java.util.Scanner(System.in);//准备接收从键盘输入的扫描仪
char c = input.next().charAt(0);//输入单个字符
```
{: id="20210309203838-kpckmtl"}

​	数字范围：'0'-'9'
{: id="20210309203838-6pfu19c"}

​	字母范围：'A'-'Z'，'a'-'z'
{: id="20210309203838-nqqasi8"}

```java
public class Test02{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入一个字符：");
		char c = input.next().charAt(0);
		if(c >= '0' && c <= '9'){
			System.out.println(c + "是数字.");
		}else if(c >= 'A' && c <= 'Z' || c >= 'a' && c <= 'z'){
			System.out.println(c + "是字母.");
		}else{
			System.out.println(c + "非数字非字母的其他字符.");
		}
	}
}
```
{: id="20210309203838-mmqqk62"}

## 第三题
{: id="20210309203838-yfge6g1"}

* {: id="20210309203838-ca4a8bn"}语法点：变量，运算符，if...else
  {: id="20210309203838-qkaiqic"}
* {: id="20210309203838-6hz793y"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-751u64z"}
  ![1557999671932](imgs/1557999671932.png)
  {: id="20210309203838-cczj136"}
* {: id="20210309203838-b19nmta"}编写步骤：
  {: id="20210309203838-64gbyg1"}
  1. {: id="20210309203838-tsku98c"}定义类 Test2
     {: id="20210309203838-pl8pj58"}
  2. {: id="20210309203838-ivtdxi8"}定义 main方法
     {: id="20210309203838-zrfmx9d"}
  3. {: id="20210309203838-zeqk1gc"}定义变量折扣 discount，初始化为1, 总价totalPrice的值从键盘输入
     {: id="20210309203838-q6szo9t"}
  4. {: id="20210309203838-lyun9eg"}判断当`totalPrice >=500` ,discount赋值为0.5
     {: id="20210309203838-wuscxsf"}
  5. {: id="20210309203838-6m3jrfw"}判断当`totalPrice >=400` 且`<500`时,discount赋值为0.6
     {: id="20210309203838-zvcio1w"}
  6. {: id="20210309203838-5rka84v"}判断当`totalPrice >=300` 且`<400`时,discount赋值为0.7
     {: id="20210309203838-xngz73n"}
  7. {: id="20210309203838-1hyo9i8"}判断当`totalPrice >=200` 且`<300`时,discount赋值为0.8
     {: id="20210309203838-noes533"}
  8. {: id="20210309203838-ctumvmr"}判断当`totalPrice >=0` 且`<200`时,discount赋值为1
     {: id="20210309203838-bne67zv"}
  9. {: id="20210309203838-xf5svcs"}判断当`totalPrice<0`时，显示输入有误
     {: id="20210309203838-2gx026z"}
  10. {: id="20210309203838-jkdyuis"}输出结果
      {: id="20210309203838-s8pt1uc"}
  {: id="20210309203838-yreijrt"}
* {: id="20210309203838-nmznycl"}开发提示：
  {: id="20210309203838-3ms0fs8"}
  键盘输入需要用到Scanner类。
  {: id="20210309203838-58pkpkj"}
  ```java
  java.util.Scanner input = new java.util.Scanner(System.in);//准备接收从键盘输入的扫描仪
  double totalPrice = input.nextDouble();//输入double值
  ```
  {: id="20210309203838-7748kv0"}
{: id="20210309203838-3tpig00"}

```java
public class Test03{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入总价格：");
		double discount = 1;
		double totalPrice = input.nextDouble();
		if(totalPrice>=500){
			discount = 0.5;
		}else if(totalPrice>=400){
			discount = 0.6;
		}else if(totalPrice>=300){
			discount = 0.7;
		}else if(discount>=200){
			discount = 0.8;
		}else if(discount >= 0){
			discount = 1;
		}else{
			System.out.println("输入有误！");
		}
		System.out.println("总价：" + totalPrice);
		System.out.println("折扣：" + discount);
		System.out.println("折扣后总价：" + totalPrice*discount);
	}
}
```
{: id="20210309203838-4a2y373"}

## 第四题
{: id="20210309203838-pudhjkw"}

语法点：变量，运算符，if...else
{: id="20210309203838-0luggew"}

案例：从键盘输入生日，判断星座
{: id="20210309203838-knsvaqg"}

![1558000803855](imgs/1558000803855.png)
{: id="20210309203838-e0ddfcl"}

* {: id="20210309203838-wqac8mc"}开发提示：
  {: id="20210309203838-ofj5tbg"}
  1. {: id="20210309203838-gjw9z0s"}各个星座的日期范围如下：
     {: id="20210309203838-guxnqvk"}
  {: id="20210309203838-xoxa678"}
{: id="20210309203838-mlk1t9d"}

![1558000604568](imgs/1558000604568.png)
{: id="20210309203838-pkbunj8"}

```java
public class Test04 {
	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入月份：");
		int month = input.nextInt();

		System.out.print("请输入日期：");
		int day = input.nextInt();

		if ((month == 1 && day >= 20) || (month == 2 && day <= 18)) {
			System.out.println("生日" + month + "月" + day + "日是水瓶座");
		} else if ((month == 2 && day >= 19) || (month == 3 && day <= 20)) {
			System.out.println("生日" + month + "月" + day + "日是双鱼座");
		}else if ((month == 3 && day >= 21) || (month == 4 && day <= 19)) {
			System.out.println("生日" + month + "月" + day + "日是白羊座");
		}else if ((month == 4 && day >= 20) || (month == 5 && day <= 20)) {
			System.out.println("生日" + month + "月" + day + "日是金牛座");
		}else if ((month == 5 && day >= 21) || (month == 6 && day <= 21)) {
			System.out.println("生日" + month + "月" + day + "日是双子座");
		}else if ((month == 6 && day >= 22) || (month == 7 && day <= 22)) {
			System.out.println("生日" + month + "月" + day + "日是巨蟹座");
		}else if ((month == 7 && day >= 23) || (month == 8 && day <= 22)) {
			System.out.println("生日" + month + "月" + day + "日是狮子座");
		}else if ((month == 8 && day >= 23) || (month == 9 && day <= 22)) {
			System.out.println("生日" + month + "月" + day + "日是处女座");
		}else if ((month == 9 && day >= 23) || (month == 10 && day <= 23)) {
			System.out.println("生日" + month + "月" + day + "日是天平座");
		}else if ((month == 10 && day >= 24) || (month == 11 && day <= 22)) {
			System.out.println("生日" + month + "月" + day + "日是天蝎座");
		}else if ((month == 11 && day >= 23) || (month == 12 && day <= 21)) {
			System.out.println("生日" + month + "月" + day + "日是射手座");
		}else if ((month == 12 && day >= 22) || (month == 1 && day <= 19)) {
			System.out.println("生日" + month + "月" + day + "日是摩羯座");
		}
	}
}
```
{: id="20210309203838-z6lkkui"}

## 第五题
{: id="20210309203838-f5ge1sv"}

语法点：变量，运算符，switch...case
{: id="20210309203838-hmodqjw"}

案例需求：编写一个程序，为一个给定的年份找出其对应的中国生肖。中国的生肖基于12年一个周期，每年用一个动物代表：rat（鼠）、ox（牛）、tiger（虎）、rabbit（兔）、dragon（龙）、snake（蛇）、
{: id="20210309203838-00ukeeb"}

​      horse（马）、sheep（羊）、monkey（候）、rooster（鸡）、dog（狗）、pig（猪）。
{: id="20210309203838-baia3sq"}

提示：2017年：鸡   2017 % 12 == 1
{: id="20210309203838-a31tzs6"}

![1558000905060](imgs/1558000905060.png)
{: id="20210309203838-iz124j9"}

```java
public class Test05 {

	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入年份：");
		int year = input.nextInt();
		
		switch(year%12){
		case 1:
			System.out.println("鸡");
			break;
		case 2:
			System.out.println("狗");
			break;
		case 3:
			System.out.println("猪");
			break;
		case 4:
			System.out.println("鼠");
			break;
		case 5:
			System.out.println("牛");
			break;
		case 6:
			System.out.println("虎");
			break;
		case 7:
			System.out.println("兔");
			break;
		case 8:
			System.out.println("龙");
			break;
		case 9:
			System.out.println("蛇");
			break;
		case 10:
			System.out.println("马");
			break;
		case 11:
			System.out.println("羊");
			break;
		case 0:
			System.out.println("猴");
			break;
		}
	}

}
```
{: id="20210309203838-580nebo"}

## 第六题
{: id="20210309203838-gdy8fmi"}

语法点：变量，运算符，if..else
{: id="20210309203838-vsh6gfz"}

案例：
{: id="20210309203838-uu5gy9m"}

![1558001161541](imgs/1558001161541.png)
{: id="20210309203838-aoe747h"}

* {: id="20210309203838-092kpbe"}开发提示：
  {: id="20210309203838-dpzongz"}
{: id="20210309203838-3v8gpg3"}

1. {: id="20210309203838-fq6jfnj"}Math.sqrt(num)：求num的平方根
   {: id="20210309203838-88ccky1"}
2. {: id="20210309203838-yvfdevm"}定义double类型变量a,b,c，并从键盘输入它们的值
   {: id="20210309203838-dz7dh88"}
   键盘输入需要用到Scanner类。
   {: id="20210309203838-j3gfuwi"}
{: id="20210309203838-gdxhkbi"}

```java
java.util.Scanner input = new java.util.Scanner(System.in);//准备接收从键盘输入的扫描仪
double totalPrice = input.nextDouble();//输入double值
```
{: id="20210309203838-l5u2mjk"}

```java
public class Test06{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("请输入方程的参数a：");
		double a = input.nextDouble();
		
		System.out.print("请输入方程的参数b：");
		double b = input.nextDouble();
		
		System.out.print("请输入方程的参数c：");
		double c = input.nextDouble();
		
		if(a!=0){
			double d = b*b - 4*a*c;
			if(d>0){
				double x1 = (-b + Math.sqrt(d))/(2*a);
				double x2 = (-b - Math.sqrt(d))/(2*a);
				System.out.println("两个解：x1 = " + x1 + ",x2 = " + x2);
			}else if(d==0){
				double x = -b/(2*a);
				System.out.println("一个解：x = " + x);
			}else{
				System.out.println("在实数范围内无解");
			}
		}else if(a==0 && b!=0){
			double x = -c/b;
			System.out.println("一个解：x = " + x);
		}else{
			System.out.println("不是方程");
		}
	}
}
```
{: id="20210309203838-gjc0vvv"}

## 第七题
{: id="20210309203838-uvaz1yk"}

语法点：变量，运算符，if和switch...case
{: id="20210309203838-mkv9b4v"}

案例：已知2019年1月1日是星期二，从键盘输入2019年的任意一天，请判断它是星期几
{: id="20210309203838-2hqrmgw"}

![1558001748751](imgs/1558001748751.png)
{: id="20210309203838-hgi8zl4"}

* {: id="20210309203838-7z3o1s0"}开发提示：
  {: id="20210309203838-sa4m40r"}
{: id="20210309203838-4fm708f"}

1. {: id="20210309203838-itbghvg"}先统计这一天是这一年的第几天days
   {: id="20210309203838-1yvxfo4"}
2. {: id="20210309203838-1k2o23w"}然后声明一个变量week，初始化为2
   {: id="20210309203838-sb9ac8p"}
3. {: id="20210309203838-pw5741w"}然后week加上days-1
   {: id="20210309203838-d5txtfm"}
4. {: id="20210309203838-q5bmjff"}然后求week与7的模数
   {: id="20210309203838-701j6b6"}
5. {: id="20210309203838-e70trc2"}然后输出结果，考虑星期天的特殊判断
   {: id="20210309203838-s029jui"}
{: id="20210309203838-bd82kdo"}

```java
public class Test07 {
	public static void main(String[] args){
		//1、从键盘分别输入年、月、日
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("月：");
		int month = input.nextInt();
		
		System.out.print("日：");
		int day = input.nextInt();
		
		//判断这一天是当年的第几天==>从1月1日开始，累加到xx月xx日这一天
		//(1)[1,month-1]个月满月天数
		//(2)第month个月的day天
		//(3)单独考虑2月份是否是29天（依据是看year是否是闰年）
		
		//2、声明一个变量days，用来存储总天数
		//int days = 0;
		//累加第month个月的day天
		//days += day;
		
		//修改上面的代码，直接把days初始化为day
		int days = day;
		
		//3、累加[1,month-1]个月满月天数
		switch(month){
			case 12:
				//累加的1-11月
				days += 30;//这个30是代表11月份的满月天数
				//这里没有break，继续往下走
			case 11:
				//累加的1-10月
				days += 31;//这个31是代表10月的满月天数
				//这里没有break，继续往下走
			case 10:
				days += 30;//9月
			case 9:
				days += 31;//8月
			case 8:
				days += 31;//7月
			case 7:
				days += 30;//6月
			case 6:
				days += 31;//5月
			case 5:
				days += 30;//4月
			case 4:
				days += 31;//3月
			case 3:
				days += 28;//2月，因为2019年的2月是28天
			case 2:
				days += 31;//1月
		}
		
		//days 里面存的是这一天是这一年的第几天
		//已知2019年1月1日是星期二
		//假设我输入的就是1月1日，那么days中就是1
		int week = 1;//2018年12月31日的星期
		week += days;
		week %= 7;
		System.out.print(month+"月" + day +"日是这一年的第"+days+"天，是星期" + (week==0?"天":week)) ;
		
	}
}	   
```
{: id="20210309203838-wk32x6s"}

# 简答题
{: id="20210309203838-gd2i1hj"}

1、switch是否能作用在byte上，是否能作用在long上，是否能作用在String上？
{: id="20210309203838-d41k258"}

```
可以作用在byte上，
不能作用在long上
可以作用在String上
```
{: id="20210309203838-lkfbhtg"}


{: id="20210309203838-5p6z6gh" type="doc"}
