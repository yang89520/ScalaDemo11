# JavaSE_day12【异常】
{: id="20210309181757-zrpmcyb"}

## 主要内容
{: id="20210309181757-gse14c3"}

- {: id="20210309181757-bugr22s"}异常的体系结构
  {: id="20210309181757-ngmatuo"}
- {: id="20210309181757-qwynfrm"}**常见异常**
  {: id="20210309181757-gz027ag"}
- {: id="20210309181757-e8p6913"}throw关键字（手动创建并抛出异常）
  {: id="20210309181757-n9zhsc4"}
- {: id="20210309181757-t4hjbqg"}**异常处理机制一：try**（掌握）
  {: id="20210309181757-9bi2pqb"}
- {: id="20210309181757-k3mer72"}**异常处理机制二：throws**（掌握）
  {: id="20210309181757-fbd1xmb"}
- {: id="20210309181757-1ymrfk3"}自定义异常
  {: id="20210309181757-6b4c6ob"}
{: id="20210309181757-1i53ews"}

## 学习目标
{: id="20210309181757-kyld4n5"}

- {: id="20210309181757-ohvzx84"}[ ] 能够辨别程序中异常和错误的区别
  {: id="20210309181757-um66ch7"}
- {: id="20210309181757-9lkpe9z"}[ ] 说出异常的分类
  {: id="20210309181757-kvu8h1s"}
- {: id="20210309181757-i4lyjgs"}[ ] 说出虚拟机处理异常的方式
  {: id="20210309181757-2oasehr"}
- {: id="20210309181757-u17q9zw"}[ ] 可以编写代码演示OOM
  {: id="20210309181757-s4yzhth"}
- {: id="20210309181757-ch5k41w"}[ ] 列出常见的5个运行时异常
  {: id="20210309181757-0zvmf3s"}
- {: id="20210309181757-ixdx5ht"}[ ] 列出常见的5个编译时异常
  {: id="20210309181757-4sio1r4"}
- {: id="20210309181757-0hrod81"}[ ] 能够使用try...catch关键字处理异常
  {: id="20210309181757-cika3zs"}
- {: id="20210309181757-f24yfrv"}[ ] 能够使用throws关键字处理异常
  {: id="20210309181757-lb95503"}
- {: id="20210309181757-onnt7ha"}[ ] 能够自定义异常类
  {: id="20210309181757-s9071wx"}
- {: id="20210309181757-l8vpaip"}[ ] 能够处理自定义异常类
  {: id="20210309181757-wrd3whs"}
{: id="20210309181757-o7l4ptm"}

# 第八章    异常
{: id="20210309181757-l20ce6s"}

## 8.1 异常概述
{: id="20210309181757-x6mc9hu"}

在使用计算机语言进行项目开发的过程中，即使程序员把代码写得 尽善尽美，在系统的运行过程中仍然会遇到一些问题，因为很多问题不是靠代码能够避免的，比如：客户输入数据的格式，读取文件是否存在，网络是否始终保持通畅等等。
{: id="20210309181757-evhxao8"}

* {: id="20210309181757-ulkn506"}**异常** ：指的是程序在执行过程中，出现的非正常的情况，如果不处理最终会导致JVM的非正常停止。
  {: id="20210309181757-23qxsjg"}
{: id="20210309181757-n5yaqq8"}

> 异常指的并不是语法错误,语法错了,编译不通过,不会产生字节码文件,根本不能运行.
> {: id="20210309181757-kmxz5zx"}
>
> 异常也不是指逻辑代码错误而没有得到想要的结果，例如：求a与b的和，你写成了a-b
> {: id="20210309181757-i14ectb"}
{: id="20210309181757-xjpfd62"}

对于异常，一般有两种解决方法：一是遇到错误就终止程序的运行。另一种方法是由程序员在编写程序时，就考虑到错误的检测、错误消息的提示，以及错误的处理。
{: id="20210309181757-l2ngeu6"}

Java中是如何表示不同的异常情况，又是如何让程序员得知，并处理异常的呢？
{: id="20210309181757-j9e437k"}

Java中把不同的异常用不同的类表示，一旦发生某种异常，就通过创建该异常类型的对象，并且抛出，然后程序员可以catch到这个异常对象，并处理，如果无法catch到这个异常对象，那么这个异常对象将会导致程序终止。
{: id="20210309181757-c74x3ez"}

## 8.2 异常体系
{: id="20210309181757-kev5ult"}

