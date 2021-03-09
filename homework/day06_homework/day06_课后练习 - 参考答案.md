# day06_课后练习
{: id="20210309203838-usxhb5h"}

# 成员变量基础练习
{: id="20210309203838-xq3ge7g"}

## 第1题
{: id="20210309203838-627zzqy"}

案例：
{: id="20210309203838-apxk0aq"}

​	声明员工类Employee，包含属性：编号、姓名、年龄、薪资，
{: id="20210309203838-79nc7pd"}

​	声明Test01测试类，并在main方法中，创建2个员工对象，并为属性赋值，并打印两个员工的信息。
{: id="20210309203838-rlgoi4e"}

![1558849379468](imgs/1558849379468.png)
{: id="20210309203838-zl0w3kz"}

```java
public class Employee {
	int id;
	String name;
	int age;
	double salary;
}
```
{: id="20210309203838-gewk10k"}

```java
public class Test01 {
	public static void main(String[] args) {
		Employee emp1 = new Employee();
		emp1.id = 1;
		emp1.name = "张三";
		emp1.age = 23;
		emp1.salary = 10000;
		
		Employee emp2 = new Employee();
		emp2.id = 2;
		emp2.name = "李四";
		emp2.age = 22;
		emp2.salary = 11000;
		
		System.out.println("员工1的编号：" + emp1.id +"，姓名：" + emp1.name + "，年龄：" + emp1.age + "，薪资：" + emp1.salary);
		System.out.println("员工2的编号：" + emp2.id +"，姓名：" + emp2.name + "，年龄：" + emp2.age + "，薪资：" + emp2.salary);
	}
}
```
{: id="20210309203838-kint76i"}

## 第2题
{: id="20210309203838-7n2sft4"}

案例：
{: id="20210309203838-ng4cspb"}

​	声明一个日期类MyDate，包含属性：年、月、日
{: id="20210309203838-2igkgcd"}

​	声明一个Test02测试类，并在main方法中，创建3个日期对象，一个是你的出生日期，一个是来尚硅谷的日期，一个是毕业的日期，并打印显示
{: id="20210309203838-cleoqbx"}

```java
public class MyDate {
	int year;
	int month;
	int day;
}

```
{: id="20210309203838-3twrrjb"}

```java
public class Test02 {
	public static void main(String[] args) {
		MyDate bir = new MyDate();
		bir.year = 1995;
		bir.month = 5;
		bir.day = 5;
		System.out.println("生日：" + bir.year + "年" + bir.month + "月" + bir.day + "日");
		
		MyDate come = new MyDate();
		come.year = 2019;
		come.month = 5;
		come.day = 12;
		System.out.println("来尚硅谷：" + come.year + "年" + come.month + "月" + come.day + "日");
		
		MyDate go = new MyDate();
		go.year = 2019;
		go.month = 10;
		go.day = 25;
		System.out.println("毕业：" + go.year + "年" + go.month + "月" + go.day + "日");
	}
}
```
{: id="20210309203838-8sarqpn"}

## 第3题
{: id="20210309203838-7tdlwnn"}

案例：
{: id="20210309203838-z7shf92"}

​	声明公民类Citizen，包含属性：姓名，生日，身份证号，其中姓名是String类型，生日是MyDate类型，身份证号也是String类型。
{: id="20210309203838-dnls7wc"}

​	声明Test03测试类，在main方法中创建你们家庭成员的几个对象，并打印信息。
{: id="20210309203838-mp094tw"}

