# JavaSE_day15【基础API与常见算法】
{: id="20210313082711-d0bo3zn"}

## 主要内容
{: id="20210313082711-3247as0"}

* {: id="20210313082711-k8mqa38"}String类
  {: id="20210313082711-8twblsn"}
* {: id="20210313082711-a46o876"}StringBuffer
  {: id="20210313082711-mqwnn87"}
* {: id="20210313082711-j4rb17c"}StringBuilder
  {: id="20210313082711-78ki3v1"}
{: id="20210313082711-ot30n0f"}

## 学习目标
{: id="20210313082711-0gvrdxq"}

* {: id="20210313082711-t1ppawd"}[ ] 熟练掌握String类的API
  {: id="20210313082711-h4t734z"}
* {: id="20210313082711-2tjw9wv"}[ ] 熟练掌握StringBuilder和StringBuffer类的API
  {: id="20210313082711-bw36gdp"}
* {: id="20210313082711-d6pkvcp"}[ ] 能够处理字符串相关的算法处理
  {: id="20210313082711-y737atz"}
{: id="20210313082711-cn6dh7h"}

# 第十章 基础API与常见算法
{: id="20210313082711-o3iic3g"}

## 10.5 字符串
{: id="20210313082711-ebuaq6y"}

`java.lang.String` 类代表字符串。Java程序中所有的字符串文字（例如`"abc"` ）都可以被看作是实现此类的实例。字符串是常量；它们的值在创建之后不能更改。字符串缓冲区支持可变的字符串。因为 String 对象是不可变的，所以可以共享。
{: id="20210313082711-bplew09"}

`String` 类包括的方法可用于检查序列的单个字符、比较字符串、搜索字符串、提取子字符串、创建字符串副本并将所有字符全部转换为大写或小写。
{: id="20210313082711-ppwcabs"}

Java 语言提供对字符串串联符号（"+"）以及将其他对象转换为字符串的特殊支持（toString()方法）。
{: id="20210313082711-5d190jp"}

### 10.5.1 字符串的特点
{: id="20210313082711-dp879ox"}

1、字符串String类型本身是final声明的，意味着我们不能继承String。
{: id="20210313082711-6e0nvdg"}

2、字符串的对象也是不可变对象，意味着一旦进行修改，就会产生新对象
{: id="20210313082711-f5mpekp"}

> 我们修改了字符串后，如果想要获得新的内容，必须重新接受。
> {: id="20210313082711-sqfkdmy"}
>
> 如果程序中涉及到大量的字符串的修改操作，那么此时的时空消耗比较高。可能需要考虑使用StringBuilder或StringBuffer的可变字符序列。
> {: id="20210313082711-6vpzrep"}
{: id="20210313082711-lnr6p8f"}

3、String对象内部是用字符数组进行保存的
{: id="20210313082711-pehygkv"}

> JDK1.9之前有一个char[] value数组，JDK1.9之后byte[]数组
> {: id="20210313082711-fyn4tgf"}
{: id="20210313082711-p474env"}

`"abc"` 等效于 `char[] data={ 'a' , 'b' , 'c' }`。
{: id="20210313082711-acosshr"}

```java
例如： 
String str = "abc";

相当于： 
char data[] = {'a', 'b', 'c'};   
String str = new String(data);
// String底层是靠字符数组实现的。
```
{: id="20210313082711-regpkob"}

4、String类中这个char[] values数组也是final修饰的，意味着这个数组不可变，然后它是private修饰，外部不能直接操作它，String类型提供的所有的方法都是用新对象来表示修改后内容的，所以保证了String对象的不可变。
{: id="20210313082711-7y4b84o"}

5、就因为字符串对象设计为不可变，那么所以字符串有常量池来保存很多常量对象
{: id="20210313082711-khqdabr"}

常量池在方法区。
{: id="20210313082711-1w4p1e7"}

如果细致的划分：
{: id="20210313082711-ytanoqp"}

（1）JDK1.6及其之前：方法区
{: id="20210313082711-k9ndscs"}

（2）JDK1.7：堆
{: id="20210313082711-b1ssosl"}

（3）JDK1.8：元空间
{: id="20210313082711-q1kktue"}

```java
String s1 = "abc";
String s2 = "abc";
System.out.println(s1 == s2);
// 内存中只有一个"abc"对象被创建，同时被s1和s2共享。
```
{: id="20210313082711-y1k7lhs"}

### 10.5.2 构造字符串对象
{: id="20210313082711-mwjkpbd"}

#### 1、使用构造方法
{: id="20210313082711-knlbij8"}

* {: id="20210313082711-o3lpqjf"}`public String() ` ：初始化新创建的 String对象，以使其表示空字符序列。
  {: id="20210313082711-9zy9vko"}
* {: id="20210313082711-7r58izv"}` String(String original)`： 初始化一个新创建的 `String` 对象，使其表示一个与参数相同的字符序列；换句话说，新创建的字符串是该参数字符串的副本。
  {: id="20210313082711-fjgr14h"}
* {: id="20210313082711-qs4ohzc"}`public String(char[] value) ` ：通过当前参数中的字符数组来构造新的String。
  {: id="20210313082711-3tcm79b"}
* {: id="20210313082711-ukif95d"}`public String(char[] value,int offset, int count) ` ：通过字符数组的一部分来构造新的String。
  {: id="20210313082711-pqobp46"}
* {: id="20210313082711-g27bg29"}`public String(byte[] bytes) ` ：通过使用平台的默认字符集解码当前参数中的字节数组来构造新的String。
  {: id="20210313082711-7d8ioj9"}
* {: id="20210313082711-cn9yfxh"}`public String(byte[] bytes,String charsetName) ` ：通过使用指定的字符集解码当前参数中的字节数组来构造新的String。
  {: id="20210313082711-4matf80"}
{: id="20210313082711-eox7t44"}

构造举例，代码如下：
{: id="20210313082711-manzvvt"}

```java
//字符串常量对象
String str = "hello";

// 无参构造
String str1 = new String（）；

//创建"hello"字符串常量的副本
String str2 = new String("hello");

//通过字符数组构造
char chars[] = {'a', 'b', 'c','d','e'};   
String str3 = new String(chars);
String str4 = new String(chars,0,3);

// 通过字节数组构造
byte bytes[] = {97, 98, 99 };   
String str5 = new String(bytes);
String str6 = new String(bytes,"GBK");
```
{: id="20210313082711-t2gdiuh"}

#### 2、使用静态方法
{: id="20210313082711-cj8pm29"}

* {: id="20210313082711-yzmcrch"}static String **copyValueOf**{: style="color: rgb(252, 13, 27);"}(char[] data)： 返回指定数组中表示该字符序列的 String
  {: id="20210313082711-lv1da4c"}
* {: id="20210313082711-k5rqfin"}static String copyValueOf(char[] data, int offset, int count)：返回指定数组中表示该字符序列的 String
  {: id="20210313082711-2wbaik0"}
* {: id="20210313082711-khdeabf"}static String valueOf(char[] data)  ： 返回指定数组中表示该字符序列的 String
  {: id="20210313082711-i4jey76"}
* {: id="20210313082711-mac2sjp"}static String valueOf(char[] data, int offset, int count) ： 返回指定数组中表示该字符序列的 String
  {: id="20210313082711-f32k4cr"}
* {: id="20210313082711-1jvtxpy"}static String valueOf(xx  value)：xx支持各种数据类型，返回各种数据类型的value参数的字符串表示形式。
  {: id="20210313082711-l4xfsrf"}
{: id="20210313082711-61ut5cp"}

```java
	public static void main(String[] args) {
		char[] data = {'h','e','l','l','o','j','a','v','a'};
		String s1 = String.copyValueOf(data);
		String s2 = String.copyValueOf(data,0,5);
		int num = 123456;
		String s3 = String.valueOf(num);
		System.out.println(s1);
		System.out.println(s2);
		System.out.println(s3);
	}
```
{: id="20210313082711-zosup6c"}

#### 3、使用""+
{: id="20210313082711-aefaf8n"}