异常的根类是`java.lang.Throwable`，其下有两个子类：`java.lang.Error`与`java.lang.Exception`，平常所说的异常指`java.lang.Exception`。
{: id="20210309181757-oq3lkud"}

![](imgs12/异常的分类.png)
{: id="20210309181757-7qqp482"}

**Throwable体系：**
{: id="20210309181757-gml3u9y"}

* {: id="20210309181757-q53bzzw"}**Error**:严重错误Error，无法通过处理的错误，只能事先避免，好比绝症。
  {: id="20210309181757-0tqm49f"}
  * {: id="20210309181757-h7ma3xp"}例如：StackOverflowError和OOM（OutOfMemoryError）。
    {: id="20210309181757-vyijscx"}
  {: id="20210309181757-ll8krjm"}
* {: id="20210309181757-af28o6l"}**Exception**:表示异常，其它因编程错误或偶然的外在因素导致的一般性问题，程序员可以通过代码的方式纠正，使程序继续运行，是必须要处理的。好比感冒、阑尾炎。
  {: id="20210309181757-wpkxsz3"}
  * {: id="20210309181757-6muoiwc"}例如：空指针访问、试图读取不存在的文件、网络连接中断、数组角标越界
    {: id="20210309181757-plppnuf"}
  {: id="20210309181757-f9yabrg"}
{: id="20210309181757-6vjct4e"}

**Throwable中的常用方法：**
{: id="20210309181757-6v4iczr"}

* {: id="20210309181757-vk3dmoc"}`public void printStackTrace()`:打印异常的详细信息。
  {: id="20210309181757-7sxsrty"}

  *包含了异常的类型,异常的原因,还包括异常出现的位置,在开发和调试阶段,都得使用printStackTrace。*
  {: id="20210309181757-r2n8jae"}
* {: id="20210309181757-kw3r3jn"}`public String getMessage()`:获取发生异常的原因。
  {: id="20210309181757-aezz5fz"}
  *提示给用户的时候,就提示错误原因。*
  {: id="20210309181757-hc5sb9d"}
{: id="20210309181757-edonqxc"}

***出现异常,不要紧张,把异常的简单类名,拷贝到API中去查。***
{: id="20210309181757-jc62ang"}

![](imgs12/简单的异常查看.bmp)
{: id="20210309181757-n63et95"}

## 8.3 异常分类
{: id="20210309181757-6rbhx2k"}

我们平常说的异常就是指Exception，因为这类异常一旦出现，我们就要对代码进行更正，修复程序。
{: id="20210309181757-th6ib44"}

**异常(Exception)的分类**:根据在编译时期还是运行时期去检查异常?
{: id="20210309181757-ll83dqt"}

* {: id="20210309181757-s9w2ufp"}**编译时期异常**:checked异常。在编译时期,就会检查,如果没有处理异常,则编译失败。(如文件找不到异常)
  {: id="20210309181757-ea8t4sq"}
* {: id="20210309181757-kk0k7im"}**运行时期异常**:runtime异常。在运行时期,检查异常.在编译时期,运行异常不会被编译器检测到(不报错)。(如数组索引越界异常，类型转换异常)。程序员应该积极避免其出现的异常，而不是使用try..catch处理，因为这类异常很普遍，若都使用try..catch或throws处理可能会对程序的可读性和运行效率产生影响。
  {: id="20210309181757-lge7e13"}
{: id="20210309181757-ku38x0o"}

![1562771528807](imgs12/1562771528807.png)
{: id="20210309181757-uuljoap"}

### 演示常见的错误和异常
{: id="20210309181757-m7ahffd"}

#### 1、VirtualMachineError
{: id="20210309181757-j0epc8j"}

最常见的就是：StackOverflowError、OutOfMemoryError
{: id="20210309181757-bsd0ra8"}

```java
	@Test
	public void test01(){
		//StackOverflowError
		digui();
	}
	
	public void digui(){
		digui();
	}
```
{: id="20210309181757-arzlk8p"}

```java
	@Test
	public void test02(){
		//OutOfMemoryError
		//方式一：
		int[] arr = new int[Integer.MAX_VALUE];
	}
	@Test
	public void test03(){
		//OutOfMemoryError
		//方式二：
		StringBuilder s = new StringBuilder();
		while(true){
			s.append("atguigu");
		}
	}
```
{: id="20210309181757-cw6yqut"}

#### 2、运行时异常
{: id="20210309181757-pjj7rmf"}