```java
public class Test03 {
	public static void main(String[] args){
		//1、创建爸爸的对象
		Citizen baba = new Citizen();
		baba.name = "小头爸爸";
		baba.cardId = "1111111";
		//左边的birthday是一个引用数据类型的变量，右边就需要赋值一个对象
		baba.birthday = new MyDate();
		//baba.birthday是对象名
		baba.birthday.year = 1967;
		baba.birthday.month = 5;
		baba.birthday.day = 2;
		
		//2、创建妈妈的对象
		Citizen mama = new Citizen();
		mama.name = "围裙妈妈";
		mama.cardId = "222222";
		
		MyDate bir = new MyDate();
		bir.year = 1970;
		bir.month = 6;
		bir.day = 1;
		
		mama.birthday = bir;
		
		//3、创建自己的对象
		Citizen self = new Citizen();
		self.name = "大头儿子";
		self.cardId = "3333333";
		
		MyDate date = new MyDate();
		date.year = 1995;
		date.month = 6;
		date.day = 12;
		
		self.birthday = date;
		
		System.out.println("爸爸的姓名：" + baba.name + "，身份证号：" + baba.cardId + "，生日：" + baba.birthday.year+"年" + baba.birthday.month + "月" + baba.birthday.day+"日");
		System.out.println("妈妈的姓名：" + mama.name + "，身份证号：" + mama.cardId + "，生日：" + mama.birthday.year+"年" + mama.birthday.month + "月" + mama.birthday.day+"日");
		System.out.println("我的姓名：" + self.name + "，身份证号：" + self.cardId + "，生日：" + self.birthday.year+"年" + self.birthday.month + "月" + mama.birthday.day+"日");
	}
}
```
{: id="20210309203838-hqqv4rw"}

# 成员方法基础练习
{: id="20210309203838-jvejz6s"}

## 第4题：
{: id="20210309203838-p2v9b1z"}

案例：
{: id="20210309203838-q5rr4sc"}

​	声明一个日期类MyDate，包含属性：年、月、日，并在MyDate类中声明几个方法：
{: id="20210309203838-yqru8bw"}

1、boolean isLeapYear()：判断当前日期的是闰年吗？
{: id="20210309203838-4mzec4s"}

2、void set(int y, int m, int d)：修改年，月，日为新日期
{: id="20210309203838-izqc92p"}

3、void puls(int years, int months, int days)：加上years年，months月，days天后的日期
{: id="20210309203838-v8gni2k"}

​	并在测试类Test04的main方法中创建对象，并调用测试
{: id="20210309203838-cmuuk3n"}

```java
public class MyDate {
	int year;
	int month;
	int day;
	
	boolean isLeapYear(){
		return year%4==0 && year%100!=0 || year%400==0;
	}
	
	void set(int y, int m, int d){
		year = y;
		month = m;
		day = d;
	}
	
	void puls(int years, int months,int days){
		day += days;
		month += months;
		year += years;
		while(month>12){
			month-=12;
			year++;
		}
		while(true){
			if(month==1 || month==3 || month==5 || month==7 || month==8 || month==10){
				if(day>31){
					day -= 31;
					month++;
				}else{
					break;
				}
			}else if(month==4 || month==6 || month==9 || month==11){
				if(day>30){
					day -= 30;
					month++;
				}else{
					break;
				}
			}else if(month==2){
				if(year%4==0 && year%100!=0 || year%400==0){
					if(day>29){
						day -= 29;
						month++;
					}else{
						break;
					}
				}else{
					if(day>28){
						day-=28;
						month++;
					}else{
						break;
					}
				}
			}else if(month == 12){
				if(day>31){
					day-=31;
					month=1;
					year++;
				}else{
					break;
				}
			}
		}
	}
}

```
{: id="20210309203838-1u8094d"}

```java
public class Test04 {
	public static void main(String[] args) {
		MyDate my = new MyDate();
		my.set(2019, 5, 13);
		
		System.out.println(my.year + "年" + my.month + "月" + my.day + "日");
		System.out.println("是闰年吗？" + my.isLeapYear());
		
		my.puls(1, 70, 70);
		System.out.println("再加1年70个月70天之后的日期是：");
		System.out.println(my.year + "年" + my.month + "月" + my.day + "日");
	}
}
```
{: id="20210309203838-vothm0q"}

## 第5题：
{: id="20210309203838-3keyuyk"}

案例：
{: id="20210309203838-vud4ou9"}

​	声明一个三角形类Triangle，包含属性：a,b,c，表示三条边，包含几个方法：
{: id="20210309203838-8ntrphs"}

