# JavaSE_day19【IO流】
{: id="20210313082711-ddkp3ss"}

## 主要内容
{: id="20210313082711-irtivla"}

* {: id="20210313082711-19v4fbm"}File类
  {: id="20210313082711-uq6qlz3"}
* {: id="20210313082711-pu3gro8"}字节流
  {: id="20210313082711-zqbhrzg"}
* {: id="20210313082711-p0bhc7y"}字符流
  {: id="20210313082711-rysxdn4"}
* {: id="20210313082711-zs2xwuq"}文件流
  {: id="20210313082711-mf33k85"}
* {: id="20210313082711-oj1rss6"}缓冲流
  {: id="20210313082711-x6sm2ix"}
* {: id="20210313082711-fco2ru8"}转换流
  {: id="20210313082711-irmxu0y"}
* {: id="20210313082711-2bvqrc4"}数据流
  {: id="20210313082711-q25625s"}
* {: id="20210313082711-hpx7lub"}对象流
  {: id="20210313082711-gslvids"}
* {: id="20210313082711-pe5ir78"}打印流
  {: id="20210313082711-s52z229"}
* {: id="20210313082711-u8qwpms"}Scanner与System与IO流
  {: id="20210313082711-79mbya5"}
{: id="20210313082711-s72lgby"}

## 教学目标
{: id="20210313082711-63q2ufw"}

- {: id="20210313082711-y44z87p"}[ ] 能够说出File对象的创建方式
  {: id="20210313082711-2l3bee8"}
- {: id="20210313082711-jxcc2jg"}[ ] 能够辨别相对路径和绝对路径
  {: id="20210313082711-7chbyes"}
- {: id="20210313082711-u8wkqu1"}[ ] 能够使用字节输出流写出数据到文件
  {: id="20210313082711-lzt4lg4"}
- {: id="20210313082711-5z1z4zy"}[ ] 能够使用字节输入流读取数据到程序
  {: id="20210313082711-ow5i3ot"}
- {: id="20210313082711-gjlwv0z"}[ ] 能够使用FileWirter写数据到文件
  {: id="20210313082711-vwvuiyh"}
- {: id="20210313082711-elv7tfy"}[ ] 能够使用FileReader从文件中读数据
  {: id="20210313082711-qqnbu79"}
- {: id="20210313082711-qgprrrf"}[ ] 能够使用字节缓冲流读取数据到程序
  {: id="20210313082711-aw3y0ro"}
- {: id="20210313082711-5o1kyy9"}[ ] 能够使用字节缓冲流写出数据到文件
  {: id="20210313082711-jmcwhbi"}
- {: id="20210313082711-aaovqex"}[ ] 能够使用转换流读取指定编码的文本文件
  {: id="20210313082711-u1mvynp"}
- {: id="20210313082711-ry0ylq6"}[ ] 能够使用转换流写入指定编码的文本文件
  {: id="20210313082711-43xz8wi"}
- {: id="20210313082711-hx7qzul"}[ ] 能够使用序列化流写出对象到文件
  {: id="20210313082711-ojb2znj"}
- {: id="20210313082711-glmefen"}[ ] 能够使用反序列化流读取文件到程序中
  {: id="20210313082711-r7amq2r"}
{: id="20210313082711-0f5xa3f"}

# 第十四章 File类与IO流
{: id="20210313082711-wyeksxj"}

## 14.1 java.io.File类
{: id="20210313082711-wm7uafu"}

### 14.1.1 概述
{: id="20210313082711-o36vkkd"}

File类是java.io包下代表与平台无关的文件和目录，也就是说如果希望在程序中操作文件和目录都可以通过File类来完成，File类能新建、删除、重命名文件和目录。
{: id="20210313082711-e7laiuo"}

在API中File的解释是文件和目录路径名的抽象表示形式，即File类是文件或目录的路径，而不是文件本身，因此File类不能直接访问文件内容本身，如果需要访问文件内容本身，则需要使用输入/输出流。
{: id="20210313082711-lpbspom"}

> File类代表磁盘或网络中某个文件或目录的路径名称，如：/atguigu/javase/io/佟刚.jpg
> {: id="20210313082711-81171zu"}
>
> 但不能直接通过File对象读取和写入数据，如果要操作数据，需要IO流。File对象好比是到水库的“路线地址”，要“存取”里面的水到你“家里”，需要“管道”。
> {: id="20210313082711-tatk3md"}
{: id="20210313082711-7nt76ij"}

![1563809289418](imgs19/1563809289418.png)
{: id="20210313082711-uewmbvb"}

### 14.1.2 构造方法
{: id="20210313082711-t4pbhc6"}

* {: id="20210313082711-ieflam7"}`public File(String pathname) ` ：通过将给定的**路径名字符串**转换为抽象路径名来创建新的 File实例。
  {: id="20210313082711-w2ui3s0"}
* {: id="20210313082711-pu0t1qr"}`public File(String parent, String child) ` ：从**父路径名字符串和子路径名字符串**创建新的 File实例。
  {: id="20210313082711-gieyuob"}
* {: id="20210313082711-pgczrlg"}`public File(File parent, String child)` ：从**父抽象路径名和子路径名字符串**创建新的 File实例。
  {: id="20210313082711-xor0zgn"}
* {: id="20210313082711-hv1bdp4"}构造举例，代码如下：
  {: id="20210313082711-p68pdkm"}
{: id="20210313082711-qputt7i"}

```java
// 文件路径名
String pathname = "D:\\aaa.txt";
File file1 = new File(pathname); 

// 文件路径名
String pathname2 = "D:\\aaa\\bbb.txt";
File file2 = new File(pathname2); 

// 通过父路径和子路径字符串
 String parent = "d:\\aaa";
 String child = "bbb.txt";
 File file3 = new File(parent, child);

// 通过父级File对象和子路径字符串
File parentDir = new File("d:\\aaa");
String child = "bbb.txt";
File file4 = new File(parentDir, child);
```
{: id="20210313082711-7r1qkpq"}

> 小贴士：
> {: id="20210313082711-ieqz0zh"}
>
> 1. {: id="20210313082711-spslyao"}一个File对象代表硬盘中实际存在的一个文件或者目录。
>    {: id="20210313082711-d52oa5i"}
> 2. {: id="20210313082711-wv7xptv"}无论该路径下是否存在文件或者目录，都不影响File对象的创建。
>    {: id="20210313082711-2elf0m2"}
> {: id="20210313082711-cg8kk27"}
{: id="20210313082711-nupr81b"}

### 14.1.3 常用方法
{: id="20210313082711-4wmqfzh"}

#### 1、获取文件和目录基本信息的方法
{: id="20210313082711-lv2a415"}

* {: id="20210313082711-j4aq2jz"}`public String getName()`  ：返回由此File表示的文件或目录的名称。
  {: id="20210313082711-052g3ul"}
* {: id="20210313082711-4b6354s"}`public long length()`  ：返回由此File表示的文件的长度。
  {: id="20210313082711-c2cwr30"}
* {: id="20210313082711-rhb2p7k"}`public String getPath()` ：将此File转换为路径名字符串。
  {: id="20210313082711-hn6amur"}
* {: id="20210313082711-b431nqx"}`public long lastModified()`：返回File对象对应的文件或目录的最后修改时间（毫秒值）
  {: id="20210313082711-6nt2tu9"}
  方法演示，代码如下：
  {: id="20210313082711-s53xsxn"}
  ```java
  import java.io.File;
  import java.time.Instant;
  import java.time.LocalDateTime;
  import java.time.ZoneId;

  public class TestFile {
      public static void main(String[] args) {
          File f = new File("d:/aaa/bbb.txt");     
          System.out.println("文件构造路径:"+f.getPath());
          System.out.println("文件名称:"+f.getName());
          System.out.println("文件长度:"+f.length()+"字节");
          System.out.println("文件最后修改时间：" + LocalDateTime.ofInstant(Instant.ofEpochMilli(f.lastModified()),ZoneId.of("Asia/Shanghai")));

          File f2 = new File("d:/aaa");     
          System.out.println("目录构造路径:"+f2.getPath());
          System.out.println("目录名称:"+f2.getName());
          System.out.println("目录长度:"+f2.length()+"字节");
          System.out.println("文件最后修改时间：" + LocalDateTime.ofInstant(Instant.ofEpochMilli(f.lastModified()),ZoneId.of("Asia/Shanghai")));
      }
  }

  输出结果：
  文件构造路径:d:\aaa\bbb.java
  文件名称:bbb.java
  文件长度:636字节
  文件最后修改时间：2019-07-23T22:01:32.065

  目录构造路径:d:\aaa
  目录名称:aaa
  目录长度:4096字节
  文件最后修改时间：2019-07-23T22:01:32.065
  ```
  {: id="20210313082711-4d34jdc"}
{: id="20210313082711-2j12njx"}

> API中说明：length()，表示文件的长度。但是File对象表示目录，则返回值未指定。
> {: id="20210313082711-4i6tkx2"}
{: id="20210313082711-s6om670"}

#### 2、各种路径问题
{: id="20210313082711-nw68g0n"}

* {: id="20210313082711-msygnbf"}`public String getPath()` ：将此File转换为路径名字符串。
  {: id="20210313082711-bcvxsnx"}
* {: id="20210313082711-bi81shb"}`public String getAbsolutePath() ` ：返回此File的绝对路径名字符串。
  {: id="20210313082711-pixc9pl"}
* {: id="20210313082711-gsad1dl"}`String getCanonicalPath()`：返回此File对象所对应的规范路径名。
  {: id="20210313082711-9xt0x53"}
{: id="20210313082711-53tebtk"}

File类可以使用文件路径字符串来创建File实例，该文件路径字符串既可以是绝对路径，也可以是相对路径。
{: id="20210313082711-ic55e7w"}

默认情况下，系统总是依据用户的工作路径来解释相对路径，这个路径由系统属性“user.dir”指定，通常也就是运行Java虚拟机时所作的路径。
{: id="20210313082711-sd1hnnw"}

* {: id="20210313082711-jks0jhz"}**绝对路径**：从盘符开始的路径，这是一个完整的路径。
  {: id="20210313082711-0l70fyr"}
* {: id="20210313082711-i9jxq6k"}**相对路径**：相对于**项目目录**的路径，这是一个便捷的路径，开发中经常使用。
  {: id="20210313082711-wsuq1f0"}
* {: id="20210313082711-060dwzo"}**规范路径**：所谓规范路径名，即对路径中的“..”等进行解析后的路径名
  {: id="20210313082711-nj0f430"}
{: id="20210313082711-fu80fm0"}

```java
	@Test
	public void test1() throws IOException{
		File f1 = new File("d:\\atguigu\\javase\\HelloIO.java");
		System.out.println("文件/目录的名称：" + f1.getName());
		System.out.println("文件/目录的构造路径名：" + f1.getPath());
		System.out.println("文件/目录的绝对路径名：" + f1.getAbsolutePath());
		System.out.println("文件/目录的规范路径名：" + f1.getCanonicalPath());
		System.out.println("文件/目录的父目录名：" + f1.getParent());
	}
	@Test
	public void test2() throws IOException{
		File f2 = new File("HelloIO.java");
		System.out.println("user.dir =" + System.getProperty("user.dir"));
		System.out.println("文件/目录的名称：" + f2.getName());
		System.out.println("文件/目录的构造路径名：" + f2.getPath());
		System.out.println("文件/目录的绝对路径名：" + f2.getAbsolutePath());
		System.out.println("文件/目录的规范路径名：" + f2.getCanonicalPath());
		System.out.println("文件/目录的父目录名：" + f2.getParent());
	}
		@Test
	public void test3() throws IOException{
		File f3 = new File("../../HelloIO.java");
		System.out.println("user.dir =" + System.getProperty("user.dir"));
		System.out.println("文件/目录的名称：" + f3.getName());
		System.out.println("文件/目录的构造路径名：" + f3.getPath());
		System.out.println("文件/目录的绝对路径名：" + f3.getAbsolutePath());
		System.out.println("文件/目录的规范路径名：" + f3.getCanonicalPath());
		System.out.println("文件/目录的父目录名：" + f3.getParent());
	}
```
{: id="20210313082711-oqljc9d"}

* {: id="20210313082711-d8w331o"}window的路径分隔符使用“\”，而Java程序中的“\”表示转义字符，所以在Windows中表示路径，需要用“\\”。或者直接使用“/”也可以，Java程序支持将“/”当成平台无关的路径分隔符。或者直接使用File.separator常量值表示。
  {: id="20210313082711-e3blkp6"}
* {: id="20210313082711-7rjnhm0"}把构造File对象指定的文件或目录的路径名，称为构造路径，它可以是绝对路径，也可以是相对路径
  {: id="20210313082711-2mjpnru"}
* {: id="20210313082711-uqfg5vp"}当构造路径是绝对路径时，那么getPath和getAbsolutePath结果一样
  {: id="20210313082711-28n1qx3"}
* {: id="20210313082711-hmd0umx"}当构造路径是相对路径时，那么getAbsolutePath的路径 = user.dir的路径 + 构造路径
  {: id="20210313082711-bigvyx6"}
* {: id="20210313082711-wsr4tg8"}当路径中不包含".."和"/开头"等形式的路径，那么规范路径和绝对路径一样，否则会将..等进行解析。路径中如果出现“..”表示上一级目录，路径名如果以“/”开头，表示从“根目录”下开始导航。
  {: id="20210313082711-x7kkkf3"}
{: id="20210313082711-185vz3h"}