```java
	@Test
	public void test01(){
	    //NullPointerException
		int[][] arr = new int[3][];
		System.out.println(arr[0].length);
	}
	
	@Test
	public void test02(){
		//ClassCastException
		Person p = new Man();
		Woman w = (Woman) p;
	}
	
	@Test
	public void test03(){
		//ArrayIndexOutOfBoundsException
		int[] arr = new int[5];
		for (int i = 1; i <= 5; i++) {
			System.out.println(arr[i]);
		}
	}
	
	@Test
	public void test04(){
		//InputMismatchException
		Scanner input = new Scanner(System.in);
		System.out.print("请输入一个整数：");
		int num = input.nextInt();
	}
	
	@Test
	public void test05(){
		int a = 1;
		int b = 0;
		//ArithmeticException
		System.out.println(a/b);
	}
```
{: id="20210309181757-p7b1b02"}

#### 3、编译时异常
{: id="20210309181757-hcyozcl"}

```java
	@Test
	public void test06() throws InterruptedException{
		Thread.sleep(1000);//休眠1秒
	}
	
	@Test
	public void test07() throws FileNotFoundException{
		FileInputStream fis = new FileInputStream("Java学习秘籍.txt");
	}
	
	@Test
	public void test08() throws SQLException{
		Connection conn = DriverManager.getConnection("....");
	}
```
{: id="20210309181757-zmm2rhy"}

## 8.4 异常的抛出机制
{: id="20210309181757-5wa5694"}

先运行下面的程序，程序会产生一个数组索引越界异常ArrayIndexOfBoundsException。我们通过图解来解析下异常产生的过程。
{: id="20210309181757-wx8mr31"}

工具类
{: id="20210309181757-ra5nl8x"}

~~~java
public class ArrayTools {
    // 对给定的数组通过给定的角标获取元素。
    public static int getElement(int[] arr, int index) {
        int element = arr[index];
        return element;
    }
}
~~~
{: id="20210309181757-lgmo0mv"}

测试类
{: id="20210309181757-gebjcdq"}

~~~java
public class ExceptionDemo {
    public static void main(String[] args) {
        int[] arr = { 34, 12, 67 };
        intnum = ArrayTools.getElement(arr, 4)
        System.out.println("num=" + num);
        System.out.println("over");
    }
}
~~~
{: id="20210309181757-d4l4mz2"}

上述程序执行过程图解：
{: id="20210309181757-g1oxqot"}

![](imgs12/异常产生过程.png)
{: id="20210309181757-nzmjzww"}

![1562772282750](imgs12/1562772282750.png)
{: id="20210309181757-732ijxq"}

## 8.5 异常的处理
{: id="20210309181757-e6zmbdj"}

Java异常处理的五个关键字：**try、catch、finally、throw、throws**
{: id="20210309181757-xvmuax2"}

### 8.5.1 异常throw
{: id="20210309181757-iv3pemd"}

Java程序的执行过程中如出现异常，会生成一个异常类对象，该异常对象将被提交给Java运行时系统，这个过程称为抛出(throw)异常。异常对象的生成有两种方式：
{: id="20210309181757-l2k92ta"}

* {: id="20210309181757-ea7vmi5"}由虚拟机自动生成：程序运行过程中，虚拟机检测到程序发生了问题，如果在当前代码中没有找到相应的处理程序，就会在后台自动创建一个对应异常类的实例对象并抛出——自动抛出
  {: id="20210309181757-o49gg90"}
* {: id="20210309181757-1psvza9"}由开发人员手动创建：Exception exception = new ClassCastException();——创建好的异常对象不抛出对程序没有任何影响，和创建一个普通对象一样，但是一旦throw抛出，就会对程序运行产生影响了。
  {: id="20210309181757-0r34x21"}
{: id="20210309181757-cyhoffv"}

下面我们说明手动抛出异常：
{: id="20210309181757-ti0nm2a"}

比如，在定义方法时，方法需要接受参数。那么，当调用方法使用接受到的参数时，首先需要先对参数数据进行合法的判断，数据若不合法，就应该告诉调用者，这时可以使用抛出异常的方式来告诉调用者。
{: id="20210309181757-n2tsrxd"}

在java中，提供了一个**throw**关键字，它用来抛出一个指定的异常对象。那么，抛出一个异常具体如何操作呢？
{: id="20210309181757-lpdg67w"}