1、boolean  isRightTriangle()：判断是否是一个直角三角形
{: id="20210309203838-9ai1g1b"}

2、boolean isIsoscelesTriangle()：判断是否是一个等腰三角形
{: id="20210309203838-0nijsvi"}

3、boolean isEquilateralTriangle()：判断是否是一个等边三角形
{: id="20210309203838-ho1v16f"}

4、double getArea()：根据三条边，用海伦公式求面积
{: id="20210309203838-on1gciy"}

5、double getLength()：求周长
{: id="20210309203838-26m6zjx"}

​	并在测试类Test05的main方法中调用测试
{: id="20210309203838-gw4jd0v"}

```java
public class Triangle {
	double a;
	double b;
	double c;

	// 判断是否是一个直角三角形
	boolean isRightTriangle() {
		// 判断值合法
		if (a > 0 && b > 0 && c > 0) {
			// 判断是否是三角形
			if (a + b > c && a + c > b && b + c > a) {
				if (a * a + b * b == c * c || b * b + c * c == a * a || a * a + c * c == b * b) {
					return true;
				}
			}
		}
		return false;
	}

	boolean isIsoscelesTriangle() {
		// 判断值合法
		if (a > 0 && b > 0 && c > 0) {
			// 判断是否是三角形
			if (a + b > c && a + c > b && b + c > a) {
				// 判断是否是等腰三角形
				if (a == b || b == c || a == c) {
					return true;
				}
			}
		}
		return false;
	}

	boolean isEquilateralTriangle() {
		// 判断值合法
		if (a > 0 && b > 0 && c > 0) {
			// 判断是否是三角形
			if (a + b > c && a + c > b && b + c > a) {
				// 判断是否是等边三角形
				if (a == b && b == c) {
					return true;
				}
			}
		}
		return false;
	}

	double getArea() {
		// 判断值合法
		if (a > 0 && b > 0 && c > 0) {
			// 判断是否是三角形
			if (a + b > c && a + c > b && b + c > a) {
				double p = (a + b + c) / 2;
				return Math.sqrt(p * (p - a) * (p - b) * (p - c));
			}
		}
		return 0;
	}

	double getLength() {
		// 判断值合法
		if (a > 0 && b > 0 && c > 0) {
			// 判断是否是三角形
			if (a + b > c && a + c > b && b + c > a) {
				return a + b + c;
			}
		}
		return 0;
	}
}

```
{: id="20210309203838-r06z7k2"}

```java
public class Test05 {
	public static void main(String[] args) {
		Triangle t = new Triangle();
		t.a = 3;
		t.b = 4;
		t.c = 5;
		
		System.out.println("是否是直接三角形：" + t.isRightTriangle());
		System.out.println("是否是等腰三角形：" + t.isIsoscelesTriangle());
		System.out.println("是否是等边三角形：" + t.isEquilateralTriangle());
		System.out.println("三角形的面积：" + t.getArea());
		System.out.println("三角形的周长：" + t.getLength());
	}
}
```
{: id="20210309203838-bto5eea"}

## 第6题：
{: id="20210309203838-gcid7fe"}

案例：
{: id="20210309203838-tatppxa"}

​	声明一个数学计算工具类MathTools，包含如下方法：
{: id="20210309203838-8h7bpy1"}

1、int add(int a, int b)：求a+b
{: id="20210309203838-k2srsr6"}

2、int subtract(int a,int b)：求a-b
{: id="20210309203838-d6upzre"}

3、int mutiply(int a, int b)：求a*b
{: id="20210309203838-d44jpmg"}

4、int divide(int a, int b)：求a/b
{: id="20210309203838-6l4zayy"}

5、int remainder(int a, int b)：求a%b
{: id="20210309203838-b63ge6o"}

6、int max(int a, int b)：求a和b中的最大值
{: id="20210309203838-s14khsc"}

7、int min(int a, int b)：求a和b中的最小值
{: id="20210309203838-kbhtik8"}

8、boolean equals(int a, int b)：判断a和b是否相等
{: id="20210309203838-hk9rd85"}

