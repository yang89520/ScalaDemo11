# day07_课后练习
{: id="20210309203838-g9cup02"}

# 基础练习
{: id="20210309203838-hlm0gy1"}

## 第1题
{: id="20210309203838-tddsqt1"}

知识点：可变参数
{: id="20210309203838-91pixsa"}

案例：
{: id="20210309203838-inl28pm"}

​	在Count类中，声明如下方法：
{: id="20210309203838-sarr1uh"}

1、public long  sum(int...  nums)：求0~n个整数的累加和，如果没有传参，就返回0
{: id="20210309203838-sopj95k"}

2、public int max(int a, int... others)：求1~n个整数中的最大值
{: id="20210309203838-kfnf30b"}

3、public String concat(String...  strings)：求0~n个字符串的拼接结果
{: id="20210309203838-h7dcm5z"}

4、public boolean isEven(int... nums)：判断0~n个整数是否都是偶数，如果都是偶数，返回true，否则返回false
{: id="20210309203838-bbjdb74"}

​	声明一个Test01测试类，并在main方法中调用测试
{: id="20210309203838-mz79str"}

```java
public class Count{
	public long sum(int...  nums){
		long sum = 0;
		for (int i = 0; i < nums.length; i++) {
			sum += nums[i];
		}
		return sum;
	}
	
	public int max(int a, int... others){
		int max = a;
		for (int i = 0; i < others.length; i++) {
			if(others[i] > max){
				max = others[i];
			}
		}
		return max;
	}
	
	public String concat(String...  strings){
		String result = "";
		for (int i = 0; i < strings.length; i++) {
			result += strings[i];
		}
		return result;
	}
	
	public boolean isEven(int... nums){
		for (int i = 0; i < nums.length; i++) {
			if(nums[i]%2 !=0){
				return false;
			}
		}
		return true;
	}
}
```
{: id="20210309203838-b2uq43q"}

```java
public class Test01 {
	public static void main(String[] args) {
		Count c = new Count();
		System.out.println("1,2,3,4,5的总和：" + c.sum(1,2,3,4,5));
		System.out.println("3,4,2,1的最大值是：" + c.max(3,4,2,1));
		System.out.println("尚，硅，谷，好拼接的结果：" + c.concat("尚","硅","谷","好"));
		System.out.println("2,4,6,8是否都是偶数：" + c.isEven(2,4,6,8));
	}
}

```
{: id="20210309203838-meejsum"}

## 第1题
{: id="20210309203838-je5ci7s"}

知识点：方法的声明与调用、方法的重载
{: id="20210309203838-9m91oej"}

案例：
{: id="20210309203838-a6ld3g8"}

​	声明一个图形工具类GraphicTools，包含如下方法：
{: id="20210309203838-vqf4y5z"}

1、void printRectangle()：该方法打印5行5列*矩形
{: id="20210309203838-9ifpqa9"}

2、void printRectangle(int line, int column, String sign)：该方法打印line行colomn列由sign组成的矩形
{: id="20210309203838-223gq8u"}

3、double getTriangleArea(double base, double height)：根据底边和底边对应的高求三角形面积
{: id="20210309203838-a2d7da2"}

4、double getTriangleArea(double a, double b, double c)：根据三角形的三条边求三角形面积，如果a,b,c不能组成三角形，打印不能组成三角形，并返回0.0
{: id="20210309203838-bos0h35"}

​	声明Test02测试类，并在main方法中调用测试
{: id="20210309203838-qn9k5iq"}

```java
public class GraphicTools {
	void printRectangle() {
		for (int i = 1; i <= 5; i++) {
			for (int j = 1; j <= 5; j++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}

	void printRectangle(int line, int column, String sign) {
		for (int i = 1; i <= line; i++) {
			for (int j = 1; j <= column; j++) {
				System.out.print(sign);
			}
			System.out.println();
		}
	}

	double getTriangleArea(double base, double height) {
		return base * height / 2;
	}

	double getTriangleArea(double a, double b, double c) {
		if(a>0 && b>0 && c>0 && a+b>c && a+c>b && b+c >a){
			double p = (a + b + c) / 2;
			return Math.sqrt(p * (p - a) * (p - b) * (p - c));
		}else{
			System.out.println(a +"," + b +"," + c + "不能构成三角形");
			return 0;
		}
	}
}

```
{: id="20210309203838-znp65b9"}