#### 3、判断功能的方法
{: id="20210313082711-0blbyxg"}

- {: id="20210313082711-4y4iuqj"}`public boolean exists()` ：此File表示的文件或目录是否实际存在。
  {: id="20210313082711-loohbdz"}
- {: id="20210313082711-dtytnxj"}`public boolean isDirectory()` ：此File表示的是否为目录。
  {: id="20210313082711-36k180z"}
- {: id="20210313082711-240c4xy"}`public boolean isFile()` ：此File表示的是否为文件。
  {: id="20210313082711-fa3rfb2"}
- {: id="20210313082711-slaupio"}`public isAbsolute()`：判断File对象对应的文件或目录是否是绝对路径
  {: id="20210313082711-1t5x629"}
- {: id="20210313082711-5v393nf"}`public boolean canRead()`：判断File对象对应的文件或目录是否可读
  {: id="20210313082711-7o990j5"}
- {: id="20210313082711-f721yae"}`public boolean canWrite()`：判断File对象对应的文件或目录是否可写
  {: id="20210313082711-g6n2aua"}
- {: id="20210313082711-k231dc1"}`public boolean isHidden()`：判断File对象对应的文件或目录是否是否隐藏
  {: id="20210313082711-nnsxu6f"}
{: id="20210313082711-fhqtihq"}

方法演示，代码如下：
{: id="20210313082711-a3y1dqm"}

```java
public class FileIs {
    public static void main(String[] args) {
        File f = new File("d:\\aaa\\bbb.java");
        File f2 = new File("d:\\aaa");
      	// 判断是否存在
        System.out.println("d:\\aaa\\bbb.java 是否存在:"+f.exists());
        System.out.println("d:\\aaa 是否存在:"+f2.exists());
      	// 判断是文件还是目录
        System.out.println("d:\\aaa 文件?:"+f2.isFile());
        System.out.println("d:\\aaa 目录?:"+f2.isDirectory());
    }
}
输出结果：
d:\aaa\bbb.java 是否存在:true
d:\aaa 是否存在:true
d:\aaa 文件?:false
d:\aaa 目录?:true
```
{: id="20210313082711-fbf9eoy"}

> 如果文件或目录不存在，那么exists()、isFile()和isDirectory()都是返回true
> {: id="20210313082711-ua8ks4e"}
{: id="20210313082711-kjn240j"}

#### 4、创建删除功能的方法
{: id="20210313082711-clemdk1"}

- {: id="20210313082711-h32yutn"}`public boolean createNewFile()` ：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
  {: id="20210313082711-fr9ognd"}
- {: id="20210313082711-tctzb7o"}`public boolean delete()` ：删除由此File表示的文件或目录。  只能删除空目录。
  {: id="20210313082711-zx30py5"}
- {: id="20210313082711-mirakq3"}`public boolean mkdir()` ：创建由此File表示的目录。
  {: id="20210313082711-ayw6f64"}
- {: id="20210313082711-94kehp8"}`public boolean mkdirs()` ：创建由此File表示的目录，包括任何必需但不存在的父目录。
  {: id="20210313082711-x03a8t5"}
{: id="20210313082711-ta9mdl5"}

方法演示，代码如下：
{: id="20210313082711-33xyoey"}

```java
public class FileCreateDelete {
    public static void main(String[] args) throws IOException {
        // 文件的创建
        File f = new File("aaa.txt");
        System.out.println("是否存在:"+f.exists()); // false
        System.out.println("是否创建:"+f.createNewFile()); // true
        System.out.println("是否存在:"+f.exists()); // true
		
     	// 目录的创建
      	File f2= new File("newDir");	
        System.out.println("是否存在:"+f2.exists());// false
        System.out.println("是否创建:"+f2.mkdir());	// true
        System.out.println("是否存在:"+f2.exists());// true

		// 创建多级目录
      	File f3= new File("newDira\\newDirb");
        System.out.println(f3.mkdir());// false
        File f4= new File("newDira\\newDirb");
        System.out.println(f4.mkdirs());// true
      
      	// 文件的删除
       	System.out.println(f.delete());// true
      
      	// 目录的删除
        System.out.println(f2.delete());// true
        System.out.println(f4.delete());// false
    }
}
```
{: id="20210313082711-f4fx2gd"}

> API中说明：delete方法，如果此File表示目录，则目录必须为空才能删除。
> {: id="20210313082711-hkhu6pt"}
{: id="20210313082711-g2egwd3"}

#### 5、创建和删除临时文件
{: id="20210313082711-7kwjut2"}

* {: id="20210313082711-i7stsyd"}`public void deleteOnExit()`：当退出JVM时，删除文件，一般用于删除临时文件，一旦请求，无法取消。
  {: id="20210313082711-2fdlci6"}
* {: id="20210313082711-kq5tkev"}public static File createTempFile(String prefix,String suffix) throws IOException在默认临时文件目录中创建一个空文件，使用给定前缀和后缀生成其名称。调用此方法等同于调用 createTempFile(prefix, suffix, null)。
  {: id="20210313082711-qdapdz1"}
  * {: id="20210313082711-l7budpj"}prefix - 用于生成文件名的前缀字符串；必须至少三个字符。
    {: id="20210313082711-biiue7m"}
  * {: id="20210313082711-rixono7"}suffix - 用于生成文件名的后缀字符串；如果为 null，默认为 ".tmp"
    {: id="20210313082711-mlwo2eo"}
  {: id="20210313082711-b8d4yiz"}
* {: id="20210313082711-305ds9e"}public static File createTempFile(String prefix,String suffix,File directory)throws IOException在指定目录中创建一个新的空文件，使用给定的前缀和后缀字符串生成其名称。
  {: id="20210313082711-puu3ggm"}
  * {: id="20210313082711-vac6mfy"}prefix - 用于生成文件名的前缀字符串；必须至少三个字符。
    {: id="20210313082711-qct1k9l"}
  * {: id="20210313082711-6fnzu3w"}suffix - 用于生成文件名的后缀字符串；如果为 null，默认为 ".tmp"
    {: id="20210313082711-ua9ovdr"}
  * {: id="20210313082711-t5fbjk7"}directory - 将创建的文件所在的目录；如果使用默认临时文件目录，则该参数为 null
    {: id="20210313082711-2t9n8kv"}
  {: id="20210313082711-w76xjst"}
{: id="20210313082711-05ymfhc"}

```java
import java.io.File;
import java.io.IOException;

import org.junit.Test;

public class TestFile {
	@Test
	public void test6() throws IOException{
		File tempFile = File.createTempFile("Hello", ".tmp");
		System.out.println(tempFile.getAbsolutePath());
		try {
			Thread.sleep(10000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		tempFile.deleteOnExit();
		//C:\Users\Irene\AppData\Local\Temp\Hello2541030191749214481.tmp
	}
}
```
{: id="20210313082711-4vpjcos"}

> 创建临时文件，通常会结合deleteOnExit()使用
> {: id="20210313082711-gszinji"}
{: id="20210313082711-ilju8kr"}

#### 6、重命名功能的方法
{: id="20210313082711-u70qktd"}

* {: id="20210313082711-6lfqrpx"}`public boolean renameTo(File dest)`：重命名文件或目录
  {: id="20210313082711-7xfuwt5"}
{: id="20210313082711-wcvlh2t"}

此方法行为的许多方面都是与平台有关的：
{: id="20210313082711-n74vort"}

如果是重命名文件，那么重命名操作无法将一个文件从一个文件系统移动到另一个文件系统，该操作不是不可分的，如果已经存在具有目标抽象路径名的文件，那么该操作可能无法获得成功。应该始终检查返回值，以确保重命名操作成功。
{: id="20210313082711-njx9xe6"}

如果是重命名目录，那么如果是windows目录，只能在同一个盘下，不能从D盘移动到E盘。
{: id="20210313082711-movhzbi"}

```java
	@Test
	public void test9(){
		File src = new File("d:/atguigu/javase/HelloIO.java");
		File dest = new File("d:/atguigu/javase/HelloFile.java");
		src.renameTo(dest);
	}
	@Test
	public void test10() {
		File src = new File("d:/atguigu/javase/HelloIO.java");
		File dest = new File("e:/HelloFile.java");
         //D盘和E盘相同的文件系统可以成功，例如都是NTFS。
		src.renameTo(dest);
	}
```
{: id="20210313082711-13z99nt"}

```java
	@Test
	public void test7() {
		 File dir = new File("D:/atguigu/javase");
		 File dest = new File("D:/atguigu/java代码");
		dir.renameTo(dest);
	}
		@Test
	public void test8() {
		 File dir = new File("D:/atguigu/javase");
		 File dest = new File("D:/temp");
		dir.renameTo(dest);
	}
```
{: id="20210313082711-thqu2jz"}

#### 7、目录的遍历
{: id="20210313082711-bov4map"}

* {: id="20210313082711-pesoi8q"}`public String[] list()` ：返回一个String数组，表示该File目录中的所有子文件或目录。
  {: id="20210313082711-arrz3cb"}
* {: id="20210313082711-imey9yc"}`public File[] listFiles()` ：返回一个File数组，表示该File目录中的所有的子文件或目录。
  {: id="20210313082711-j0g3fct"}
* {: id="20210313082711-p8szocg"}`public File[] listFiles(FileFilter filter)`：返回所有满足指定过滤器的文件和目录。如果给定 filter 为 null，则接受所有路径名。否则，当且仅当在路径名上调用过滤器的 FileFilter.accept(java.io.File) 方法返回 true 时，该路径名才满足过滤器。如果当前File对象不表示一个目录，或者发生 I/O 错误，则返回 null。
  {: id="20210313082711-1atoiff"}
* {: id="20210313082711-ql1rh0h"}`public File[] listFiles(FilenameFilter filter)`：返回所有满足指定过滤器的文件和目录。如果给定 filter 为 null，则接受所有路径名。否则，当且仅当在路径名上调用过滤器的 FilenameFilter.accept(java.io.File, java.lang.String) 方法返回 true 时，该路径名才满足过滤器。如果当前File对象不表示一个目录，或者发生 I/O 错误，则返回 null。
  {: id="20210313082711-tprbl1b"}
* {: id="20210313082711-md1j9a8"}`public static File[] listRoots()`：列出可用的文件系统根。
  {: id="20210313082711-j25hux1"}
{: id="20210313082711-8nru29o"}

```java
public class FileFor {
    public static void main(String[] args) {
        File dir = new File("d:\\java_code");
      
      	//获取当前目录下的文件以及文件夹的名称。
		String[] names = dir.list();
		for(String name : names){
			System.out.println(name);
		}
        //获取当前目录下的文件以及文件夹对象，只要拿到了文件对象，那么就可以获取更多信息
        File[] files = dir.listFiles();
        for (File file : files) {
            System.out.println(file);
        }
    }
}
```
{: id="20210313082711-978uf9q"}

> 小贴士：
> {: id="20210313082711-xne9n1h"}
>
> 调用listFiles方法的File对象，表示的必须是实际存在的目录，否则返回null，无法进行遍历。
> {: id="20210313082711-jsdhoyo"}
{: id="20210313082711-vxfunpj"}

```java
import java.io.File;
import java.io.FilenameFilter;
import java.io.IOException;

import org.junit.Test;

public class TestFile {
	@Test
	public void test6() throws IOException {
		File dir = new File("D:/atguigu/javaee/JavaSE20190624/code/day03_code");
		File[] listFiles = dir.listFiles(new FilenameFilter() {

			@Override
			public boolean accept(File dir, String name) {
				return name.endsWith(".java");
			}
		});
		if (listFiles != null) {
			for (File sub : listFiles) {
				if (sub.isFile()) {
					System.out.println(sub);
				}
			}
		}
	}
}
```
{: id="20210313082711-9mtnhor"}

### 14.1.4 递归实现多级目录操作
{: id="20210313082711-fk24c5j"}

#### 1、递归打印多级目录
{: id="20210313082711-8k94d93"}

**分析**：多级目录的打印。遍历之前，无从知道到底有多少级目录，所以我们可以使用递归实现。
{: id="20210313082711-7u7qjjz"}

**代码实现**：
{: id="20210313082711-a6bfy8m"}

```java
	@Test
	public void test3() {
		 File dir = new File("d:/atguigu");
		 listSubFiles(dir);
	}

	public void listSubFiles(File dir) {
		if (dir != null && dir.isDirectory()) {
			File[] listFiles = dir.listFiles();
			if (listFiles != null) {
				for (File sub : listFiles) {
					listSubFiles(sub);//递归调用
				}
			}
		}
		System.out.println(dir);
	}
```
{: id="20210313082711-9ntc1hw"}

#### 2、递归打印某目录下（包括子目录）中所有满足条件的文件
{: id="20210313082711-w6qnce5"}

示例代码：列出"D:/atguigu"下所有".java"文件
{: id="20210313082711-m8xlb1i"}

