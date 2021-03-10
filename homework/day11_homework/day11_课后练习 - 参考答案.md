# day11_课后练习
{: id="20210310174140-0id5h8v"}

# 代码阅读题
{: id="20210310174140-fn14bmz"}

## 第1题
{: id="20210310174140-dw0suf8"}

```java
interface A{
	int x = 0;
}
class B{
	int x = 1;
}
class C extends B implements A{
	public void printX(){
		System.out.println(x);
	}
	public static void main(String[] args) {
		new C().printX();
	}
}
```
{: id="20210310174140-9kd51br"}

```java
//编译不通过，因为在C类中x有歧义。
interface A{
	int x = 0;
}
class B{
	int x = 1;
}
class C extends B implements A{
	public void printX(){
//		System.out.println(x);//有歧义，要么写super.x，要么写A.x
	}
	public static void main(String[] args) {
		new C().printX();
	}
}
```
{: id="20210310174140-qht4p2m"}

## 第2题
{: id="20210310174140-flay7m9"}

```java
public class Test10 {
    public static void main(String[] args) {
        Out.In in = new Out().new In();
        in.print();
    }
}
class Out {
    private int age = 12;
    class In {
        private int age = 13;
        public void print() {
            int age = 14;
            System.out.println("局部变量：" + age);//14
            System.out.println("内部类变量：" + this.age);//13
            System.out.println("外部类变量：" + Out.this.age);//12
        }
    }
}

//因为我们要创建内部类In对象时，需要外部类的对象。Out.this就表示哪个外部类对象。
//非静态内部类可以调用外部类的属性和方法，但是重新声明的重名属性age不会覆盖外部类，
//在堆中拥有不同的内存地址
```
{: id="20210310174140-ncqniqh" updated="20210310185425"}

## 第3题
{: id="20210310174140-umvzarb"}

```java
package com.atguigu.test11;

public class Test11 {
	public static void main(String[] args) {
        Out out = new Out();
        out.Print(3);
    }
}
class Out {
    private int age = 12;
    public void Print(final int x) {
        class In {
            public void inPrint() {
                System.out.println(x);//3
                System.out.println(age);//12
            }
        }
        new In().inPrint();
    }
}
//外部类的属性非静态方法全能使用，方法中的局部内部类
//就相当于方法体，所以一样能够访问外部属性和形参的值
```
{: id="20210310174140-6rw731y" updated="20210310190353"}

# 注解编程题
{: id="20210310174140-4awhioy"}

## 第4题
{: id="20210310174140-weejzyo"}

案例：
{: id="20210310174140-ho7tv1l"}

```
1、编写图形工具类：ShapTools
```

{: id="20210310174140-8i50lrz"}

```
（1）声明方法1：public static void printRectangle()，打印5行5列*组成的矩形图形
```

{: id="20210310174140-cpxco29"}

```
（2）声明方法2：public static void printRectangle(int line, int column, String sign)，打印line行column列由sign组成的矩形图形
```

{: id="20210310174140-ruh9l08"}

```
（3）给这个类加上文档注释：包含@author，@param等
```

{: id="20210310174140-285fyi4"}

```
（4）给方法1标记已过时注解
```

{: id="20210310174140-u800i8c"}

```
2、编写测试类Test04
```

{: id="20210310174140-m7e5o9w"}

```
在测试类中调用上面的两个方法测试，如果有警告，就在main方法上抑制警告
```

{: id="20210310174140-1h325kc"}

```java
package com.atguigu.test04;

public class Test04 {
	public static void main(String[] args) {
		ShapTools.printRectangle();
		ShapTools.printRectangle(3, 10, "#");
	}
}
class ShapTools{
	@Deprecated
	public static void printRectangle(){
		for (int i = 0; i < 5; i++) {
			for (int j = 0; j < 5; j++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
	public static void printRectangle(int line, int column, String sign){
		for (int i = 0; i < line; i++) {
			for (int j = 0; j < column; j++) {
				System.out.print(sign);
			}
			System.out.println();
		}
	}
}
```
{: id="20210310174140-gmrflxi"}

![](imgs/1559467323991.png)
{: id="20210310174140-9flj1zc"}

## 第5题
{: id="20210310174140-9wlhqi8"}

案例：
{: id="20210310174140-yxgnwv1"}

