# day11_课后练习
{: id="20210310174140-7s3c6o8"}

# 代码阅读题
{: id="20210310174140-s8f9xtb"}

## 第1题
{: id="20210310174140-ksek4dz"}

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
{: id="20210310174140-m8kh0fz"}

## 第2题
{: id="20210310174140-n41m4w8"}

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
            System.out.println("局部变量：" + age);
            System.out.println("内部类变量：" + this.age);
            System.out.println("外部类变量：" + Out.this.age);
        }
    }
}
```
{: id="20210310174140-otdmr9a"}

## 第3题
{: id="20210310174140-ze44wrc"}

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
                System.out.println(x);
                System.out.println(age);
            }
        }
        new In().inPrint();
    }
}
```
{: id="20210310174140-8akvkb8"}

# 注解编程题
{: id="20210310174140-2s7z50b"}

## 第4题
{: id="20210310174140-xxmmhr4"}

案例：
{: id="20210310174140-ip28115"}

​	1、编写图形工具类：ShapTools
{: id="20210310174140-zinwsuc"}

​	（1）声明方法1：public static void printRectangle()，打印5行5列*组成的矩形图形
{: id="20210310174140-cswptfv"}

​	（2）声明方法2：public static void printRectangle(int line, int column, String sign)，打印line行column列由sign组成的矩形图形
{: id="20210310174140-02q7zv5"}

​	（3）给这个类加上文档注释：包含@author，@param等
{: id="20210310174140-lb8qusi"}

​	（4）给方法1标记已过时注解
{: id="20210310174140-a30calm"}

​	2、编写测试类Test04
{: id="20210310174140-q2tcrvd"}

​	在测试类中调用上面的两个方法测试，并在main方法上抑制警告
{: id="20210310174140-7z7rof2"}

## 第5题
{: id="20210310174140-tmf7qin"}

案例：
{: id="20210310174140-bb7auwj"}

​	1、声明自定义注解@Table
{: id="20210310174140-jqzvj3h"}

​	（1）加上String类型的配置参数value
{: id="20210310174140-16uo8i3"}

​	（2）并限定@Table的使用位置为类上
{: id="20210310174140-eevk7j1"}

​	（3）并指定生命周期为“运行时”
{: id="20210310174140-ahmli8y"}

​	2、声明自定义注解@Column
{: id="20210310174140-exo8qmz"}

​	（1）加上String类型的配置参数name，表示表格的列名
{: id="20210310174140-s0fq1i7"}

​	（2）加上String类型的配置参数type，表示表格的列数据类型
{: id="20210310174140-std7ppa"}

​	（3）并限定@Column的使用位置在属性上
{: id="20210310174140-9uv1j5o"}

​	（4）并指定生命周期为“运行时”
{: id="20210310174140-blqsb15"}

​	3、声明User类，
{: id="20210310174140-1itao1b"}

​	（1）属性：id, username, password, email
{: id="20210310174140-pypsqjp"}

​	（2）在User类上，标记@Table注解，并为value赋值为"t_user"
{: id="20210310174140-hzmzm0t"}

​	（3）在User类的每一个属性上标记@Column，并为name和type赋值，例如：
{: id="20210310174140-lu98ws1"}

​		id：name赋值为no，type赋值为int
{: id="20210310174140-jveh2sj"}

​		username：name赋值为username，type赋值为varchar(20)
{: id="20210310174140-uyuy6tr"}

​		password：name赋值为pwd，type赋值为char(6)
{: id="20210310174140-id4pru9"}

​		email：name赋值为email，type赋值为varchar(50)
{: id="20210310174140-kaomp58"}

# 内部类编程题
{: id="20210310174140-5hzfy94"}

## 第6题
{: id="20210310174140-0maq0ag"}

编写一个匿名内部类，它继承Object，并在匿名内部类中，声明一个方法public void test()打印尚硅谷。
{: id="20210310174140-aw5trwz"}

请编写代码调用这个方法。
{: id="20210310174140-mtipvei"}

## 第7题
{: id="20210310174140-mv7dbs3"}

案例：将第4题，改用匿名内部类实现实现接口，来代替CompareBig和CompareColor
{: id="20210310174140-qcwm4nt"}

## 第8题
{: id="20210310174140-ep7de11"}

案例：将第5题，改用匿名内部类实现接口，来代替V1Filter、V2Filter、AFilter
{: id="20210310174140-01yqlo1"}

## 第9题
{: id="20210310174140-avpsbgs"}

案例：
{: id="20210310174140-fsabmzw"}

​	1、声明一个接口：Selector，包含抽象方法：
{: id="20210310174140-0jlhtzl"}

​	（1）boolean hasNext()
{: id="20210310174140-wdfa9ol"}

​	（2）Object next()
{: id="20210310174140-mc1ctwb"}

​	2、声明一个接口：Touchable，包含抽象方法：
{: id="20210310174140-zaty38e"}

​	（1）Selector select()
{: id="20210310174140-tpyiy1g"}

​	3、声明一个MyArrayList类，当做容器类使用，模拟动态数组数据结构的容器
{: id="20210310174140-rf8nv85"}

​	（1）包含私有属性：
{: id="20210310174140-wq1eh52"}

​	①Object[] all；用于保存对象，初始化长度为2
{: id="20210310174140-q6cqma3"}

​	②int total；记录实际存储的对象个数
{: id="20210310174140-du3re0j"}