```java
	@Test
	public void test5() {
		 File dir = new File("D:/atguigu");
		 listByFileFilter(dir);
	}
	
	public void listByFileFilter(File file) {
		if (file != null && file.isDirectory()) {
			File[] listFiles = file.listFiles(new FilenameFilter() {

				@Override
				public boolean accept(File dir, String name) {
					return name.endsWith(".java") || new File(dir,name).isDirectory();
				}
			});
			if (listFiles != null) {
				for (File sub : listFiles) {
					if(sub.isFile()){
						System.out.println(sub);
					}
					listByFileFilter(sub);
				}
			}
		}
	}
```
{: id="20210313082711-j1tdq94"}

#### 3、递归求目录总大小
{: id="20210313082711-lim71gc"}

```java
	@Test
	public void test4() {
		 File dir = new File("D:/atguigu");
		 long length = getLength(dir);
		 System.out.println("大小：" + length);
	}
	
	public long getLength(File dir){
		if (dir != null && dir.isDirectory()) {
			File[] listFiles = dir.listFiles();
			if(listFiles!=null){
				long sum = 0;
				for (File sub : listFiles) {
					sum += getLength(sub);
				}
				return sum;
			}
		}else if(dir != null && dir.isFile()){
			return dir.length();
		}
		return 0;
	}
```
{: id="20210313082711-6uvsl1v"}

#### 4、递归删除非空目录
{: id="20210313082711-i56sb8b"}

如果目录非空，连同目录下的文件和文件夹一起删除
{: id="20210313082711-m8hausv"}

```java
	@Test
	public void test6() {
		 File dir = new File("D:/atguigu/javase");
		 forceDeleteDir(dir);
	}
	public void forceDeleteDir(File dir) {
		if (dir != null && dir.isDirectory()) {
			File[] listFiles = dir.listFiles();
			if(listFiles!=null){
				for (File sub : listFiles) {
					forceDeleteDir(sub);
				}
			}
		}
		dir.delete();
	}
```
{: id="20210313082711-gr8g99b"}

## 14.2 IO概述
{: id="20210313082711-sfru84t"}

### 1、什么是IO
{: id="20210313082711-is836cf"}

生活中，你肯定经历过这样的场景。当你编辑一个文本文件，忘记了`ctrl+s` ，可能文件就白白编辑了。当你电脑上插入一个U盘，可以把一个视频，拷贝到你的电脑硬盘里。那么数据都是在哪些设备上的呢？键盘、内存、硬盘、外接设备等等。
{: id="20210313082711-10xyhtx"}

我们把这种数据的传输，可以看做是一种数据的流动，按照流动的方向，以内存为基准，分为`输入input` 和`输出output` ，即流向内存是输入流，流出内存的输出流。
{: id="20210313082711-gq9hz6b"}

Java中I/O操作主要是指使用`java.io`包下的内容，进行输入、输出操作。**输入**也叫做**读取**数据，**输出**也叫做作**写出**数据。
{: id="20210313082711-a9cna6r"}

### 2、IO的分类
{: id="20210313082711-vz5vda9"}

根据数据的流向分为：**输入流**和**输出流**。
{: id="20210313082711-8x5u2ww"}

- {: id="20210313082711-wrtaykp"}**输入流** ：把数据从`其他设备`上读取到`内存`中的流。
  {: id="20210313082711-d39n3n2"}
  - {: id="20210313082711-q2jkseq"}以InputStream,Reader结尾
    {: id="20210313082711-z4niljz"}
  {: id="20210313082711-ex6a8j8"}
- {: id="20210313082711-c76qxc1"}**输出流** ：把数据从`内存` 中写出到`其他设备`上的流。
  {: id="20210313082711-o0ldb3v"}
  - {: id="20210313082711-y7ywi9q"}以OutputStream、Writer结尾
    {: id="20210313082711-m9nibko"}
  {: id="20210313082711-bzt7uvs"}
{: id="20210313082711-w9277v2"}

根据数据的类型分为：**字节流**和**字符流**。
{: id="20210313082711-ia0rjy3"}

- {: id="20210313082711-qar8e8y"}**字节流** ：以字节为单位，读写数据的流。
  {: id="20210313082711-mtwnphi"}
  - {: id="20210313082711-6y30zfr"}以InputStream和OutputStream结尾
    {: id="20210313082711-wiv8opr"}
  {: id="20210313082711-00obw48"}
- {: id="20210313082711-k35yj25"}**字符流** ：以字符为单位，读写数据的流。
  {: id="20210313082711-jx52qns"}
  - {: id="20210313082711-297qtey"}以Reader和Writer结尾
    {: id="20210313082711-4vkmf75"}
  {: id="20210313082711-c0az25l"}
{: id="20210313082711-yxigcf5"}

根据IO流的角色不同分为：**节点流**和**处理流**。
{: id="20210313082711-bwmjybw"}

* {: id="20210313082711-ady8bee"}**节点流**：可以从或向一个特定的地方（节点）读写数据。如FileReader.
  {: id="20210313082711-hgxuuei"}
* {: id="20210313082711-ugz0866"}**处理流**：是对一个已存在的流进行连接和封装，通过所封装的流的功能调用实现数据读写。如BufferedReader.处理流的构造方法总是要带一个其他的流对象做参数。一个流对象经过其他流的多次包装，称为流的链接。
  {: id="20210313082711-dtxktt9"}
{: id="20210313082711-bfut4fb"}

> 这种设计是装饰模式（Decorator Pattern）也称为包装模式（Wrapper Pattern），其使用一种对客户端透明的方式来动态地扩展对象的功能，它是通过继承扩展功能的替代方案之一。在现实生活中你也有很多装饰者的例子，例如：人需要各种各样的衣着，不管你穿着怎样，但是，对于你个人本质来说是不变的，充其量只是在外面加上了一些装饰，有，“遮羞的”、“保暖的”、“好看的”、“防雨的”....
> {: id="20210313082711-2skantk"}
{: id="20210313082711-1j7jgft"}

**常用的节点流：** 　
{: id="20210313082711-l5q03lq"}

* {: id="20210313082711-0f5nxha"}文 件 FileInputStream FileOutputStrean FileReader FileWriter 文件进行处理的节点流。
  {: id="20210313082711-9gx4cmu"}
* {: id="20210313082711-28xf1g7"}字符串 StringReader StringWriter 对字符串进行处理的节点流。
  {: id="20210313082711-v0c0w39"}
* {: id="20210313082711-cful8ee"}数 组 ByteArrayInputStream ByteArrayOutputStream CharArrayReader CharArrayWriter 对数组进行处理的节点流（对应的不再是文件，而是内存中的一个数组）。
  {: id="20210313082711-vet9nh6"}
* {: id="20210313082711-i98m4n3"}管 道 PipedInputStream、PipedOutputStream、PipedReader、PipedWriter对管道进行处理的节点流。
  {: id="20210313082711-mdy90xb"}
{: id="20210313082711-ejfppr3"}

**常用处理流：**
{: id="20210313082711-ujl7c95"}

* {: id="20210313082711-rcg3c5n"}缓冲流：BufferedInputStream、BufferedOutputStream、BufferedReader、BufferedWriter---增加缓冲功能，避免频繁读写硬盘。
  {: id="20210313082711-n8yyee3"}
* {: id="20210313082711-ohw6lyi"}转换流：InputStreamReader、OutputStreamReader---实现字节流和字符流之间的转换。
  {: id="20210313082711-6f4dn0m"}
* {: id="20210313082711-y6g52ns"}数据流：DataInputStream、DataOutputStream -提供读写Java基础数据类型功能
  {: id="20210313082711-ockcs72"}
* {: id="20210313082711-4ft5qf6"}对象流：ObjectInputStream、ObjectOutputStream--提供直接读写Java对象功能
  {: id="20210313082711-u5re0v4"}
{: id="20210313082711-tz9c9n5"}

### 3、4大顶级抽象父类们
{: id="20210313082711-m5ubpl0"}

|            |        **输入流**        |           输出流           |
| :--------: | :-----------------------: | :------------------------: |
| **字节流** | 字节输入流**InputStream** | 字节输出流**OutputStream** |
| **字符流** |   字符输入流**Reader**   |    字符输出流**Writer**    |
{: id="20210313082711-krf7e91"}

## 14.3 字节流
{: id="20210313082711-g6cmrop"}

### 14.3.1  一切皆为字节
{: id="20210313082711-e31vgo0"}

一切文件数据(文本、图片、视频等)在存储时，都是以二进制数字的形式保存，都一个一个的字节，那么传输时一样如此。所以，字节流可以传输任意文件数据。在操作流的时候，我们要时刻明确，无论使用什么样的流对象，底层传输的始终为二进制数据。
{: id="20210313082711-kkqsqm1"}

### 14.3.2 字节输出流【OutputStream】
{: id="20210313082711-usefxbw"}

`java.io.OutputStream `抽象类是表示字节输出流的所有类的超类，将指定的字节信息写出到目的地。它定义了字节输出流的基本共性功能方法。
{: id="20210313082711-h29u0ig"}

- {: id="20210313082711-3ptmwbu"}`public void close()` ：关闭此输出流并释放与此流相关联的任何系统资源。
  {: id="20210313082711-dohaz3o"}
- {: id="20210313082711-0z8as0e"}`public void flush() ` ：刷新此输出流并强制任何缓冲的输出字节被写出。
  {: id="20210313082711-yj8mjrz"}
- {: id="20210313082711-ck6lr53"}`public void write(byte[] b)`：将 b.length字节从指定的字节数组写入此输出流。
  {: id="20210313082711-odznxxg"}
- {: id="20210313082711-sdek0gl"}`public void write(byte[] b, int off, int len)` ：从指定的字节数组写入 len字节，从偏移量 off开始输出到此输出流。
  {: id="20210313082711-q8wlsjk"}
- {: id="20210313082711-47uo3mf"}`public abstract void write(int b)` ：将指定的字节输出流。
  {: id="20210313082711-b919t7n"}
{: id="20210313082711-a6ylmkk"}

> 小贴士：
> {: id="20210313082711-pus0w1o"}
>
> close方法，当完成流的操作时，必须调用此方法，释放系统资源。
> {: id="20210313082711-753v8em"}
{: id="20210313082711-oidhsz0"}

### 14.3.3 FileOutputStream类
{: id="20210313082711-5kba7xm"}

`OutputStream`有很多子类，我们从最简单的一个子类开始。
{: id="20210313082711-q4pp8i1"}

`java.io.FileOutputStream `类是文件输出流，用于将数据写出到文件。
{: id="20210313082711-6x97m07"}

#### 构造方法
{: id="20210313082711-dng0bwu"}

- {: id="20210313082711-6gw4mq8"}`public FileOutputStream(File file)`：创建文件输出流以写入由指定的 File对象表示的文件。
  {: id="20210313082711-8hus4ta"}
- {: id="20210313082711-q7fww08"}`public FileOutputStream(String name)`： 创建文件输出流以指定的名称写入文件。
  {: id="20210313082711-dq7a0to"}
{: id="20210313082711-abj0z6s"}

当你创建一个流对象时，必须传入一个文件路径。该路径下，如果没有这个文件，会创建该文件。如果有这个文件，会清空这个文件的数据。
{: id="20210313082711-zh59of0"}

- {: id="20210313082711-y3kp3lh"}构造举例，代码如下：
  {: id="20210313082711-7dd10n9"}
{: id="20210313082711-aj6mujg"}

```java
public class FileOutputStreamConstructor throws IOException {
    public static void main(String[] args) {
   	 	// 使用File对象创建流对象
        File file = new File("a.txt");
        FileOutputStream fos = new FileOutputStream(file);
      
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("b.txt");
    }
}
```
{: id="20210313082711-l79v8t0"}

#### 写出字节数据
{: id="20210313082711-j718lbz"}

1. {: id="20210313082711-eu40kia"}**写出字节**：`write(int b)` 方法，每次可以写出一个字节数据，代码使用演示：
   {: id="20210313082711-n033soh"}
{: id="20210313082711-96fsx7h"}

```java
public class FOSWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("fos.txt");     
      	// 写出数据
      	fos.write(97); // 写出第1个字节
      	fos.write(98); // 写出第2个字节
      	fos.write(99); // 写出第3个字节
      	// 关闭资源
        fos.close();
    }
}
输出结果：
abc
```
{: id="20210313082711-h06g67m"}

> 小贴士：
> {: id="20210313082711-p1tdfw4"}
>
> 1. {: id="20210313082711-p6vnpu2"}虽然参数为int类型四个字节，但是只会保留一个字节的信息写出。
>    {: id="20210313082711-2tr7y1v"}
> 2. {: id="20210313082711-udbo9rr"}流操作完毕后，必须释放系统资源，调用close方法，千万记得。
>    {: id="20210313082711-2jixos4"}
> {: id="20210313082711-ex81avw"}
{: id="20210313082711-0u70u6p"}

2. {: id="20210313082711-3bepfau"}**写出字节数组**：`write(byte[] b)`，每次可以写出数组中的数据，代码使用演示：
   {: id="20210313082711-5h9alng"}
{: id="20210313082711-4bd3t0j"}

```java
public class FOSWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("fos.txt");     
      	// 字符串转换为字节数组
      	byte[] b = "尚硅谷".getBytes();
      	// 写出字节数组数据
      	fos.write(b);
      	// 关闭资源
        fos.close();
    }
}
输出结果：
尚硅谷
```
{: id="20210313082711-e7zl3h1"}