```java
public class Test02 {
	public static void main(String[] args) {
		GraphicTools tools = new GraphicTools();

		tools.printRectangle();
		System.out.println("--------------------------");

		tools.printRectangle(5, 10, "#");
		System.out.println("--------------------------");

		System.out.println("底边为3，高为4的三角形面积：" + tools.getTriangleArea(3, 4));
		System.out.println("边为3，4，5的三角形面积：" + tools.getTriangleArea(3, 4, 5));
	}
}
```
{: id="20210309203838-9q00q4f"}

## 第3题
{: id="20210309203838-tjef2y7"}

知识点：方法的重载
{: id="20210309203838-fmi8mbi"}

案例：
{: id="20210309203838-hdt7d6c"}

​	声明一个数组工具类MyArrays，包含如下方法：
{: id="20210309203838-bero2mp"}

1、int  binarySearch(int[]  arr,  int  value)：使用二分查找法在arr数组中查找value的下标，如果value不存在，就返回-1，如果数组arr不是有序的，结果将不一定正确
{: id="20210309203838-mrdfy8d"}

2、int  binarySearch(char[]  arr,  char  value)：使用二分查找法在arr数组中查找value的下标，如果value不存在，就返回-1，如果数组arr不是有序的，结果将不一定正确
{: id="20210309203838-k7wpx63"}

3、int  binarySearch(double[]  arr,  double  value)：使用二分查找法在arr数组中查找value的下标，如果value不存在，就返回-1，如果数组arr不是有序的，结果将不一定正确
{: id="20210309203838-r9msngj"}

4、int[]  copy(int[] arr , int length)：从指定的arr数组的arr[0]开始复制得到一个新数组，新数组的长度为length。
{: id="20210309203838-llf9x2b"}

5、double[]  copy(double[] arr , int length)：从指定的arr数组的arr[0]开始复制得到一个新数组，新数组的长度为length。
{: id="20210309203838-o6bp1p6"}

6、char[]  copy(char[] arr , int length)：从指定的arr数组的arr[0]开始复制得到一个新数组，新数组的长度为length。
{: id="20210309203838-qe8pc6j"}

7、void sort(int[] arr)：可以给arr数组从小到大排序，用冒泡排序实现
{: id="20210309203838-ws1cbuh"}

8、void sort(char[] arr)：可以给arr数组从小到大排序，用冒泡排序实现
{: id="20210309203838-uxko8lb"}

9、void sort(double[] arr)：可以给arr数组从小到大排序，用冒泡排序实现
{: id="20210309203838-y5s7zlc"}

​	声明Test03测试类，并在main方法中调用测试
{: id="20210309203838-jgssk45"}

```java
public class MyArrays {
	public int binarySearch(int[] arr, int value) {
		int left = 0;
		int right = arr.length - 1;
		int mid = (left + right) / 2;

		while (left <= right) {
			if (arr[mid] == value) {
				return mid;
			} else if (value > arr[mid]) {
				left = mid + 1;
			} else if (value < arr[mid]) {
				right = mid - 1;
			}
			mid = (left + right) / 2;
		}
		return -1;
	}
	
	public int binarySearch(char[] arr, int value) {
		int left = 0;
		int right = arr.length - 1;
		int mid = (left + right) / 2;

		while (left <= right) {
			if (arr[mid] == value) {
				return mid;
			} else if (value > arr[mid]) {
				left = mid + 1;
			} else if (value < arr[mid]) {
				right = mid - 1;
			}
			mid = (left + right) / 2;
		}
		return -1;
	}
	
	public int binarySearch(double[] arr, int value) {
		int left = 0;
		int right = arr.length - 1;
		int mid = (left + right) / 2;

		while (left <= right) {
			if (arr[mid] == value) {
				return mid;
			} else if (value > arr[mid]) {
				left = mid + 1;
			} else if (value < arr[mid]) {
				right = mid - 1;
			}
			mid = (left + right) / 2;
		}
		return -1;
	}

	public int[] copy(int[] arr, int length) {
		// (1)创建新数组
		int[] newArr = new int[length];

		// (2)复制元素
		for (int i = 0; i < arr.length && i < newArr.length; i++) {
			newArr[i] = arr[i];
		}

		return newArr;
	}
	public double[] copy(double[] arr, int length) {
		// (1)创建新数组
		double[] newArr = new double[length];

		// (2)复制元素
		for (int i = 0; i < arr.length && i < newArr.length; i++) {
			newArr[i] = arr[i];
		}

		return newArr;
	}
	public char[] copy(char[] arr, int length) {
		// (1)创建新数组
		char[] newArr = new char[length];

		// (2)复制元素
		for (int i = 0; i < arr.length && i < newArr.length; i++) {
			newArr[i] = arr[i];
		}

		return newArr;
	}
	

	public void sort(int[] arr) {
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
	public void sort(double[] arr) {
		for (int i = 1; i < arr.length; i++) {
			for (int j = 0; j < arr.length - i; j++) {
				if (arr[j] > arr[j + 1]) {
					double temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}
	}
	public void sort(char[] arr) {
		for (int i = 1; i < arr.length; i++) {
			for (int j = 0; j < arr.length - i; j++) {
				if (arr[j] > arr[j + 1]) {
					char temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}
	}
	
	public void print(int[] arr){
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
	public void print(double[] arr){
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
	public void print(char[] arr){
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
{: id="20210309203838-e7m3iub"}

```java
public class Test03 {