1. {: id="20210309181757-ffwnu7a"}创建一个异常对象。封装一些提示信息(信息可以自己编写)。
   {: id="20210309181757-xpngdfw"}
2. {: id="20210309181757-60xdfes"}需要将这个异常对象告知给调用者。怎么告知呢？怎么将这个异常对象传递到调用者处呢？通过关键字throw就可以完成。throw 异常对象。
   {: id="20210309181757-3jhkkfp"}
   throw**用在方法内**，用来抛出一个异常对象，将这个异常对象传递到调用者处，并**结束**当前方法的执行。
   {: id="20210309181757-yfogcmb"}
{: id="20210309181757-02ch2kh"}

**使用格式：**
{: id="20210309181757-z7vhr89"}

~~~
throw new 异常类名(参数);
~~~
{: id="20210309181757-jq3jyxj"}

例如：
{: id="20210309181757-qsq6opv"}

~~~java
throw new NullPointerException("要访问的arr数组不存在");

throw new ArrayIndexOutOfBoundsException("该索引在数组中不存在，已超出范围");
~~~
{: id="20210309181757-8myoem5"}

学习完抛出异常的格式后，我们通过下面程序演示下throw的使用。
{: id="20210309181757-xhv5lpr"}

~~~java
public class ThrowDemo {
    public static void main(String[] args) {
        //创建一个数组 
        int[] arr = {2,4,52,2};
        //根据索引找对应的元素 
        int index = 4;
        int element = getElement(arr, index);

        System.out.println(element);
        System.out.println("over");
    }
    /*
     * 根据 索引找到数组中对应的元素
     */
    public static int getElement(int[] arr,int index){ 
        if(arr == null){
            /*
             判断条件如果满足，当执行完throw抛出异常对象后，方法已经无法继续运算。
             这时就会结束当前方法的执行，并将异常告知给调用者。这时就需要通过异常来解决。 
              */
            throw new NullPointerException("要访问的arr数组不存在");
        }
       	//判断  索引是否越界
        if(index<0 || index>arr.length-1){
             /*
             判断条件如果满足，当执行完throw抛出异常对象后，方法已经无法继续运算。
             这时就会结束当前方法的执行，并将异常告知给调用者。这时就需要通过异常来解决。 
              */
             throw new ArrayIndexOutOfBoundsException("哥们，角标越界了~~~");
        }
        int element = arr[index];
        return element;
    }
}
~~~
{: id="20210309181757-vjrmwrr"}

> 注意：如果产生了问题，我们就会throw将问题描述类即异常进行抛出，也就是将问题返回给该方法的调用者。
> {: id="20210309181757-e2pg8f5"}
>
> 那么对于调用者来说，该怎么处理呢？一种是进行捕获处理，另一种就是继续讲问题声明出去，使用throws声明处理。
> {: id="20210309181757-wwhcpj4"}
{: id="20210309181757-5ewdj53"}

#### 练习1
{: id="20210309181757-crkspj3"}

1、声明Husband类，包含姓名和妻子属性，属性私有化，提供一个Husband(String name)的构造器，重写toString方法，返回丈夫姓名和妻子的姓名
{: id="20210309181757-aqj917k"}

2、声明Wife类，包含姓名和丈夫属性，属性私有化，提供一个Wife(String name)的构造器，重写toString方法，返回妻子的姓名和丈夫的姓名
{: id="20210309181757-0mtix0j"}

3、声明TestMarry类，在main中，创建Husband和Wife对象后直接打印妻子和丈夫对象，查看异常情况，看如何解决
{: id="20210309181757-rv4hphy"}

```java

```
{: id="20210309181757-x13zmia"}

#### 练习2
{: id="20210309181757-7drth3n"}

1、声明银行账户类Account
{: id="20210309181757-yyxtkzx"}

（1）包含账号、余额属性，要求属性私有化，提供无参和有参构造，
{: id="20210309181757-cuh8uw2"}

（2）包含取款方法，当取款金额为负数时，抛出IllegalArgumentException，异常信息为“取款金额有误，不能为负数”，当取款金额超过余额时，抛出UnsupportedOperationException，异常信息为“取款金额不足，不支持当前取款操作”
{: id="20210309181757-g6a9put"}

（3）包含存款方法，当取款金额为负数时，抛出IllegalArgumentException，异常信息为“存款金额有误，不能为负数”
{: id="20210309181757-hsqjkvt"}