```
1、声明自定义注解@Table
```

{: id="20210310174140-rdcqz88"}

```
（1）加上String类型的配置参数value
```

{: id="20210310174140-ffw7oyu"}

```
（2）并限定@Table的使用位置为类上
```

{: id="20210310174140-mjx7gby"}

```
（3）并指定生命周期为“运行时”
```

{: id="20210310174140-i4etl9p"}

```
2、声明自定义注解@Column
```

{: id="20210310174140-2238xrt"}

```
（1）加上String类型的配置参数name，表示表格的列名
```

{: id="20210310174140-6xopfvv"}

```
（2）加上String类型的配置参数type，表示表格的列数据类型
```

{: id="20210310174140-tfna0nd"}

```
（3）并限定@Column的使用位置在属性上
```

{: id="20210310174140-aebakue"}

```
（4）并指定生命周期为“运行时”
```

{: id="20210310174140-97pwuql"}

```
3、声明User类，
```

{: id="20210310174140-1vbz9yq"}

```
（1）属性：id, username, password, email
```

{: id="20210310174140-b7bkhg3"}

```
（2）在User类上，标记@Table注解，并为value赋值为"t_user"
```

{: id="20210310174140-k6ln659"}

```
（3）在User类的每一个属性上标记@Column，并为name和type赋值，例如：
```

{: id="20210310174140-188i5wd"}

```
id：name赋值为no，type赋值为int
```

{: id="20210310174140-k1brb2y"}

```
username：name赋值为username，type赋值为varchar(20)
```

{: id="20210310174140-ojp7fcy"}

```
password：name赋值为pwd，type赋值为char(6)
```

{: id="20210310174140-ro862ke"}

```
email：name赋值为email，type赋值为varchar(50)
```

{: id="20210310174140-mf0za95"}

```java
package com.atguigu.test05;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface Table {
	String value();
}
```
{: id="20210310174140-hcwtm6h"}

```java
package com.atguigu.test05;

import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Target(ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Column {
	String name();
	String type();
}

```
{: id="20210310174140-l6nvo0k"}

```java
package com.atguigu.test05;

@Table("t_user")
public class User {
	@Column(name="no",type="int")
	private int id;

	@Column(name="username",type="varchar(20)")
	private String username;

	@Column(name="pwd",type="char(6)")
	private String password;

	@Column(name="email",type="varchar(50)")
	private String email;

	public User(int id, String username, String password, String email) {
		super();
		this.id = id;
		this.username = username;
		this.password = password;
		this.email = email;
	}
	public User() {
		super();
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getUsername() {
		return username;
	}
	public void setUsername(String username) {
		this.username = username;
	}
	public String getPassword() {
		return password;
	}
	public void setPassword(String password) {
		this.password = password;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	@Override
	public String toString() {
		return "User [id=" + id + ", username=" + username + ", password=" + password + ", email=" + email + "]";
	}

}
```
{: id="20210310174140-dk3dg3a"}

# 内部类编程代码题
{: id="20210310174140-wmxl379"}

## 第6题
{: id="20210310174140-1uc93uh"}

编写一个匿名内部类，它继承Object，并在匿名内部类中，声明一个方法public void test()打印尚硅谷。
{: id="20210310174140-7mu459d"}

请编写代码调用这个方法。
{: id="20210310174140-hy4n095"}

```java
package com.atguigu.test06;

public class Test06 {
	public static void main(String[] args) {
		new Object(){
			public void test(){
				System.out.println("尚硅谷");
			}
		}.test();
	}
}

```
{: id="20210310174140-v4gm4w5"}

## 第7题
{: id="20210310174140-c3d8rnc"}

案例：将第4题，改用匿名内部类实现实现接口，来代替CompareBig和CompareColor
{: id="20210310174140-ukjwezu"}