	public static void main(String[] args) {
		int[] arr = {3,4,2,7,1};
		
		MyArrays my = new MyArrays();
		my.print(arr);
		System.out.println("1在数组中的下标：" + my.binarySearch(arr, 1));//结果错误，因为数组无序
		
		my.sort(arr);
		my.print(arr);
		System.out.println("1在数组中的下标：" + my.binarySearch(arr, 1));
		
		my.print(my.copy(arr, 10));
	}

}
```
{: id="20210309203838-gv1b9n0"}

## 第4题
{: id="20210309203838-lmxe9ej"}

知识点：方法的参数传递机制
{: id="20210309203838-ubb9blr"}

案例：
{: id="20210309203838-lr5u6y1"}

​	声明圆Circle类，包含radius属性（本题属性不私有化）
{: id="20210309203838-4b0k7j3"}

​	在PassParamDemo类中，声明如下方法，并体会方法的参数传递机制：
{: id="20210309203838-em7caut"}

1、public void  doubleNumber(int num)：尝试将num变为原来的2倍大，看是否可以将给num赋值的实参变量值也扩大2倍，如果不能，请画图说明为什么？
{: id="20210309203838-sh7q875"}

2、public void toUpperCase(char letter)：尝试将letter的小写字母转为大写字母，看是否可以将给letter赋值的实参变量值也转为大写，如果不能，请画图说明为什么？
{: id="20210309203838-kqr0aom"}

3、public void expandCircle(Circle  c，double times)：尝试将Circle的c对象的半径扩大为原来的times倍，看是否可以将给c赋值的实参对象的半径也扩大times倍，如果可以，请画图说明为什么？
{: id="20210309203838-eg6agyc"}

4、public void sort(int[] arr)：尝试对arr数组实现从小到大排序，看是否可以将给arr赋值的实参数组也排序，如果可以，请画图说明为什么？
{: id="20210309203838-zs2b9pb"}

​	在Test04测试类的main()方法中调用测试
{: id="20210309203838-53ppsyf"}

```java
public class Circle {
	double radius;
}
```
{: id="20210309203838-lmg3k4a"}

```java
public class PassParamDemo {
	public void doubleNumber(int x) {
		x *= 2;
	}

	public void toUpperCase(char letter) {
		letter = (char) (letter - 32);
	}

	public void expandCircle(Circle c, double times) {
		c.radius *= times;
	}