任意数据类型与"字符串"进行拼接，结果都是字符串
{: id="20210313082711-44djw77"}

```java
	public static void main(String[] args) {
		int num = 123456;
		String s = num + "";
		System.out.println(s);
	
		Student stu = new Student();
		String s2 = stu + "";//自动调用对象的toString()，然后与""进行拼接
		System.out.println(s2);
	}
```
{: id="20210313082711-osw4j90"}

### 10.5.3 字符串的对象的个数
{: id="20210313082711-yxnfbmi"}

1、字符串常量对象
{: id="20210313082711-bba0bwj"}

```java
String str1 = "hello";//1个，在常量池中
```
{: id="20210313082711-jcjznl0"}

2、字符串的普通对象和常量对象一起
{: id="20210313082711-zk7z2uh"}

```java
String str3 = new String("hello");
//str3首先指向堆中的一个字符串对象，然后堆中字符串的value数组指向常量池中常量对象的value数组
```
{: id="20210313082711-2c8mm7y"}

### 10.5.4 字符串对象的内存分析
{: id="20210313082711-pdfkjdu"}

```java
String s;

String s = null;

String s = "";
String s = new String();
String s = new String("");

String s = "abc";
String s = new String("abc");

char[] arr = {'a','b'};
String s = new String(arr);


char[] arr = {'a','b','c','d','e'};
String s = new String(arr,0,3);
```
{: id="20210313082711-7f4e8ha"}

![1562945799274](imgs15/1562945799274.png)
{: id="20210313082711-n6nqor2"}

### 10.5.5 字符串拼接问题
{: id="20210313082711-9w8m2jn"}

#### 1、拼接结果的存储和比较问题
{: id="20210313082711-rz4nfsv"}

原则：
{: id="20210313082711-dpmd8jr"}

（1）常量+常量：结果是常量池
{: id="20210313082711-qyti8xf"}

（2）常量与变量 或 变量与变量：结果是堆
{: id="20210313082711-d8a97zp"}

（3）拼接后调用intern方法：结果在常量池
{: id="20210313082711-tw20uv5"}

```java
	@Test
	public void test06(){
		String s1 = "hello";
		String s2 = "world";
		String s3 = "helloworld";
	
		String s4 = (s1 + "world").intern();//把拼接的结果放到常量池中
		String s5 = (s1 + s2).intern();
	
		System.out.println(s3 == s4);//true
		System.out.println(s3 == s5);//true
	}

	@Test
	public void test05(){
		final String s1 = "hello";
		final String s2 = "world";
		String s3 = "helloworld";
	
		String s4 = s1 + "world";//s4字符串内容也helloworld，s1是常量，"world"常量，常量+ 常量 结果在常量池中
		String s5 = s1 + s2;//s5字符串内容也helloworld，s1和s2都是常量，常量+ 常量 结果在常量池中
		String s6 = "hello" + "world";//常量+ 常量 结果在常量池中，因为编译期间就可以确定结果
	
		System.out.println(s3 == s4);//true
		System.out.println(s3 == s5);//true
		System.out.println(s3 == s6);//true
	}

	@Test
	public void test04(){
		String s1 = "hello";
		String s2 = "world";
		String s3 = "helloworld";
	
		String s4 = s1 + "world";//s4字符串内容也helloworld，s1是变量，"world"常量，变量 + 常量的结果在堆中
		String s5 = s1 + s2;//s5字符串内容也helloworld，s1和s2都是变量，变量 + 变量的结果在堆中
		String s6 = "hello" + "world";//常量+ 常量 结果在常量池中，因为编译期间就可以确定结果
	
		System.out.println(s3 == s4);//false
		System.out.println(s3 == s5);//false
		System.out.println(s3 == s6);//true
	}
```
{: id="20210313082711-rbuaknf"}

![1562946547647](imgs15/1562946547647.png)
{: id="20210313082711-hx1ae8c"}

![1562946558630](imgs15/1562946558630.png)
{: id="20210313082711-af9d6db"}

#### 2、拼接效率问题
{: id="20210313082711-xa697b3"}

```java
public class TestString {
	public static void main(String[] args) {
		String str = "0";
		for (int i = 0; i <= 5; i++) {
			str += i;  
		}
		System.out.println(str);
	}
}
```
{: id="20210313082711-st1nl5g"}

![1562946595771](imgs15/1562946595771.png)
{: id="20210313082711-rq3zsmh"}

不过现在的JDK版本，都会使用可变字符序列对如上代码进行优化，我们反编译查看字节码：
{: id="20210313082711-9ojw38d"}

```cmd
javap -c TestString.class
```
{: id="20210313082711-8mdupfc"}

![1563106868437](imgs15/1563106868437.png)
{: id="20210313082711-1qiu10z"}

#### 3、两种拼接
{: id="20210313082711-9a4suh6"}

```java
public class TestString {
	public static void main(String[] args) {
		String str = "hello";
		String str2 = "world";
		String str3 ="helloworld";
	
		String str4 = "hello".concat("world");
		String str5 = "hello"+"world";
	
		System.out.println(str3 == str4);//false
		System.out.println(str3 == str5);//true
	}
}
```
{: id="20210313082711-p67r3az"}

> concat方法拼接，哪怕是两个常量对象拼接，结果也是在堆。
> {: id="20210313082711-8hpcmqz"}
{: id="20210313082711-p5d93vu"}

### 10.5.6  字符串对象的比较
{: id="20210313082711-fshbqco"}

1、==：比较是对象的地址
{: id="20210313082711-9cop5uh"}

> 只有两个字符串变量都是指向字符串的常量对象时，才会返回true
> {: id="20210313082711-m9bioxk"}
{: id="20210313082711-itil3ff"}

```java
String str1 = "hello";
String str2 = "hello";
System.out.println(str1 == str2);//true
  
String str3 = new String("hello");
String str4 = new String("hello");
System.out.println(str1 == str4); //false
System.out.println(str3 == str4); //false
```
{: id="20210313082711-w9r8oyk"}

2、equals：比较是对象的内容，因为String类型重写equals，区分大小写
{: id="20210313082711-sawl4l5"}

只要两个字符串的字符内容相同，就会返回true
{: id="20210313082711-2ld2i48"}

```java
String str1 = "hello";
String str2 = "hello";
System.out.println(str1.equals(str2));//true
  
String str3 = new String("hello");
String str4 = new String("hello");
System.out.println(str1.equals(str3));//true
System.out.println(str3.equals(str4));//true
```
{: id="20210313082711-7xrtq4t"}

3、equalsIgnoreCase：比较的是对象的内容，不区分大小写
{: id="20210313082711-ad2ggxi"}

```java
String str1 = new String("hello");
String str2 = new String("HELLO");
System.out.println(str1.equalsIgnoreCase(strs)); //true
```
{: id="20210313082711-wvyebqh"}

4、compareTo：String类型重写了Comparable接口的抽象方法，自然排序，按照字符的Unicode编码值进行比较大小的，严格区分大小写
{: id="20210313082711-0okxje2"}

```java
String str1 = "hello";
String str2 = "world";
str1.compareTo(str2) //小于0的值
```
{: id="20210313082711-7qpeoqm"}

5、compareToIgnoreCase：不区分大小写，其他按照字符的Unicode编码值进行比较大小
{: id="20210313082711-ru9i7qv"}

```java
String str1 = new String("hello");
String str2 = new String("HELLO");
str1.compareToIgnoreCase(str2)  //等于0
```
{: id="20210313082711-59b01qt"}

### 10.5.7 空字符的比较
{: id="20210313082711-8l1ta5h"}

1、哪些是空字符串
{: id="20210313082711-jk4vrbw"}

```java
String str1 = "";
String str2 = new String();
String str3 = new String("");
```
{: id="20210313082711-uxvdlmt"}

空字符串：长度为0
{: id="20210313082711-cfw2i8d"}

2、如何判断某个字符串是否是空字符串
{: id="20210313082711-yub430p"}

```java
if("".equals(str))

if(str!=null  && str.isEmpty())

if(str!=null && str.equals(""))

if(str!=null && str.length()==0)
```
{: id="20210313082711-m4nksnn"}