```java
package com.atguigu.test07;

public class Test07 {
	public static void main(String[] args) {
		Worker w = new Worker();
		Apple a1 = new Apple(5, "青色");
		Apple a2 = new Apple(3, "红色");
	
		w.pickApple(new CompareAble(){}, a1, a2);
		w.pickApple(new CompareAble(){
			@Override
			public void compare(Apple a1, Apple a2) {
				System.out.println("挑红的：");
				if("红色".equals(a1.getColor())){
					System.out.println(a1);
				}
				if("红色".equals(a2.getColor())){
					System.out.println(a2);
				}
			}
		}, a1, a2);
	}
}
class Apple{
	private double size;
	private String color;
	public Apple(double size, String color) {
		super();
		this.size = size;
		this.color = color;
	}
	public Apple() {
		super();
	}
	public double getSize() {
		return size;
	}
	public void setSize(double size) {
		this.size = size;
	}
	public String getColor() {
		return color;
	}
	public void setColor(String color) {
		this.color = color;
	}
	@Override
	public String toString() {
		return size + "-" + color;
	}

}
interface CompareAble{
	default void compare(Apple a1,Apple a2){
		System.out.println("默认挑大的：");
		if(a1.getSize() > a2.getSize()){
			System.out.println(a1);
		}else{
			System.out.println(a2);
		}
	}
}
class Worker{
	public void pickApple(CompareAble c,Apple a1,Apple a2){
		c.compare(a1, a2);
	}
}
```
{: id="20210310174140-gvosspb"}

## 第8题
{: id="20210310174140-fu6kms8"}

案例：将第5题，改用匿名内部类实现接口，来代替V1Filter、V2Filter、AFilter
{: id="20210310174140-z6isdnf"}

```java
package com.atguigu.test08;

public class Test08 {
	public static void main(String[] args) {
		User[] all = new User[15];
		for (int i = 0; i < all.length; i++) {
			all[i] = new User(null,i+1);
		}
		Receptionist r1 = new Receptionist(new Filter(){
			@Override
			public void filterUser(User u) {
				u.setType("v1");
			}
		});
		for (int i = 0; i < 5; i++) {
			r1.recept(all[i]);
		}
		Receptionist r2 = new Receptionist(new Filter(){
			@Override
			public void filterUser(User u) {
				u.setType("v2");
			}
		});
		for (int i = 5; i < 10; i++) {
			r2.recept(all[i]);
		}
		Receptionist r3 = new Receptionist(new Filter(){
			@Override
			public void filterUser(User u) {
				u.setType("A");
			}
		
		});
		for (int i = 10; i < 15; i++) {
			r3.recept(all[i]);
		}
		for (int i = 0; i < all.length; i++) {
			System.out.println(all[i]);
		}
	}
}
class User{
	private String type;
	private int id;
	public User(String type, int id) {
		super();
		this.type = type;
		this.id = id;
	}
	public String getType() {
		return type;
	}
	public void setType(String type) {
		this.type = type;
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	@Override
	public String toString() {
		return id + "-" + type;
	}
}
interface Filter{
	void filterUser(User u);
}

class Receptionist{
	private Filter filter;

	public Receptionist(Filter filter) {
		super();
		this.filter = filter;
	}

	public Filter getFilter() {
		return filter;
	}

	public void setFilter(Filter filter) {
		this.filter = filter;
	}
	public void recept(User u){
		if(u.getType() != null){
			return ;
		}
		filter.filterUser(u);
	}
}

```
{: id="20210310174140-udgudg9"}

## 第9题
{: id="20210310174140-lhicquo"}

案例：
{: id="20210310174140-jzfyfw0"}

```
1、声明一个接口：Selector，包含抽象方法：
```

{: id="20210310174140-j2sfu2l"}

```
（1）boolean hasNext()
```

{: id="20210310174140-vh4zc9v"}

```
（2）Object next()
```

{: id="20210310174140-qyyxfi2"}

```
2、声明一个接口：Touchable，包含抽象方法：
```

{: id="20210310174140-ilhphlx"}

```
（1）Selector select()
```

{: id="20210310174140-ilpbnn5"}

```
3、声明一个MyArrayList类，当做容器类使用，模拟动态数组数据结构的容器
```

{: id="20210310174140-ve952dj"}

```
（1）包含私有属性：
```

{: id="20210310174140-zm3uci1"}

```
①Object[] all；用于保存对象，初始化长度为2
```

{: id="20210310174140-bo215mv"}

```
②int total；记录实际存储的对象个数
```

{: id="20210310174140-8v49agb"}

```
（2）包含方法：
```

{: id="20210310174140-ypfgap9"}

```
①public void add(Object element)：用于添加一个元素到当前容器中，如果数组all已满，就扩容为原来的2倍
```

{: id="20210310174140-awguowk"}