	public void sort(int[] arr) {
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

}

```
{: id="20210309203838-pjpyzd1"}

```java
public class Test04 {
	public static void main(String[] args){
		PassParamDemo p = new PassParamDemo();
		
		int x = 1;
		p.doubleNumber(x);
		System.out.println("x = " + x);
		
		char letter = 'a';
		p.toUpperCase(letter);
		System.out.println(letter);
		
		Circle c = new Circle();
		c.radius = 1.0;
		
		p.expandCircle(c, 5);
		System.out.println("半径：" + c.radius);
		
		int[] arr = {3,4,2,7,1};
		p.sort(arr);
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + " ");
		}
		System.out.println();
	}
}
```
{: id="20210309203838-dmnerjd"}

## 第5题
{: id="20210309203838-5w64b0e"}

知识点：对象数组
{: id="20210309203838-kei5hck"}

案例：
{: id="20210309203838-dbvy89o"}

​	1、声明一个Employee员工类，
{: id="20210309203838-2fahjix"}

​		包含属性：编号(id)、姓名(name)、薪资(salary)、年龄(age)，此时属性不私有化
{: id="20210309203838-uf37zrw"}

​		包含方法：
{: id="20210309203838-sczmgrm"}

​		（1）void printInfo()：可以打印员工的详细信息
{: id="20210309203838-o60vvas"}

​		（2）void setInfo(int  i, String n, double s, int a)：可以同时给id,name,salary,age赋值
{: id="20210309203838-5vv3g86"}

​	2、声明一个EmployeeManager类，包含如下方法：
{: id="20210309203838-gr28kt9"}

​	（1）public void print(Emplyee[] all)：遍历打印员工数组中的每个员工的详细信息
{: id="20210309203838-d40p5dx"}

​	（2）public void sort(Employee[] all)：将all员工数组按照年龄从高到低排序
{: id="20210309203838-pjemo1c"}

​	（3）public void addSalary(Employee[] all, double increament)：将all员工数组的每一个员工的工资，增加increament
{: id="20210309203838-hov2jpm"}

​	3、声明Test05测试类
{: id="20210309203838-j2tkpck"}

（1）public static void main(String[] args)：在main方法中，创建Employee[]数组，并创建5个员工对象放到数组中，并为员工对象的属性赋值
{: id="20210309203838-ehwcq03"}

（2）创建EmployeeManager对象，
{: id="20210309203838-na8ydpy"}

（3）调用print方法，显示员工信息
{: id="20210309203838-qsxvq8w"}

（4）调用sort方法对员工数组进行按照年龄排序，并调用print方法，显示员工信息
{: id="20210309203838-f2mvy3t"}

（5）调用addSalary方法给每一个员工加薪1000元，并调用print方法，显示员工信息
{: id="20210309203838-4tpbbe1"}

```java
public class Employee {
	int id;
	String name;
	double salary;
	int age;
	
	void printInfo(){
		System.out.println("编号：" + id + "，姓名：" + name + "，薪资：" + salary + "，年龄：" +age);
	}
	void setInfo(int  i, String n, double s, int a){
		id = i;
		name = n;
		salary = s;
		age = a;
	}
}

```
{: id="20210309203838-e79fw0m"}

```java
public class EmployeeManager {
	public void print(Employee[] all){
		for(int i=0; i<all.length; i++){
			all[i].printInfo();
		}
	}
	
	public void sort(Employee[] all){
		for(int i=1; i<all.length; i++){
			for(int j=0; j<all.length-i; j++){
				//从高到低
				if(all[j].age < all[j+1].age){
					Employee temp = all[j];
					all[j] = all[j+1];
					all[j+1] = temp;
				}
			}
		}
	}
	
	public void addSalary(Employee[] all, double increament){
		for(int i=0; i<all.length; i++){
			all[i].salary += increament;
		}
	}
}

```
{: id="20210309203838-wftfa8b"}

```java
public class Test05 {
	public static void main(String[] args){
		Employee[] all = new Employee[5];
		all[0] = new Employee();
		all[0].setInfo(1,"张三",10000,23);
		
		all[1] = new Employee();
		all[1].setInfo(2,"李四",12000,23);
		
		all[2] = new Employee();
		all[2].setInfo(3,"王五",8000,18);
		
		all[3] = new Employee();
		all[3].setInfo(4,"赵六",6000,20);
		
		all[4] = new Employee();
		all[4].setInfo(5,"钱七",15000,21);
		
		EmployeeManager em = new EmployeeManager();
		
		em.print(all);
		System.out.println("------------------------------------------");
		
		em.sort(all);
		em.print(all);
		System.out.println("------------------------------------------");
		
		em.addSalary(all, 200);
		em.print(all);
	}
}