### 10.5.8 字符串的常用方法
{: id="20210313082711-gpu5p5y"}

#### 1、系列1
{: id="20210313082711-jfoxv3p"}

（1）boolean isEmpty()：字符串是否为空
{: id="20210313082711-b11rtin"}

（2）int length()：返回字符串的长度
{: id="20210313082711-voxawag"}

（3）String concat(xx)：拼接，等价于+
{: id="20210313082711-9d8une9"}

（4）boolean equals(Object obj)：比较字符串是否相等，区分大小写
{: id="20210313082711-hkpqvbf"}

（5）boolean equalsIgnoreCase(Object obj)：比较字符串是否相等，区分大小写
{: id="20210313082711-5lzn59j"}

（6）int compareTo(String other)：比较字符串大小，区分大小写，按照Unicode编码值比较大小
{: id="20210313082711-bs0hjoe"}

（7）int compareToIgnoreCase(String other)：比较字符串大小，不区分大小写
{: id="20210313082711-pyslobg"}

（8）String toLowerCase()：将字符串中大写字母转为小写
{: id="20210313082711-46h4por"}

（9）String toUpperCase()：将字符串中小写字母转为大写
{: id="20210313082711-3ufhggn"}

（10）String trim()：去掉字符串前后空白符
{: id="20210313082711-8ukgqe4"}

```java
	@Test
	public void test01(){
		//将用户输入的单词全部转为小写，如果用户没有输入单词，重新输入
		Scanner input = new Scanner(System.in);
		String word;
		while(true){
			System.out.print("请输入单词：");
			word = input.nextLine();
			if(word.trim().length()!=0){
				word = word.toLowerCase();
				break;
			}
		}
		System.out.println(word);
	}

	@Test
	public void test02(){
        //随机生成验证码，验证码由0-9，A-Z,a-z的字符组成
		char[] array = new char[26*2+10];
		for (int i = 0; i < 10; i++) {
			array[i] = (char)('0' + i);
		}
		for (int i = 10,j=0; i < 10+26; i++,j++) {
			array[i] = (char)('A' + j);
		}
		for (int i = 10+26,j=0; i < array.length; i++,j++) {
			array[i] = (char)('a' + j);
		}
		String code = "";
		Random rand = new Random();
		for (int i = 0; i < 4; i++) {
			code += array[rand.nextInt(array.length)];
		}
		System.out.println("验证码：" + code);
		//将用户输入的单词全部转为小写，如果用户没有输入单词，重新输入
		Scanner input = new Scanner(System.in);
		System.out.print("请输入验证码：");
		String inputCode = input.nextLine();
	
		if(!code.equalsIgnoreCase(inputCode)){
			System.out.println("验证码输入不正确");
		}
	}
```
{: id="20210313082711-jkqhhdd"}

#### 2、系列2：查找
{: id="20210313082711-pzrrlqr"}

（11）boolean contains(xx)：是否包含xx
{: id="20210313082711-utgc02q"}

（12）int indexOf(xx)：从前往后找当前字符串中xx，即如果有返回第一次出现的下标，要是没有返回-1
{: id="20210313082711-7tyrmdd"}

（13）int lastIndexOf(xx)：从后往前找当前字符串中xx，即如果有返回最后一次出现的下标，要是没有返回-1
{: id="20210313082711-0xrr7f6"}

```java
	@Test
	public void test01(){
		String str = "尚硅谷是一家靠谱的培训机构，尚硅谷可以说是IT培训的小清华，JavaEE是尚硅谷的当家学科，尚硅谷的大数据培训是行业独角兽。尚硅谷的前端和运维专业一样独领风骚。";
		System.out.println("是否包含清华：" + str.contains("清华"));
		System.out.println("培训出现的第一次下标：" + str.indexOf("培训"));
		System.out.println("培训出现的最后一次下标：" + str.lastIndexOf("培训"));
	}
```
{: id="20210313082711-g2pw27h"}

#### 3、系列3：字符串截取
{: id="20210313082711-xsld5gd"}

（14）String substring(int beginIndex) ：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
{: id="20210313082711-7uqkph3"}

（15）String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。
{: id="20210313082711-w980zu6"}

```java
	@Test
	public void test01(){
		String str = "helloworldjavaatguigu";
		String sub1 = str.substring(5);
		String sub2 = str.substring(5,10);
		System.out.println(sub1);
		System.out.println(sub2);
	}

	@Test
	public void test02(){
		String fileName = "快速学习Java的秘诀.dat";
		//截取文件名
		System.out.println("文件名：" + fileName.substring(0,fileName.lastIndexOf(".")));
		//截取后缀名
		System.out.println("后缀名：" + fileName.substring(fileName.lastIndexOf(".")));
	}
```
{: id="20210313082711-ms4vh1p"}

#### 4、系列4：和字符相关
{: id="20210313082711-8r2dv73"}

（16）char charAt(index)：返回[index]位置的字符
{: id="20210313082711-e1p75tg"}

（17）char[] toCharArray()： 将此字符串转换为一个新的字符数组返回
{: id="20210313082711-6cbg0zp"}

（18）String(char[] value)：返回指定数组中表示该字符序列的 String。
{: id="20210313082711-gtssyzk"}

（19）String(char[] value, int offset, int count)：返回指定数组中表示该字符序列的 String。
{: id="20210313082711-oxwswhu"}

（20）static String copyValueOf(char[] data)： 返回指定数组中表示该字符序列的 String
{: id="20210313082711-32ohgwq"}

（21）static String copyValueOf(char[] data, int offset, int count)：返回指定数组中表示该字符序列的 String
{: id="20210313082711-3f7zjt6"}

（22）static String valueOf(char[] data, int offset, int count) ： 返回指定数组中表示该字符序列的 String
{: id="20210313082711-f4dpzr9"}

（23）static String valueOf(char[] data)  ：返回指定数组中表示该字符序列的 String
{: id="20210313082711-8p1g42o"}

```java
	@Test
	public void test01(){
		//将字符串中的字符按照大小顺序排列
		String str = "helloworldjavaatguigu";
		char[] array = str.toCharArray();
		Arrays.sort(array);
		str = new String(array);
		System.out.println(str);
	}

	@Test
	public void test02(){
		//将首字母转为大写
		String str = "jack";
		str = Character.toUpperCase(str.charAt(0))+str.substring(1);
		System.out.println(str);
	}
```
{: id="20210313082711-jdat9yh"}

#### 5、系列5：编码与解码
{: id="20210313082711-npzarf3"}

（24）byte[] getBytes()：编码，把字符串变为字节数组，按照平台默认的字符编码进行编码
{: id="20210313082711-h6qr6ab"}

```
byte[] getBytes(字符编码方式)：按照指定的编码方式进行编码
```

{: id="20210313082711-bvye8n7"}

（25）new String(byte[] ) 或 new String(byte[], int, int)：解码，按照平台默认的字符编码进行解码
{: id="20210313082711-i3du7s8"}

```
new String(byte[]，字符编码方式 ) 或 new String(byte[], int, int，字符编码方式)：解码，按照指定的编码方式进行解码
```

{: id="20210313082711-b0bzk9h"}

```java
	/*
	 * GBK，UTF-8，ISO8859-1所有的字符编码都向下兼容ASCII码
	 */
	public static void main(String[] args) throws Exception {
		String str = "中国";
		System.out.println(str.getBytes("ISO8859-1").length);// 2
		// ISO8859-1把所有的字符都当做一个byte处理，处理不了多个字节
		System.out.println(str.getBytes("GBK").length);// 4 每一个中文都是对应2个字节
		System.out.println(str.getBytes("UTF-8").length);// 6 常规的中文都是3个字节

		/*
		 * 不乱码：（1）保证编码与解码的字符集名称一样（2）不缺字节
		 */
		System.out.println(new String(str.getBytes("ISO8859-1"), "ISO8859-1"));// 乱码
		System.out.println(new String(str.getBytes("GBK"), "GBK"));// 中国
		System.out.println(new String(str.getBytes("UTF-8"), "UTF-8"));// 中国
	}
```
{: id="20210313082711-kvgixu0"}

