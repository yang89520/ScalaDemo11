# day11_课后练习

# 代码阅读题

## 第1题

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

## 第2题

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
```

## 第3题

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
```

# 注解编程题

## 第4题

案例：

​	1、编写图形工具类：ShapTools

​	（1）声明方法1：public static void printRectangle()，打印5行5列*组成的矩形图形

​	（2）声明方法2：public static void printRectangle(int line, int column, String sign)，打印line行column列由sign组成的矩形图形

​	（3）给这个类加上文档注释：包含@author，@param等

​	（4）给方法1标记已过时注解

​	2、编写测试类Test04

​	在测试类中调用上面的两个方法测试，如果有警告，就在main方法上抑制警告

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

![](imgs/1559467323991.png)

## 第5题

案例：

​	1、声明自定义注解@Table

​	（1）加上String类型的配置参数value

​	（2）并限定@Table的使用位置为类上

​	（3）并指定生命周期为“运行时”

​	2、声明自定义注解@Column

​	（1）加上String类型的配置参数name，表示表格的列名

​	（2）加上String类型的配置参数type，表示表格的列数据类型

​	（3）并限定@Column的使用位置在属性上

​	（4）并指定生命周期为“运行时”

​	3、声明User类，

​	（1）属性：id, username, password, email

​	（2）在User类上，标记@Table注解，并为value赋值为"t_user"

​	（3）在User类的每一个属性上标记@Column，并为name和type赋值，例如：

​		id：name赋值为no，type赋值为int

​		username：name赋值为username，type赋值为varchar(20)

​		password：name赋值为pwd，type赋值为char(6)

​		email：name赋值为email，type赋值为varchar(50)

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



# 内部类编程代码题

## 第6题

编写一个匿名内部类，它继承Object，并在匿名内部类中，声明一个方法public void test()打印尚硅谷。

请编写代码调用这个方法。

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

## 第7题

案例：将第4题，改用匿名内部类实现实现接口，来代替CompareBig和CompareColor

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



## 第8题

案例：将第5题，改用匿名内部类实现接口，来代替V1Filter、V2Filter、AFilter

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

## 第9题

案例：

​	1、声明一个接口：Selector，包含抽象方法：

​	（1）boolean hasNext()

​	（2）Object next()

​	2、声明一个接口：Touchable，包含抽象方法：

​	（1）Selector select()

​	3、声明一个MyArrayList类，当做容器类使用，模拟动态数组数据结构的容器

​	（1）包含私有属性：

​	①Object[] all；用于保存对象，初始化长度为2

​	②int total；记录实际存储的对象个数

​	（2）包含方法：

​	①public void add(Object element)：用于添加一个元素到当前容器中，如果数组all已满，就扩容为原来的2倍

​	②public void remove(int index)：如果index<0或index>=total就打印“没有这个元素”并返回，否则删除index位置的元素

​	③public void set(int index, Object value)：如果index<0或index>=total就打印“没有这个元素”并返回，否则就替换index位置的元素为value

​	④public Object get(int index)：如果index<0或index>=total就打印“没有这个元素”并返回null，否则返回index位置的元素

​	⑤让类MyArrayList实现Touchable接口，并重写Selector select()方法，返回内部类MySelector的对象

​	⑥在类MyArrayList中声明private的内部类MySelector，实现Selector接口

​	A：在内部类MySelector声明一个属性：int cursor（游标）

​	B：MySelector实现Selector接口，并重写两个抽象方法，其中

* ​		boolean hasNext()实现为：return cursor != total
* ​		Object next()实现为：return all[cursor++]

4、在测试类Test06_01中，

（1）创建MyArrayList的对象list

（2）调用list的add方法，添加3个对象

（3）调用list的remove方法，删除[1]的对象

（4）调用list的set方法，替换[1]的对象

（5）调用list的get方法，获取[1]的对象

（6）调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象

5、在测试类Test06_02中，

（1）声明静态的MyArrayList类型的list类变量，

（2）声明public static void init()方法，

​	①在方法中创建MyArrayList类型对象，

​	②并调用list的add()方法，添加3个对象，

​	③并在init()方法上标记JUnit4的@BeforeClass注解

（3）声明public void before()方法，

​	①打印“该测试方法开始前list中的数据如下："

​	②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象

​	③并在before()方法上标记JUnit4的@Before的注解

（4）声明public void after()方法，

​	①打印“该测试方法结束后list中的数据如下："

​	②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象

​	③并在after()方法上标记JUnit4的@After的注解

（5）声明public void testAdd()方法，

​	①在方法中，打印“现在测试的是testAdd()方法"

​	②在方法中，再次调用list的add()方法往list容器对象中添加1个对象

​	③并在testAdd()方法上标记JUnit4的@Test的注解

（6）声明public void testRemove()方法，

​	①在方法中，打印“现在测试的是testRemove()方法"

​	②调用list的remove方法，删除[1]的对象

​	③并在testRemove()方法上标记JUnit4的@Test的注解

（7）声明public void testSet()方法

​	①在方法中，打印“现在测试的是testSet()方法"

​	②调用list的set方法，替换[1]的对象

​	③并在testSet()方法上标记JUnit4的@Test的注解

（8）声明public void testGet()方法

​	①在方法中，打印“现在测试的是testGet()方法"

​	②调用list的get方法，获取[1]的对象，并打印

​	③并在testGet()方法上标记JUnit4的@Test的注解

```java
package com.atguigu.test06;

public interface Selector {
	boolean hasNext();
	Object next();
}

```

```java
package com.atguigu.test06;

public interface Touchable {
	Selector select();
}

```

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