```
{: id="20210309203838-hkuq1o8"}

# 递归练习（难）
{: id="20210309203838-ivkmamn"}

## 第6题
{: id="20210309203838-vzpeh1g"}

用递归实现不死神兔：故事得从西元1202年说起，话说有一位意大利青年，名叫斐波那契。
{: id="20210309203838-v9o5bro"}

在他的一部著作中提出了一个有趣的问题：假设一对刚出生的小兔一个月后就能长成大兔，
{: id="20210309203838-genb619"}

再过一个月就能生下一对小兔，并且此后每个月都生一对小兔，没有发生死亡，
{: id="20210309203838-ke4ak0o"}

问：现有一对刚出生的兔子2年后(24个月)会有多少对兔子?
{: id="20210309203838-wpajjw0"}

```java
public class Test06 {
	public static void main(String[] args) {
		Count c = new Count();
		int sum = c.sum(24);
		System.out.println(sum);
	}
	

}
class Count{
	//从出生后第3个月起每个月都生一对兔子，小兔子长到第三个月后每个月又生一对兔子
	/*
	 * 第1个月，1对		f(1) = 1
	 * 第2个月，1对		f(2) = 2
	 * 第3个月，2对      老兔子本身1对，加上生出来的一对第1个月
	 * 			 		f(3) = f(2) + f(1)
	 * 第4个月，3对	    老兔子本身1对，上月出生的兔子第2个月，老兔子又生出一对新的第1个月		
	 * 				整理： 老兔子本身1对，老兔子又生出一对新的第1个月==》等价于第3个月的状态      
	 					  上月出生的兔子第2个月，==>等价于第2个月的兔子状态
	 * 						f(4) = f(3)+f(2)
	 
	 * 第5个月，5对     老兔子本身1对，老兔子又生出1对新的第1个月，第3个月初始的兔子也成新的老兔子1对，
     					它也生出一对新的第1个月，第4个月出生的兔子第2个月1对
	 *	整理分析：
	 *老兔子本身1对，老兔子又生出1对新的第1个月，第4个月出生的兔子第2个月1对  ==》等价于第4个月的状态
	 *第3个月初始的兔子也成新的老兔子1对，它也生出一对新的第1个月  ==》等价于第2个月的兔子状态
	 * 			f(5) = f(4) + f(2)
	 
	 * ....    f(n) = f(n-1) + f(n-2)
	 * 			
	 */
	public int sum(int n){
		if(n==1 || n==2){
			return 1;
		}else{
			return sum(n-1) + sum(n-2);
		}
	}
}
```
{: id="20210309203838-jzoe7we"}

## 第7题
{: id="20210309203838-jvdj6ww"}

描述：猴子吃桃子问题，猴子第一天摘下若干个桃子，当即吃了快一半，还不过瘾，又多吃了一个。第二天又将仅剩下的桃子吃掉了一半，又多吃了一个。以后每天都吃了前一天剩下的一半多一个。到第十天，只剩下一个桃子。试求第一天共摘了多少桃子？
{: id="20210309203838-aplrler"}

```java
public class Test07 {
	public static void main(String[] args) {
		Count c = new Count();
		System.out.println(c.sum(1));
		System.out.println(c.sum(2));
		System.out.println(c.sum(3));
		System.out.println(c.sum(4));
		System.out.println(c.sum(5));
		System.out.println(c.sum(6));
		System.out.println(c.sum(7));
		System.out.println(c.sum(8));
		System.out.println(c.sum(9));
		System.out.println(c.sum(10));
	}
	

}
class Count{
	public int sum(int n){
		if(n==10){//第10天
			return 1;
		}else{
			/*
			 * 第9天没吃之前是  第10天+1个的2倍
			 * 第8天没吃之前是  第9天+1个的2倍
			 * 。。。。
			 */
			return (sum(n+1)+1)*2;
		}
	}
}
```
{: id="20210309203838-1nhnccs"}

## 第8题
{: id="20210309203838-eq9gczv"}

通项公式如下：f(n)=n + (n-1) + (n-2) + .... + 1，其中n是大于等于5并且小于10000的整数，例如：f(5) = 5 + 4 + 3 + 2 + 1，f(10) = 10 + 9 + 8 + 7+ 6 + 5 + 4 + 3 + 2 + 1，请用递归的方式完成方法long f( int n)的方法体。
{: id="20210309203838-e923bm1"}

```java
public class Test8 {
	public static void main(String[] args) {
		Count c = new Count();
		System.out.println(c.f(5));
		System.out.println(c.f(10));
	}
}
class Count{
	public long f(int n) {
		long sum = 0;
		if(n==1){
			sum += 1;
		}else if(n>1){
			sum += n + f(n-1);
		}
		return sum;
	}
}
```
{: id="20210309203838-fjixmlc"}

## 第9题
{: id="20210309203838-2tyhic3"}

有n步台阶，一次只能上1步或2步，共有多少种走法？
{: id="20210309203838-iubezhi"}

```java
/*
 * 1级：1
 * 2级：2   1步1步  和 2步
 * 3级：上到1级的总走法（因为从1级上到3级直接跨2步）  + 上到2级的总走法（从2级上到3级直接跨1步）
 * 					因为从1级走1步就归到上到2级的走法里面了
 * 4级：上到2级的总走法 + 上到3级的总走法
 * ...
 * 
 * 即最后一步要么跨1步，要么跨2步
 */