9、boolean isEven(int a)：判断a是否是偶数
{: id="20210309203838-5h1is0f"}

10、boolean isPrimeNumer(int a)：判断a是否是素数
{: id="20210309203838-hobftin"}

11、int round(double d)：返回d的四舍五入后的整数值
{: id="20210309203838-jm7ggbc"}

​	声明一个Test06测试类，并在main方法中调用测试
{: id="20210309203838-syzzoj1"}

```java
public class MathTools {
	static int add(int a, int b) {
		return a + b;
	}

	static int subtract(int a, int b) {
		return a - b;
	}

	static int mutiply(int a, int b) {
		return a * b;
	}

	static int divide(int a, int b) {
		return a / b;
	}

	static int remainder(int a, int b) {
		return a % b;
	}

	static int max(int a, int b) {
		return a > b ? a : b;
	}

	static int min(int a, int b) {
		return a < b ? a : b;
	}

	static boolean equals(int a, int b) {
		return a == b;
	}

	static boolean isEven(int a) {
		return a % 2 == 0;
	}
	
	static boolean isPrimeNumber(int a){
		for (int i = 2; i < a; i++) {
			if(a%i == 0){
				return false;
			}
		}
		return true;
	}
	
	static int round(double d){
		return (int)(d + 0.5);
	}
}

```
{: id="20210309203838-843fx3s"}

```java

public class Test06 {
	public static void main(String[] args) {
		int a = 5;
		int b = 3;
		System.out.println(a + "+" + b  + "=" + MathTools.add(a,b));
		System.out.println(a + "-" + b  + "=" + MathTools.subtract(a,b));
		System.out.println(a + "*" + b  + "=" + MathTools.mutiply(a,b));
		System.out.println(a + "/" + b  + "=" + MathTools.divide(a,b));
		System.out.println(a + "%" + b  + "=" + MathTools.remainder(a,b));
		System.out.println(a + "," + b + "的最大值：" + MathTools.max(a, b));
		System.out.println(a + "," + b + "的最小值：" + MathTools.min(a, b));
		System.out.println(a + "==" + b + "？" + MathTools.equals(a,b));
		System.out.println(a + "是偶数？" + MathTools.isEven(a));
		System.out.println(a + "是素数？" + MathTools.isPrimeNumber(a));
		System.out.println("5.4四舍五入的结果：" + MathTools.round(5.4));
		System.out.println("5.6四舍五入的结果：" + MathTools.round(5.6));
	}
}
```
{: id="20210309203838-ymnwox6"}

## 第7题：
{: id="20210309203838-mozy3fy"}

案例：
{: id="20210309203838-31opn83"}

​	声明一个数组管理工具类MyArrays，包含如下方法：
{: id="20210309203838-gl8hmd2"}

1、void sort(int[] arr)：可以为任意一维整型数组arr实现从小到大排序
{: id="20210309203838-d3z8rea"}

2、int indexOf(int[] arr, int value)：可以在任意一维整型数组arr中查找value值的下标，如果不存在返回-1
{: id="20210309203838-nuz6wxj"}

3、int[] copy(int[] arr, int len)：可以实现从任意一维数组arr中复制一个新数组返回，新数组的长度为len，从arr[0]开始复制
{: id="20210309203838-qu79zbc"}

4、void print(int[] arr)：可以打印数组的元素，效果：[1,2,3,4,5]
{: id="20210309203838-d7o45vn"}

​	声明一个Test07测试类，并在main方法中调用测试
{: id="20210309203838-6lthkfs"}