3. {: id="20210313082711-091iyzs"}**写出指定长度字节数组**：`write(byte[] b, int off, int len)` ,每次写出从off索引开始，len个字节，代码使用演示：
   {: id="20210313082711-o2gemz9"}
{: id="20210313082711-2idf1xe"}

```java
public class FOSWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("fos.txt");     
      	// 字符串转换为字节数组
      	byte[] b = "abcde".getBytes();
		// 写出从索引2开始，2个字节。索引2是c，两个字节，也就是cd。
        fos.write(b,2,2);
      	// 关闭资源
        fos.close();
    }
}
输出结果：
cd
```
{: id="20210313082711-fa8m2zy"}

#### 数据追加续写
{: id="20210313082711-6hsii11"}

经过以上的演示，每次程序运行，创建输出流对象，都会清空目标文件中的数据。如何保留目标文件中数据，还能继续添加新数据呢？
{: id="20210313082711-5j10bax"}

- {: id="20210313082711-m12ds90"}`public FileOutputStream(File file, boolean append)`： 创建文件输出流以写入由指定的 File对象表示的文件。
  {: id="20210313082711-piacloy"}
- {: id="20210313082711-apfiwgo"}`public FileOutputStream(String name, boolean append)`： 创建文件输出流以指定的名称写入文件。
  {: id="20210313082711-osyl4i6"}
{: id="20210313082711-rbfef4v"}

这两个构造方法，参数中都需要传入一个boolean类型的值，`true` 表示追加数据，`false` 表示清空原有数据。这样创建的输出流对象，就可以指定是否追加续写了，代码使用演示：
{: id="20210313082711-bpvkyr7"}

```java
public class FOSWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("fos.txt"，true);     
      	// 字符串转换为字节数组
      	byte[] b = "abcde".getBytes();
		// 写出从索引2开始，2个字节。索引2是c，两个字节，也就是cd。
        fos.write(b);
      	// 关闭资源
        fos.close();
    }
}
文件操作前：cd
文件操作后：cdabcde
```
{: id="20210313082711-ddkopi5"}

#### 写出换行
{: id="20210313082711-ri7mkkd"}

Windows系统里，换行符号是`\r\n` 。把
{: id="20210313082711-5v1iukz"}

以指定是否追加续写了，代码使用演示：
{: id="20210313082711-em26bst"}

```java
public class FOSWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileOutputStream fos = new FileOutputStream("fos.txt");  
      	// 定义字节数组
      	byte[] words = {97,98,99,100,101};
      	// 遍历数组
        for (int i = 0; i < words.length; i++) {
          	// 写出一个字节
            fos.write(words[i]);
          	// 写出一个换行, 换行符号转成数组写出
            fos.write("\r\n".getBytes());
        }
      	// 关闭资源
        fos.close();
    }
}

输出结果：
a
b
c
d
e
```
{: id="20210313082711-zkhh8xo"}

> - {: id="20210313082711-s2sg5iv"}回车符`\r`和换行符`\n` ：
>   {: id="20210313082711-5x5oz1a"}
>   - {: id="20210313082711-h8gxga9"}回车符：回到一行的开头（return）。
>     {: id="20210313082711-j51gsfx"}
>   - {: id="20210313082711-brc9m4w"}换行符：下一行（newline）。
>     {: id="20210313082711-oqiacej"}
>   {: id="20210313082711-m44fm7w"}
> - {: id="20210313082711-3z8lj12"}系统中的换行：
>   {: id="20210313082711-t8k1xj8"}
>   - {: id="20210313082711-x4wgvur"}Windows系统里，每行结尾是 `回车+换行` ，即`\r\n`；
>     {: id="20210313082711-4ogetir"}
>   - {: id="20210313082711-hyx4odg"}Unix系统里，每行结尾只有 `换行` ，即`\n`；
>     {: id="20210313082711-nnoez7j"}
>   - {: id="20210313082711-k6yclxl"}Mac系统里，每行结尾是 `回车` ，即`\r`。从 Mac OS X开始与Linux统一。
>     {: id="20210313082711-wxlui96"}
>   {: id="20210313082711-lqwjy1b"}
> {: id="20210313082711-021ghif"}
{: id="20210313082711-1e12ion"}

### 14.3.4 字节输入流【InputStream】
{: id="20210313082711-mvfvz9h"}

`java.io.InputStream `抽象类是表示字节输入流的所有类的超类，可以读取字节信息到内存中。它定义了字节输入流的基本共性功能方法。
{: id="20210313082711-m5naq2n"}

- {: id="20210313082711-qrk1vxa"}`public void close()` ：关闭此输入流并释放与此流相关联的任何系统资源。
  {: id="20210313082711-qv83ph2"}
- {: id="20210313082711-2itmvz9"}`public abstract int read()`： 从输入流读取数据的下一个字节。
  {: id="20210313082711-xdognq3"}
- {: id="20210313082711-j7y6v78"}`public int read(byte[] b)`： 从输入流中读取一些字节数，并将它们存储到字节数组 b中 。
  {: id="20210313082711-tquys98"}
{: id="20210313082711-fzhm4d5"}

> 小贴士：
> {: id="20210313082711-s1ti3fo"}
>
> close方法，当完成流的操作时，必须调用此方法，释放系统资源。
> {: id="20210313082711-hnr19n6"}
{: id="20210313082711-kthmbec"}

### 14.3.5 FileInputStream类
{: id="20210313082711-z2ythae"}

`java.io.FileInputStream `类是文件输入流，从文件中读取字节。
{: id="20210313082711-djvhy4g"}

#### 构造方法
{: id="20210313082711-k2nupl8"}

- {: id="20210313082711-8n1c6nt"}`FileInputStream(File file)`： 通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的 File对象 file命名。
  {: id="20210313082711-2i1enj8"}
- {: id="20210313082711-ubb53ct"}`FileInputStream(String name)`： 通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的路径名 name命名。
  {: id="20210313082711-49zpgzz"}
{: id="20210313082711-ad57u22"}

当你创建一个流对象时，必须传入一个文件路径。该路径下，如果没有该文件,会抛出`FileNotFoundException` 。
{: id="20210313082711-7i92ybt"}

- {: id="20210313082711-8lw8saj"}构造举例，代码如下：
  {: id="20210313082711-yuvyukq"}
{: id="20210313082711-kpz9j0n"}

```java
public class FileInputStreamConstructor throws IOException{
    public static void main(String[] args) {
   	 	// 使用File对象创建流对象
        File file = new File("a.txt");
        FileInputStream fis = new FileInputStream(file);
      
        // 使用文件名称创建流对象
        FileInputStream fis = new FileInputStream("b.txt");
    }
}
```
{: id="20210313082711-5l1tn3b"}

#### 读取字节数据
{: id="20210313082711-vz0ip00"}

1. {: id="20210313082711-y7ki5cg"}**读取字节**：`read`方法，每次可以读取一个字节的数据，提升为int类型，读取到文件末尾，返回`-1`，代码使用演示：
   {: id="20210313082711-zuwzx31"}
{: id="20210313082711-jmn2dih"}

```java
public class FISRead {
    public static void main(String[] args) throws IOException{
      	// 使用文件名称创建流对象
       	FileInputStream fis = new FileInputStream("read.txt");
      	// 读取数据，返回一个字节
        int read = fis.read();
        System.out.println((char) read);
        read = fis.read();
        System.out.println((char) read);
        read = fis.read();
        System.out.println((char) read);
        read = fis.read();
        System.out.println((char) read);
        read = fis.read();
        System.out.println((char) read);
      	// 读取到末尾,返回-1
       	read = fis.read();
        System.out.println( read);
		// 关闭资源
        fis.close();
    }
}
输出结果：
a
b
c
d
e
-1
```
{: id="20210313082711-tt2mt42"}

循环改进读取方式，代码使用演示：
{: id="20210313082711-dufzw9n"}

```java
public class FISRead {
    public static void main(String[] args) throws IOException{
      	// 使用文件名称创建流对象
       	FileInputStream fis = new FileInputStream("read.txt");
      	// 定义变量，保存数据
        int b ；
        // 循环读取
        while ((b = fis.read())!=-1) {
            System.out.println((char)b);
        }
		// 关闭资源
        fis.close();
    }
}
输出结果：
a
b
c
d
e
```
{: id="20210313082711-xfbms6a"}

> 小贴士：
> {: id="20210313082711-6oo1h2j"}
>
> 1. {: id="20210313082711-a97y1of"}虽然读取了一个字节，但是会自动提升为int类型。
>    {: id="20210313082711-5jp45cw"}
> 2. {: id="20210313082711-rpabrne"}流操作完毕后，必须释放系统资源，调用close方法，千万记得。
>    {: id="20210313082711-gnr4nzc"}
> {: id="20210313082711-giy90hn"}
{: id="20210313082711-88yxa48"}

2. {: id="20210313082711-i71loy4"}**使用字节数组读取**：`read(byte[] b)`，每次读取b的长度个字节到数组中，返回读取到的有效字节个数，读取到末尾时，返回`-1` ，代码使用演示：
   {: id="20210313082711-alto1wl"}
{: id="20210313082711-apxyal5"}

```java
public class FISRead {
    public static void main(String[] args) throws IOException{
      	// 使用文件名称创建流对象.
       	FileInputStream fis = new FileInputStream("read.txt"); // 文件中为abcde
      	// 定义变量，作为有效个数
        int len ；
        // 定义字节数组，作为装字节数据的容器   
        byte[] b = new byte[2];
        // 循环读取
        while (( len= fis.read(b))!=-1) {
           	// 每次读取后,把数组变成字符串打印
            System.out.println(new String(b));
        }
		// 关闭资源
        fis.close();
    }
}

输出结果：
ab
cd
ed
```
{: id="20210313082711-xxbxh9h"}

错误数据`d`，是由于最后一次读取时，只读取一个字节`e`，数组中，上次读取的数据没有被完全替换，所以要通过`len` ，获取有效的字节，代码使用演示：
{: id="20210313082711-ek5eiay"}

```java
public class FISRead {
    public static void main(String[] args) throws IOException{
      	// 使用文件名称创建流对象.
       	FileInputStream fis = new FileInputStream("read.txt"); // 文件中为abcde
      	// 定义变量，作为有效个数
        int len ；
        // 定义字节数组，作为装字节数据的容器   
        byte[] b = new byte[2];
        // 循环读取
        while (( len= fis.read(b))!=-1) {
           	// 每次读取后,把数组的有效字节部分，变成字符串打印
            System.out.println(new String(b，0，len));//  len 每次读取的有效字节个数
        }
		// 关闭资源
        fis.close();
    }
}

输出结果：
ab
cd
e
```
{: id="20210313082711-fjibol7"}

> 小贴士：
> {: id="20210313082711-nwy3zdb"}
>
> 使用数组读取，每次读取多个字节，减少了系统间的IO操作次数，从而提高了读写的效率，建议开发中使用。
> {: id="20210313082711-6uamdlv"}
{: id="20210313082711-d5fgcv0"}

### 14.3.6 字节流练习：图片复制
{: id="20210313082711-qykfvlg"}

![](imgs19/2_copy.jpg)
{: id="20210313082711-3wcyspr"}

复制图片文件，代码使用演示：
{: id="20210313082711-211jizq"}

```java
public class Copy {
    public static void main(String[] args) throws IOException {
        // 1.创建流对象
        // 1.1 指定数据源
        FileInputStream fis = new FileInputStream("D:\\test.jpg");
        // 1.2 指定目的地
        FileOutputStream fos = new FileOutputStream("test_copy.jpg");

        // 2.读写数据
        // 2.1 定义数组
        byte[] b = new byte[1024];
        // 2.2 定义长度
        int len;
        // 2.3 循环读取
        while ((len = fis.read(b))!=-1) {
            // 2.4 写出数据
            fos.write(b, 0 , len);
        }

        // 3.关闭资源
        fos.close();
        fis.close();
    }
}
```
{: id="20210313082711-fcutihi"}

> 小贴士：
> {: id="20210313082711-njtd6or"}
>
> 流的关闭原则：先开后关，后开先关。
> {: id="20210313082711-e95h9sp"}
{: id="20210313082711-w2pq9i3"}

## 14.4 字符流
{: id="20210313082711-ht7mqjj"}

当使用字节流读取文本文件时，可能会有一个小问题。就是遇到中文字符时，可能不会显示完整的字符，那是因为一个中文字符可能占用多个字节存储。所以Java提供一些字符流类，以字符为单位读写数据，专门用于处理文本文件。
{: id="20210313082711-4073tge"}

### 14.4.1 字符输入流【Reader】
{: id="20210313082711-e0rav0p"}

`java.io.Reader`抽象类是表示用于读取字符流的所有类的超类，可以读取字符信息到内存中。它定义了字符输入流的基本共性功能方法。
{: id="20210313082711-iap7xlb"}

- {: id="20210313082711-b0av4sp"}`public void close()` ：关闭此流并释放与此流相关联的任何系统资源。
  {: id="20210313082711-s0zve0k"}
- {: id="20210313082711-1m8mewn"}`public int read()`： 从输入流读取一个字符。
  {: id="20210313082711-wvt41gt"}
- {: id="20210313082711-xg7t6a1"}`public int read(char[] cbuf)`： 从输入流中读取一些字符，并将它们存储到字符数组 cbuf中 。
  {: id="20210313082711-brktaqf"}
{: id="20210313082711-c5u0oet"}