```
②public void remove(int index)：如果index<0或index>=total就打印“没有这个元素”并返回，否则删除index位置的元素
```

{: id="20210310174140-os68131"}

```
③public void set(int index, Object value)：如果index<0或index>=total就打印“没有这个元素”并返回，否则就替换index位置的元素为value
```

{: id="20210310174140-e8ar4yl"}

```
④public Object get(int index)：如果index<0或index>=total就打印“没有这个元素”并返回null，否则返回index位置的元素
```

{: id="20210310174140-lv4ossf"}

```
⑤让类MyArrayList实现Touchable接口，并重写Selector select()方法，返回内部类MySelector的对象
```

{: id="20210310174140-mkii82e"}

```
⑥在类MyArrayList中声明private的内部类MySelector，实现Selector接口
```

{: id="20210310174140-idoexin"}

```
A：在内部类MySelector声明一个属性：int cursor（游标）
```

{: id="20210310174140-gwzaoae"}

```
B：MySelector实现Selector接口，并重写两个抽象方法，其中
```

{: id="20210310174140-2552jom"}

* {: id="20210310174140-xetydmw"}
  ```
  boolean hasNext()实现为：return cursor != total
  ```

  {: id="20210310174140-h0ovwpr"}
* {: id="20210310174140-yyhayn9"}
  ```
  Object next()实现为：return all[cursor++]
  ```

  {: id="20210310174140-v0ccmng"}
{: id="20210310174140-0sxxvau"}

4、在测试类Test06_01中，
{: id="20210310174140-9xey6zx"}

（1）创建MyArrayList的对象list
{: id="20210310174140-i4lv01k"}

（2）调用list的add方法，添加3个对象
{: id="20210310174140-y26huy4"}

（3）调用list的remove方法，删除[1]的对象
{: id="20210310174140-o1kavip"}

（4）调用list的set方法，替换[1]的对象
{: id="20210310174140-iahrkqw"}

（5）调用list的get方法，获取[1]的对象
{: id="20210310174140-xh807ci"}

（6）调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
{: id="20210310174140-8j8qmx1"}

5、在测试类Test06_02中，
{: id="20210310174140-qaeg8y2"}

（1）声明静态的MyArrayList类型的list类变量，
{: id="20210310174140-4ft10wk"}

（2）声明public static void init()方法，
{: id="20210310174140-nbbqwme"}

```
①在方法中创建MyArrayList类型对象，
```

{: id="20210310174140-we06s96"}

```
②并调用list的add()方法，添加3个对象，
```

{: id="20210310174140-mulp3ix"}

```
③并在init()方法上标记JUnit4的@BeforeClass注解
```

{: id="20210310174140-6dpx6om"}

（3）声明public void before()方法，
{: id="20210310174140-zqx139w"}

```
①打印“该测试方法开始前list中的数据如下："
```

{: id="20210310174140-ygdl5sq"}

```
②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
```

{: id="20210310174140-uhtmtur"}

```
③并在before()方法上标记JUnit4的@Before的注解
```

{: id="20210310174140-iuq8xu1"}

（4）声明public void after()方法，
{: id="20210310174140-5owwxsh"}

```
①打印“该测试方法结束后list中的数据如下："
```

{: id="20210310174140-6g1miw1"}

```
②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
```

{: id="20210310174140-h4segvf"}

```
③并在after()方法上标记JUnit4的@After的注解
```

{: id="20210310174140-v841t5x"}

（5）声明public void testAdd()方法，
{: id="20210310174140-vk2xszl"}

```
①在方法中，打印“现在测试的是testAdd()方法"
```

{: id="20210310174140-echtd60"}

```
②在方法中，再次调用list的add()方法往list容器对象中添加1个对象
```

{: id="20210310174140-jgnd2vj"}

```
③并在testAdd()方法上标记JUnit4的@Test的注解
```

{: id="20210310174140-nmv0aqg"}

（6）声明public void testRemove()方法，
{: id="20210310174140-n9q9gnu"}

```
①在方法中，打印“现在测试的是testRemove()方法"
```

{: id="20210310174140-yld8tt9"}

```
②调用list的remove方法，删除[1]的对象
```

{: id="20210310174140-3kavxww"}

```
③并在testRemove()方法上标记JUnit4的@Test的注解
```

{: id="20210310174140-jocl62c"}