##### 字符编码发展
{: id="20210313082711-5tphqi5"}

##### **ASCII码**
{: id="20210313082711-ikj5gtm"}

计算机一开始发明的时候是用来解决数字计算的问题，后来人们发现，计算机还可以做更多的事，例如文本处理。但由于计算机只识“数”，因此人们必须告诉计算机哪个数字来代表哪个特定字符，例如65代表字母‘A’，66代表字母‘B’，以此类推。但是计算机之间字符-数字的对应关系必须得一致，否则就会造成同一段数字在不同计算机上显示出来的字符不一样。因此美国国家标准协会ANSI制定了一个标准，规定了常用字符的集合以及每个字符对应的编号，这就是ASCII字符集（Character Set），也称ASCII码。
{: id="20210313082711-xk6pjlq"}

那时候的字符编解码系统非常简单，就是简单的查表过程。其中：
{: id="20210313082711-rsjtisq"}

* {: id="20210313082711-gov1wnk"}0～31及127(共33个)是控制字符或通信专用字符（其余为可显示字符），如控制符：LF（换行）、CR（回车）、FF（换页）、DEL（删除）、BS（退格)
  {: id="20210313082711-630uunb"}
* {: id="20210313082711-4zgkar2"}32～126(共95个)是字符(32是空格），其中48～57为0到9十个阿拉伯数字。
  {: id="20210313082711-fxhoz7i"}
* {: id="20210313082711-ch6na9c"}65～90为26个大写英文字母，97～122号为26个小写英文字母，其余为一些标点符号、运算符号等。
  {: id="20210313082711-rwo756o"}
{: id="20210313082711-keam2fq"}

##### **OEM字符集的衍生**
{: id="20210313082711-5cy401b"}

当计算机开始发展起来的时候，人们逐渐发现，ASCII字符集里那可怜的128个字符已经不能再满足他们的需求了。人们就在想，一个字节能够表示的数字（编号）有256个，而ASCII字符只用到了0x00~0x7F，也就是占用了前128个，后面128个数字不用白不用，因此很多人打起了后面这128个数字的主意。可是问题在于，很多人同时有这样的想法，但是大家对于0x80-0xFF这后面的128个数字分别对应什么样的字符，却有各自的想法。这就导致了当时销往世界各地的机器上出现了大量各式各样的OEM字符集。不同的OEM字符集导致人们无法跨机器交流各种文档。例如职员甲发了一封简历résumés给职员乙，结果职员乙看到的却是r?sum?s，因为é字符在职员甲机器上的OEM字符集中对应的字节是0x82，而在职员乙的机器上，由于使用的OEM字符集不同，对0x82字节解码后得到的字符却是?。
{: id="20210313082711-iunigai"}

##### **多字节字符集（MBCS）和中文字符集**
{: id="20210313082711-2zpd26g"}

上面我们提到的字符集都是基于单字节编码，也就是说，一个字节翻译成一个字符。这对于拉丁语系国家来说可能没有什么问题，因为他们通过扩展第8个比特，就可以得到256个字符了，足够用了。但是对于亚洲国家来说，256个字符是远远不够用的。因此这些国家的人为了用上电脑，又要保持和ASCII字符集的兼容，就发明了多字节编码方式，相应的字符集就称为多字节字符集（Muilti-Bytes Charecter Set）。例如中国使用的就是双字节字符集编码。
{: id="20210313082711-x8kg1z3"}

例如目前最常用的中文字符集GB2312，涵盖了所有简体字符以及一部分其他字符；GBK（K代表扩展的意思）则在GB2312的基础上加入了对繁体字符等其他非简体字符。这两个字符集的字符都是使用1-2个字节来表示。Windows系统采用936代码页来实现对GBK字符集的编解码。在解析字节流的时候，如果遇到字节的最高位是0的话，那么就使用936代码页中的第1张码表进行解码，这就和单字节字符集的编解码方式一致了。如果遇到字节的最高位是1的话，那么就表示需要两个字节值才能对应一个字符。
{: id="20210313082711-ldyq7u8"}

![1563199557136](imgs15/1563199557136.png)
{: id="20210313082711-3sol2xs"}

##### **ANSI标准、国家标准、ISO标准**
{: id="20210313082711-qfpg0qt"}

不同ASCII衍生字符集的出现，让文档交流变得非常困难，因此各种组织都陆续进行了标准化流程。例如美国ANSI组织制定了ANSI标准字符编码（注意，我们现在通常说到ANSI编码，通常指的是平台的默认编码，例如英文操作系统中是ISO-8859-1，中文系统是GBK），ISO组织制定的各种ISO标准字符编码，还有各国也会制定一些国家标准字符集，例如中国的GBK，GB2312和GB18030。
{: id="20210313082711-n0gyvz7"}

操作系统在发布的时候，通常会往机器里预装这些标准的字符集还有平台专用的字符集，这样只要你的文档是使用标准字符集编写的，通用性就比较高了。例如你用GB2312字符集编写的文档，在中国大陆内的任何机器上都能正确显示。同时，我们也可以在一台机器上阅读多个国家不同语言的文档了，前提是本机必须安装该文档使用的字符集。
{: id="20210313082711-st8l711"}

##### **Unicode的出现**
{: id="20210313082711-rxv5pvc"}

虽然通过使用不同字符集，我们可以在一台机器上查阅不同语言的文档，但是我们仍然**无法解决一个问题：如果一份文档中含有不同国家的不同语言的字符，那么无法在一份文档中显示所有字符**。为了解决这个问题，我们需要一个全人类达成共识的巨大的字符集，这就是Unicode字符集。
{: id="20210313082711-v6lf4vx"}

Unicode字符集涵盖了目前人类使用的所有字符，并为每个字符进行统一编号，分配唯一的字符码（Code Point）。Unicode字符集将所有字符按照使用上的频繁度划分为17个层面（Plane），每个层面上有216=65536个字符码空间。其中第0个层面BMP，基本涵盖了当今世界用到的所有字符。其他的层面要么是用来表示一些远古时期的文字，要么是留作扩展。我们平常用到的Unicode字符，一般都是位于BMP层面上的。目前Unicode字符集中尚有大量字符空间未使用。
{: id="20210313082711-asjuzzw"}

Unicode同样也不完美，这里就有三个的问题，一个是，我们已经知道，英文字母只用一个字节表示就够了，第二个问题是如何才能区别Unicode和ASCII？计算机怎么知道两个字节表示一个符号，而不是分别表示两个符号呢？第三个，如果和GBK等双字节编码方式一样，用最高位是1或0表示两个字节和一个字节，就少了很多值无法用于表示字符，不够表示所有字符。Unicode在很长一段时间内无法推广，直到互联网的出现，为解决Unicode如何在网络上传输的问题，于是面向传输的众多 UTF（UCS Transfer Format）标准出现了，顾名思义，UTF-8就是每次8个位传输数据，而UTF-16就是每次16个位。UTF-8就是在互联网上使用最广的一种Unicode的实现方式，这是为传输而设计的编码，并使编码无国界，这样就可以显示全世界上所有文化的字符了。
{: id="20210313082711-y7iwwf0"}

UTF-8最大的一个特点，就是它是一种变长的编码方式。它可以使用1~4个字节表示一个符号。从unicode到uft-8并不是直接的对应，而是要过一些算法和规则来转换（**即Uncidoe字符集≠UTF-8编码方式**）。
{: id="20210313082711-5f7dn91"}

并不是直接的对应，而是要过一些算法和规则来转换（**即Uncidoe字符集≠UTF-8编码方式**）。
{: id="20210313082711-wvea1gh"}

Unicode符号范围         | UTF-8编码方式
{: id="20210313082711-cshydy0"}

(十六进制)                      |        （二进制）
{: id="20210313082711-22xxv9h"}

—————————————————————–
{: id="20210313082711-gvc3cfl"}

0000 0000-0000 007F | 0xxxxxxx（兼容原来的ASCII）
{: id="20210313082711-er19nvf"}

0000 0080-0000 07FF | 110xxxxx 10xxxxxx
{: id="20210313082711-8x6tgw1"}

0000 0800-0000 FFFF | 1110xxxx 10xxxxxx 10xxxxxx
{: id="20210313082711-z40d619"}

0001 0000-0010 FFFF | 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx
{: id="20210313082711-qgn2ys9"}

![1563199860263](imgs15/1563199860263.png)
{: id="20210313082711-9j8q6zs"}

因此，Unicode只是定义了一个庞大的、全球通用的字符集，并为每个字符规定了唯一确定的编号，具体存储成什么样的字节流，取决于字符编码方案。推荐的Unicode编码是UTF-16和UTF-8。
{: id="20210313082711-h0u2pe4"}

早期字符编码、字符集和代码页等概念都是表达同一个意思。例如GB2312字符集、GB2312编码，936代码页，实际上说的是同个东西。
{: id="20210313082711-k24hj1x"}

但是对于Unicode则不同，Unicode字符集只是定义了字符的集合和唯一编号，Unicode编码，则是对UTF-8、UCS-2/UTF-16等具体编码方案的统称而已，并不是具体的编码方案。所以当需要用到字符编码的时候，你可以写gb2312，codepage936，utf-8，utf-16，但请不要写Unicode。
{: id="20210313082711-5ndyhx3"}

#### 6、系列6：开头与结尾
{: id="20210313082711-kxki1im"}

（26）boolean startsWith(xx)：是否以xx开头
{: id="20210313082711-v4n860v"}

（27）boolean endsWith(xx)：是否以xx结尾
{: id="20210313082711-f3957sr"}

```java
	@Test
	public void test2(){
		String name = "张三";
		System.out.println(name.startsWith("张"));
	}

	@Test
	public void test(){
		String file = "Hello.txt";
		if(file.endsWith(".java")){
			System.out.println("Java源文件");
		}else if(file.endsWith(".class")){
			System.out.println("Java字节码文件");
		}else{
			System.out.println("其他文件");
		}
	}
```
{: id="20210313082711-kmymsbj"}

#### 7、系列7：正则匹配
{: id="20210313082711-90yz41e"}

（28）boolean matchs(正则表达式)：判断当前字符串是否匹配某个正则表达式
{: id="20210313082711-wgy2yg1"}

##### 常用正则表达式：
{: id="20210313082711-dox18an"}

###### 字符类
{: id="20210313082711-x93m5g6"}

`[abc]`：`a`、`b` 或 `c`（简单类）
{: id="20210313082711-tyaa1rh"}

`[^abc]`：任何字符，除了 `a`、`b` 或 `c`（否定）
{: id="20210313082711-cxax9p1"}

`[a-zA-Z]`：`a` 到 `z` 或 `A` 到 `Z`，两头的字母包括在内（范围）
{: id="20210313082711-04ywg7y"}

###### 预定义字符类
{: id="20210313082711-108hjq3"}

`.`：任何字符（与[行结束符](#lt)可能匹配也可能不匹配）
{: id="20210313082711-dow59b9"}

`\d`：数字：`[0-9]`
{: id="20210313082711-m68vgtl"}

`\D`：非数字： `[^0-9]`
{: id="20210313082711-c56c9wy"}

`\s`：空白字符：`[ \t\n\x0B\f\r]`
{: id="20210313082711-2u587gl"}

`\S`：非空白字符：`[^\s]`
{: id="20210313082711-sbm9xha"}

`\w`：单词字符：`[a-zA-Z_0-9]`
{: id="20210313082711-saif1vn"}

`\W`：非单词字符：`[^\w]`
{: id="20210313082711-69bl9xw"}

###### POSIX 字符类（仅 US-ASCII）
{: id="20210313082711-4z2lzx4"}

``\p{Lower} ``小写字母字符：[a-z]
{: id="20210313082711-ih1f0vj"}

``\p{Upper} ``大写字母字符：[A-Z]
{: id="20210313082711-xnkkhiz"}

``\p{ASCII} ``所有 ASCII：[\x00-\x7F]
{: id="20210313082711-h4lk9rg"}

``\p{Alpha} ``字母字符：[\p{Lower}\p{Upper}]
{: id="20210313082711-uxfhqpa"}

``\p{Digit}`` 十进制数字：[0-9]
{: id="20210313082711-xmy9wsh"}

``\p{Alnum} ``字母数字字符：[\p{Alpha}\p{Digit}]
{: id="20210313082711-3voiqe0"}

``\p{Punct}`` 标点符号：!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
{: id="20210313082711-glnhyzc"}

``\p{Blank}`` 空格或制表符：[ \t]
{: id="20210313082711-c21e5vn"}

###### 边界匹配器
{: id="20210313082711-t98vajj"}

`^`：行的开头
{: id="20210313082711-94n5r60"}

`$`：行的结尾
{: id="20210313082711-5dpng58"}

###### Greedy 数量词
{: id="20210313082711-boevjh8"}

*X*`?`：*X*，一次或一次也没有
{: id="20210313082711-nzfr4kk"}

*X*`*`：*X*，零次或多次
{: id="20210313082711-aowkafa"}

*X*`+`：*X*，一次或多次
{: id="20210313082711-77jp7ep"}

*X*`{`*n*`}`：*X*，恰好 *n* 次
{: id="20210313082711-7qxq2sr"}

*X*`{`*n*`,}`：*X*，至少 *n* 次
{: id="20210313082711-r22alt2"}

*X*`{`*n*`,`*m*`}`：*X*，至少 *n* 次，但是不超过 *m* 次
{: id="20210313082711-sl5et55"}

###### Logical 运算符
{: id="20210313082711-01pi496"}

*XY*：*X* 后跟 *Y*
{: id="20210313082711-2jr8w5m"}

*X*`|`*Y*：*X* 或 *Y*
{: id="20210313082711-t2beguy"}

`(`*X*`)`：X，作为捕获组
{: id="20210313082711-h1vd72j"}

###### 特殊构造（非捕获）
{: id="20210313082711-ya589kp"}

(?:X) X，作为非捕获组
{: id="20210313082711-657i1m8"}

(?=X) X，通过零宽度的正 lookahead
{: id="20210313082711-zcnjduh"}

(?!X) X，通过零宽度的负 lookahead
{: id="20210313082711-4vstn07"}

(?<=X) X，通过零宽度的正 lookbehind
{: id="20210313082711-esibsal"}

(?<!X) X，通过零宽度的负 lookbehind
{: id="20210313082711-yz7fvft"}

(?>X) X，作为独立的非捕获组
{: id="20210313082711-8uneb72"}

```java
	@Test
	public void test1(){
		//简单判断是否全部是数字，这个数字可以是1~n位
		String str = "12a345";
	
		//正则不是Java的语法，它是独立与Java的规则
		//在正则中\是表示转义，
		//同时在Java中\也是转义
		boolean flag = str.matches("\\d+");
		System.out.println(flag);
	}

	@Test
	public void test2(){
		String str = "123456789";
	
		//判断它是否全部由数字组成，并且第1位不能是0，长度为9位
		//第一位不能是0，那么数字[1-9]
		//接下来8位的数字，那么[0-9]{8}+
		boolean flag = str.matches("[1-9][0-9]{8}+");
		System.out.println(flag);
	}

	@Test
    public void test03(){
        //密码要求：必须有大写字母，小写字母，数字组成，6位
        System.out.println("Cly892".matches("^(?=.*[A-Z])(?=.*[a-z])(?=.*[0-9])[A-Za-z0-9]{6}$"));//true
        System.out.println("1A2c45".matches("^(?=.*[A-Z])(?=.*[a-z])(?=.*[0-9])[A-Za-z0-9]{6}$"));//true
        System.out.println("Clyyyy".matches("^(?=.*[A-Z])(?=.*[0-9])[A-Za-z0-9]{6}$"));//false
    }
```
{: id="20210313082711-58dpdv8"}

1.验证用户名和密码，要求第一个字必须为字母，一共6~16位字母数字下划线组成：（^[a-zA-Z]\w{5,15}$）
{: id="20210313082711-l1mzy7u"}

2.验证电话号码：xxx/xxxx-xxxxxxx/xxxxxxxx：（^(\d{3,4}-)\d{7,8}$）
{: id="20210313082711-vt6kxmb"}

3.验证手机号码：( ^(13[0-9]|14[5|7]|15[0|1|2|3|5|6|7|8|9]|18[0|1|2|3|5|6|7|8|9])\d{8}$ )
{: id="20210313082711-9ewwm55"}

4.验证身份证号： (^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)
{: id="20210313082711-rd2k449"}

5.验证Email地址：(^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$)
{: id="20210313082711-b5rrzkc"}

6.只能输入由数字和26个英文字母组成的字符串：(^[A-Za-z0-9]+$)
{: id="20210313082711-o7bkuzt"}

7.整数或者小数：(^[0-9]+(\.\[0-9\]+){0,1}$)
{: id="20210313082711-1urxh67"}

8.中文字符的正则表达式：([\u4e00-\u9fa5])
{: id="20210313082711-n1jrqt5"}

9.金额校验(非零开头的最多带两位小数的数字)：(^(\[1-9\][0-9]*)+(.[0-9]{1,2})?$)
{: id="20210313082711-bk2yh37"}

10.IPV4地址：(((\\d{1,2})|(1\\d{1,2})|(2[0-4]\\d)|(25[0-5]))\\.){3}((\\d{1,2})|(1\\d{1,2})|(2[0-4]\\d)|(25[0-5]))
{: id="20210313082711-pb7d9cl"}

#### 8、系列8：替换
{: id="20210313082711-bkgxwuh"}

（29）String replace(xx,xx)：不支持正则
{: id="20210313082711-mfbsb01"}

（30）String replaceFirst(正则，value)：替换第一个匹配部分
{: id="20210313082711-n61xzxz"}

（31）String repalceAll(正则， value)：替换所有匹配部分
{: id="20210313082711-d66m3ww"}

```java
	@Test
	public void test4(){
		String str = "hello244world.java;887";
		//把其中的非字母去掉
		str = str.replaceAll("[^a-zA-Z]", "");
		System.out.println(str);
	}
```
{: id="20210313082711-uhw8z5j"}

#### 9、系列9：拆分
{: id="20210313082711-li0ixsa"}

（32）String[] split(正则)：按照某种规则进行拆分
{: id="20210313082711-7eu1nss"}

```java
	@Test
	public void test4(){
		String str = "张三.23|李四.24|王五.25";
		//|在正则中是有特殊意义，我这里要把它当做普通的|
		String[] all = str.split("\\|");
	
		//转成一个一个学生对象
		Student[] students = new Student[all.length];
		for (int i = 0; i < students.length; i++) {
			//.在正则中是特殊意义，我这里想要表示普通的.
			String[] strings = all[i].split("\\.");//张三,  23
			String name = strings[0];
			int age = Integer.parseInt(strings[1]);
			students[i] = new Student(name,age);
		}
	
		for (int i = 0; i < students.length; i++) {
			System.out.println(students[i]);
		}
	
	}

	@Test
	public void test3(){
		String str = "1Hello2World3java4atguigu5";
		str = str.replaceAll("^\\d|\\d$", "");
		String[] all = str.split("\\d");
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i]);
		}
	}

	@Test
	public void test2(){
		String str = "1Hello2World3java4atguigu";
		str = str.replaceFirst("\\d", "");
		System.out.println(str);
		String[] all = str.split("\\d");
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i]);
		}
	}


	@Test
	public void test1(){
		String str = "Hello World java atguigu";
		String[] all = str.split(" ");
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i]);
		}
	}
```
{: id="20210313082711-ogzbuc9"}

## 10.6 可变字符序列
{: id="20210313082711-wspb540"}

### 10.6.1 String与可变字符序列的区别
{: id="20210313082711-4omun2c"}

因为String对象是不可变对象，虽然可以共享常量对象，但是对于频繁字符串的修改和拼接操作，效率极低。因此，JDK又在java.lang包提供了可变字符序列StringBuilder和StringBuffer类型。
{: id="20210313082711-wktg13k"}

StringBuffer：老的，线程安全的（因为它的方法有synchronized修饰）
{: id="20210313082711-ylpsrli"}

StringBuilder：线程不安全的
{: id="20210313082711-zp19w3n"}

### 10.6.2 StringBuilder、StringBuffer的API
{: id="20210313082711-fulvdaa"}

常用的API，StringBuilder、StringBuffer的API是完全一致的
{: id="20210313082711-5tb6aec"}

（1）StringBuffer append(xx)：拼接，追加
{: id="20210313082711-w29gtvk"}

（2）StringBuffer insert(int index, xx)：在[index]位置插入xx
{: id="20210313082711-ga8jjyx"}

（3）StringBuffer delete(int start, int end)：删除[start,end)之间字符
{: id="20210313082711-34qhbf7"}

StringBuffer deleteCharAt(int index)：删除[index]位置字符
{: id="20210313082711-5ttt893"}

（4）void setCharAt(int index, xx)：替换[index]位置字符
{: id="20210313082711-l2of2sl"}

（5）StringBuffer reverse()：反转
{: id="20210313082711-uli0zru"}

（6）void setLength(int newLength) ：设置当前字符序列长度为newLength
{: id="20210313082711-5ehgphc"}

（7）StringBuffer replace(int start, int end, String str)：替换[start,end)范围的字符序列为str
{: id="20210313082711-0yv0hmy"}

（8）int indexOf(String str)：在当前字符序列中查询str的第一次出现下标
{: id="20210313082711-xsjpwhn"}

```
int indexOf(String str, int fromIndex)：在当前字符序列[fromIndex,最后]中查询str的第一次出现下标
```

{: id="20210313082711-p3oeiqz"}

```
int lastIndexOf(String str)：在当前字符序列中查询str的最后一次出现下标
```

{: id="20210313082711-9friwlf"}

```
int lastIndexOf(String str, int fromIndex)：在当前字符序列[fromIndex,最后]中查询str的最后一次出现下标
```

{: id="20210313082711-i3vipph"}

（9）String substring(int start)：截取当前字符序列[start,最后]
{: id="20210313082711-z3v249w"}

（10）String substring(int start, int end)：截取当前字符序列[start,end)
{: id="20210313082711-inpgf0h"}

（11）String toString()：返回此序列中数据的字符串表示形式
{: id="20210313082711-0cjyfhm"}

```java
	@Test
	public void test6(){
		StringBuilder s = new StringBuilder("helloworld");
		s.setLength(30);
		System.out.println(s);
	}
	@Test
	public void test5(){
		StringBuilder s = new StringBuilder("helloworld");
		s.setCharAt(2, 'a');
		System.out.println(s);
	}


	@Test
	public void test4(){
		StringBuilder s = new StringBuilder("helloworld");
		s.reverse();
		System.out.println(s);
	}

	@Test
	public void test3(){
		StringBuilder s = new StringBuilder("helloworld");
		s.delete(1, 3);
		s.deleteCharAt(4);
		System.out.println(s);
	}


	@Test
	public void test2(){
		StringBuilder s = new StringBuilder("helloworld");
		s.insert(5, "java");
		s.insert(5, "chailinyan");
		System.out.println(s);
	}

	@Test
	public void test1(){
		StringBuilder s = new StringBuilder();
		s.append("hello").append(true).append('a').append(12).append("atguigu");
		System.out.println(s);
		System.out.println(s.length());
	}
```
{: id="20210313082711-k6526l1"}

### 10.6.3 效率测试
{: id="20210313082711-xkro6rr"}

```java
/*
 * Runtime：JVM运行时环境
 * Runtime是一个单例的实现
 */
public class TestTime {
	public static void main(String[] args) {
//		testStringBuilder();
		testStringBuffer();
//		testString();
	}
	public static void testString(){
		long start = System.currentTimeMillis();
		String s = new String("0");
		for(int i=1;i<=10000;i++){
			s += i;
		}
		long end = System.currentTimeMillis();
		System.out.println("String拼接+用时："+(end-start));//444
	
		long memory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
        System.out.println("String拼接+memory占用内存: " + memory);//53185144字节
	}
	public static void testStringBuilder(){
		long start = System.currentTimeMillis();
		StringBuilder s = new StringBuilder("0");
		for(int i=1;i<=10000;i++){
			s.append(i);
		}
		long end = System.currentTimeMillis();
		System.out.println("StringBuilder拼接+用时："+(end-start));//4
		long memory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
        System.out.println("StringBuilder拼接+memory占用内存: " + memory);//1950488
	}
	public static void testStringBuffer(){
		long start = System.currentTimeMillis();
		StringBuffer s = new StringBuffer("0");
		for(int i=1;i<=10000;i++){
			s.append(i);
		}
		long end = System.currentTimeMillis();
		System.out.println("StringBuffer拼接+用时："+(end-start));//7
		long memory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
        System.out.println("StringBuffer拼接+memory占用内存: " + memory);//1950488
	}
}
```
{: id="20210313082711-vlq7c8n"}

## 10.7 字符串特点相关面试题
{: id="20210313082711-zdq8dor"}

### 1、面试题：字符串的length和数组的length有什么不同？
{: id="20210313082711-hkm7qix"}

字符串的length()，数组的length属性
{: id="20210313082711-ibzu5ob"}

### 2、字符串对象不可变
{: id="20210313082711-4pjnh0f"}

<img src="imgs15/1563201668749.png" alt="1563201668749" style="zoom:200%;" />

{: id="20210316151939-c8bqcmo"}

```java
class TEXT{
	public int num;
	public String str;

	public TEXT(int num, String str){
		this.num = num;
		this.str = str;
	}
}
public class Class4 {
    //tIn是传对象的地址，修改形参的属性，会影响实参
    //intIn是传数据，基本数据类型的形参修改和实参无关
    //Integer和String对象不可变
	public static void f1(TEXT tIn, int intIn, Integer integerIn, String strIn){
		tIn.num =200;
		tIn.str = "bcd";//形参和实参指向的是同一个TEXT的对象，修改了属性，就相当于修改实参对象的属性
		intIn = 200;//基本数据类型的形参是实参的“副本”，无论怎么修改和实参都没关系
		integerIn = 200;//Integer对象和String对象一样都是不可变，一旦修改都是新对象，和实参无关
		strIn = "bcd";
	}
	public static void main(String[] args) {
		TEXT tIn = new TEXT(100, "abc");//tIn.num = 100, tIn.str="abc"
		int intIn = 100;
		Integer integerIn = 100;
		String strIn = "abc";
	
		f1(tIn,intIn,integerIn,strIn);
	
		System.out.println(tIn.num + tIn.str + intIn + integerIn + strIn);
		//200 + bcd + 100 + 100 + abc
	}
}
```
{: id="20210313082711-fnpbmbe"}

![1572834610162](imgs15/1572834610162.png)
{: id="20210313082711-oih93wg"}

### 3、字符串对象个数
{: id="20210313082711-xgfzc6u"}

![1572834413234](imgs15/1572834413234.png)
{: id="20210313082711-l1xsm2c"}

![1572835014847](imgs15/1572835014847.png)
{: id="20210313082711-z81ko60"}

### 4、字符串对象比较
{: id="20210313082711-p4j8vey"}

![1572834430257](imgs15/1572834430257.png)
{: id="20210313082711-mgkf0o0"}

![1572834653725](imgs15/1572834653725.png)
{: id="20210313082711-tns3qo9"}

![1572834908977](imgs15/1572834908977.png)
{: id="20210313082711-p5u4pmy"}

### 5、空字符串
{: id="20210313082711-g75z4kw"}

![1572834804165](imgs15/1572834804165.png)
{: id="20210313082711-nefwe8d"}

## 10.8 字符串算法相关面试题
{: id="20210313082711-ez93sqn"}

### 1、编程题
{: id="20210313082711-obtyn38"}

在字符串中找出连续最长数字串，返回这个串的长度，并打印这个最长数字串。
{: id="20210313082711-ks5osov"}

例如：abcd12345cd125se123456789，返回9，打印出123456789
{: id="20210313082711-3oo8kdp"}

![1573715990196](imgs15/1573715990196.png)
{: id="20210313082711-t3hf4x2"}

```java
public class TestExer1 {
	public static void main(String[] args) {
		String str = "abcd12345cd125se123456789";
	
		//去掉最前和最后的字母
		str =	str.replaceAll("^[a-zA-Z]+", "");
	
		//[a-zA-Z]：表示字母范围
		//+：一次或多次
		String[] strings = str.split("[a-zA-Z]+");
	
		String max = "";
		for (String string : strings) {
			if(string.length() > max.length()) {
				max = string;
			}
		}
		System.out.println("最长的数字串：" + max + "，它的长度为：" + max.length());
	}
}
```
{: id="20210313082711-yhgvcx5"}

### 2、编程题
{: id="20210313082711-omkimf0"}

不能使用trim()，实现去除字符串两端的空格。
{: id="20210313082711-fbps9es"}

```java
	public static void main(String[] args) {
		String str ="    he   llo   ";
		System.out.println(myTrim(str));
		System.out.println(myTrim2(str));
		System.out.println(myTrim3(str));
	}

	public static String myTrim3(String str){
		//利用正则表达式
		//^表示开头    \s表示  空白符   *表示0次或多次     |表示或者    $表示结尾
		return str.replaceAll("(^\\s*)|(\\s*$)", "");
	}

	public static String myTrim2(String str){
		while(str.startsWith(" ")){
			str = str.replaceFirst(" ", "");
		}
		while(str.endsWith(" ")){
			str = str.substring(0, str.length()-1);
		}
		return str;
	}

	public static String myTrim(String str){
		char[] array = str.toCharArray();
		int start =0;
		for(int i=0;i<array.length;i++){
			if(array[i] == ' '){
				start++;
			}else{
				break;
			}
		}
		int end = array.length-1;
		for(int i=end;i>=0;i--){
			if(array[i] == ' '){
				end--;
			}else{
				break;
			}
		}
	
		String result = str.substring(start,end+1);
	
		return result;
	}
```
{: id="20210313082711-h08uhab"}

### 3、编程题
{: id="20210313082711-07g4nqy"}

将字符串中指定部分进行反转。比如将“abcdefgho”反转为”abfedcgho”
{: id="20210313082711-53eng5r"}

```java
	public static void main(String[] args) {
		String str ="abcdefgho";
		System.out.println(str);
		System.out.println(reverse(str,2,5));

	}

	//从第start个字符，到第end个字符
	public static String reverse(String str,int start,int end){
		char[] array = str.toCharArray();
		for(int i = start,j=end;i< j;i++,j--){
			char temp =array[i];
			array[i]=array[j];
			array[j]=temp;
		}
		String s = new String(array);
		return s;
	}

	//从第start个字符，到第end个字符
	public static String reverse(String str,int start,int end){
        String left = str.substring(0,start);
		String middle = str.substring(start,end+1);
        String left = str.substring(end+1);
		return left+new StringBuilder(middle).reverse()+right;
	}
```
{: id="20210313082711-zjcqprp"}

### 4、编程题
{: id="20210313082711-7oxlpe9"}

获取一个字符串在另一个字符串中出现的次数。
{: id="20210313082711-9ttlc0e"}

```
比如：获取"ab"在 “abababkkcadkabkebfkabkskab”中出现的次数
```

{: id="20210313082711-1ps7tzg"}

```java
	public static void main(String[] args) {
		String str1="ab";
		String str2="abababkkcadkabkebfkabkskab";
		System.out.println(count(str1,str2));
	}

	public static int count(String str1,String str2){
		int count =0;
		do{
			int index = str2.indexOf(str1);
			if(index !=-1){
				count++;
				str2 = str2.substring(index + str1.length());
			}else{
				break;
			}
		
		}while(true);
		return count;
	}
```
{: id="20210313082711-x3zybpa"}

### 5、编程题
{: id="20210313082711-kjrerb6"}

获取两个字符串中最大相同子串。
{: id="20210313082711-yspi1iq"}

比如：str1 = "abcwerthelloyuiodef“;str2 = "cvhellobnm"
{: id="20210313082711-ghhxg9o"}

提示：将短的那个串进行长度依次递减的子串与较长的串比较。
{: id="20210313082711-k7cg388"}

```java
	public static void main(String[] args) {
		String str=findMaxSubString("abcwerthelloyuiodef","cvhellobnm");
		System.out.println(str);
	}

	//提示：将短的那个串进行长度依次递减的子串与较长的串比较。
	public static String findMaxSubString(String str1,String str2){
		String result="";
	
		String mixStr = str1.length()<str2.length()?str1:str2;
		String maxStr = str1.length()>str2.length()?str1:str2;
	
		//外循环控制从左到右的下标，内循环控制从右到左的下标
		for(int i=0;i<mixStr.length();i++){
			for(int j=mixStr.length();j>=i;j--){
				String str=mixStr.substring(i, j);
				if(maxStr.contains(str)){
					//找出最大相同子串
					if(result.length()<str.length()){
						result = str;
					}
				}
			}
		}
		return result;
	}
```
{: id="20210313082711-2ggq56n"}

### 6、编程题
{: id="20210313082711-vk4tmix"}

编写代码完成如下功能
{: id="20210313082711-vsy1kgu"}

public static String replace(String text, String target, String replace){
{: id="20210313082711-9utr0jo"}

....
{: id="20210313082711-xx4eas9"}

}
{: id="20210313082711-q2lnhn2"}

示例：replace(“aabbccbb”, “bb”, “dd”);  结果：aaddccdd
{: id="20210313082711-fw0zomb"}

注意：不能使用String及StringBuffer等类的replace等现成的替换API方法。
{: id="20210313082711-ht10pwe"}

![1573716569424](imgs15/1573716569424.png)
{: id="20210313082711-i29x02l"}

```java
	public static void main(String[] args) {
		System.out.println(replace("aabbcbcbb","bb","dd"));
	}
	public static String replace(String text, String target, String replace){
		while(true) {
			int index = text.indexOf(target);
			if(index!=-1) {
				text = text.substring(0,index) + replace + text.substring(index+target.length());
			}else {
				break;
			}
		}
		return text;
	}
```
{: id="20210313082711-08l73h0"}

### 7、编程题
{: id="20210313082711-a72bd6f"}

1个字符串中可能包含a-z中的多个字符，字符也可能重复，例如：String data = “aabcexmkduyruieiopxzkkkkasdfjxjdsds”;写一个程序，对于给定一个这样的字符串求出字符串出现次数最多的那个字母以及出现的次数（若次数最多的字母有多个，则全部求出）
{: id="20210313082711-73anxzf"}

![1574169374414](imgs15/1574169374414.png)
{: id="20210313082711-rzcv37c"}

```java
	public static void main(String[] args) {
		String str = "aabbyolhljlhlxxmnbwyteuhfhjloiqqbhrg";
	
		//统计每个字母的次数
		int[] counts = new int[26];
		char[] letters = str.toCharArray();
		for (int i = 0; i < letters.length; i++) {
			counts[letters[i]-97]++;
		}
	
		//找出最多次数值
		int max = counts[0];
		for (int i = 1; i < counts.length; i++) {
			if(max < counts[i]) {
				max = counts[i];
			}
		}
		//找出所有最多次数字母
		for (int i = 0; i < counts.length; i++) {
			if(counts[i] == max) {
				System.out.println((char)(i+97));
			}
		}
	}
```
{: id="20210313082711-729je9b"}

> 如果学习完集合之后，该题还可以使用Map集合写出不同的答案
> {: id="20210313082711-rrffoh1"}
{: id="20210313082711-4744zv0"}

### 8、编程题
{: id="20210313082711-ynao04p"}

假设日期段用两个6位长度的正整数表示，例如：(201401，201406)用来表示2014年1月到2014年6月，求两个日期段的重叠月份数。例如：输入：时间段1：201401和201406，时间段2：201403和201409，输出：4
{: id="20210313082711-obd92gy"}

解释：重叠月份：3,4,5,6月共4个月
{: id="20210313082711-1xve69o"}

情形1：两个时间段都是同一年内的，实现代码如下：
{: id="20210313082711-1mv403s"}

```java
	public static void main(String[] args) {
		String date1Start = "201401";
		String date1End = "201406";
	
		String date2Start = "201403";
		String date2End = "201409";
	
		int date1StartMonth = Integer.parseInt(date1Start.substring(4));
		int date1EndMonth = Integer.parseInt(date1End.substring(4));
	
		int date2StartMonth = Integer.parseInt(date2Start.substring(4));
		int date2EndMonth = Integer.parseInt(date2End.substring(4));
	
		int start = date1StartMonth >= date2StartMonth ? date1StartMonth : date2StartMonth;
		int end = date1EndMonth <= date2EndMonth ? date1EndMonth : date2EndMonth;
        System.out.println("重叠月份数："+(end-start+1));
      
		System.out.println("重叠的月份有：");
		for (int i = start; i <= end; i++) {
			System.out.println(i);
		}      
	}
```
{: id="20210313082711-qua4fhk"}

情形2：两个时间段可能不在同一年内的，实现代码如下：
{: id="20210313082711-cgabxsr"}

```java
	public static void main(String[] args) {
		String date1Start = "201401";
		String date1End = "201506";
	
		String date2Start = "201403";
		String date2End = "201505";
	
		String date1 = handleDate(date1Start,date1End);
		String date2 = handleDate(date2Start,date2End);
		System.out.println(date1);
		System.out.println(date2);
	
		String sameDate = findMaxSubString(date1,date2);

		System.out.println("重叠的月份数：" + sameDate.length()/6);
		if (!"".equals(sameDate)) {
			System.out.println("重叠的月份有：");
			while (sameDate.length() > 0) {
				String sameMonth = sameDate.substring(0, 6);
				System.out.println(sameMonth);
				sameDate = sameDate.substring(6);
			}
		
		}
	}

	public static String findMaxSubString(String str1,String str2){
		String result="";
	
		String mixStr = str1.length()<str2.length()?str1:str2;
		String maxStr = str1.length()>str2.length()?str1:str2;
	
		//外循环控制从左到右的下标，内循环控制从右到左的下标
		for(int i=0;i<mixStr.length();i++){
			for(int j=mixStr.length();j>=i;j--){
				String str=mixStr.substring(i, j);
				if(maxStr.contains(str)){
					//找出最大相同子串
					if(result.length()<str.length()){
						result = str;
					}
				}
			}
		}
		return result;
	}

	public static String handleDate(String dateStart, String dateEnd) {
		int dateStartYear = Integer.parseInt(dateStart.substring(0,4));
		int dateEndYear = Integer.parseInt(dateEnd.substring(0,4));
		int dateStartMonth = Integer.parseInt(dateStart.substring(4));
		int dateEndMonth = Integer.parseInt(dateEnd.substring(4));
	
		String date = "";
		if(dateStartYear == dateEndYear) {//一年之内
			for (int i = dateStartMonth; i <=dateEndMonth; i++) {
				if(i<10) {
					date += dateStartYear+"0"+i;
				}else {
					date += dateStartYear+""+i;
				}
			}
		}else {//跨年
			for (int i = dateStartMonth; i <=12; i++) {//date1StartYear起始年
				if(i<10) {
					date += dateStartYear+"0"+i;
				}else {
					date += dateStartYear+""+i;
				}
			}
			for (int i = dateStartYear+1; i < dateEndYear; i++) {//中间间隔年
				for (int j = 1; j <= 12; j++) {
					if(j<10) {
						date += i+"0"+j;
					}else {
						date += i+""+j;
					}
				}
			}
			for (int i = 1; i <= dateEndMonth; i++) {//date1EndYear结束年
				if(i<10) {
					date += dateEndYear+"0"+i;
				}else {
					date += dateEndYear+""+i;
				}
			}
		}
		return date;
	}
}
```
{: id="20210313082711-01yv6dw"}


{: id="20210313082711-215limr" type="doc"}