### 14.4.2 FileReader类
{: id="20210313082711-0vbm8pj"}

`java.io.FileReader `类是读取字符文件的便利类。构造时使用系统默认的字符编码和默认字节缓冲区。
{: id="20210313082711-kpuzu70"}

> 小贴士：
> {: id="20210313082711-wmvjgta"}
>
> 1. {: id="20210313082711-8gomnve"}字符编码：字节与字符的对应规则。Windows系统的中文编码默认是GBK编码表。
>    {: id="20210313082711-kne1kbi"}
> {: id="20210313082711-3z6l9w0"}
>
> eclipse中默认GBK，idea中默认UTF-8
> {: id="20210313082711-3vm92eo"}
>
> 2. {: id="20210313082711-785eb7h"}字节缓冲区：一个字节数组，用来临时存储字节数据。
>    {: id="20210313082711-ykv90wr"}
> {: id="20210313082711-fb8cjnz"}
{: id="20210313082711-3t5cd5r"}

#### 构造方法
{: id="20210313082711-gg630ng"}

- {: id="20210313082711-8txitu5"}`FileReader(File file)`： 创建一个新的 FileReader ，给定要读取的File对象。
  {: id="20210313082711-6k63e1w"}
- {: id="20210313082711-vigu4i5"}`FileReader(String fileName)`： 创建一个新的 FileReader ，给定要读取的文件的名称。
  {: id="20210313082711-owxsoxs"}
{: id="20210313082711-403r7cq"}

当你创建一个流对象时，必须传入一个文件路径。类似于FileInputStream 。
{: id="20210313082711-o8gp3fo"}

- {: id="20210313082711-6y3tbpc"}构造举例，代码如下：
  {: id="20210313082711-g5iybeu"}
{: id="20210313082711-bnay7s5"}

```java
public class FileReaderConstructor throws IOException{
    public static void main(String[] args) {
   	 	// 使用File对象创建流对象
        File file = new File("a.txt");
        FileReader fr = new FileReader(file);
      
        // 使用文件名称创建流对象
        FileReader fr = new FileReader("b.txt");
    }
}
```
{: id="20210313082711-yhs67mk"}

#### 读取字符数据
{: id="20210313082711-wci6yg4"}

1. {: id="20210313082711-asvny1v"}**读取字符**：`read`方法，每次可以读取一个字符的数据，提升为int类型，读取到文件末尾，返回`-1`，循环读取，代码使用演示：
   {: id="20210313082711-rxwo26k"}
{: id="20210313082711-8c6ltrp"}

```java
public class FRRead {
    public static void main(String[] args) throws IOException {
      	// 使用文件名称创建流对象
       	FileReader fr = new FileReader("read.txt");
      	// 定义变量，保存数据
        int b ；
        // 循环读取
        while ((b = fr.read())!=-1) {
            System.out.println((char)b);
        }
		// 关闭资源
        fr.close();
    }
}
输出结果：
尚
硅
谷
```
{: id="20210313082711-n831tq0"}

> 小贴士：虽然读取了一个字符，但是会自动提升为int类型。
> {: id="20210313082711-bjxru5w"}
{: id="20210313082711-l2wfvla"}

2. {: id="20210313082711-h6hm6tw"}**使用字符数组读取**：`read(char[] cbuf)`，每次读取b的长度个字符到数组中，返回读取到的有效字符个数，读取到末尾时，返回`-1` ，代码使用演示：
   {: id="20210313082711-x5840wk"}
{: id="20210313082711-xmjhrc4"}

```java
public class FRRead {
    public static void main(String[] args) throws IOException {
      	// 使用文件名称创建流对象
       	FileReader fr = new FileReader("read.txt");
      	// 定义变量，保存有效字符个数
        int len ；
        // 定义字符数组，作为装字符数据的容器
         char[] cbuf = new char[2];
        // 循环读取
        while ((len = fr.read(cbuf))!=-1) {
            System.out.println(new String(cbuf));
        }
		// 关闭资源
        fr.close();
    }
}
输出结果：
尚硅
谷硅
```
{: id="20210313082711-ea2qsi2"}

获取有效的字符改进，代码使用演示：
{: id="20210313082711-w6uxko2"}

```java
public class FISRead {
    public static void main(String[] args) throws IOException {
      	// 使用文件名称创建流对象
       	FileReader fr = new FileReader("read.txt");
      	// 定义变量，保存有效字符个数
        int len ；
        // 定义字符数组，作为装字符数据的容器
        char[] cbuf = new char[2];
        // 循环读取
        while ((len = fr.read(cbuf))!=-1) {
            System.out.println(new String(cbuf,0,len));
        }
    	// 关闭资源
        fr.close();
    }
}

输出结果：
尚硅
谷
```
{: id="20210313082711-mjselcf"}

### 14.4.3 字符输出流【Writer】
{: id="20210313082711-42raz1h"}

`java.io.Writer `抽象类是表示用于写出字符流的所有类的超类，将指定的字符信息写出到目的地。它定义了字节输出流的基本共性功能方法。
{: id="20210313082711-xrh34fn"}

- {: id="20210313082711-w3fcojk"}`void write(int c)` 写入单个字符。
  {: id="20210313082711-4y6anwx"}
- {: id="20210313082711-11ea1w4"}`void write(char[] cbuf) `写入字符数组。
  {: id="20210313082711-i5x1j21"}
- {: id="20210313082711-hpwkwt7"}`abstract  void write(char[] cbuf, int off, int len) `写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
  {: id="20210313082711-q00q8sb"}
- {: id="20210313082711-vqskl8i"}`void write(String str) `写入字符串。
  {: id="20210313082711-nvv65em"}
- {: id="20210313082711-5mucr49"}`void write(String str, int off, int len)` 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
  {: id="20210313082711-6lrthzj"}
- {: id="20210313082711-uejoytv"}`void flush() `刷新该流的缓冲。
  {: id="20210313082711-zttzqh5"}
- {: id="20210313082711-yl40agz"}`void close()` 关闭此流，但要先刷新它。
  {: id="20210313082711-b58c9jc"}
{: id="20210313082711-0iupa24"}

### 14.4.4 FileWriter类
{: id="20210313082711-pyepkqv"}

`java.io.FileWriter `类是写出字符到文件的便利类。构造时使用系统默认的字符编码和默认字节缓冲区。
{: id="20210313082711-1ka17f3"}

#### 构造方法
{: id="20210313082711-s1cjwps"}

- {: id="20210313082711-2kz5eij"}`FileWriter(File file)`： 创建一个新的 FileWriter，给定要读取的File对象。
  {: id="20210313082711-debcczi"}
- {: id="20210313082711-djxrnx4"}`FileWriter(String fileName)`： 创建一个新的 FileWriter，给定要读取的文件的名称。
  {: id="20210313082711-sje1dfa"}
{: id="20210313082711-niyh7t4"}

当你创建一个流对象时，必须传入一个文件路径，类似于FileOutputStream。
{: id="20210313082711-6b3b62a"}

- {: id="20210313082711-sem1szu"}构造举例，代码如下：
  {: id="20210313082711-ao8lbgn"}
{: id="20210313082711-wgikhv7"}

```java
public class FileWriterConstructor {
    public static void main(String[] args) throws IOException {
   	 	// 使用File对象创建流对象
        File file = new File("a.txt");
        FileWriter fw = new FileWriter(file);
      
        // 使用文件名称创建流对象
        FileWriter fw = new FileWriter("b.txt");
    }
}
```
{: id="20210313082711-qooje76"}

#### 基本写出数据
{: id="20210313082711-lvd8ql4"}

**写出字符**：`write(int b)` 方法，每次可以写出一个字符数据，代码使用演示：
{: id="20210313082711-3s8tqn6"}

```java
public class FWWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileWriter fw = new FileWriter("fw.txt");     
      	// 写出数据
      	fw.write(97); // 写出第1个字符
      	fw.write('b'); // 写出第2个字符
      	fw.write('C'); // 写出第3个字符
      	fw.write(30000); // 写出第4个字符，中文编码表中30000对应一个汉字。
      
      	/*
        【注意】关闭资源时,与FileOutputStream不同。
      	 如果不关闭,数据只是保存到缓冲区，并未保存到文件。
        */
        // fw.close();
    }
}
输出结果：
abC田
```
{: id="20210313082711-w0gtsph"}

> 小贴士：
> {: id="20210313082711-v8tj5ht"}
>
> 1. {: id="20210313082711-573bmm9"}虽然参数为int类型四个字节，但是只会保留一个字符的信息写出。
>    {: id="20210313082711-aym7ikv"}
> 2. {: id="20210313082711-r66fqvy"}未调用close方法，数据只是保存到了缓冲区，并未写出到文件中。
>    {: id="20210313082711-l6vfzmj"}
> {: id="20210313082711-2cp5eix"}
{: id="20210313082711-p0hj48k"}

#### 关闭和刷新
{: id="20210313082711-ooh07jp"}

因为内置缓冲区的原因，如果不关闭输出流，无法写出字符到文件中。但是关闭的流对象，是无法继续写出数据的。如果我们既想写出数据，又想继续使用流，就需要`flush` 方法了。
{: id="20210313082711-ehsl6fb"}

- {: id="20210313082711-8sote2m"}`flush` ：刷新缓冲区，流对象可以继续使用。
  {: id="20210313082711-cbjcs2u"}
- {: id="20210313082711-csvpvmk"}`close `:先刷新缓冲区，然后通知系统释放资源。流对象不可以再被使用了。
  {: id="20210313082711-093nlry"}
{: id="20210313082711-8peliki"}

代码使用演示：
{: id="20210313082711-0i3f7h6"}

```java
public class FWWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileWriter fw = new FileWriter("fw.txt");
        // 写出数据，通过flush
        fw.write('刷'); // 写出第1个字符
        fw.flush();
        fw.write('新'); // 继续写出第2个字符，写出成功
        fw.flush();
      
      	// 写出数据，通过close
        fw.write('关'); // 写出第1个字符
        fw.close();
        fw.write('闭'); // 继续写出第2个字符,【报错】java.io.IOException: Stream closed
        fw.close();
    }
}
```
{: id="20210313082711-thvktix"}

> 小贴士：即便是flush方法写出了数据，操作的最后还是要调用close方法，释放系统资源。
> {: id="20210313082711-2ej13ju"}
{: id="20210313082711-fgl9ixf"}

#### 写出其他数据
{: id="20210313082711-vll0vcq"}

1. {: id="20210313082711-1jqatv7"}**写出字符数组** ：`write(char[] cbuf)` 和 `write(char[] cbuf, int off, int len)` ，每次可以写出字符数组中的数据，用法类似FileOutputStream，代码使用演示：
   {: id="20210313082711-g6gbonr"}
{: id="20210313082711-omgetw5"}

```java
public class FWWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileWriter fw = new FileWriter("fw.txt");     
      	// 字符串转换为字节数组
      	char[] chars = "尚硅谷".toCharArray();
      
      	// 写出字符数组
      	fw.write(chars); // 尚硅谷
        
		// 写出从索引1开始，2个字节。索引1是'硅'，两个字节，也就是'硅谷'。
        fw.write(b,1,2); // 硅谷
      
      	// 关闭资源
        fos.close();
    }
}
```
{: id="20210313082711-68buizj"}

2. {: id="20210313082711-kv9acam"}**写出字符串**：`write(String str)` 和 `write(String str, int off, int len)` ，每次可以写出字符串中的数据，更为方便，代码使用演示：
   {: id="20210313082711-t8wep9h"}
{: id="20210313082711-l5wa0g6"}

```java
public class FWWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象
        FileWriter fw = new FileWriter("fw.txt");     
      	// 字符串
      	String msg = "尚硅谷";
      
      	// 写出字符数组
      	fw.write(msg); //尚硅谷
      
		// 写出从索引1开始，2个字节。索引1是'硅'，两个字节，也就是'硅谷'。
        fw.write(msg,1,2);	// 尚硅谷
      	
        // 关闭资源
        fos.close();
    }
}
```
{: id="20210313082711-jy1t4z6"}

3. {: id="20210313082711-ecj57hx"}**续写和换行**：操作类似于FileOutputStream。
   {: id="20210313082711-qzd236e"}
{: id="20210313082711-gl12fmx"}

```java
public class FWWrite {
    public static void main(String[] args) throws IOException {
        // 使用文件名称创建流对象，可以续写数据
        FileWriter fw = new FileWriter("fw.txt"，true);     
      	// 写出字符串
        fw.write("尚");
      	// 写出换行
      	fw.write("\r\n");
      	// 写出字符串
  		fw.write("硅谷");
      	// 关闭资源
        fw.close();
    }
}
输出结果:
尚
硅谷
```
{: id="20210313082711-ebzyyl2"}

> 小贴士：字符流，只能操作文本文件，不能操作图片，视频等非文本文件。
> {: id="20210313082711-q27lixm"}
>
> 当我们单纯读或者写文本文件时  使用字符流 其他情况使用字节流
> {: id="20210313082711-oibj1ua"}
{: id="20210313082711-zshnzjx"}

## 14.5 缓冲流
{: id="20210313082711-wr9k233"}

缓冲流,也叫高效流，按照数据类型分类：
{: id="20210313082711-pts860z"}

* {: id="20210313082711-yki7368"}**字节缓冲流**：`BufferedInputStream`，`BufferedOutputStream`
  {: id="20210313082711-vfd388i"}