2、编写测试类，创建账号对象，并调用取款和存款方法，并传入非法参数，测试发生对应的异常。
{: id="20210309181757-xj1c0qg"}

```java

```
{: id="20210309181757-nisyqr1"}

### 8.5.2 声明异常throws
{: id="20210309181757-151llrc"}

**声明异常**：将问题标识出来，报告给调用者。如果方法内通过throw抛出了**编译时异常**，而没有捕获处理（稍后讲解该方式），那么必须通过throws进行声明，让调用者去处理。
{: id="20210309181757-commdc2"}

关键字**throws**运用于方法声明之上,用于表示当前方法不处理异常,而是提醒该方法的调用者来处理异常(抛出异常).
{: id="20210309181757-246gr6o"}

**声明异常格式：**
{: id="20210309181757-u9y7mli"}

~~~
修饰符 返回值类型 方法名(参数) throws 异常类名1,异常类名2…{   }	
~~~
{: id="20210309181757-8bh6t5s"}

声明异常的代码演示：
{: id="20210309181757-a26em61"}

~~~java
import java.io.File;
import java.io.FileNotFoundException;

public class TestException {
	public static void main(String[] args) throws FileNotFoundException {
		readFile("不敲代码学会Java秘籍.txt");
	}
	
	// 如果定义功能时有问题发生需要报告给调用者。可以通过在方法上使用throws关键字进行声明
	public static void readFile(String filePath) throws FileNotFoundException{
		File file = new File(filePath);
		if(!file.exists()){
			throw new FileNotFoundException(filePath+"文件不存在");
		}
	}
	
}
~~~
{: id="20210309181757-2pdm44b"}

throws用于进行异常类的声明，若该方法可能有多种异常情况产生，那么在throws后面可以写多个异常类，用逗号隔开。
{: id="20210309181757-g5dds3u"}

~~~java
import java.io.File;
import java.io.FileNotFoundException;

public class TestException {
	public static void main(String[] args) throws FileNotFoundException,IllegalAccessException {
		readFile("不敲代码学会Java秘籍.txt");
	}
	
	// 如果定义功能时有问题发生需要报告给调用者。可以通过在方法上使用throws关键字进行声明
	public static void readFile(String filePath) throws FileNotFoundException,IllegalAccessException{
		File file = new File(filePath);
		if(!file.exists()){
			throw new FileNotFoundException(filePath+"文件不存在");
		}
		if(!file.isFile()){
			throw new IllegalAccessException(filePath + "不是文件，无法直接读取");
		}
		//...
	}
	
}
~~~
{: id="20210309181757-ea2zetb"}

#### 练习
{: id="20210309181757-xvkgknx"}

1、声明银行账户类Account
{: id="20210309181757-h6e2p9d"}

（1）包含账号、余额属性，要求属性私有化，提供无参和有参构造，
{: id="20210309181757-lcknqfb"}

（2）包含取款方法，当取款金额为负数时，抛出Exception，异常信息为“越取你余额越多，想得美”，当取款金额超过余额时，抛出Exception，异常信息为“取款金额不足，不支持当前取款操作”
{: id="20210309181757-d5t2cod"}

（3）包含存款方法，当取款金额为负数时，抛出Exception，异常信息为“越存余额越少，你愿意吗？”
{: id="20210309181757-ih7wsi8"}

2、编写测试类，创建账号对象，并调用取款和存款方法，并传入非法参数，测试发生对应的异常。
{: id="20210309181757-ett6f6l"}

```java

```
{: id="20210309181757-my5ighb"}

### 8.5.3 捕获异常try…catch
{: id="20210309181757-um09d1o"}

如果异常出现的话,会立刻终止程序,所以我们得处理异常:
{: id="20210309181757-3f5yi1n"}

1. {: id="20210309181757-avt3jif"}该方法不处理,而是声明抛出,由该方法的调用者来处理(throws)。
   {: id="20210309181757-tyl8f2m"}
2. {: id="20210309181757-fdpuzwf"}在方法中使用try-catch的语句块来处理异常。
   {: id="20210309181757-4m79r2t"}
{: id="20210309181757-enpix5a"}

**try-catch**的方式就是捕获异常。
{: id="20210309181757-wlg833d"}

* {: id="20210309181757-ruhog1o"}**捕获异常**：Java中对异常有针对性的语句进行捕获，可以对出现的异常进行指定方式的处理。
  {: id="20210309181757-kpm7lz9"}
{: id="20210309181757-afl6q5w"}