​	（2）包含方法：
{: id="20210310174140-br3p5ga"}

​	①public void add(Object element)：用于添加一个元素到当前容器中，如果数组all已满，就扩容为原来的2倍
{: id="20210310174140-dee7orn"}

​	②public void remove(int index)：如果index<0或index>=total就打印“没有这个元素”并返回，否则删除index位置的元素
{: id="20210310174140-rqbu17e"}

​	③public void set(int index, Object value)：如果index<0或index>=total就打印“没有这个元素”并返回，否则就替换index位置的元素为value
{: id="20210310174140-6dmtrzn"}

​	④public Object get(int index)：如果index<0或index>=total就打印“没有这个元素”并返回null，否则返回index位置的元素
{: id="20210310174140-sjiagpe"}

​	⑤让类MyArrayList实现Touchable接口，并重写Selector select()方法，返回内部类MySelector的对象
{: id="20210310174140-xyhmdk0"}

​	⑥在类MyArrayList中声明private的内部类MySelector，实现Selector接口
{: id="20210310174140-48mx5u8"}

​	A：在内部类MySelector声明一个属性：int cursor（游标）
{: id="20210310174140-m1nx27i"}

​	B：MySelector实现Selector接口，并重写两个抽象方法，其中
{: id="20210310174140-z0yms8u"}

* {: id="20210310174140-qqkeczm"}​		boolean hasNext()实现为：return cursor != total
  {: id="20210310174140-vlcy5y3"}
* {: id="20210310174140-004ytg8"}​		Object next()实现为：return all[cursor++]
  {: id="20210310174140-81wlb6h"}
{: id="20210310174140-mxl8y33"}

4、在测试类Test06_01中，
{: id="20210310174140-5wd93am"}

（1）创建MyArrayList的对象list
{: id="20210310174140-5kcvct4"}

（2）调用list的add方法，添加3个对象
{: id="20210310174140-0aj75cx"}

（3）调用list的remove方法，删除[1]的对象
{: id="20210310174140-twphtpp"}

（4）调用list的set方法，替换[1]的对象
{: id="20210310174140-r2rlgvt"}

（5）调用list的get方法，获取[1]的对象
{: id="20210310174140-m1rlztw"}

（6）调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
{: id="20210310174140-smuwfl9"}

5、在测试类Test06_02中，
{: id="20210310174140-4t6wpe8"}

（1）声明静态的MyArrayList类型的list类变量，
{: id="20210310174140-qme886d"}

（2）声明public static void init()方法，
{: id="20210310174140-3wntmky"}

​	①在方法中创建MyArrayList类型对象，
{: id="20210310174140-5zn2kx4"}

​	②并调用list的add()方法，添加3个对象，
{: id="20210310174140-kwkhgt3"}

​	③并在init()方法上标记JUnit4的@BeforeClass注解
{: id="20210310174140-uzlrkl7"}

（3）声明public void before()方法，
{: id="20210310174140-1uc8sd3"}

​	①打印“该测试方法开始前list中的数据如下："
{: id="20210310174140-gbyk1lw"}

​	②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
{: id="20210310174140-w5anhly"}

​	③并在before()方法上标记JUnit4的@Before的注解
{: id="20210310174140-0z8io6j"}

（4）声明public void after()方法，
{: id="20210310174140-ahuileg"}

​	①打印“该测试方法结束后list中的数据如下："
{: id="20210310174140-r2jshck"}

​	②调用list的select方法，获取Selector的对象，并调用hasNext()和next()遍历容器中所有的对象
{: id="20210310174140-5wco8nj"}

​	③并在after()方法上标记JUnit4的@After的注解
{: id="20210310174140-sb5vvm9"}

（5）声明public void testAdd()方法，
{: id="20210310174140-40o18ks"}

​	①在方法中，打印“现在测试的是testAdd()方法"
{: id="20210310174140-jcpnnva"}

​	②在方法中，再次调用list的add()方法往list容器对象中添加1个对象
{: id="20210310174140-ys29u2p"}

​	③并在testAdd()方法上标记JUnit4的@Test的注解
{: id="20210310174140-g2jeiun"}

（6）声明public void testRemove()方法，
{: id="20210310174140-01z85oj"}

​	①在方法中，打印“现在测试的是testRemove()方法"
{: id="20210310174140-ove8ts2"}

​	②调用list的remove方法，删除[1]的对象
{: id="20210310174140-owegmkd"}

​	③并在testRemove()方法上标记JUnit4的@Test的注解
{: id="20210310174140-6rm5yzj"}

（7）声明public void testSet()方法
{: id="20210310174140-k422ddn"}

​	①在方法中，打印“现在测试的是testSet()方法"
{: id="20210310174140-zf5u9il"}

​	②调用list的set方法，替换[1]的对象
{: id="20210310174140-ey2g2wn"}

​	③并在testSet()方法上标记JUnit4的@Test的注解
{: id="20210310174140-tc78pvh"}

（8）声明public void testGet()方法
{: id="20210310174140-25mfubi"}

​	①在方法中，打印“现在测试的是testGet()方法"
{: id="20210310174140-d4opuna"}

​	②调用list的get方法，获取[1]的对象，并打印
{: id="20210310174140-ziwov50"}

​	③并在testGet()方法上标记JUni
{: id="20210310174140-zuzur2v"}


{: id="20210310174140-pulc7kx" type="doc"}