* {: id="20210313082711-2z6a2sj"}**字符缓冲流**：`BufferedReader`，`BufferedWriter`
  {: id="20210313082711-nghdeil"}
{: id="20210313082711-kbyobyv"}

缓冲流的基本原理，是在创建流对象时，会创建一个内置的默认大小的缓冲区数组，通过缓冲区读写，减少系统IO次数，从而提高读写的效率。
{: id="20210313082711-7hxvqkh"}

### 14.5.1 字节缓冲流
{: id="20210313082711-l2nqrh9"}

#### 构造方法
{: id="20210313082711-tjz7ux5"}

* {: id="20210313082711-mbu6xq1"}`public BufferedInputStream(InputStream in)` ：创建一个 新的缓冲输入流。
  {: id="20210313082711-3or30wk"}
* {: id="20210313082711-d2bm0c0"}`public BufferedOutputStream(OutputStream out)`： 创建一个新的缓冲输出流。
  {: id="20210313082711-4x96hx6"}
{: id="20210313082711-0npfje8"}

构造举例，代码如下：
{: id="20210313082711-73059bt"}

```java
// 创建字节缓冲输入流
BufferedInputStream bis = new BufferedInputStream(new FileInputStream("bis.txt"));
// 创建字节缓冲输出流
BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("bos.txt"));
```
{: id="20210313082711-rao2k19"}

#### 效率测试
{: id="20210313082711-rzt5wr7"}

查询API，缓冲流读写方法与基本的流是一致的，我们通过复制大文件（375MB），测试它的效率。
{: id="20210313082711-73f6mrj"}

1. {: id="20210313082711-53v2int"}基本流，代码如下：
   {: id="20210313082711-zp4t4at"}
{: id="20210313082711-nxfbdpd"}

```java
public class BufferedDemo {
    public static void main(String[] args) throws IOException {
        // 记录开始时间
      	long start = System.currentTimeMillis();
		// 创建流对象
        FileInputStream fis = new FileInputStream("jdk9.exe");
        FileOutputStream fos = new FileOutputStream("copy.exe");
        	// 读写数据
        int b;
        while ((b = fis.read()) != -1) {
                fos.write(b);
        }
        
        fos.close();
        fis.close();
        
		// 记录结束时间
        long end = System.currentTimeMillis();
        System.out.println("普通流复制时间:"+(end - start)+" 毫秒");
    }
}

十几分钟过去了...
```
{: id="20210313082711-p38346v"}

2. {: id="20210313082711-7hpbmb5"}缓冲流，代码如下：
   {: id="20210313082711-imc3zh9"}
{: id="20210313082711-rrjesp2"}

```java
public class BufferedDemo {
    public static void main(String[] args) throws IOException {
        // 记录开始时间
      	long start = System.currentTimeMillis();
		// 创建流对象
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream("jdk9.exe"));
	    BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("copy.exe"));
        // 读写数据
        int b;
        while ((b = bis.read()) != -1) {
            bos.write(b);
        }
        
        bos.close();
        bis.close();
        
		// 记录结束时间
        long end = System.currentTimeMillis();
        System.out.println("缓冲流复制时间:"+(end - start)+" 毫秒");
    }
}

缓冲流复制时间:8016 毫秒
```
{: id="20210313082711-p4o3ewx"}

如何更快呢？
{: id="20210313082711-nrhr35x"}

使用数组的方式，代码如下：
{: id="20210313082711-myw01i0"}

```java
public class BufferedDemo {
    public static void main(String[] args) throws IOException {
      	// 记录开始时间
        long start = System.currentTimeMillis();
		// 创建流对象
		BufferedInputStream bis = new BufferedInputStream(new FileInputStream("jdk9.exe"));
		BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("copy.exe"));
          	// 读写数据
        int len;
        byte[] bytes = new byte[8*1024];
        while ((len = bis.read(bytes)) != -1) {
            bos.write(bytes, 0 , len);
        }
        
        bos.close();
        bis.close();
		// 记录结束时间
        long end = System.currentTimeMillis();
        System.out.println("缓冲流使用数组复制时间:"+(end - start)+" 毫秒");
    }
}
缓冲流使用数组复制时间:666 毫秒
```
{: id="20210313082711-9l8i55s"}

### 14.5.2 字符缓冲流
{: id="20210313082711-n53e31m"}

#### 构造方法
{: id="20210313082711-1qwud5w"}

* {: id="20210313082711-fzramss"}`public BufferedReader(Reader in)` ：创建一个 新的缓冲输入流。
  {: id="20210313082711-kezcoe8"}
* {: id="20210313082711-7qaby7a"}`public BufferedWriter(Writer out)`： 创建一个新的缓冲输出流。
  {: id="20210313082711-2l9oy15"}
{: id="20210313082711-kiq66r8"}

构造举例，代码如下：
{: id="20210313082711-f0uq8ab"}

```java
// 创建字符缓冲输入流
BufferedReader br = new BufferedReader(new FileReader("br.txt"));
// 创建字符缓冲输出流
BufferedWriter bw = new BufferedWriter(new FileWriter("bw.txt"));
```
{: id="20210313082711-8aylhif"}

#### 特有方法
{: id="20210313082711-w6hpcdu"}

字符缓冲流的基本方法与普通字符流调用方式一致，不再阐述，我们来看它们具备的特有方法。
{: id="20210313082711-85ywem1"}

* {: id="20210313082711-qp8ocoj"}BufferedReader：`public String readLine()`: 读一行文字。
  {: id="20210313082711-zvbaw8b"}
* {: id="20210313082711-hz6yzlo"}BufferedWriter：`public void newLine()`: 写一行行分隔符,由系统属性定义符号。
  {: id="20210313082711-yypd6yr"}
{: id="20210313082711-fgs45rd"}

`readLine`方法演示，代码如下：
{: id="20210313082711-idtq4uq"}

```java
public class BufferedReaderDemo {
    public static void main(String[] args) throws IOException {
      	 // 创建流对象
        BufferedReader br = new BufferedReader(new FileReader("in.txt"));
		// 定义字符串,保存读取的一行文字
        String line  = null;
      	// 循环读取,读取到最后返回null
        while ((line = br.readLine())!=null) {
            System.out.print(line);
            System.out.println("------");
        }
		// 释放资源
        br.close();
    }
}
```
{: id="20210313082711-o3xdq03"}

`newLine`方法演示，代码如下：
{: id="20210313082711-vrlpe1j"}

```java
public class BufferedWriterDemo throws IOException {
  public static void main(String[] args) throws IOException  {
    	// 创建流对象
  	BufferedWriter bw = new BufferedWriter(new FileWriter("out.txt"));
    	// 写出数据
      bw.write("尚");
    	// 写出换行
      bw.newLine();
      bw.write("硅");
      bw.newLine();
      bw.write("谷");
      bw.newLine();
  	// 释放资源
      bw.close();
  }
}
输出效果:
尚
硅
谷
```
{: id="20210313082711-g7qdcys"}

## 14.6 转换流
{: id="20210313082711-mumb99a"}

### 14.6.1 字符编码和字符集
{: id="20210313082711-oj8wju1"}

#### 字符编码
{: id="20210313082711-2vbm92k"}

计算机中储存的信息都是用二进制数表示的，而我们在屏幕上看到的数字、英文、标点符号、汉字等字符是二进制数转换之后的结果。按照某种规则，将字符存储到计算机中，称为**编码** 。反之，将存储在计算机中的二进制数按照某种规则解析显示出来，称为**解码** 。比如说，按照A规则存储，同样按照A规则解析，那么就能显示正确的文本符号。反之，按照A规则存储，再按照B规则解析，就会导致乱码现象。
{: id="20210313082711-8sdh7ux"}

编码:字符(能看懂的)--字节(看不懂的)
{: id="20210313082711-oh50fpg"}

解码:字节(看不懂的)-->字符(能看懂的)
{: id="20210313082711-l8jeni5"}

* {: id="20210313082711-ggsw7sr"}**字符编码`Character Encoding`** : 就是一套自然语言的字符与二进制数之间的对应规则。
  {: id="20210313082711-l3zw55i"}

  编码表:生活中文字和计算机中二进制的对应规则
  {: id="20210313082711-jwp9aus"}
{: id="20210313082711-7mzhxsa"}

#### 字符集
{: id="20210313082711-66b2gae"}

* {: id="20210313082711-mua0kl2"}**字符集 `Charset`**：也叫编码表。是一个系统支持的所有字符的集合，包括各国家文字、标点符号、图形符号、数字等。
  {: id="20210313082711-8t6s9zz"}
{: id="20210313082711-cbe54vy"}

计算机要准确的存储和识别各种字符集符号，需要进行字符编码，一套字符集必然至少有一套字符编码。常见字符集有ASCII字符集、GBK字符集、Unicode字符集等。
{: id="20210313082711-brwac4o"}

![](imgs19/1_charset.jpg)
{: id="20210313082711-gkbz3ep"}

可见，当指定了**编码**，它所对应的**字符集**自然就指定了，所以**编码**才是我们最终要关心的。
{: id="20210313082711-wnmcrpr"}

* {: id="20210313082711-yeqiun5"}**ASCII字符集** ：
  {: id="20210313082711-4cd01yx"}
  * {: id="20210313082711-u0fmkb3"}ASCII（American Standard Code for Information Interchange，美国信息交换标准代码）是基于拉丁字母的一套电脑编码系统，用于显示现代英语，主要包括控制字符（回车键、退格、换行键等）和可显示字符（英文大小写字符、阿拉伯数字和西文符号）。
    {: id="20210313082711-h6txbk0"}
  * {: id="20210313082711-eic468b"}基本的ASCII字符集，使用7位（bits）表示一个字符，共128字符。
    {: id="20210313082711-b47ylsn"}
  * {: id="20210313082711-7nwfn31"}ASCII的扩展字符集使用8位（bits）表示一个字符，共256字符，方便支持欧洲常用字符。
    {: id="20210313082711-a0spurb"}
  {: id="20210313082711-apg5nz1"}
* {: id="20210313082711-0lycjk9"}**ISO-8859-1字符集**：
  {: id="20210313082711-6nrnlq2"}
  * {: id="20210313082711-5co7sce"}拉丁码表，别名Latin-1，用于显示欧洲使用的语言，包括荷兰、丹麦、德语、意大利语、西班牙语等。
    {: id="20210313082711-g2s45cj"}
  * {: id="20210313082711-4nqsgyq"}ISO-8859-1使用单字节编码，兼容ASCII编码。
    {: id="20210313082711-mwl62zq"}
  {: id="20210313082711-ohc6t5w"}
* {: id="20210313082711-9uf3ggn"}**GBxxx字符集**：
  {: id="20210313082711-r94glcw"}
  * {: id="20210313082711-jynbpu8"}GB就是国标的意思，是为了显示中文而设计的一套字符集。
    {: id="20210313082711-7cxynj7"}
  * {: id="20210313082711-zxxeojb"}**GB2312**：简体中文码表。一个小于127的字符的意义与原来相同。但两个大于127的字符连在一起时，就表示一个汉字，这样大约可以组合了包含7000多个简体汉字，此外数学符号、罗马希腊的字母、日文的假名们都编进去了，连在ASCII里本来就有的数字、标点、字母都统统重新编了两个字节长的编码，这就是常说的"全角"字符，而原来在127号以下的那些就叫"半角"字符了。
    {: id="20210313082711-p2ti9hq"}
  * {: id="20210313082711-vp1q8vx"}**GBK**：最常用的中文码表。是在GB2312标准基础上的扩展规范，使用了双字节编码方案，共收录了21003个汉字，完全兼容GB2312标准，同时支持繁体汉字以及日韩汉字等。
    {: id="20210313082711-hnp35oo"}
  * {: id="20210313082711-m6jbzat"}**GB18030**：最新的中文码表。收录汉字70244个，采用多字节编码，每个字可以由1个、2个或4个字节组成。支持中国国内少数民族的文字，同时支持繁体汉字以及日韩汉字等。
    {: id="20210313082711-5buwowh"}
  {: id="20210313082711-35wh6do"}
* {: id="20210313082711-dos8j9r"}**Unicode字符集** ：
  {: id="20210313082711-9fyk1rn"}
  * {: id="20210313082711-hnk8txf"}Unicode编码系统为表达任意语言的任意字符而设计，是业界的一种标准，也称为统一码、标准万国码。
    {: id="20210313082711-8nlkwum"}
  * {: id="20210313082711-rimpqee"}它最多使用4个字节的数字来表达每个字母、符号，或者文字。有三种编码方案，UTF-8、UTF-16和UTF-32。最为常用的UTF-8编码。
    {: id="20210313082711-aorwnc4"}
  * {: id="20210313082711-dp0tvnr"}UTF-8编码，可以用来表示Unicode标准中任何字符，它是电子邮件、网页及其他存储或传送文字的应用中，优先采用的编码。互联网工程工作小组（IETF）要求所有互联网协议都必须支持UTF-8编码。所以，我们开发Web应用，也要使用UTF-8编码。它使用一至四个字节为每个字符编码，编码规则：
    {: id="20210313082711-4hcsg03"}
    1. {: id="20210313082711-4b9skv1"}128个US-ASCII字符，只需一个字节编码。
       {: id="20210313082711-dr9fnde"}
    2. {: id="20210313082711-wudh9s0"}拉丁文等字符，需要二个字节编码。
       {: id="20210313082711-jnh09xq"}
    3. {: id="20210313082711-gdoobu6"}大部分常用字（含中文），使用三个字节编码。
       {: id="20210313082711-pf1agiz"}
    4. {: id="20210313082711-4yzwaov"}其他极少使用的Unicode辅助字符，使用四字节编码。
       {: id="20210313082711-v3jmfhd"}
    {: id="20210313082711-vkr6nw1"}
  {: id="20210313082711-6fhrb0x"}
{: id="20210313082711-x06fiqo"}