捕获异常语法如下：
{: id="20210309181757-gwysnem"}

~~~java
try{
     编写可能会出现异常的代码
}catch(异常类型1  e){
     处理异常的代码
     //记录日志/打印异常信息/继续抛出异常
}catch(异常类型2  e){
     处理异常的代码
     //记录日志/打印异常信息/继续抛出异常
}
....
~~~
{: id="20210309181757-ru6uet1"}

**try：**该代码块中编写可能产生异常的代码。
{: id="20210309181757-p01blv1"}

**catch：**用来进行某种异常的捕获，实现对捕获到的异常进行处理。
{: id="20210309181757-deo1z2a"}

* {: id="20210309181757-9n44efm"}可以有多个catch块，按顺序匹配。
  {: id="20210309181757-ffxegaj"}
* {: id="20210309181757-jo1a1tr"}如果多个异常类型有包含关系，那么小上大下
  {: id="20210309181757-ka77jle"}
{: id="20210309181757-6zl3czw"}

演示如下：
{: id="20210309181757-b1dh2ax"}

~~~java
public class TestException {
	public static void main(String[] args)  {
		try {
			readFile("不敲代码学会Java秘籍.txt");
		} catch (FileNotFoundException e) {
//			e.printStackTrace();
//			System.out.println("好好敲代码，不要老是想获得什么秘籍");
			System.out.println(e.getMessage());
		} catch (IllegalAccessException e) {
			e.printStackTrace();
		} 
		
		System.out.println("继续学习吧...");
	}
	
	// 如果定义功能时有问题发生需要报告给调用者。可以通过在方法上使用throws关键字进行声明
	public static void readFile(String filePath) throws FileNotFoundException, IllegalAccessException{
		File file = new File(filePath);
		if(!file.exists()){
			throw new FileNotFoundException(filePath+"文件不存在");
		}
		if(!file.isFile()){
			throw new IllegalAccessException(filePath + "不是文件，无法直接读取");
		}
		//...
	}
	
}
~~~
{: id="20210309181757-sqblro7"}

如何获取异常信息：
{: id="20210309181757-a8rt0sa"}

Throwable类中定义了一些查看方法:
{: id="20210309181757-c1mdylt"}

