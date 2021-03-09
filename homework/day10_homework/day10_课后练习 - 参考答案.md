# day10_课后练习
{: id="20210309203838-if7h5d4"}

# 接口编程代码题
{: id="20210309203838-14b5q4g"}

## 第1题
{: id="20210309203838-0apvyu4"}

* {: id="20210309203838-kya5bpn"}语法点：接口
  {: id="20210309203838-dqwt6da"}
* {: id="20210309203838-8vgrxrj"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-j1vy8wx"}
{: id="20210309203838-190xyg6"}

![1559196806364](imgs/1559196806364.png)
{: id="20210309203838-jdhilol"}

* {: id="20210309203838-v8b4ee4"}编写步骤：
  {: id="20210309203838-263u23j"}
{: id="20210309203838-j02emi6"}

1. {: id="20210309203838-2ji7fgh"}定义接口A，普通类B实现接口A
   {: id="20210309203838-9zgyb9k"}
2. {: id="20210309203838-r4fcvh1"}A接口中，定义抽象方法showA。
   {: id="20210309203838-5iib0ps"}
3. {: id="20210309203838-6pza5cv"}A接口中，定义默认方法showB。
   {: id="20210309203838-xs4bzuh"}
4. {: id="20210309203838-rdqnksc"}B类中，重写showA方法
   {: id="20210309203838-imm5rq1"}
5. {: id="20210309203838-mgr1a4v"}测试类中，创建B类对象，调用showA方法，showB方法。
   {: id="20210309203838-71jqrmf"}
{: id="20210309203838-3hzx53g"}

```java
package com.atguigu.test01;

public class Test01 {
	public static void main(String[] args) {
		B b = new B();
		b.showA();
		b.showB();
	}
}
interface A{
	void showA();
	default void showB(){
		System.out.println("BBB");
	}
}
class B implements A{

	@Override
	public void showA() {
		System.out.println("AAA");
	}
	
}
```
{: id="20210309203838-uz5yj9t"}

## 第2题
{: id="20210309203838-f93bsro"}

* {: id="20210309203838-bx7jx0d"}语法点：接口，多态
  {: id="20210309203838-txozs0e"}
* {: id="20210309203838-v4r1hi2"}按步骤编写代码，效果如图所示：
  {: id="20210309203838-j2h87xb"}
{: id="20210309203838-g30rubt"}

![1559197812068](imgs/1559197696317.png)
{: id="20210309203838-15q362p"}

* {: id="20210309203838-ahos2cn"}编写步骤
  {: id="20210309203838-1damaua"}
{: id="20210309203838-lfguhv8"}

1. {: id="20210309203838-b7yevc7"}定义接口Universe，提供抽象方法doAnything。
   {: id="20210309203838-eidf2xf"}
2. {: id="20210309203838-2vatc88"}定义普通类Star，提供成员发光shine方法，打印“star:星星一闪一闪亮晶晶"
   {: id="20210309203838-g9iwd8z"}
3. {: id="20210309203838-0k6mkz7"}定义普通类Sun，
   {: id="20210309203838-qbnw02k"}
   继承Star类，重写shine方法，打印"sun:光照八分钟，到达地球"
   {: id="20210309203838-o3cxytq"}
   实现Universe接口，实现doAnything，打印"sun:太阳吸引着9大行星旋转"
   {: id="20210309203838-hctmq4z"}
4. {: id="20210309203838-4biqm3l"}测试类中，创建Star对象，调用shine方法
   {: id="20210309203838-2awgewh"}
5. {: id="20210309203838-emk5xer"}测试类中，多态的方式创建Sun对象，调用doAnything方法，向下转型，调用shine方法。
   {: id="20210309203838-1tfczgl"}
{: id="20210309203838-xjxz2d8"}

```java
package com.atguigu.test02;

public class Test02 {
	public static void main(String[] args) {
		Star s = new Star();
		s.shine();
		
		System.out.println("======================");
		Universe u = new Sun();
		u.doAnything();
		Star sun = (Star) u;
		sun.shine();
	}
}
interface Universe{
	void doAnything();
}
class Star{
	public void shine(){
		System.out.println("star:星星一闪一闪亮晶晶");
	}
}
class Sun extends Star implements Universe{
	@Override
	public void shine(){
		System.out.println("sun:光照8分钟到达地球");
	}
	@Override
	public void doAnything() {
		System.out.println("sun:太阳吸引着9大行星旋转");
	}
	
}
```
{: id="20210309203838-uadqmmd"}

## 第3题
{: id="20210309203838-rwnf6dn"}

* {: id="20210309203838-jsg4j8b"}模拟玩家选择角色。
  {: id="20210309203838-t7gek93"}
* {: id="20210309203838-ilrr6tx"}定义接口FightAble：
  {: id="20210309203838-dpgicce"}
  * {: id="20210309203838-ni3a6to"}抽象方法：specialFight。
    {: id="20210309203838-i8atao1"}
  * {: id="20210309203838-szjxfr7"}默认方法：commonFight,方法中打印"普通打击"。
    {: id="20210309203838-b74t48m"}
  {: id="20210309203838-ntnonbo"}
* {: id="20210309203838-1psn3ug"}定义战士类：
  {: id="20210309203838-r2sfji9"}
  * {: id="20210309203838-yekdkkz"}实现FightAble接口,重写方法中打印"武器攻击"。
    {: id="20210309203838-2rdgmuf"}
  {: id="20210309203838-rnmffbq"}
* {: id="20210309203838-32i4pxv"}定义法师类Mage：
  {: id="20210309203838-ms61aqv"}
  * {: id="20210309203838-gjvbivi"}实现FightAble接口,重写方法中打印"法术攻击"。
    {: id="20210309203838-6imkqlg"}
  {: id="20210309203838-a5utd4l"}
* {: id="20210309203838-mxztqcl"}定义玩家类Player：
  {: id="20210309203838-68qw2wc"}
  * {: id="20210309203838-15wqlgr"}静态方法：FightAble select(String str)，根据指令选择角色。
    {: id="20210309203838-lkdepds"}
    * {: id="20210309203838-akucgy6"}法力角色，选择法师。
      {: id="20210309203838-yjdgm9m"}
    * {: id="20210309203838-3jqpruh"}武力角色，选择战士。
      {: id="20210309203838-tvp0otk"}
    {: id="20210309203838-brfk6f3"}
  {: id="20210309203838-1hedp9l"}
* {: id="20210309203838-tbimgzy"}代码实现，效果如图所示：
  {: id="20210309203838-ht9v583"}
{: id="20210309203838-vd8ec23"}

![1559199324400](imgs/1559199324400.png)
{: id="20210309203838-kjp2h0a"}

```java
package com.atguigu.test03;

import java.util.Scanner;

public class Test3 {
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		System.out.print("选择：");
		String role1 = input.next();
		
		FightAble f1 = Player.select(role1);
		f1.specialFight();
		f1.commonFight();
		
		System.out.println("====================");
		
		System.out.print("选择：");
		String role2 = input.next();
		
		FightAble f2 = Player.select(role2);
		f2.specialFight();
		f2.commonFight();
		
		input.close();
	}
}
interface FightAble{
	void specialFight();
	default void commonFight(){
		System.out.println("普通攻击");
	}
}
class Soldier implements FightAble{

	@Override
	public void specialFight() {
		System.out.println("武器攻击");
	}
	
}
class Mage implements FightAble{

	@Override
	public void specialFight() {
		System.out.println("法术攻击");
	}
	
}
class Player{

	public static FightAble select(String str){
		if("法力角色".equals(str)){
			return new Mage();
		}else if("武力角色".equals(str)){
			return new Soldier();
		}
		return null;
	}
	
}
```
{: id="20210309203838-dm4tdmr"}

## 第4题
{: id="20210309203838-ouaybhf"}

* {: id="20210309203838-8aj3f8j"}模拟工人挑苹果。
  {: id="20210309203838-vh10vpa"}
* {: id="20210309203838-lmm0k5b"}定义苹果类：
  {: id="20210309203838-i7uy2b6"}
  * {: id="20210309203838-emuuyd0"}属性：大小，颜色。
    {: id="20210309203838-b8053vv"}
  * {: id="20210309203838-ogvrd6k"}提供基本的构造方法和get方法，set方法
    {: id="20210309203838-7m7lvp4"}
  {: id="20210309203838-c9rj8tw"}
* {: id="20210309203838-pe4cjcr"}定义接口CompareAble：
  {: id="20210309203838-t2njf4l"}
  * {: id="20210309203838-43fuvxv"}定义默认方法compare，挑选较大苹果。
    {: id="20210309203838-6z68jrb"}
  {: id="20210309203838-8kubs9k"}
* {: id="20210309203838-n0f1107"}定义接口实现类CompareBig。
  {: id="20210309203838-ccrt70j"}
* {: id="20210309203838-3qmj67f"}定义接口实现类CompareColor。挑选红色苹果。
  {: id="20210309203838-3437smd"}
* {: id="20210309203838-j54v7mj"}定义工人类：
  {: id="20210309203838-jssgh4i"}
  * {: id="20210309203838-tmopf92"}成员方法：挑选苹果public void pickApple(CompareAble c,Apple a1,Apple a2)。
    {: id="20210309203838-j9l8ph6"}
  {: id="20210309203838-hy81iwk"}
* {: id="20210309203838-pm1q22r"}测试类：
  {: id="20210309203838-n8tn97e"}
  * {: id="20210309203838-1fyprm1"}创建Worker对象。
    {: id="20210309203838-r4mxpg2"}
  * {: id="20210309203838-zmo7b3a"}创建两个Apple对象，一个Apple（5，"青色"）,一个Apple（3，"红色"）
    {: id="20210309203838-ud69oz6"}
  {: id="20210309203838-96fb135"}
* {: id="20210309203838-npqw373"}代码实现，效果如图所示：
  {: id="20210309203838-w7wbzk2"}
{: id="20210309203838-3p14jwh"}

![1559207642477](imgs/1559207642477.png)
{: id="20210309203838-l4ver18"}

```java
package com.atguigu.test04;

public class Test04 {
	public static void main(String[] args) {
		Worker w = new Worker();
		Apple a1 = new Apple(5, "青色");
		Apple a2 = new Apple(3, "红色");
		
		w.pickApple(new CompareBig(), a1, a2);
		w.pickApple(new CompareColor(), a1, a2);
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
class CompareBig implements CompareAble{
	
}
class CompareColor  implements CompareAble{

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
	
}
class Worker{
	public void pickApple(CompareAble c,Apple a1,Apple a2){
		c.compare(a1, a2);
	}
}
```
{: id="20210309203838-vyq602s"}

## 第5题
{: id="20210309203838-sjnutiq"}

* {: id="20210309203838-4jvmdet"}模拟接待员接待用户，根据用户id，给用户分组。
  {: id="20210309203838-9eyg01i"}
* {: id="20210309203838-ojbmfva"}定义用户类：
  {: id="20210309203838-nvnrbyu"}
  * {: id="20210309203838-ltm2all"}属性：用户类型，用户id
    {: id="20210309203838-fuclj99"}
  * {: id="20210309203838-d3oiqss"}提供基本的构造方法和get方法，set方法
    {: id="20210309203838-ya6mwwp"}
  {: id="20210309203838-nawi2re"}
* {: id="20210309203838-c3p1u6p"}定义接口Filter：
  {: id="20210309203838-i1bst6i"}
  * {: id="20210309203838-5lagoo2"}提供抽象方法filterUser（User u）
    {: id="20210309203838-twwe8hz"}
  {: id="20210309203838-6tbd3uf"}
* {: id="20210309203838-xyvdcbq"}定义实现类V1Filter，实现抽象方法，将用户设置为v1
  {: id="20210309203838-i4tdclx"}
* {: id="20210309203838-68nvft2"}定义实现类V2Filter，实现抽象方法，将用户设置为v2
  {: id="20210309203838-9fr41mx"}
* {: id="20210309203838-toyfl2c"}定义实现类AFilter，实现抽象方法，将用户设置为A
  {: id="20210309203838-gutb80m"}
* {: id="20210309203838-1d6cz1x"}定义接待员类Receptionist：
  {: id="20210309203838-8gt1j1k"}
  * {: id="20210309203838-ler8ill"}属性：接口Filter
    {: id="20210309203838-73l5h92"}
  * {: id="20210309203838-vzf8754"}提供基本的构造方法和get方法，set方法
    {: id="20210309203838-eqivgvv"}
  * {: id="20210309203838-k296wfp"}成员方法：接待用户方法，设置用户类型。
    {: id="20210309203838-vi2d366"}
  {: id="20210309203838-8wdh1sz"}
* {: id="20210309203838-fwaevqb"}测试类：
  {: id="20210309203838-b9ecwoe"}
  * {: id="20210309203838-kt1986p"}初始化15个User对象，id为1-15。
    {: id="20210309203838-8vp78rw"}
  * {: id="20210309203838-yn1fwbn"}创建三个接待员对象。
    {: id="20210309203838-ix8jjo5"}
    * {: id="20210309203838-q2t1tst"}第一个接待员，设置接待规则，将1-5号用户类型设置为v1。
      {: id="20210309203838-h3cl2xg"}
    * {: id="20210309203838-xotur56"}第二个接待员，设置接待规则，将6-10号用户类型设置为v2。
      {: id="20210309203838-6y4fm2d"}
    * {: id="20210309203838-7cw9pro"}第三个接待员，设置接待规则，将11-15号用户类型设置为A。
      {: id="20210309203838-xgb4xuq"}
    {: id="20210309203838-kp602jd"}
  * {: id="20210309203838-1y347bc"}遍历数组，给用户分区。
    {: id="20210309203838-h4gnjcb"}
  {: id="20210309203838-p1aulih"}
* {: id="20210309203838-scmosat"}代码实现，效果如图所示：
  {: id="20210309203838-mdar27d"}
{: id="20210309203838-wz7yomw"}

![1559215024155](imgs/1559215024155.png)
{: id="20210309203838-92ops51"}

```java
package com.atguigu.test05;

public class Test05 {
	public static void main(String[] args) {
		User[] all = new User[15];
		for (int i = 0; i < all.length; i++) {
			all[i] = new User(null,i+1);
		}
		V1Filter v1F = new V1Filter();
		V2Filter v2F = new V2Filter();
		AFilter aF = new AFilter();
		Receptionist r1 = new Receptionist(v1F);
		for (int i = 0; i < 5; i++) {
			r1.recept(all[i]);
		}
		Receptionist r2 = new Receptionist(v2F);
		for (int i = 5; i < 10; i++) {
			r2.recept(all[i]);
		}
		Receptionist r3 = new Receptionist(aF);
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

class V1Filter implements Filter{

	@Override
	public void filterUser(User u) {
		u.setType("v1");
	}
	
}
class V2Filter implements Filter{

	@Override
	public void filterUser(User u) {
		u.setType("v2");
	}
	
}
class AFilter implements Filter{

	@Override
	public void filterUser(User u) {
		u.setType("A");
	}
	
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
{: id="20210309203838-xibn2ub"}

# 包装类代码题
{: id="20210309203838-4wl4kng"}

## 第1题
{: id="20210309203838-gixgk9r"}

```java
	public static void main(String[] args) {
		Integer i1 = 128;
		Integer i2 = 128;
		int i3 = 128;
		int i4 = 128;
		System.out.println(i1 == i2);
		System.out.println(i3 == i4);
		System.out.println(i1 == i3);
	}
```
{: id="20210309203838-us098yx"}

```java
	public static void main(String[] args) {
		Integer i1 = 128;
		Integer i2 = 128;
		int i3 = 128;
		int i4 = 128;
		System.out.println(i1 == i2);//false，比较地址，128超过Integer缓存对象
		System.out.println(i3 == i4);//true，比较数据值
		System.out.println(i1 == i3);//true，i1自动拆箱按照基本数据类型比较
        //包装类对象与基本数据类型进行比较时，就会把包装类对象自动拆箱，按照基本数据类型的规则进行比较
	}
```
{: id="20210309203838-ajwwi6v"}

## 第2题
{: id="20210309203838-etvh4lq"}

```java
	public static void main(String[] args) {
		double a = 2.0;
		double b = 2.0;
		Double c = 2.0;
		Double d = 2.0;
		System.out.println(a == b);
		System.out.println(c == d);
		System.out.println(a == d);
	}
```
{: id="20210309203838-xyydalm"}

```java
	public static void main(String[] args) {
		double a = 2.0;
		double b = 2.0;
		Double c = 2.0;
		Double d = 2.0;
		System.out.println(a == b);//true，基本数据类型比较数据值
		System.out.println(c == d);//false，对象比较地址值，Double没有缓存对象
		System.out.println(a == d);//true,d自动拆箱，按照基本数据类型比较
	}
```
{: id="20210309203838-ktzq4h4"}

# 枚举编程题
{: id="20210309203838-erln2fh"}

## 第1题
{: id="20210309203838-x2f5xau"}

案例：
{: id="20210309203838-cv35iqq"}

​	1、声明颜色枚举类：
{: id="20210309203838-zmskwuw"}

​		7个常量对象：赤、橙、黄、绿、青、蓝、紫。
{: id="20210309203838-uh33c1j"}

​	2、在测试类中，使用枚举类，获取绿色对象，并打印对象。
{: id="20210309203838-6bz4ewx"}

```java
package com.atguigu.test01;

public class Test01 {
	public static void main(String[] args) {
		Color c = Color.GREEN;
		System.out.println(c);
	}
}
enum Color{
	RED,ORANGE,YELLOW,GREEN,CYAN,BLUE,PURPLE
}
```
{: id="20210309203838-hws2wsx"}

## 第2题
{: id="20210309203838-eyvtc97"}

案例：
{: id="20210309203838-5vwmpgk"}

​	1、声明月份枚举类Month：
{: id="20210309203838-5peue02"}

​	（1）创建：1-12月常量对象
{: id="20210309203838-0n4ei3u"}

​	（2）声明两个属性：value（月份值，例如：JANUARY的value为1），
{: id="20210309203838-9fx9fic"}

​						description（描述，例如：JANUARY的description为1月份是一年的开始）。
{: id="20210309203838-dnos4j6"}

​	（3）声明一个有参构造，创建12个对象
{: id="20210309203838-8lhcg4r"}

​	（4） 声明一个方法：public static Month getByValue(int value)
{: id="20210309203838-8fzc5sj"}

​	（5）重写toString()：返回对象信息，例如：1->JANUARY->1月份是一年的开始。
{: id="20210309203838-s36lot3"}

​	2、在测试类中，从键盘输入1个1-12的月份值，获取对应的月份对象，并打印对象
{: id="20210309203838-4odensu"}

```java
package com.atguigu.test02;

import java.util.Scanner;

public class Test02 {
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		System.out.print("请输入月份值（1-12）：");
		int m = input.nextInt();
		
		Month month = Month.getByValue(m);
		System.out.println(month);
		
		input.close();
	}
}
enum Month{
	JANUARY(1,"1月份是一年的开始"),
	FEBRUARY(2,"2月份是一年中最短的一个月"),
	MARCH(3,"3月春暖花开"),
	APRIL(4,"4月阳光明媚"),
	MAY(5,"5月清凉初夏"),
	JUNE(6,"6月骄阳似火"),
	JULY(7,"7月下半年的第一个月"),
	AUGUST(8,"8月人已晒干"),
	SEPTEMBER(9,"秋风送爽"),
	OCTOBER(10,"10月全国同欢"),
	NOVEMBER(11,"11月寻找秋裤"),
	DECMEBER(12,"12月冰天雪地");
	