### 14.6.2 编码引出的问题
{: id="20210313082711-u4xecza"}

在Eclipse中，使用`FileReader` 读取项目中的文本文件。由于Eclipse的设置UTF-8编码但是，当读取Windows系统中创建的文本文件时，由于Windows系统的默认是GBK编码，就会出现乱码。
{: id="20210313082711-s1mtcyy"}

```java
public class ReaderDemo {
    public static void main(String[] args) throws IOException {
        FileReader fileReader = new FileReader("E:\\File_GBK.txt");
        int read;
        while ((read = fileReader.read()) != -1) {
            System.out.print((char)read);
        }
        fileReader.close();
    }
}
输出结果：
���
```
{: id="20210313082711-u6ac7vz"}

那么如何读取GBK编码的文件呢？
{: id="20210313082711-s18orfx"}

### 14.6.3 InputStreamReader类
{: id="20210313082711-ld8kp7z"}

转换流`java.io.InputStreamReader`，是Reader的子类，是从字节流到字符流的桥梁。它读取字节，并使用指定的字符集将其解码为字符。它的字符集可以由名称指定，也可以接受平台的默认字符集。
{: id="20210313082711-mdqx5sg"}

#### 构造方法
{: id="20210313082711-j6i3jpb"}

* {: id="20210313082711-61x3syw"}`InputStreamReader(InputStream in)`: 创建一个使用默认字符集的字符流。
  {: id="20210313082711-h5g95xj"}
* {: id="20210313082711-t1iv5sv"}`InputStreamReader(InputStream in, String charsetName)`: 创建一个指定字符集的字符流。
  {: id="20210313082711-bm56ydl"}
{: id="20210313082711-4l7s51w"}

构造举例，代码如下：
{: id="20210313082711-jahz4hw"}

```java
InputStreamReader isr = new InputStreamReader(new FileInputStream("in.txt"));
InputStreamReader isr2 = new InputStreamReader(new FileInputStream("in.txt") , "GBK");
```
{: id="20210313082711-468pa5x"}

#### 指定编码读取
{: id="20210313082711-pk4krp1"}

```java
public class ReaderDemo2 {
    public static void main(String[] args) throws IOException {
      	// 定义文件路径,文件为gbk编码
        String FileName = "E:\\file_gbk.txt";
      	// 创建流对象,默认UTF8编码
        InputStreamReader isr = new InputStreamReader(new FileInputStream(FileName));
      	// 创建流对象,指定GBK编码
        InputStreamReader isr2 = new InputStreamReader(new FileInputStream(FileName) , "GBK");
		// 定义变量,保存字符
        int read;
      	// 使用默认编码字符流读取,乱码
        while ((read = isr.read()) != -1) {
            System.out.print((char)read); // ��Һ�
        }
        isr.close();
      
      	// 使用指定编码字符流读取,正常解析
        while ((read = isr2.read()) != -1) {
            System.out.print((char)read);// 大家好
        }
        isr2.close();
    }
}
```
{: id="20210313082711-3erjux2"}

### 14.6.4 OutputStreamWriter类
{: id="20210313082711-zyn4zrb"}

转换流`java.io.OutputStreamWriter` ，是Writer的子类，是从字符流到字节流的桥梁。使用指定的字符集将字符编码为字节。它的字符集可以由名称指定，也可以接受平台的默认字符集。
{: id="20210313082711-sjm8x94"}

#### 构造方法
{: id="20210313082711-xihknxt"}

- {: id="20210313082711-tfq0t6g"}`OutputStreamWriter(OutputStream in)`: 创建一个使用默认字符集的字符流。
  {: id="20210313082711-49jxa81"}
- {: id="20210313082711-m7o1jql"}`OutputStreamWriter(OutputStream in, String charsetName)`: 创建一个指定字符集的字符流。
  {: id="20210313082711-5itli3w"}
{: id="20210313082711-1gngl93"}

构造举例，代码如下：
{: id="20210313082711-at54iyz"}

```java
OutputStreamWriter isr = new OutputStreamWriter(new FileOutputStream("out.txt"));
OutputStreamWriter isr2 = new OutputStreamWriter(new FileOutputStream("out.txt") , "GBK");
```
{: id="20210313082711-2jck8he"}

#### 指定编码写出
{: id="20210313082711-hww6mfk"}

```java
public class OutputDemo {
    public static void main(String[] args) throws IOException {
      	// 定义文件路径
        String FileName = "E:\\out.txt";
      	// 创建流对象,默认UTF8编码
        OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream(FileName));
        // 写出数据
      	osw.write("你好"); // 保存为6个字节
        osw.close();
      	
		// 定义文件路径
		String FileName2 = "E:\\out2.txt";
     	// 创建流对象,指定GBK编码
        OutputStreamWriter osw2 = new OutputStreamWriter(new FileOutputStream(FileName2),"GBK");
        // 写出数据
      	osw2.write("你好");// 保存为4个字节
        osw2.close();
    }
}
```
{: id="20210313082711-qiys7tt"}

### 14.6.5 转换流理解图解
{: id="20210313082711-safcem0"}

**转换流是字节与字符间的桥梁！**
{: id="20210313082711-q6nmmyh"}

![](imgs19/2_zhuanhuan.jpg)
{: id="20210313082711-4bdlwa8"}

### 14.6.6 练习：转换文件编码
{: id="20210313082711-p4ze91s"}

将GBK编码的文本文件，转换为UTF-8编码的文本文件。
{: id="20210313082711-shmlevs"}

#### 案例分析
{: id="20210313082711-74tg0li"}

1. {: id="20210313082711-wp1jtbk"}指定GBK编码的转换流，读取文本文件。
   {: id="20210313082711-vo5vikb"}
2. {: id="20210313082711-58oa4b5"}使用UTF-8编码的转换流，写出文本文件。
   {: id="20210313082711-70oel39"}
{: id="20210313082711-00ajord"}

#### 案例实现
{: id="20210313082711-uz7xe9u"}

```java
public class TransDemo {
   public static void main(String[] args) {      
    	// 1.定义文件路径
     	String srcFile = "file_gbk.txt";
        String destFile = "file_utf8.txt";
		// 2.创建流对象
    	// 2.1 转换输入流,指定GBK编码
        InputStreamReader isr = new InputStreamReader(new FileInputStream(srcFile) , "GBK");
    	// 2.2 转换输出流,默认utf8编码
        OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream(destFile));
		// 3.读写数据
    	// 3.1 定义数组
        char[] cbuf = new char[1024];
    	// 3.2 定义长度
        int len;
    	// 3.3 循环读取
        while ((len = isr.read(cbuf))!=-1) {
            // 循环写出
          	osw.write(cbuf,0,len);
        }
    	// 4.释放资源
        osw.close();
        isr.close();
  	}
}
```
{: id="20210313082711-aygyii7"}

## 14.7 数据流
{: id="20210313082711-e8ow5bu"}

前面学习的IO流，在程序代码中，要么将数据直接按照字节处理，要么按照字符处理。那么，如果要在程序中直接处理Java的基础数据类型，怎么办呢？
{: id="20210313082711-nz49e03"}

```java
String name = “巫师”;
int age = 300;
char gender = ‘男’;
int energy = 5000;
double price = 75.5;
boolean relive = true;
```
{: id="20210313082711-cbkd0wu"}

完成这个需求，可以使用DataOutputStream进行写，随后用DataInputStream进行读取，而且顺序要一致。
{: id="20210313082711-054zmmz"}

示例代码：
{: id="20210313082711-szscw4v"}

```java
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class TestData {
	public void save() throws IOException{
		String name = "巫师";
		int age = 300;
		char gender = '男';
		int energy = 5000;
		double price = 75.5;
		boolean relive = true;
		
		DataOutputStream dos = new DataOutputStream(new FileOutputStream("game.dat"));
		dos.writeUTF(name);
		dos.writeInt(age);
		dos.writeChar(gender);
		dos.writeInt(energy);
		dos.writeDouble(price);
		dos.writeBoolean(relive);
		dos.close();
	}	
	public void reload()throws IOException{
		DataInputStream dis = new DataInputStream(new FileInputStream("game.dat"));
		String name = dis.readUTF();
		int age = dis.readInt();
		char gender = dis.readChar();
		int energy = dis.readInt();
		double price = dis.readDouble();
		boolean relive = dis.readBoolean();
		
		System.out.println(name+"," + age + "," + gender + "," + energy + "," + price + "," + relive);
		
		dis.close();
	}
}
```
{: id="20210313082711-a19st33"}

## 14.8 序列化
{: id="20210313082711-qqngoj2"}

### 14.8.1 概述
{: id="20210313082711-chj8nu6"}

Java 提供了一种对象**序列化**的机制。用一个字节序列可以表示一个对象，该字节序列包含该`对象的类型`和`对象中存储的属性`等信息。字节序列写出到文件之后，相当于文件中**持久保存**了一个对象的信息。
{: id="20210313082711-8w4ay9g"}

反之，该字节序列还可以从文件中读取回来，重构对象，对它进行**反序列化**。`对象的数据`、`对象的类型`和`对象中存储的数据`信息，都可以用来在内存中创建对象。看图理解序列化：
{: id="20210313082711-e9bouet"}

![](imgs19/3_xuliehua.jpg)
{: id="20210313082711-gq171ic"}

### 14.8.2 ObjectOutputStream类
{: id="20210313082711-gm7r6fl"}

`java.io.ObjectOutputStream ` 类，将Java对象的原始数据类型写出到文件,实现对象的持久存储。
{: id="20210313082711-vs59xpl"}

#### 构造方法
{: id="20210313082711-delf8s4"}

* {: id="20210313082711-wqz35az"}`public ObjectOutputStream(OutputStream out) `： 创建一个指定OutputStream的ObjectOutputStream。
  {: id="20210313082711-fxd5hhb"}
{: id="20210313082711-3xujsbj"}

构造举例，代码如下：
{: id="20210313082711-zox82mu"}

```java
FileOutputStream fileOut = new FileOutputStream("employee.txt");
ObjectOutputStream out = new ObjectOutputStream(fileOut);
```
{: id="20210313082711-8lv1u8b"}

#### 序列化操作
{: id="20210313082711-o1ygn1x"}

* {: id="20210313082711-t7bfl4r"}该类必须实现`java.io.Serializable ` 接口，`Serializable` 是一个标记接口，不实现此接口的类将不会使任何状态序列化或反序列化，会抛出`NotSerializableException` 。
  {: id="20210313082711-za3k8ga"}
  * {: id="20210313082711-3f4n3wo"}如果对象的某个属性也是引用数据类型，那么如果该属性也要序列化的话，也要实现`Serializable` 接口
    {: id="20210313082711-h7i3zaj"}
  {: id="20210313082711-lri29om"}
* {: id="20210313082711-vfs54qw"}该类的所有属性必须是可序列化的。如果有一个属性不需要可序列化的，则该属性必须注明是瞬态的，使用`transient` 关键字修饰。
  {: id="20210313082711-7zcfca7"}
* {: id="20210313082711-jby8uzy"}静态变量的值不会序列化
  {: id="20210313082711-szy8e0d"}
{: id="20210313082711-nz2sflh"}

```java
public class Employee implements java.io.Serializable {
    public static String company = "尚硅谷";
    public String name;
    public String address;
    public transient int age; // transient瞬态修饰成员,不会被序列化
    public void addressCheck() {
      	System.out.println("Address  check : " + name + " -- " + address);
    }
}
```
{: id="20210313082711-umufqlk"}

2.写出对象方法
{: id="20210313082711-e2k3h93"}

* {: id="20210313082711-c72ji4r"}`public final void writeObject (Object obj)` : 将指定的对象写出。
  {: id="20210313082711-e6916ac"}
{: id="20210313082711-t96gbap"}

```java
public class SerializeDemo{
   	public static void main(String [] args)   {
    	Employee e = new Employee();
    	e.name = "zhangsan";
    	e.address = "beiqinglu";
    	e.age = 20; 
    	try {
      		// 创建序列化流对象
          ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("employee.txt"));
        	// 写出对象
        	out.writeObject(e);
        	// 释放资源
        	out.close();
        	fileOut.close();
        	System.out.println("Serialized data is saved"); // 姓名，地址被序列化，年龄没有被序列化。
        } catch(IOException i)   {
            i.printStackTrace();
        }
   	}
}
输出结果：
Serialized data is saved
```
{: id="20210313082711-pt4wtzc"}

### 14.8.3 ObjectInputStream类
{: id="20210313082711-hgp4pbf"}

ObjectInputStream反序列化流，将之前使用ObjectOutputStream序列化的原始数据恢复为对象。
{: id="20210313082711-n0jvad5"}