* {: id="20210309181757-u62irk6"}`public String getMessage()`:获取异常的描述信息,原因(提示给用户的时候,就提示错误原因。
  {: id="20210309181757-1jn0jbr"}
* {: id="20210309181757-1p69q7s"}`public void printStackTrace()`:打印异常的跟踪栈信息并输出到控制台。
  {: id="20210309181757-2vbqgsj"}
{: id="20210309181757-k1cozcc"}

​            *包含了异常的类型,异常的原因,还包括异常出现的位置,在开发和调试阶段,都得使用printStackTrace。*
{: id="20210309181757-zm8ya7r"}

### 8.5.4 finally块
{: id="20210309181757-rizeq79"}

**finally**：有一些特定的代码无论异常是否发生，都需要执行。另外，因为异常会引发程序跳转，导致有些语句执行不到。而finally就是解决这个问题的，在finally代码块中存放的代码都是一定会被执行的。
{: id="20210309181757-dv4s6zl"}

什么时候的代码必须最终执行？
{: id="20210309181757-6jwz3w1"}

当我们在try语句块中打开了一些物理资源(磁盘文件/网络连接/数据库连接等),我们都得在使用完之后,最终关闭打开的资源。
{: id="20210309181757-n2gebw4"}

finally的语法:
{: id="20210309181757-pnel48f"}

```java
 try{
     
 }catch(...){
     
 }finally{
     无论try中是否发生异常，也无论catch是否捕获异常，也不管try和catch中是否有return语句，都一定会执行
 }
 
 或
  try{
     
 }finally{
     无论try中是否发生异常，也不管try中是否有return语句，都一定会执行
 } 
```
{: id="20210309181757-pu3ndoi"}

> 注意:finally不能单独使用。
> {: id="20210309181757-80j5dqz"}
{: id="20210309181757-yjp1rfi"}

比如在我们之后学习的IO流中，当打开了一个关联文件的资源，最后程序不管结果如何，都需要把这个资源关闭掉。
{: id="20210309181757-gkljax6"}

finally代码参考如下：
{: id="20210309181757-9qc6s94"}

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class TestException {
	public static void main(String[] args)  {
		readFile("不敲代码学会Java秘籍.txt");
		System.out.println("继续学习吧...");
	}
	
	// 如果定义功能时有问题发生需要报告给调用者。可以通过在方法上使用throws关键字进行声明
	public static void readFile(String filePath) {
		File file = new File(filePath);
		FileInputStream fis = null;
		try {
			
			if(!file.exists()){
				throw new FileNotFoundException(filePath+"文件不存在");
			}
			if(!file.isFile()){
				throw new IllegalAccessException(filePath + "不是文件，无法直接读取");
			}
			fis = new FileInputStream(file);
			//...
		} catch (Exception e) {
			//抓取到的是编译期异常  抛出去的是运行期 
			throw new RuntimeException(e);
		}finally{
			System.out.println("无论如何，这里的代码一定会被执行");
			try {
				if(fis!=null){
					fis.close();
				}
			} catch (IOException e) {
				//抓取到的是编译期异常  抛出去的是运行期 
				throw new RuntimeException(e);
			}
		}
		
	}
}
```
{: id="20210309181757-babh92i"}

> 当只有在try或者catch中调用退出JVM的相关方法，例如System.exit(0),此时finally才不会执行,否则finally永远会执行。
> {: id="20210309181757-mti5t8a"}
{: id="20210309181757-emq9td5"}

![](imgs12\死了都要try.bmp)
{: id="20210309181757-7tpfhma"}

### 8.5.5 finally与return
{: id="20210309181757-7dttne7"}

#### 形式一：从try回来
{: id="20210309181757-wtqbk9j"}

```java
public class TestReturn {
	public static void main(String[] args) {
		int result = test("12");
		System.out.println(result);
	}

	public static int test(String str){
		try{
			Integer.parseInt(str);
			return 1;
		}catch(NumberFormatException e){
			return -1;
		}finally{
			System.out.println("test结束");
		}
	}
}
```
{: id="20210309181757-4m89tjs"}

#### 形式二：从catch回来
{: id="20210309181757-aaqj3fx"}

```java
public class TestReturn {
	public static void main(String[] args) {
		int result = test("a");
		System.out.println(result);
	}

	public static int test(String str){
		try{
			Integer.parseInt(str);
			return 1;
		}catch(NumberFormatException e){
			return -1;
		}finally{
			System.out.println("test结束");
		}
	}
}
```
{: id="20210309181757-uavh4cs"}

#### 形式三：从finally回来
{: id="20210309181757-n89hm1v"}

```java
public class TestReturn {
	public static void main(String[] args) {
		int result = test("a");
		System.out.println(result);
	}

	public static int test(String str){
		try{
			Integer.parseInt(str);
			return 1;
		}catch(NumberFormatException e){
			return -1;
		}finally{
            System.out.println("test结束");
			return 0;
		}
	}
}
```
{: id="20210309181757-v0zi7w2"}

## 8.6 异常注意事项
{: id="20210309181757-gjdvmv8"}

* {: id="20210309181757-gsbidfj"}多个异常使用捕获又该如何处理呢？
  {: id="20210309181757-nwvi82p"}

  1. {: id="20210309181757-m6zobdw"}多个异常分别处理。
     {: id="20210309181757-ykgf9in"}
  2. {: id="20210309181757-zz257iw"}多个异常一次捕获，多次处理。(推荐)
     {: id="20210309181757-j73320z"}
  3. {: id="20210309181757-q1g7u9z"}多个异常一次捕获一次处理。
     {: id="20210309181757-em5ffs7"}
  {: id="20210309181757-ujhyqob"}

  一般我们是使用一次捕获多次处理方式，格式如下：
  {: id="20210309181757-g99rlff"}

  ```java
  try{
       编写可能会出现异常的代码
  }catch(异常类型A  e){  当try中出现A类型异常,就用该catch来捕获.
       处理异常的代码
       //记录日志/打印异常信息/继续抛出异常
  }catch(异常类型B  e){  当try中出现B类型异常,就用该catch来捕获.
       处理异常的代码
       //记录日志/打印异常信息/继续抛出异常
  }
  ```
  {: id="20210309181757-vsbaipc"}

  > 注意:这种异常处理方式，要求多个catch中的异常不能相同，并且若catch中的多个异常之间有子父类异常的关系，那么子类异常要求在上面的catch处理，父类异常在下面的catch处理。
  > {: id="20210309181757-ddpd0vm"}
  >
  {: id="20210309181757-ppckv8l"}
* {: id="20210309181757-25o62uh"}运行时异常被抛出可以不处理。即不捕获也不声明抛出。
  {: id="20210309181757-92e280c"}
* {: id="20210309181757-ed5j83c"}如果finally有return语句,永远返回finally中的结果,避免该情况.
  {: id="20210309181757-wrhpac2"}
* {: id="20210309181757-7pwqufw"}如果父类抛出了多个异常,子类重写父类方法时,抛出和父类相同的异常或者是父类异常的子类或者不抛出异常。
  {: id="20210309181757-so0yu7f"}
* {: id="20210309181757-jajnt53"}父类方法没有抛出异常，子类重写父类该方法时也不可抛出异常。此时子类方法中产生了编译时异常，只能捕获处理，不能声明抛出
  {: id="20210309181757-sksxaua"}
{: id="20210309181757-d2x3tc5"}

## 8.7 自定义异常
{: id="20210309181757-ri3qcc7"}

**为什么需要自定义异常类:**
{: id="20210309181757-cujorzv"}

我们说了Java中不同的异常类,分别表示着某一种具体的异常情况,那么在开发中总是有些异常情况是Java开发人员没有定义好的,此时我们根据自己业务的异常情况来定义异常类。例如年龄负数问题，考试成绩负数问题等等。那么能不能自己定义异常呢？可以
{: id="20210309181757-jbvozoc"}

**异常类如何定义:**
{: id="20210309181757-1qe1ubg"}

1. {: id="20210309181757-4g6zdox"}自定义一个编译期异常: 自定义类 并继承于`java.lang.Exception`。
   {: id="20210309181757-4jksw0p"}
2. {: id="20210309181757-hp8st0m"}自定义一个运行时期的异常类:自定义类 并继承于`java.lang.RuntimeException`。
   {: id="20210309181757-ql7key5"}
{: id="20210309181757-mkwhnd4"}

**演示自定义异常：**
{: id="20210309181757-wlzowes"}

要求：我们模拟注册操作，如果用户名已存在，则抛出异常并提示：亲，该用户名已经被注册。
{: id="20210309181757-qaj8xb1"}

首先定义一个登陆异常类RegisterException：
{: id="20210309181757-u9z2rj7"}

~~~java
// 业务逻辑异常
public class RegisterException extends Exception {
    /**
     * 空参构造
     */
    public RegisterException() {
    }

    /**
     *
     * @param message 表示异常提示
     */
    public RegisterException(String message) {
        super(message);
    }
}
~~~
{: id="20210309181757-f2al0j7"}

模拟登陆操作，使用数组模拟数据库中存储的数据，并提供当前注册账号是否存在方法用于判断。
{: id="20210309181757-y81125h"}

~~~java
public class Demo {
    // 模拟数据库中已存在账号
    private static String[] names = {"bill","hill","jill"};
   
    public static void main(String[] args) {     
        //调用方法
        try{
              // 可能出现异常的代码
            checkUsername("nill");
            System.out.println("注册成功");//如果没有异常就是注册成功
        }catch(RegisterException e){
            //处理异常
            e.printStackTrace();
        }
    }

    //判断当前注册账号是否存在
    //因为是编译期异常，又想调用者去处理 所以声明该异常
    public static boolean checkUsername(String uname) throws LoginException{
        for (int i=0; i<names.length; i++) {
            if(names[i].equals(uname)){//如果名字在这里面 就抛出登陆异常
                throw new RegisterException("亲"+name+"已经被注册了！");
            }
        }
        return true;
    }
}
~~~
{: id="20210309181757-01nouby"}

结论：
{: id="20210309181757-42ezibd"}

* {: id="20210309181757-pv36tgu"}从Exception类或者它的子类派生一个子类即可
  {: id="20210309181757-arvwhnr"}
* {: id="20210309181757-d3of6u5"}习惯上，自定义异常类应该包含2个构造器：一个是无参构造，另一个是带有详细信息的构造器
  {: id="20210309181757-fp8r0mj"}
* {: id="20210309181757-z7q4599"}自定义的异常只能通过throw抛出。
  {: id="20210309181757-4xm6umm"}
* {: id="20210309181757-yp4xzig"}自定义异常最重要的是异常类的名字，当异常出现时，可以根据名字判断异常类型。
  {: id="20210309181757-zm0mlvv"}
{: id="20210309181757-a9767e5"}


{: id="20210309181757-6b0x7r6" type="doc"}