```java
public class MyArrays {
	static void sort(int[] arr) {
		for (int i = 1; i < arr.length; i++) {
			for (int j = 0; j < arr.length - i; j++) {
				if (arr[j] > arr[j + 1]) {
					int temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}
	}

	static int indexOf(int[] arr, int value) {
		for (int i = 0; i < arr.length; i++) {
			if (value == arr[i]) {
				return i;
			}
		}
		return -1;
	}

	static int[] copy(int[] arr, int len) {
		// (1)创建新数组
		int[] newArr = new int[len];

		// (2)复制元素
		// [i]既不能超过旧数组下标范围，也不能超过新数组下标范围
		for (int i = 0; i < newArr.length && i < arr.length; i++) {
			newArr[i] = arr[i];
		}
		// (3)返回新数组
		return newArr;
	}
	
	static void print(int[] arr){
		System.out.print("[");
		for (int i = 0; i < arr.length; i++) {
			if(i==0){
				System.out.print(arr[i]);
			}else{
				System.out.print("," + arr[i]);
			}
		}
		System.out.println("]");
	}
}

```
{: id="20210309203838-w7n7rjb"}

```java
public class Test07 {
	public static void main(String[] args) {		
		int[] all = {4,5,2,6,1};
		System.out.println("排序前：");
		MyArrays.print(all);
		
		MyArrays.sort(all);
		System.out.println("排序后：");
		MyArrays.print(all);
		
		
		int index = MyArrays.indexOf(all, 4);
		System.out.println("4在数组的下标是：" + index);
		
		System.out.println("新数组：");
		int[] copyArr = MyArrays.copy(all, 10);
		MyArrays.print(copyArr);
	}
}
```
{: id="20210309203838-wv2wp07"}

## 第8题：
{: id="20210309203838-e8ehhrw"}

案例：
{: id="20210309203838-9df7er6"}

​	声明一个常识工具类CommonsTools，包含如下方法：
{: id="20210309203838-brtyool"}

1、String getWeekName(int week)：根据星期值，返回对应的英语单词
{: id="20210309203838-5dbm5no"}

2、String getMonthName(int month)：根据月份值，返回对应的英语单词
{: id="20210309203838-p41o9d2"}

3、int getTotalDaysOfMonth(int year, int month)：返回某年某月的总天数
{: id="20210309203838-9nsme2m"}

4、int getTotalDaysOfYear(int year)：获取某年的总天数
{: id="20210309203838-bleydja"}

5、boolean isLeapYear(int year)：判断某年是否是闰年
{: id="20210309203838-xxve0e2"}

​	声明一个Test08测试类，并在main方法中调用测试
{: id="20210309203838-z5c8cni"}

```java
public class CommonsTools {
	static String getWeekName(int week){
		switch(week){
		case 1:
			return "Monday";
		case 2:
			return "Tuesday";
		case 3:
			return "Wednesday";
		case 4:
			return "Thursday";
		case 5:
			return "Friday";
		case 6:
			return "Saturday";
		case 7:
			return "Sunday";
		}
		return "";
	}
	
	static String getMonthName(int month){
		String[] all = {"January","February","March","April","May","June","July","August","September","October","November","December"};
		if(month >= 1 && month <= 12){
			return all[month-1];
		}
		return "";
	}
	
	static int getTotalDaysOfMonth(int year, int month){
		int[] days = {31,28,31,30,31,30,31,31,30,31,30,31};
		if(isLeapYear(year)){
			days[1]++;//闰年2月29天
		}
		if(month >= 1 && month <= 12){
			return days[month-1];
		}
		return 0;
	}
	
	static int getTotalDaysOfYear(int year){
		if(isLeapYear(year)){
			return 366;
		}
		return 365;
	}
	
	static boolean isLeapYear(int year){
		return year%4==0 && year%100!=0 || year%400==0;
	}
}

```
{: id="20210309203838-r7u2lfw"}

```java
public class Test08 {
	public static void main(String[] args) {
		System.out.println("3月：" + CommonsTools.getMonthName(3));
		System.out.println("周三：" + CommonsTools.getWeekName(3));
		System.out.println("2019-2的总天数：" + CommonsTools.getTotalDaysOfMonth(2019, 2));
		System.out.println("2019年是否是闰年？" + CommonsTools.isLeapYear(2019) );
		System.out.println("2019年的总天数：" + CommonsTools.getTotalDaysOfYear(2019));
	}
}
```
{: id="20210309203838-xcod5r4"}


{: id="20210309203838-ugjtmjt" type="doc"}