#### 构造方法
{: id="20210313082711-pvx27qf"}

* {: id="20210313082711-ph26pzf"}`public ObjectInputStream(InputStream in) `： 创建一个指定InputStream的ObjectInputStream。
  {: id="20210313082711-zv61dkg"}
{: id="20210313082711-q0srn8r"}

#### 反序列化操作1
{: id="20210313082711-nkykf2q"}

如果能找到一个对象的class文件，我们可以进行反序列化操作，调用`ObjectInputStream`读取对象的方法：
{: id="20210313082711-1mggow5"}

- {: id="20210313082711-2mdak0g"}`public final Object readObject ()` : 读取一个对象。
  {: id="20210313082711-xn97fyg"}
{: id="20210313082711-hn308mw"}

```java
public class DeserializeDemo {
   public static void main(String [] args)   {
        Employee e = null;
        try {		
             // 创建反序列化流
             FileInputStream fileIn = new FileInputStream("employee.txt");
             ObjectInputStream in = new ObjectInputStream(fileIn);
             // 读取一个对象
             e = (Employee) in.readObject();
             // 释放资源
             in.close();
             fileIn.close();
        }catch(IOException i) {
             // 捕获其他异常
             i.printStackTrace();
             return;
        }catch(ClassNotFoundException c)  {
        	// 捕获类找不到异常
             System.out.println("Employee class not found");
             c.printStackTrace();
             return;
        }
        // 无异常,直接打印输出
        System.out.println("Name: " + e.name);	// zhangsan
        System.out.println("Address: " + e.address); // beiqinglu
        System.out.println("age: " + e.age); // 0
    }
}
```
{: id="20210313082711-xxn3lio"}

**对于JVM可以反序列化对象，它必须是能够找到class文件的类。如果找不到该类的class文件，则抛出一个 `ClassNotFoundException` 异常。**
{: id="20210313082711-it038v4"}

#### **反序列化操作2**
{: id="20210313082711-xyegowg"}

**另外，当JVM反序列化对象时，能找到class文件，但是class文件在序列化对象之后发生了修改，那么反序列化操作也会失败，抛出一个`InvalidClassException`异常。**发生这个异常的原因如下：
{: id="20210313082711-owwg0z5"}

* {: id="20210313082711-u14vlin"}该类的序列版本号与从流中读取的类描述符的版本号不匹配
  {: id="20210313082711-1rvsm4i"}
* {: id="20210313082711-u8zc47s"}该类包含未知数据类型
  {: id="20210313082711-nc0yzep"}
{: id="20210313082711-zwa2j3p"}

`Serializable` 接口给需要序列化的类，提供了一个序列版本号。`serialVersionUID` 该版本号的目的在于验证序列化的对象和对应类是否版本匹配。
{: id="20210313082711-u0pfgvh"}

```java
public class Employee implements java.io.Serializable {
     // 加入序列版本号
     private static final long serialVersionUID = 1L;
     public String name;
     public String address;
     // 添加新的属性 ,重新编译, 可以反序列化,该属性赋为默认值.
     public int eid; 

     public void addressCheck() {
         System.out.println("Address  check : " + name + " -- " + address);
     }
}
```
{: id="20210313082711-6thx6ce"}

### 14.8.4 练习：序列化集合
{: id="20210313082711-euprf37"}

1. {: id="20210313082711-0l260ft"}将存有多个自定义对象的集合序列化操作，保存到`list.txt`文件中。
   {: id="20210313082711-onugvhu"}
2. {: id="20210313082711-erho099"}反序列化`list.txt` ，并遍历集合，打印对象信息。
   {: id="20210313082711-lkqh1af"}
{: id="20210313082711-nw0vyxi"}

#### 案例分析
{: id="20210313082711-gz4koqb"}

1. {: id="20210313082711-w2bnldq"}把若干学生对象 ，保存到集合中。
   {: id="20210313082711-vfarmg3"}
2. {: id="20210313082711-et0sjk0"}把集合序列化。
   {: id="20210313082711-e2uepdx"}
3. {: id="20210313082711-2vxikn5"}反序列化读取时，只需要读取一次，转换为集合类型。
   {: id="20210313082711-6wazz1v"}
4. {: id="20210313082711-yp98moi"}遍历集合，可以打印所有的学生信息
   {: id="20210313082711-loae9qa"}
{: id="20210313082711-ghxoxcf"}

#### 案例实现
{: id="20210313082711-c8c8xft"}

```java
public class SerTest {
	public static void main(String[] args) throws Exception {
		// 创建 学生对象
		Student student = new Student("老王", "laow");
		Student student2 = new Student("老张", "laoz");
		Student student3 = new Student("老李", "laol");

		ArrayList<Student> arrayList = new ArrayList<>();
		arrayList.add(student);
		arrayList.add(student2);
		arrayList.add(student3);
		// 序列化操作
		// serializ(arrayList);
		
		// 反序列化  
		ObjectInputStream ois  = new ObjectInputStream(new FileInputStream("list.txt"));
		// 读取对象,强转为ArrayList类型
		ArrayList<Student> list  = (ArrayList<Student>)ois.readObject();
		
      	for (int i = 0; i < list.size(); i++ ){
          	Student s = list.get(i);
        	System.out.println(s.getName()+"--"+ s.getPwd());
      	}
	}

	private static void serializ(ArrayList<Student> arrayList) throws Exception {
		// 创建 序列化流 
		ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("list.txt"));
		// 写出对象
		oos.writeObject(arrayList);
		// 释放资源
		oos.close();
	}
}
```
{: id="20210313082711-dtycanl"}

### 14.8.5 java.io.Externalizable接口
{: id="20210313082711-8qt5zpf"}

除了Serializable接口之外，还可以实现java.io.Externalizable接口，但是要求重写：
{: id="20210313082711-dk67rkj"}

void readExternal(ObjectInput in)
void writeExternal(ObjectOutput out)
{: id="20210313082711-uo72ekj"}

关于哪些属性序列化和反序列化，由程序员自己定。**虽然可以自己决定任意属性的输出和读取，但是还是建议不要输出静态的和transient属性。**
{: id="20210313082711-qefk2wn"}

学生类：
{: id="20210313082711-4csuiup"}

```java
import java.io.Externalizable;
import java.io.IOException;
import java.io.ObjectInput;
import java.io.ObjectOutput;

public class Student implements Externalizable{
	private static String school = "atguigu";
	private String name;
	private transient int age;
	private int score;
	public Student(String name, int age, int score) {
		super();
		this.name = name;
		this.age = age;
		this.score = score;
	}
	public Student() {
		super();
	}
	public static String getSchool() {
		return school;
	}
	public static void setSchool(String school) {
		Student.school = school;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	public int getScore() {
		return score;
	}
	public void setScore(int score) {
		this.score = score;
	}
	@Override
	public String toString() {
		return "Student [name=" + name +",age =" +age + ", score=" + score +",schoool = " + school+ "]";
	}
	
	//一下两个方法不是程序员手动调用，而是在对象被序列化和反序列时，IO流自动调用
	@Override
	public void writeExternal(ObjectOutput out) throws IOException {
		//在这个方法中，程序员自己定，哪些属性需要序列化，及其顺序
		out.writeUTF(school);
		out.writeUTF(name);
		out.writeInt(score);
		out.writeInt(age);
	}
	@Override
	public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
		//读取的顺序要与写的顺序一致
		school = in.readUTF();
		name = in.readUTF();
		score = in.readInt();
		age = in.readInt();
	}
	
}
```
{: id="20210313082711-cb46py8"}

测试类
{: id="20210313082711-mkbydsf"}

```java
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;

import org.junit.Test;

/*
 * 类通过实现 java.io.Serializable 接口以启用其序列化功能。未实现此接口的类将无法使其任何状态序列化或反序列化。
 * 		序列化接口没有方法或字段，仅用于标识可序列化的语义。
 * 
 * java.io.Externalizable 实例类的唯一特性是可以被写入序列化流中，该类负责保存和恢复实例内容。 
 * 		则它要实现 Externalizable 接口的 writeExternal 和 readExternal 方法。
 * 
 *  void readExternal(ObjectInput in) 
 *  void writeExternal(ObjectOutput out)  
 *  
 *  虽然可以自己决定任意属性的输出和读取，但是还是建议不要输出静态的和transient属性
 */
public class TestExternalizable {
	@Test
	public void in()throws IOException, ClassNotFoundException{
		FileInputStream fis = new FileInputStream("stu.dat");
		ObjectInputStream ois = new ObjectInputStream(fis);
		
		Object obj = ois.readObject();
		
		System.out.println(obj);
		
		ois.close();
		fis.close();
	}
	
	@Test
	public void out()throws IOException{
		Student student = new Student("张三", 23, 89);
		Student.setSchool("尚硅谷");
		
		FileOutputStream fos = new FileOutputStream("stu.dat");
		ObjectOutputStream oos = new ObjectOutputStream(fos);
		
		oos.writeObject(student);
		
		oos.close();
		fos.close();
	}
}

```
{: id="20210313082711-rkd1hxl"}

## 14.9 重新认识PrintStream和Scanner、System.in和out
{: id="20210313082711-x3i0s7y"}

### 14.9.1 PrintStream类
{: id="20210313082711-vnhjjmf"}

平时我们在控制台打印输出，是调用`print`方法和`println`方法完成的，这两个方法都来自于`java.io.PrintStream`类，该类能够方便地打印各种数据类型的值，是一种便捷的输出方式。
{: id="20210313082711-w40aiou"}

#### 构造方法
{: id="20210313082711-9mmc9qf"}

* {: id="20210313082711-noiara5"}`public PrintStream(String fileName)  `： 使用指定的文件名创建一个新的打印流。
  {: id="20210313082711-2lkphs3"}
{: id="20210313082711-mu1gc00"}

构造举例，代码如下：
{: id="20210313082711-phq55yz"}

```java
PrintStream ps = new PrintStream("ps.txt")；
```
{: id="20210313082711-p5eg8vl"}

#### 改变打印流向
{: id="20210313082711-2posf28"}

`System.out`就是`PrintStream`类型的，只不过它的流向是系统规定的，打印在控制台上。不过，既然是流对象，我们就可以玩一个"小把戏"，改变它的流向。
{: id="20210313082711-qg2vn8x"}

```java
public class PrintDemo {
    public static void main(String[] args) throws IOException {
		// 调用系统的打印流,控制台直接输出97
        System.out.println(97);
      
		// 创建打印流,指定文件的名称
        PrintStream ps = new PrintStream("ps.txt");
      	
      	// 设置系统的打印流流向,输出到ps.txt
        System.setOut(ps);
      	// 调用系统的打印流,ps.txt中输出97
        System.out.println(97);
    }
}
```
{: id="20210313082711-0opkkdy"}

### 14.9.2 Scanner类
{: id="20210313082711-7yfb7es"}

#### 构造方法
{: id="20210313082711-9pjhnua"}

* {: id="20210313082711-rmo95m4"}Scanner(File source) ：构造一个新的 Scanner，它生成的值是从指定文件扫描的。
  {: id="20210313082711-gm50n53"}
* {: id="20210313082711-9midbbo"}Scanner(File source, String charsetName) ：构造一个新的 Scanner，它生成的值是从指定文件扫描的。
  {: id="20210313082711-wtk2n1p"}
* {: id="20210313082711-wlos907"}Scanner(InputStream source) ：构造一个新的 Scanner，它生成的值是从指定的输入流扫描的。
  {: id="20210313082711-2hsryzf"}
* {: id="20210313082711-bri4t3a"}Scanner(InputStream source, String charsetName) ：构造一个新的 Scanner，它生成的值是从指定的输入流扫描的。
  {: id="20210313082711-73uv0b6"}
{: id="20210313082711-oim89qb"}

#### 常用方法：
{: id="20210313082711-th6l4gt"}

* {: id="20210313082711-dyez9bz"}boolean hasNextXxx()： 如果通过使用nextXxx()方法，此扫描器输入信息中的下一个标记可以解释为默认基数中的一个 Xxx 值，则返回 true。
  {: id="20210313082711-yb4lr0z"}
* {: id="20210313082711-lxkrz3t"}Xxx nextXxx()： 将输入信息的下一个标记扫描为一个Xxx
  {: id="20210313082711-e702w76"}
{: id="20210313082711-swk8fww"}

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Scanner;

import org.junit.Test;

public class TestFile {
	@Test
	public void test1() throws IOException {
		Scanner input = new Scanner(System.in);
		ArrayList<String> list = new ArrayList<>();
		while(true){
			System.out.print("请输入一个单词：");
			String str = input.nextLine();
			if("stop".equals(str)){
				break;
			}
			list.add(str);
		}
		System.out.println(list);
		input.close();
	}
	@Test
	public void test2() throws IOException {
		Scanner input = new Scanner(new File("1.txt"));
		while(input.hasNextLine()){
			String str = input.nextLine();
			System.out.println(str);
		}
		input.close();
	}
	
	@Test
	public void test3() throws FileNotFoundException{
		System.setIn(new FileInputStream("1.txt"));
		Scanner input = new Scanner(System.in);
		while(input.hasNextLine()){
			String str = input.nextLine();
			System.out.println(str);
		}
		input.close();
	}
}
```
{: id="20210313082711-f939qsk"}


{: id="20210313082711-u7ijmvm" type="doc"}