	private int value;
	private String description;
	
	private Month(int value,String description){
		this.value = value;
		this.description = description;
	}
	
	public static Month getByValue(int value){
		return Month.values()[value-1];
	}
	
	public String toString(){
		return value + "->" + name() + "->" + description;
	}
}
```
{: id="20210309203838-735ztmb"}

## 第3题
{: id="20210309203838-rge7m7a"}

案例：
{: id="20210309203838-c5uf6xe"}

​	1、声明可支付接口Payable：
{: id="20210309203838-gtusofo"}

​		包含抽象方法：void pay();
{: id="20210309203838-8l5xjkf"}

​	2、声明支付枚举类Payment：
{: id="20210309203838-ul2cigm"}

​	（1）创建常量对象：支付宝（ALIPAY），微信（WECHAT），信用卡（CREDIT_CARD），储蓄卡（DEPOSIT_CARD）
{: id="20210309203838-m40iv76"}

​	（2）枚举类Payment实现接口Payable
{: id="20210309203838-zwk0crw"}

​	①支付宝/微信：对接口的实现是打印“扫码支付”
{: id="20210309203838-w58zb7q"}

​	②信用卡/储蓄卡：对接口的实现是打印“输入卡号支付”
{: id="20210309203838-16s5nl5"}

​	3、在测试类中，获取所有支付对象，并调用它们的pay()
{: id="20210309203838-70ugf9a"}

```java
package com.atguigu.test03;

public class Test03 {
	public static void main(String[] args) {
		Payment[] values = Payment.values();
		for (int i = 0; i < values.length; i++) {
			values[i].pay();
		}
	}
}
interface Payable{
	void pay();
}
enum Payment implements Payable{
	ALIPAY{
		@Override
		public void pay() {
			System.out.println("扫码支付");
		}
	},WECHAT{
		@Override
		public void pay() {
			System.out.println("扫码支付");
		}
	},CREDIT_CARD,DEPOSIT_CARD;

	@Override
	public void pay() {
		System.out.println("输入卡号支付");
	}
}

```
{: id="20210309203838-y9xbp66"}


{: id="20210309203838-17rta9x" type="doc"}
