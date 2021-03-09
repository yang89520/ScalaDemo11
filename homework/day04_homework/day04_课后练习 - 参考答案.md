# day04_课后练习
{: id="20210309203838-3k16u1s"}

## 第一题
{: id="20210309203838-bz9elmx"}

* {: id="20210309203838-m5o6c1m"}语法点：运算符，while，if
  {: id="20210309203838-nzfo8t5"}
* {: id="20210309203838-a5vqlx3"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-2fmx7fu"}
  ![1558008838926](imgs\\1558008838926.png)
  {: id="20210309203838-6y78c5l"}
* {: id="20210309203838-6hosa6h"}编写步骤：
  {: id="20210309203838-ecwdeei"}
  1. {: id="20210309203838-izm1pw6"}定义类 Test1
     {: id="20210309203838-ogqx1un"}
  2. {: id="20210309203838-imvqwsn"}定义 main方法
     {: id="20210309203838-44mka22"}
  3. {: id="20210309203838-mxjjk3e"}定义变量i为0,i2为10
     {: id="20210309203838-kpzinh5"}
  4. {: id="20210309203838-ysb89wu"}使用第一个while循环,当条件为`i小于5` 时,则进入循环
     {: id="20210309203838-6i3jqzn"}
  5. {: id="20210309203838-6qtr1kh"}循环内,i自增,i2自增
     {: id="20210309203838-753j3oe"}
  6. {: id="20210309203838-jrqdhmh"}循环内,使用if判断,当`i大于等于 2 ` 并且` i2小于15` 时,同时输出i和i2的值
     {: id="20210309203838-aobvcx6"}
  7. {: id="20210309203838-42wesuf"}使用第二个while循环,当条件为`i2小于20` 时,则进入循环
     {: id="20210309203838-x6f5gia"}
  8. {: id="20210309203838-j8imm4f"}循环内,i自增,i2自增
     {: id="20210309203838-kwzu3uf"}
  9. {: id="20210309203838-w7wawxi"}循环内,使用if判断,当`i大于8 ` 或者`i2小于等于18` 时,同时输出i和i2的值
     {: id="20210309203838-cwblqcz"}
  {: id="20210309203838-rg4v2kq"}
{: id="20210309203838-p75qoqc"}

```java
public class Test01 {
	public static void main(String[] args) {
		int i = 0;
		int i2 = 10;
		while(i<5){
			i++;
			i2++;
			if(i>=2 && i2<15){
				System.out.println("i:" + i + ",i2:" + i2);
			}
		}
		System.out.println("----------------------");
		while(i2<20){
			i++;
			i2++;
			if(i>8 || i2<=18){
				System.out.println("i:" + i + ",i2:" + i2);
			}
		}
	}
}

```
{: id="20210309203838-d2jpmxl"}

## 第二题
{: id="20210309203838-lyz7fbd"}

* {: id="20210309203838-pw4njo2"}语法点：方法，运算符，for，while
  {: id="20210309203838-6k3n3be"}
* {: id="20210309203838-r6ywt2e"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-06qi3pd"}
  ![1558009109555](imgs\\1558009109555.png)
  {: id="20210309203838-4eqnyr3"}
* {: id="20210309203838-cxvh5ey"}编写步骤
  {: id="20210309203838-l7zdjqx"}
{: id="20210309203838-izczte2"}

1. {: id="20210309203838-oaoecix"}定义类 Test2，定义 main方法
   {: id="20210309203838-f1qaypm"}
2. {: id="20210309203838-3wqh8t9"}main方法中,定义int类型变量 a为1
   {: id="20210309203838-vac08zh"}
3. {: id="20210309203838-v8suse4"}使用while循环,判断a<=5,进入循环.
   {: id="20210309203838-a5wl84h"}
4. {: id="20210309203838-1qtm0tq"}while循环内部,使用for循环,初始化int类型变量b为1,当b<=5时进入循环, 步进表达式b++
   {: id="20210309203838-1lpz5n5"}
5. {: id="20210309203838-5k5rlnw"}for循环内,不换行输出i并拼接" "
   {: id="20210309203838-65gtb0y"}
6. {: id="20210309203838-bl9fals"}for循环外,输出换行.
   {: id="20210309203838-k8dizrt"}
7. {: id="20210309203838-8r5cfrz"}for循环外,a自增.
   {: id="20210309203838-tpsa2bj"}
{: id="20210309203838-9x4v67i"}

```java
public class Test02 {
	public static void main(String[] args) {
		int a = 1;
		System.out.println("--------------------------");
		while(a<=5){
			for (int b = 1; b <= 5; b++) {
				System.out.print(b+" ");
			}
			System.out.println();
			a++;
		}
		System.out.println("--------------------------");
	}
}

```
{: id="20210309203838-46wx8al"}

## 第三题
{: id="20210309203838-rxnfo59"}

* {: id="20210309203838-8fs6q39"}语法点：运算符，for，if
  {: id="20210309203838-xumu8u6"}
* {: id="20210309203838-d1bx1bu"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-kpjpb05"}
  ![1558843065030](imgs/1558843065030.png)
  {: id="20210309203838-b0iwnjd"}
* {: id="20210309203838-lgnlj4e"}编写步骤
  {: id="20210309203838-90qy3dv"}
  1. {: id="20210309203838-1f5fcnf"}定义类 Test5
     {: id="20210309203838-ezb1uz8"}
  2. {: id="20210309203838-cod3hii"}定义 main方法
     {: id="20210309203838-kk7igrn"}
  3. {: id="20210309203838-nwc0cip"}定义变量jj为20,a为0,b为0
     {: id="20210309203838-9w7r16t"}
  4. {: id="20210309203838-n12aay9"}使用for循环,初始化值ii为0,当`ii<jj` 时进入循环,步进表达式为ii+=2,jj自减
     {: id="20210309203838-hxnafag"}
  5. {: id="20210309203838-qc1ub28"}循环内,使用if判断ii被3整除,ii赋值给a,并输出ii拼接"Hello"
     {: id="20210309203838-0sx2kmi"}
  6. {: id="20210309203838-mwvovba"}不被3整除,ii赋值给b,并输出ii拼接"World"
     {: id="20210309203838-3zgliwl"}
  7. {: id="20210309203838-xir3haj"}循环外,按照格式,打印a与b的乘积
     {: id="20210309203838-t4zf6zr"}
  {: id="20210309203838-rdugz4q"}
{: id="20210309203838-9zx16x3"}

```java
public class Test03 {
	public static void main(String[] args) {
		int jj = 20;
		int a = 0;
		int b = 0;
		for(int ii = 0;ii < jj;ii+=2,jj--){
			if(ii % 3 == 0){
				a = ii;
				System.out.println(ii + " Hello");
			}else{
				b = ii;
				System.out.println(ii + "  World");
			}
		}
		System.out.println("a*b=" + a + "*" + b + "=" + a*b); 
	}
}
```
{: id="20210309203838-il95pna"}

## 第四题
{: id="20210309203838-kcl3p41"}

* {: id="20210309203838-shxxpy9"}语法点：运算符，for，switch
  {: id="20210309203838-qbai7by"}
* {: id="20210309203838-iw6q0vq"}打印星座信息，效果如图所示：
  {: id="20210309203838-i2fc656"}
{: id="20210309203838-ipyni8l"}

![1558009283090](imgs\\1558009283090.png)
{: id="20210309203838-qusmvbo"}

开发提示：
{: id="20210309203838-8pkn69v"}

* {: id="20210309203838-3anzkdw"}1-12的规律数字，可以使用for循环处理
  {: id="20210309203838-f6yuy5l"}
* {: id="20210309203838-24rm3an"}根据不同的数字，匹配显示不同的文字，可以使用switch匹配
  {: id="20210309203838-v9mdhqt"}
{: id="20210309203838-g1i8oct"}

```java
public class Test04 {
	public static void main(String[] args) {
		for (int i = 1; i <= 12; i++) {
			switch(i){
			case 1:
				System.out.println( i + "：水瓶座");
				break;
			case 2:
				System.out.println( i + "：双鱼座");
				break;
			case 3:
				System.out.println( i + "：白羊座");
				break;
			case 4:
				System.out.println( i + "：金牛座");
				break;
			case 5:
				System.out.println( i + "：双子座");
				break;
			case 6:
				System.out.println( i + "：巨蟹座");
				break;
			case 7:
				System.out.println( i + "：狮子座");
				break;
			case 8:
				System.out.println( i + "：处女座");
				break;
			case 9:
				System.out.println( i + "：天平座");
				break;
			case 10:
				System.out.println( i + "：天蝎座");
				break;
			case 11:
				System.out.println( i + "：射手座");
				break;
			case 12:
				System.out.println( i + "：摩羯座");
				break;
			}
		}
	}
}

```
{: id="20210309203838-tyzwu8f"}

## 第五题
{: id="20210309203838-aje8s6p"}

语法点：运算符，for，if
{: id="20210309203838-rfpokym"}

案例需求：从键盘分别输入年、月、日，使用循环for+if实现，判断这一天是当年的第几天
{: id="20210309203838-xzdid3i"}

![1558052080046](imgs/1558052080046.png)
{: id="20210309203838-3amwdba"}

注：判断一年是否是闰年的标准：
{: id="20210309203838-mv6eji3"}

​       1）可以被4整除，但不可被100整除
{: id="20210309203838-mpd6qq5"}

​       2）可以被400整除
{: id="20210309203838-2p6yde9"}

* {: id="20210309203838-26m30r1"}开发提示：
  {: id="20210309203838-4vmpadb"}
  1. {: id="20210309203838-ofdn9ys"}循环1-month月
     {: id="20210309203838-pjwxaj3"}
  2. {: id="20210309203838-dfbrm5b"}在循环中判断该月是31天、30天、28/29天，分别累加
     {: id="20210309203838-266u1k5"}
  {: id="20210309203838-idzgihq"}
{: id="20210309203838-763l5sy"}

```java
public class Test05 {
	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);

		System.out.print("请输入年：");
		int year = input.nextInt();

		System.out.print("请输入月：");
		int month = input.nextInt();

		System.out.print("请输入日：");
		int day = input.nextInt();

		int days = day;
		for (int i = 1; i < month; i++) {
			if (i == 4 || i == 6 || i == 9 || i == 11) {
				days += 30;
			} else if (i == 2) {
				if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
					days += 29;
				} else {
					days += 28;
				}
			} else {
				days += 31;
			}
		}

		System.out.println(year + "年" + month + "月" + day + "日是这一年的第" + days + "天");
	}
}
```
{: id="20210309203838-miysad5"}

## 第六题
{: id="20210309203838-yuc9f1v"}

案例需求：假设从2000年1月1日开始三天打鱼，两天晒网，从键盘输入今天的日期年、月、日，显示今天是打鱼还是晒网？
{: id="20210309203838-7kpfemz"}

```java
public class Test06 {
	public static void main(String[] args){
		//1、从键盘分别输入年、月、日
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("年：");
		int year = input.nextInt();
		
		System.out.print("月：");
		int month = input.nextInt();
		
		System.out.print("日：");
		int day = input.nextInt();
		
		/*
		（1）先算出，这一天距离2000年1月1日是第几天
		①第month月的day天
		②第year年的[1,month-1]的满月
		③从[2000,year-1]的满年天数
		（2）用总天数%5，看余数，余数是1,2,3是打鱼，4和0是晒网
		*/
		
		int days = day;//①第month月的day天
		
		//②累加[1,month-1]的满月天数
		for(int i=1; i<month; i++){//这个i代表月份
			if(i==4 || i==6 || i==9 || i==11){
				days+=30;
			}else if(i==2){
				if(year%4==0 && year%100!=0 || year%400==0){
					days+=29;
				}else{
					days+=28;
				}
			}else{
				days+=31;
			}
		}
		
		//③从[2000,year-1]的满年天数
		for(int i=2000; i<year; i++){//这个i代表年份
			if(i%4==0 && i%100!=0 || i%400==0){
				days+=366;
			}else{
				days+=365;
			}
		}
		
		//判断
		if(days%5==1 || days%5==2 || days%5==3){
			System.out.println("打鱼");
		}else{
			System.out.println("晒网");
		}
	}
}

```
{: id="20210309203838-k2ds3d1"}

## 第七题
{: id="20210309203838-w69s8ip"}

* {: id="20210309203838-qssmw79"}打印倒三角形，效果如图所示：
  {: id="20210309203838-awsihmy"}

  ![1558009685692](imgs/1558009685692.png)
  {: id="20210309203838-rt9zzra"}
* {: id="20210309203838-xchv9di"}开发提示：
  {: id="20210309203838-9vqdvs4"}
  * {: id="20210309203838-cg3y95h"}平面图形涉及到有行有列，考虑到嵌套for循环
    {: id="20210309203838-ql99fnv"}
  * {: id="20210309203838-1jpgwaz"}一个外循环控制行，两个内循环控制输出内容
    {: id="20210309203838-gy8acv9"}
  * {: id="20210309203838-a0lwq1r"}一个内循环负责输出空格，另一个内循环输出"*"
    {: id="20210309203838-uuetqh2"}
  {: id="20210309203838-egdudhx"}
{: id="20210309203838-8qjt0cw"}

```java
public class Test07 {
	public static void main(String[] args){
		for(int i=1; i<=5; i++){//控制行数
			/*
			每一行有三件事：
			（1）打印n个空格
			（2）打印m个" *"
			（3）换行
			*/
			//（1）打印n个空格
			/*
			第1行：0个，当i=1, j应该让它第一次循环都不满足	j<i
			第2行：1个，当i=2, j运行1次，j=1
			第3行：2个，当i=3, j运行2次，j=1,2
			第4行：3个，当i=4, j运行3次，j=1,2,3
			第5行：4个，当i=5, j运行4次，j=1,2,3,4
			*/
			for(int j=1; j<i; j++){
				System.out.print(" ");
			}
			//（2）打印m个" *"
			/*
			第1行：5个，当i=1,j运行5次，j=1,2,3,4,5		j<=6-i
			第2行：4个，当i=2,j运行4次，j=1,2,3,4
			第3行：3个，当i=3,j运行3次，j=1,2,3
			第4行：2个，当i=4,j运行2次，j=1,2
			第5行：1个，当i=5,j运行1次，j=1
			*/
			for(int j=1; j<=6-i; j++){
				System.out.print(" *");
			}
			
			
			//（3）换行
			System.out.println();
		}
	}
}

```
{: id="20210309203838-dqvq0tw"}

```java
class Day04_Test07_2{
	public static void main(String[] args){
		for(int i=1; i<=5; i++){//控制行数
			/*
			每一行有三件事：
			（1）打印n个空格
			（2）打印m个" *"
			（3）换行
			*/
			//（1）打印n个空格
			/*
			第1行：0个，当i=1, j应该让它第一次循环都不满足	j<i
			第2行：1个，当i=2, j运行1次，j=1
			第3行：2个，当i=3, j运行2次，j=1,2
			第4行：3个，当i=4, j运行3次，j=1,2,3
			第5行：4个，当i=5, j运行4次，j=1,2,3,4
			*/
			for(int j=1; j<i; j++){
				System.out.print(" ");
			}
			//（2）打印m个" *"
			/*
			第1行：5个，当i=1,j运行5次，j=5,4,3,2,1  j>=i
			第2行：4个，当i=2,j运行4次，j=5,4,3,2
			第3行：3个，当i=3,j运行3次，j=5,4,3
			第4行：2个，当i=4,j运行2次，j=5,4
			第5行：1个，当i=5,j运行1次，j=5
			*/
			for(int j=5; j>=i; j--){
				System.out.print(" *");
			}
			
			
			//（3）换行
			System.out.println();
		}
	}
}
```
{: id="20210309203838-l4a1chs"}

## 第八题
{: id="20210309203838-ue5ehct"}

* {: id="20210309203838-y79acnd"}打印『X』对称图形，效果如图所示：
  {: id="20210309203838-cplvo57"}

  ![1558009720001](imgs/1558009720001.png)
  {: id="20210309203838-xt9g54j"}
* {: id="20210309203838-sygabl8"}开发提示：
  {: id="20210309203838-184zpo3"}
  * {: id="20210309203838-5ksp3w4"}平面图形涉及到有行有列，考虑到嵌套for循环
    {: id="20210309203838-iiqsv8t"}
  * {: id="20210309203838-dub2dap"}一个外循环控制行，一个内循环控制输出内容
    {: id="20210309203838-533yxuy"}
  * {: id="20210309203838-o9rs6rp"}在内循环中，根据变量的变化规律，判断输出"O"还是"*"
    {: id="20210309203838-jlmtwag"}
  {: id="20210309203838-3wtvidb"}
{: id="20210309203838-gpyzbg0"}

```java
public class Test08 {
	public static void main(String[] args){
		for(int i=1; i<=7; i++){//控制行数
			//(1)打印该行的*或o
			/*
			发现O+*的总个数是7个
			当i=1, 当j=1和j=7的时候是O，其余的是* 
			当i=2, 当j=2和j=6的时候是O，其余的是* 
			当i=3, 当j=3和j=5的时候是O，其余的是* 
			当i=4, 当j=4的时候是O，其余的是* 
			当i=5, 当j=5和j=3的时候是O，其余的是* 
			当i=6, 当j=6和j=2的时候是O，其余的是* 
			当i=7, 当j=7和j=1的时候是O，其余的是* 
			*/
			for(int j=1; j<=7; j++){
				if(i==j || i==8-j){
					System.out.print("O");
				}else{
					System.out.print("*");
				}
			}
			
			//(2)每一行的最后一件事是换行
			System.out.println();
		}
	}
}

```
{: id="20210309203838-9r7lf08"}

## 第九题
{: id="20210309203838-cxuxbko"}

* {: id="20210309203838-18bz4ao"}打印菱形
  {: id="20210309203838-f87fn3d"}

  ![1558009763069](imgs/1558009763069.png)
  {: id="20210309203838-14luxbx"}

  或
  {: id="20210309203838-r9ncxjx"}

  ![1558009783968](imgs/1558009783968.png)
  {: id="20210309203838-5cpzaen"}
* {: id="20210309203838-ehb4z84"}开发提示：
  {: id="20210309203838-sqd3ks6"}
  * {: id="20210309203838-6h1wbtl"}平面图形涉及到有行有列，考虑到嵌套for循环
    {: id="20210309203838-kh212xi"}
  * {: id="20210309203838-jq7rlt5"}一个外循环控制行，两个内循环控制输出内容
    {: id="20210309203838-xlv8wjm"}
  * {: id="20210309203838-gg7s8xp"}一个内循环负责输出空格，另一个内循环输出"*"
    {: id="20210309203838-a8rrtmh"}
  {: id="20210309203838-ran6v88"}
{: id="20210309203838-69f5nia"}

```java
public class Test09 {
	public static void main(String[] args){
		//上半部分：正的等腰三角形
		//5行
		for(int i=1; i<=5; i++){
			//(1)打印空格
			/*
			当i=1,打印4个空格，j=4,3,2,1	j>=i
			当i=2,打印3个空格，j=4,3,2
			当i=3,打印2个空格，j=4,3
			当i=4,打印1个空格，j=4
			当i=5,打印0个空格，j=4,让循环条件一次都不满足
			*/
			for(int j=4; j>=i; j--){
				System.out.print("  ");
			}
			//(2)打印*
			/*
			当i=1,打印1个,j=1					j<=2*i-1
			当i=2,打印3个,j=1,2,3,
			当i=3,打印5个,j=1,2,3,4,5
			当i=4,打印7个,j=1,2,3,4,5,6,7
			当i=5,打印9个,j=1,2,3,4,5,6,7,8,9
			*/
			for(int j=1; j<=2*i-1; j++){
				System.out.print("* ");
			}
			//(3)换行
			System.out.println();
		}
		
		
		//下半部分：倒立的等腰三角形
		//4行
		for(int i=1; i<=4; i++){
			//(1)打印空格
			/*
			当i=1,1个空格,j=1		j<=i
			当i=2,2个空格,j=1,2	
			当i=3,3个空格,j=1,2,3
			当i=4,4个空格,j=1,2,3,4
			*/
			for(int j=1; j<=i; j++){
				System.out.print("  ");
			}
			//(2)打印*
			/*
			当i=1,7个*，j=1,2,3,4,5,6,7  j<=9-2*i;
			当i=2,5个*，j=1,2,3,4,5
			当i=3,3个*，j=1,2,3
			当i=4,1个*，j=1
			*/
			for(int j=1; j<=9-2*i; j++){
				System.out.print("* ");
			}
			//(3)换行
			System.out.println();
		}
	}
}

```
{: id="20210309203838-1jilbt1"}

```java
public class Test09_02 {
	public static void main(String[] args){
		//上半部分：正的等腰三角形
		//5行
		for(int i=1; i<=5; i++){
			//(1)打印空格
			/*
			当i=1,打印4个空格，j=4,3,2,1	j>=i
			当i=2,打印3个空格，j=4,3,2
			当i=3,打印2个空格，j=4,3
			当i=4,打印1个空格，j=4
			当i=5,打印0个空格，j=4,让循环条件一次都不满足
			*/
			for(int j=4; j>=i; j--){
				System.out.print("  ");
			}
			//(2)打印*
			/*
			当i=1,打印1个,j=1					j<=2*i-1
			当i=2,打印3个,j=1,2,3,
			当i=3,打印5个,j=1,2,3,4,5
			当i=4,打印7个,j=1,2,3,4,5,6,7
			当i=5,打印9个,j=1,2,3,4,5,6,7,8,9
			*/
			for(int j=1; j<=2*i-1; j++){
				//不是全部打印*
				if(j==1 || j==2*i-1){
					System.out.print("* ");
				}else{
					System.out.print("  ");
				}
			}
			//(3)换行
			System.out.println();
		}
		
		
		//下半部分：倒立的等腰三角形
		//4行
		for(int i=1; i<=4; i++){
			//(1)打印空格
			/*
			当i=1,1个空格,j=1		j<=i
			当i=2,2个空格,j=1,2	
			当i=3,3个空格,j=1,2,3
			当i=4,4个空格,j=1,2,3,4
			*/
			for(int j=1; j<=i; j++){
				System.out.print("  ");
			}
			//(2)打印*
			/*
			当i=1,7个*，j=1,2,3,4,5,6,7  j<=9-2*i;
			当i=2,5个*，j=1,2,3,4,5
			当i=3,3个*，j=1,2,3
			当i=4,1个*，j=1
			*/
			for(int j=1; j<=9-2*i; j++){
				//不是全部打印*
				if(j==1 || j==9-2*i){
					System.out.print("* ");
				}else{
					System.out.print("  ");
				}
			}
			//(3)换行
			System.out.println();
		}
	}
}

```
{: id="20210309203838-ywqyepg"}


{: id="20210309203838-mwrxyow" type="doc"}