（7）声明public void testSet()方法
{: id="20210310174140-5dhcaj7"}

```
①在方法中，打印“现在测试的是testSet()方法"
```

{: id="20210310174140-qihgneo"}

```
②调用list的set方法，替换[1]的对象
```

{: id="20210310174140-xj1cqh2"}

```
③并在testSet()方法上标记JUnit4的@Test的注解
```

{: id="20210310174140-tyk3z0y"}

（8）声明public void testGet()方法
{: id="20210310174140-0utcc49"}

```
①在方法中，打印“现在测试的是testGet()方法"
```

{: id="20210310174140-3tuzp34"}

```
②调用list的get方法，获取[1]的对象，并打印
```

{: id="20210310174140-qic3nwg"}

```
③并在testGet()方法上标记JUnit4的@Test的注解
```

{: id="20210310174140-4codb33"}

```java
package com.atguigu.test06;

public interface Selector {
	boolean hasNext();
	Object next();
}

```
{: id="20210310174140-bercwmv"}

```java
package com.atguigu.test06;

public interface Touchable {
	Selector select();
}

```
{: id="20210310174140-pvhyon2"}

```java
package com.atguigu.test06;

import java.util.Arrays;

public class MyArrayList implements Touchable{
	private Object[] all = new Object[2];
	private int total;

	public void add(Object element){
		if(total>=all.length){
			all = Arrays.copyOf(all, all.length*2);
		}
		all[total++] = element;
	}

	public void remove(int index){
		if(index < 0 || index >= total){
			System.out.println("没有这个元素");
			return;
		}
		System.arraycopy(all, index+1, all, index, total-index-1);
		all[--total]=null;
	}

	public void set(int index, Object value){
		if(index < 0 || index >= total){
			System.out.println("没有这个元素");
			return;
		}
		all[index] = value;
	}

	public Object get(int index){
		if(index < 0 || index >= total){
			System.out.println("没有这个元素");
			return null;
		}
		return all[index];
	}

	@Override
	public Selector select() {
		return new MySelector();
	}

	private class MySelector implements Selector{
		private int cursor;
		@Override
		public boolean hasNext() {
			return cursor != total;
		}

		@Override
		public Object next() {
			return all[cursor++];
		}
	
	}
}
```
{: id="20210310174140-2e4sqgi"}

```java
package com.atguigu.test06;

public class Test06_01 {
	public static void main(String[] args) {
		MyArrayList list = new MyArrayList();
	
		//---add()---
		list.add("张三");
		list.add("李四");
		list.add("王五");
	
		//---remove()---
		list.remove(1);
	
		//---set()---
		list.set(1,"赵六");
	
		//---get()---
		Object obj = list.get(1);
		System.out.println("[1] = " + obj);
	
		//---select()---
		Selector select = list.select();
		while(select.hasNext()){
			Object next = select.next();
			System.out.println(next);
		}
	}
}
```
{: id="20210310174140-jkcgk1h"}

```java
package com.atguigu.test06;

import org.junit.After;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class Test06_02 {
	private static MyArrayList list;

	@BeforeClass
	public static void init(){
		list = new MyArrayList();
		list.add("张三");
		list.add("李四");
		list.add("王五");
	}

	@Before
	public void before(){
		System.out.println("该测试方法开始前list中的数据如下：");
		Selector select = list.select();
		while(select.hasNext()){
			Object next = select.next();
			System.out.println(next);
		}
	}

	@After
	public void after(){
		System.out.println("该测试方法结束后list中的数据如下：");
		Selector select = list.select();
		while(select.hasNext()){
			Object next = select.next();
			System.out.println(next);
		}
	}

	@Test
	public void testAdd(){
		System.out.println("现在测试的是testAdd()方法");
		list.add("柴林燕");
	}

	@Test
	public void testRemove(){
		System.out.println("现在测试的是testRemove()方法");
		list.remove(1);
	}

	@Test
	public void testSet(){
		System.out.println("现在测试的是testSet()方法");
		list.set(1,"赵六");
	}

	@Test
	public void testGet(){
		System.out.println("现在测试的是testGet()方法");
		Object object = list.get(1);
		System.out.println(object);
	}

}
```
{: id="20210310174140-tpqx665"}


{: id="20210310174140-gp2g5e1" type="doc"}