public class Test9 {
	public static void main(String[] args) {
		Count c = new Count();
		System.out.println(c.f(10));
	}
	
}
class Count{
	public int f(int n) {
		if (n <= 2){
			return n;
		}
		return f(n - 1) + f(n - 2);
	}
}
```
{: id="20210309203838-5lx2rk2"}

# 代码阅读题
{: id="20210309203838-57sw0lv"}

## 第10题
{: id="20210309203838-4ulajit"}

知识点：方法的参数传递
{: id="20210309203838-nedpiyt"}

案例：分析运行结果
{: id="20210309203838-f3yhs3q"}

```java
package com.atguigu.test10;

public class Test10 {
	public static void main(String[] args) {
		Other o = new Other();
		new Test12().addOne(o);
		System.out.println(o.i);
	}
	
	public void addOne(Other o){
		o.i++;
	}
}
class Other{
	public int i;
}
```
{: id="20210309203838-7wo5qhl"}

```java
package com.atguigu.test10;

/*
 * 方法的参数传递机制：
 * 形参是基本数据类型，那么实参给形参的是数据值的副本，形参的修改不影响实参；
 * 形参是引用数据类型，那么实参给形参的是地址值的副本，形参对象修改属性相当于实参对象修改属性
 */
public class Test10 {
	public static void main(String[] args) {
		Other o = new Other();
		new Test12().addOne(o);
		System.out.println(o.i);//1
	}
	
	public void addOne(Other o){
		o.i++;
	}
}
class Other{
	public int i;
}
```
{: id="20210309203838-5i2sozz"}

## 第11题
{: id="20210309203838-3z54u4m"}

知识点：方法的参数传递
{: id="20210309203838-6bilysf"}

案例：分析运行结果
{: id="20210309203838-8nvpsnw"}

```java
package com.atguigu.test11;

public class Test11 {
	public static void main(String[] args) {
		int i = 0;
		change(i);
		i = i++;
		System.out.println("i = " + i);
	}
	public static void change(int i){
		i++;
	}
}

```
{: id="20210309203838-9ktotib"}

```java
package com.atguigu.test11;

/*
 * 1、方法的参数传递机制：
 * 形参是基本数据类型，那么实参给形参的是数据值的副本，形参的修改不影响实参；
 * 形参是引用数据类型，那么实参给形参的是地址值的副本，形参对象修改属性相当于实参对象修改属性
 * 
 * 2、自增运算符
 * ++在后，先加载值后自增；
 * ++在前，先自增后加载值
 * 
 * i = i++;
 * ①先加载i的值"0"，②i自增,i=1，③最后算赋值，把刚才的“0”赋值给i
 */
public class Test11 {
	public static void main(String[] args) {
		int i = 0;
		change(i);
		i = i++;
		System.out.println("i = " + i);//i=0
	}
	public static void change(int i){
		i++;
	}
}

```
{: id="20210309203838-c9r6jt1"}


{: id="20210309203838-rpuclxg" type="doc"}
