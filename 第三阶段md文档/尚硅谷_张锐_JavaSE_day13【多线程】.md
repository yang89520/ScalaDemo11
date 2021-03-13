# JavaSE_day13【多线程】
{: id="20210313082711-rduzz7i"}

## 主要内容
{: id="20210313082711-k2qu105"}

- {: id="20210313082711-fn7s5ni"}多线程
  {: id="20210313082711-154w0yq"}
{: id="20210313082711-m6sif4n"}

## 学习目标
{: id="20210313082711-xsq0tqa"}

- {: id="20210313082711-ik0lyeh"}[ ] 说出进程的概念
  {: id="20210313082711-uzkk0zl"}
- {: id="20210313082711-fhp8b8t"}[ ] 说出线程的概念
  {: id="20210313082711-13dx7t7"}
- {: id="20210313082711-4c2kpri"}[ ] 能够理解并发与并行的区别
  {: id="20210313082711-ibdgj6r"}
- {: id="20210313082711-03iw17j"}[ ] 能够开启新线程
  {: id="20210313082711-z34d49x"}
- {: id="20210313082711-ifstnsi"}[ ] 能够描述Java中多线程运行原理
  {: id="20210313082711-b3jp9ro"}
- {: id="20210313082711-xeva9zn"}[ ] 能够使用继承类的方式创建多线程
  {: id="20210313082711-fs25e9s"}
- {: id="20210313082711-suvk9oo"}[ ] 能够使用实现接口的方式创建多线程
  {: id="20210313082711-zmgzjbq"}
- {: id="20210313082711-4x2qpfv"}[ ] 能够说出实现接口方式的好处
  {: id="20210313082711-3ocye18"}
- {: id="20210313082711-enpeey2"}[ ] 能够解释安全问题的出现的原因
  {: id="20210313082711-a3kdj8v"}
- {: id="20210313082711-o05hh7d"}[ ] 能够使用同步代码块解决线程安全问题
  {: id="20210313082711-wxuxjmz"}
- {: id="20210313082711-omjnbki"}[ ] 能够使用同步方法解决线程安全问题
  {: id="20210313082711-q93zw59"}
- {: id="20210313082711-9kxdafc"}[ ] 能够说出线程6个状态的名称
  {: id="20210313082711-ik1omv8"}
- {: id="20210313082711-4noargn"}[ ] 能够理解线程通信概念
  {: id="20210313082711-pw2u1vr"}
- {: id="20210313082711-faw2fgs"}[ ] 能够理解等待唤醒机制
  {: id="20210313082711-3frn36b"}
- {: id="20210313082711-qgx7h64"}[ ] 能够说出线程的生命周期
  {: id="20210313082711-fnttvc0"}
{: id="20210313082711-r9izqbe"}

# 第九章 多线程
{: id="20210313082711-23087vf"}

我们在之前，学习的程序在没有跳转语句的前提下，都是由上至下依次执行，那现在想要设计一个程序，边打游戏边听歌，怎么设计？
{: id="20210313082711-gzuzdjg"}

要解决上述问题,咱们得使用多进程或者多线程来解决.
{: id="20210313082711-agkvaqg"}

## 9.1 相关概念
{: id="20210313082711-uz84vot"}

### 9.1.1 并发与并行（了解）
{: id="20210313082711-xyj6c07"}

* {: id="20210313082711-4u33osu"}**并行**（parallel）：指两个或多个事件在**同一时刻**发生（同时发生）。指在同一时刻，有多条指令在多个处理器上同时执行。
  {: id="20210313082711-dncj0oi"}
* {: id="20210313082711-c87u48m"}**并发**（concurrency）：指两个或多个事件在**同一个时间段内**发生。指在同一个时刻只能有一条指令执行，但**多个进程**{: style="background-color: rgb(255, 253, 56);"}的指令被快速**轮换执行**{: style="background-color: rgb(255, 253, 56);"}，使得在宏观上具有多个进程同时执行的效果。
  {: id="20210313082711-fmvl53v"}
{: id="20210313082711-c25k4hg"}

![](imgs13\并行与并发.bmp)
{: id="20210313082711-t1rq3nz"}

在操作系统中，安装了多个程序，并发指的是在一段时间内宏观上有多个程序同时运行，这在单 CPU 系统中，每一时刻只能有一个程序执行，即微观上这些程序是分时的交替运行，只不过是给人的感觉是同时运行，那是因为分时交替运行的时间是非常短的。
{: id="20210313082711-tznz3eq"}

而在多个 CPU 系统中，则这些可以并发执行的程序便可以分配到多个处理器上（CPU），实现多任务并行执行，即利用每个处理器来处理一个可以并发执行的程序，这样多个程序便可以同时执行。目前电脑市场上说的多核 CPU，便是多核处理器，核越多，**并行**处理的程序越多，能大大的提高电脑运行的效率。
{: id="20210313082711-84bpy5o"}

> 注意：**单核**处理器的计算机肯定是**不能并行**的处理多个任务的，只能是多个任务在单个CPU上并发运行。同理，线程也是一样的，从宏观角度上理解线程是并行运行的，但是从微观角度上分析却是串行运行的，即一个线程一个线程的去运行，当系统只有一个CPU时，线程会以某种顺序执行多个线程，我们把这种情况称之为**线程调度**{: style="background-color: rgb(255, 253, 56);"}。
> {: id="20210313082711-b0dyvqx"}
{: id="20210313082711-izghkpz"}

### 9.1.2 线程与进程
{: id="20210313082711-s0zvftl"}

* {: id="20210313082711-v4wobm1"}**程序**：为了完成某个任务和功能，选择一种编程语言编写的一组指令的集合。
  {: id="20210313082711-dl18qhe"}
* {: id="20210313082711-sktam4j"}**软件**：**1个或多个**应用程序+相关的素材和资源文件等构成一个软件系统。
  {: id="20210313082711-cys7rie"}
* {: id="20210313082711-u1wdsww"}**进程**：是指一个内存中运行的应用程序，每个进程都有一个**独立的内存空间**{: style="background-color: rgb(255, 253, 56);"}，进程也是程序的一次执行过程，是**系统运行程序的基本单位**{: style="background-color: rgb(255, 253, 56);"}；系统运行一个程序即是一个进程从创建、运行到消亡的过程。
  {: id="20210313082711-4r08mup"}
* {: id="20210313082711-ywgu611"}**线程**：线程是进程中的一个执行单元，负责当前进程中程序的执行，**一个进程中至少有一个线程**{: style="background-color: rgb(255, 253, 56);"}。一个进程中是可以有多个线程的，这个应用程序也可以称之为多线程程序。
  {: id="20210313082711-ivl0t0t"}

  简而言之：一个软件中至少有一个应用程序，应用程序的一次运行就是一个进程，一个进程中至少有一个线程。
  {: id="20210313082711-1bies7u"}
* {: id="20210313082711-pxqdfsx"}面试题：进程是操作系统调度和分配资源的最小单位，**线程是CPU调度的最小单位**{: style="background-color: rgb(255, 253, 56);"}。不同的进程之间是不共享内存的。**进程之间的数据交换和通信的成本是很高**{: style="background-color: rgb(255, 253, 56);"}。不同的线程是共享同一个进程的内存的。当然不同的线程也有自己独立的内存空间。对于方法区，堆中中的同一个对象的内存，线程之间是可以共享的，但是栈的局部变量永远是独立的。
  {: id="20210313082711-x5g62gw"}
{: id="20210313082711-0yct3rd"}

例如：
{: id="20210313082711-km4gkni"}

#### 一个软件中包含多个进程
{: id="20210313082711-xt1rdqe"}

![1563267154695](imgs13/1563267154695.png)
{: id="20210313082711-90axbrm"}

#### 每个应用程序的运行都是一个进程
{: id="20210313082711-oyfq0b4"}

我们可以再电脑底部任务栏，右键----->打开任务管理器,可以查看当前任务的进程：
{: id="20210313082711-zkuro7m"}

![](imgs13\进程概念.png)
{: id="20210313082711-cybxiq5"}

#### 一个应用程序的多次运行，就是多个进程
{: id="20210313082711-n1bitew"}

![1563267431480](imgs13/1563267431480.png)
{: id="20210313082711-9ojl1iv"}

#### 一个进程中包含多个线程
{: id="20210313082711-j8ugx6v"}

![1563270525077](imgs13/1563270525077.png)
{: id="20210313082711-g0ue59x"}

### 9.1.3 线程调度
{: id="20210313082711-uup973q"}

- {: id="20210313082711-3y7r95s"}**分时调度**{: style="background-color: rgb(255, 253, 56);"}
  {: id="20210313082711-rabw16l"}

  所有线程轮流使用 CPU 的使用权，平均分配每个线程占用 CPU 的时间。
  {: id="20210313082711-307aovr"}
- {: id="20210313082711-2eapy3f"}**抢占式调度**{: style="background-color: rgb(255, 253, 56);"}
  {: id="20210313082711-88ndzf1"}

  优先让优先级高的线程使用 CPU，如果线程的优先级相同，那么会随机选择一个(线程随机性)，Java使用的为抢占式调度。
  {: id="20210313082711-za0bpqb"}

  - {: id="20210313082711-ns8u4h5"}抢占式调度详解
    {: id="20210313082711-sdbpkls"}
  {: id="20210313082711-cgwaujy"}

  大部分操作系统都支持多进程并发运行，现在的操作系统几乎都支持同时运行多个程序。比如：现在我们上课一边使用编辑器，一边使用录屏软件，同时还开着画图板，dos窗口等软件。此时，这些程序是在同时运行，”感觉这些软件好像在同一时刻运行着“。
  {: id="20210313082711-44hvh9n"}

  实际上，CPU(中央处理器)使用抢占式调度模式在多个线程间进行着高速的切换。对于CPU的一个核而言，某个时刻，只能执行一个线程，而 CPU的在多个线程间切换速度相对我们的感觉要快，看上去就是在同一时刻运行。
  其实，**多线程程序并不能提高程序的运行速度，但能够提高程序运行效率，让CPU的使用率更高。**{: style="background-color: rgb(255, 253, 56);"}
  {: id="20210313082711-vqfczaw"}

  ![抢占式调度](imgs13/抢占式调度.bmp)
  {: id="20210313082711-ja1u5pk"}
{: id="20210313082711-hugllka"}

## 9.2 另行创建和启动线程
{: id="20210313082711-e1umrqt"}

一个多线程程序的状态：
{: id="20210313082711-phrxvma"}

![](imgs13\Snipaste_2020-07-28_19-19-06.png)
{: id="20210313082711-iafpw9k"}

当运行Java程序时，其实已经有一个线程了，那就是main线程。
{: id="20210313082711-yb9pyov"}

![1563281796505](imgs13/1563281796505.png)
{: id="20210313082711-214fscn"}

那么如何创建和启动main线程以外的线程呢？
{: id="20210313082711-hmk6zue"}

### 9.2.1 继承Thread类
{: id="20210313082711-20u2iku"}

Java使用`java.lang.Thread`类代表**线程**，所有的线程对象都必须是Thread类或其子类的实例。每个线程的作用是完成一定的任务，实际上就是执行一段程序流即一段顺序执行的代码。Java使用线程执行体来代表这段程序流。Java中通过继承Thread类来**创建**并**启动多线程**的步骤如下：
{: id="20210313082711-0j4yckr"}

1. {: id="20210313082711-w6nlo6g"}定义Thread类的子类，并重写该类的run()方法，该run()方法的方法体就代表了线程需要完成的任务,因此把run()方法称为线程执行体。
   {: id="20210313082711-cjryswy"}
2. {: id="20210313082711-alqnc3y"}创建Thread子类的实例，即创建了线程对象
   {: id="20210313082711-wez9txs"}
3. {: id="20210313082711-me3cmkc"}调用线程对象的start()方法来启动该线程
   {: id="20210313082711-11b7lyt"}
{: id="20210313082711-aeu9k34"}

代码如下：
{: id="20210313082711-gzsttnw"}

测试类：
{: id="20210313082711-9wizgnu"}

~~~java
public class Demo01 {
	public static void main(String[] args) {
		//创建自定义线程对象
		MyThread mt = new MyThread("新的线程！");
		//开启新线程
		mt.start();
		//在主方法中执行for循环
		for (int i = 0; i < 10; i++) {
			System.out.println("main线程！"+i);
		}
	}
}
~~~
{: id="20210313082711-sunl0w1"}

自定义线程类：
{: id="20210313082711-urqs55m"}

~~~java
public class MyThread extends Thread {
	//定义指定线程名称的构造方法
	public MyThread(String name) {
		//调用父类的String参数的构造方法，指定线程的名称
		super(name);
	}
	/**
	 * 重写run方法，完成该线程执行的逻辑
	 */
	@Override
	public void run() {
		for (int i = 0; i < 10; i++) {
			System.out.println(getName()+"：正在执行！"+i);
		}
	}
}
~~~
{: id="20210313082711-ah4jeth"}

### 9.2.2 实现Runnable接口
{: id="20210313082711-vq33cul"}

Java有单继承的限制，当我们无法继承Thread类时，那么该如何做呢？在核心类库中提供了Runnable接口，我们可以实现Runnable接口，重写run()方法，然后再通过Thread类的对象代理启动和执行我们的线程体run()方法
{: id="20210313082711-vk82cci"}

步骤如下：
{: id="20210313082711-8uno72k"}

1. {: id="20210313082711-12fbygx"}定义Runnable接口的实现类，并重写该接口的run()方法，该run()方法的方法体同样是该线程的线程执行体。
   {: id="20210313082711-bj615o1"}
2. {: id="20210313082711-tpdr2hr"}创建Runnable实现类的实例，并以此实例作为Thread的target来创建Thread对象，该Thread对象才是真正
   的线程对象。
   {: id="20210313082711-d9n9skv"}
3. {: id="20210313082711-k5nj8ud"}调用线程对象的start()方法来启动线程。
   代码如下：
   {: id="20210313082711-2hcpi78"}
{: id="20210313082711-hsz6h2c"}

```java
  public class MyRunnable implements Runnable{
  	@Override  
      public void run() {
          for (int i = 0; i < 20; i++) {
          	System.out.println(Thread.currentThread().getName()+" "+i);         
  		}       
  	}    
  }
```
{: id="20210313082711-oq0w2p4"}

```java
  public class Demo {
      public static void main(String[] args) {
          //创建自定义类对象  线程任务对象
          MyRunnable mr = new MyRunnable();
          //创建线程对象
          Thread t = new Thread(mr, "小强");
          t.start();
          for (int i = 0; i < 20; i++) {
              System.out.println("旺财 " + i);
          }
      }
  }
```
{: id="20210313082711-q9accur"}

通过实现Runnable接口，使得该类有了多线程类的特征。run()方法是多线程程序的一个执行目标。所有的多线程
代码都在run方法里面。Thread类实际上也是实现了Runnable接口的类。
{: id="20210313082711-2gzrbx6"}

在启动的多线程的时候，需要先通过Thread类的构造方法Thread(Runnable target) 构造出对象，然后调用Thread对象的start()方法来运行多线程代码。
{: id="20210313082711-amli1wg"}

实际上所有的多线程代码都是通过运行Thread的start()方法来运行的。因此，不管是继承Thread类还是实现
Runnable接口来实现多线程，最终还是通过Thread的对象的API来控制线程的，熟悉Thread类的API是进行多线程编程的基础。
{: id="20210313082711-blo68kq"}

tips:Runnable对象仅仅作为Thread对象的target，Runnable实现类里包含的run()方法仅作为线程执行体。
而实际的线程对象依然是Thread实例，只是该Thread线程负责执行其target的run()方法。
{: id="20210313082711-qkw3q4f"}

### 9.2.3 使用匿名内部类对象来实现线程的创建和启动
{: id="20210313082711-h12lsdf"}

```java
new Thread("新的线程！"){
	@Override
	public void run() {
		for (int i = 0; i < 10; i++) {
			System.out.println(getName()+"：正在执行！"+i);
		}
	}
}.start();
```
{: id="20210313082711-m34tm4s"}

```java
		new Thread(new Runnable(){
			@Override
			public void run() {
				for (int i = 0; i < 10; i++) {
					System.out.println(Thread.currentThread().getName()+"：" + i);
				}
			}
		}).start();
```
{: id="20210313082711-ced9glv"}

### 9.2.4 练习：
{: id="20210313082711-tebrc74"}

创建一个子线程，在线程中输出1-100之间的偶数，另外一个子线程输出1-100之间的奇数。
{: id="20210313082711-1ww89px"}

## 9.3 Thread类
{: id="20210313082711-19wojrk"}

### 9.3.1 构造方法
{: id="20210313082711-atrdy2h"}

public Thread() :分配一个新的线程对象。
public Thread(String name) :分配一个指定名字的新的线程对象。
public Thread(Runnable target) :分配一个带有指定目标新的线程对象。
public Thread(Runnable target,String name) :分配一个带有指定目标新的线程对象并指定名字。
{: id="20210313082711-xf0jerp"}

### 9.3.2 常用方法系列1
{: id="20210313082711-9ta9qso"}

* {: id="20210313082711-hp0b0a4"}public void run() :此线程要执行的任务在此处定义代码。
  {: id="20210313082711-zmutuvl"}
* {: id="20210313082711-25aj1t1"}public String getName() :获取当前线程名称。
  {: id="20210313082711-a4rbb47"}
* {: id="20210313082711-hilsxyx"}public static Thread currentThread() :返回对当前正在执行的线程对象的引用。
  {: id="20210313082711-7whagx0"}
* {: id="20210313082711-ljtaaue"}public final boolean isAlive()：测试线程是否处于活动状态。如果线程已经启动且尚未终止，则为活动状态。
  {: id="20210313082711-kvxbaxh"}
* {: id="20210313082711-jltu50e"}public final int getPriority() ：返回线程优先级
  {: id="20210313082711-0m68p38"}
* {: id="20210313082711-tdc1mrf"}public final void setPriority(int newPriority) ：改变线程的优先级
  {: id="20210313082711-syr4n6k"}

  * {: id="20210313082711-wr9832y"}每个线程都有一定的优先级，优先级高的线程将获得较多的执行机会。每个线程默认的优先级都与创建它的父线程具有相同的优先级。Thread类提供了setPriority(int newPriority)和getPriority()方法类设置和获取线程的优先级，其中setPriority方法需要一个整数，并且范围在[1,10]之间，通常推荐设置Thread类的三个优先级常量：
    {: id="20210313082711-1fv6qnu"}
  * {: id="20210313082711-272ud3z"}MAX_PRIORITY（10）：最高优先级
    {: id="20210313082711-qddcskm"}
  * {: id="20210313082711-7te1ejx"}MIN _PRIORITY （1）：最低优先级
    {: id="20210313082711-mb20rg0"}
  * {: id="20210313082711-kqr299l"}NORM_PRIORITY （5）：普通优先级，默认情况下main线程具有普通优先级。
    {: id="20210313082711-dc5v7h6"}
  {: id="20210313082711-ko8nj0y"}
{: id="20210313082711-fo4zxm9"}

```java
	public static void main(String[] args) {
		Thread t = new Thread(){
			public void run(){
				System.out.println(getName() + "的优先级：" + getPriority());
			}
		};
		t.setPriority(Thread.MAX_PRIORITY);
		t.start();
	
		System.out.println(Thread.currentThread().getName() +"的优先级：" + Thread.currentThread().getPriority());
	}
```
{: id="20210313082711-joj8288"}

### 9.3.3 常用方法系列2
{: id="20210313082711-u8d9i71"}

* {: id="20210313082711-913s4ga"}public void start() :导致此线程开始执行; Java虚拟机调用此线程的run方法。
  {: id="20210313082711-7wjwl3g"}
* {: id="20210313082711-lsrbqor"}public static void sleep(long millis) :使当前正在执行的线程以指定的毫秒数暂停（暂时停止执行）。
  {: id="20210313082711-rwsutin"}
* {: id="20210313082711-n8ohrr8"}public static void yield()：yield只是让当前线程暂停一下，让系统的线程调度器重新调度一次，希望优先级与当前线程相同或更高的其他线程能够获得执行机会，但是这个不能保证，完全有可能的情况是，当某个线程调用了yield方法暂停之后，线程调度器又将其调度出来重新执行。
  {: id="20210313082711-1dtiibr"}
* {: id="20210313082711-eohrhei"}void join() ：等待该线程终止。
  {: id="20210313082711-y9uy0bo"}

  void join(long millis) ：等待该线程终止的时间最长为 millis 毫秒。如果millis时间到，将不再等待。
  {: id="20210313082711-yg88i88"}

  void join(long millis, int nanos) ：等待该线程终止的时间最长为 millis 毫秒 + nanos 纳秒。
  {: id="20210313082711-zs84l53"}
* {: id="20210313082711-z9sfaq1"}public final void stop()：强迫线程停止执行。 该方法具有固有的不安全性，已经标记为@Deprecated不建议再使用，那么我们就需要通过其他方式来停止线程了，其中一种方式是使用变量的值的变化来控制线程是否结束。
  {: id="20210313082711-2h28975"}
{: id="20210313082711-qbwf6g6"}

#### 示例代码：倒计时
{: id="20210313082711-b7licfc"}

```java
	public static void main(String[] args) {
		for (int i = 10; i>=0; i--) {
			System.out.println(i);
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		System.out.println("新年快乐！");
	}
```
{: id="20210313082711-9fp9xga"}

#### 示例代码：强行加塞
{: id="20210313082711-fx02mg6"}

主线程：打印[1,10]，每隔10毫秒打印一个数字，
{: id="20210313082711-eet9xyn"}

自定义线程类：不停的问是否结束，输入Y或N，
{: id="20210313082711-8t8xdnz"}

现在当主线程打印完5之后，就让自定义线程类加塞，直到自定义线程类结束，主线程再继续。
{: id="20210313082711-k9bv9zf"}

```java
import java.util.Scanner;

public class TestJoin {
	public static void main(String[] args) {
		ChatThread t = new ChatThread();
		t.start();
	
		for (int i = 1; i <= 10; i++) {
			System.out.println("main:" + i);
			try {
				Thread.sleep(10);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
         //当main打印到5之后，需要等join进来的线程停止后才会继续了。
			if(i==5){
				try {
					t.join();
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	}
}
class ChatThread extends Thread{
	public void run(){
		Scanner input = new Scanner(System.in);
		while(true){
			System.out.println("是否结束？（Y、N）");
			char confirm = input.next().charAt(0);
			if(confirm == 'Y' || confirm == 'y'){
				break;
			}
		}
		input.close();
	}
}
```
{: id="20210313082711-ijsnszx"}

#### 示例代码：龟兔赛跑
{: id="20210313082711-67ek2yk"}

案例：编写乌龟类(Tortoise)和兔子类(Rabbit)， 编写龟兔赛跑多线程程序，设赛跑长度为30米。乌龟和兔子每跑完10米输出一次结果。
兔子的速度是10米每秒,兔子每跑完10米休眠的时间10秒。
乌龟的速度是1米每秒,乌龟每跑完10米的休眠时间是1秒。
案例完成思路要求：
乌龟定义一个线程,兔子定义一个线程，
两个线程同时开启，
提示：可以使用Thread.sleep(毫秒数)来模拟耗时。
{: id="20210313082711-mis2m2q"}

```java
public class TortoiseAndRabbitTest {

	public static void main(String[] args) {
		Tortoise t = new Tortoise();
		Rabbit r = new Rabbit();
		new Thread(t).start();
		new Thread(r).start();
	}

}

class Tortoise implements Runnable{

	@Override
	public void run() {
		for(int i=1;i<=30;i++){//i代表米数，每次+1代表跑过了一米。
			try {
				Thread.sleep(1000);//每次循环休眠1一秒，代表一秒钟跑了一米
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			System.out.println("乌龟跑了一米~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
			if(i==30){
				System.out.println("乌龟跑到了终点=============================");
				break;
			}
			if(i%10==0){
				try {
					Thread.sleep(1000);//每隔十米乌龟要休眠一秒
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	}

}


class Rabbit implements Runnable{

	@Override
	public void run() {
		// TODO Auto-generated method stub
		for(int i=1;i<=30;i++){//i代表米数，每次+1代表跑过了一米。
			try {
				Thread.sleep(100);//每次循环休眠0.1一秒，代表一秒钟跑了十米
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			System.out.println("兔子跑了一米~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
			if(i==30){
				System.out.println("兔子跑到了终点=============================");
				break;
			}
			if(i%10==0){
				try {
					Thread.sleep(10000);//每隔十米兔子要休眠是秒
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	}

}
```
{: id="20210313082711-nlz7z6x"}

> volatile的作用是确保不会因编译器的优化而省略某些指令，volatile的变量是说这变量可能会被意想不到地改变，每次都小心地重新读取这个变量的值，而不是使用保存在寄存器里的备份，这样，编译器就不会去假设这个变量的值了。
> {: id="20210313082711-bnvvf6z"}
{: id="20210313082711-tilprzm"}

### 9.3.4 守护线程（了解）
{: id="20210313082711-bo3guev"}

有一种线程，它是在后台运行的，它的任务是为其他线程提供服务的，这种线程被称为“守护线程”。JVM的垃圾回收线程就是典型的守护线程。
{: id="20210313082711-1vkl4da"}

守护线程有个特点，就是如果所有非守护线程都死亡，那么守护线程自动死亡。
{: id="20210313082711-bd3c23i"}

调用setDaemon(true)方法可将指定线程设置为守护线程。必须在线程启动之前设置，否则会报IllegalThreadStateException异常。
{: id="20210313082711-svydue9"}

调用isDaemon()可以判断线程是否是守护线程。
{: id="20210313082711-g5mj795"}

```java
public class TestThread {
	public static void main(String[] args) {
		MyDaemon m = new MyDaemon();
		m.setDaemon(true);
		m.start();

		for (int i = 1; i <= 100; i++) {
			System.out.println("main:" + i);
		}
	}
}

class MyDaemon extends Thread {
	public void run() {
		while (true) {
			System.out.println("我一直守护者你...");
			try {
				Thread.sleep(1);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
}
```
{: id="20210313082711-hbbb9vf"}

## 9.4 线程安全
{: id="20210313082711-wn8ur9j"}

### 9.4.1 线程安全
{: id="20210313082711-37xw3u7"}

我们通过一个案例，演示线程的安全问题：
电影院要卖票，我们模拟电影院的卖票过程。本次电影的座位共100个(本场电影只能卖100张票)。
我们来模拟电影院的售票窗口，实现多个窗口同时卖电影票(多个窗口一起卖这100张票)
方式一：
{: id="20210313082711-ydcrh07"}

```java
public class Ticket implements Runnable {
	private int ticket = 100;

	/*
	 * 执行卖票操作
	 */
	@Override
	public void run() {
		// 每个窗口卖票的操作
		// 窗口永远开启
		while (true) {
            if (ticket > 0) { // 有票可以卖
                    // 出票操作
                // 使用sleep模拟一下出票时间
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                // 获取当前线程对象的名字
                String name = Thread.currentThread().getName();
                System.out.println(name + "正在卖:" + ticket--);
            }
		}
	}
}
```
{: id="20210313082711-mvhlyg0"}

测试类：
{: id="20210313082711-i1w0ox2"}

```java
public class Demo {
	public static void main(String[] args) {
		// 创建线程任务对象
		Ticket ticket = new Ticket();
		// 创建三个窗口对象
		Thread t1 = new Thread(ticket, "窗口1");
		Thread t2 = new Thread(ticket, "窗口2");
		Thread t3 = new Thread(ticket, "窗口3");
		// 同时卖票
		t1.start();
		t2.start();
		t3.start();
	}
}
```
{: id="20210313082711-g0f31rg"}

方式二：
{: id="20210313082711-56x45ae"}

```java
public class TestThread {
	public static void main(String[] args) {
		Ticket t1 = new Ticket("窗口一");
		Ticket t2 = new Ticket("窗口二");
		Ticket t3 = new Ticket("窗口三");
	
		t1.start();
		t2.start();
		t3.start();
	}
}

class Ticket extends Thread{
	private static int ticket = 100;

	public Ticket() {
		super();
	}

	public Ticket(String name) {
		super(name);
	}

	/*
	 * 执行卖票操作
	 */
	@Override
	public void run() {
		// 每个窗口卖票的操作
		// 窗口永远开启
		while (true) {
            if (ticket > 0) { // 有票可以卖
                // 出票操作
                // 使用sleep模拟一下出票时间
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                // 获取当前线程对象的名字
                System.out.println(getName() + "正在卖:" + ticket--);
            }
		}
	}
}
```
{: id="20210313082711-s07mhs1"}

发现程序出现了两个问题：
{: id="20210313082711-rqbsbz9"}

1. {: id="20210313082711-k0dpmkd"}相同的票数,比如某张票被卖了两回。
   {: id="20210313082711-is8ui68"}
2. {: id="20210313082711-6cq889f"}不存在的票，比如0票与-1票，是不存在的。
   {: id="20210313082711-z48mnhg"}
{: id="20210313082711-4e3c7o1"}

这种问题，几个窗口(线程)票数不同步了，这种问题称为线程不安全。
{: id="20210313082711-oebbceu"}

当我们使用多个线程访问**同一资源**（可以是同一个变量、同一个文件、同一条记录等）的时候，若多个线程只有读操作，那么不会发生线程安全问题，但是如果多个线程中对资源有读和写的操作，就容易出现线程安全问题。
要解决上述多线程并发访问一个资源的安全性问题:也就是解决重复票与不存在票问题，Java中提供了同步机制
(synchronized)来解决。
{: id="20210313082711-g72fbox"}

![1563372934332](imgs13/1563372934332.png)
{: id="20210313082711-757n6a5"}

根据案例简述：
{: id="20210313082711-m0vlbj7"}

窗口1线程进入操作的时候，窗口2和窗口3线程只能在外等着，窗口1操作结束，窗口1和窗口2和窗口3才有机会进入代码去执行。也就是说在某个线程修改共享资源的时候，其他线程不能修改该资源，等待修改完毕同步之后，才能去抢夺CPU资源，完成对应的操作，保证了数据的同步性，解决了线程不安全的现象。
{: id="20210313082711-2t4cct1"}

为了保证每个线程都能正常执行原子操作,Java引入了线程同步机制。
那么怎么去使用呢？有三种方式完成同步操作：
{: id="20210313082711-gdtlpxt"}

1. {: id="20210313082711-rhlgmln"}同步代码块。
   {: id="20210313082711-0508kss"}
2. {: id="20210313082711-vb01qhw"}同步方法。
   {: id="20210313082711-1hm2c6s"}
3. {: id="20210313082711-loonb9r"}锁机制
   {: id="20210313082711-kc7cxed"}
{: id="20210313082711-3fsvgzg"}

### 9.4.2 同步代码块
{: id="20210313082711-m6fc50r"}

* {: id="20210313082711-kbkxvim"}同步代码块： synchronized 关键字可以用于方法中的某个区块中，表示只对这个区块的资源实行互斥访问。
  格式:
  {: id="20210313082711-p3y9ljj"}

  ```java
  synchronized(同步锁){
       需要同步操作的代码
  }
  ```
  {: id="20210313082711-hmbxo99"}

  * {: id="20210313082711-tgmkx4m"}同步锁:
    对象的同步锁只是一个概念,可以想象为在对象上标记了一个锁.
    {: id="20210313082711-cx6v26v"}
  {: id="20210313082711-z2eyyyz"}

  ```
  锁对象 可以是任意类型。
  ```

  {: id="20210313082711-wkmdk0t"}

  ```
  多个线程对象  要使用同一把锁。
  注意:在任何时候,最多允许一个线程拥有同步锁,谁拿到锁就进入代码块,其他的线程只能在外等着(BLOCKED)。
  使用同步代码块解决代码：
  ```

  {: id="20210313082711-y93hul5"}

  ```java
  public class Ticket implements Runnable {
  	private int ticket = 100;

  	/*
  	 * 执行卖票操作
  	 */
  	@Override
  	public void run() {
  		// 每个窗口卖票的操作
  		// 窗口永远开启
          while (true) {
              synchronized (this) {//这里可以选择this作为锁，是因为对于这几个线程，Ticket的this是同一个 
                  if (ticket > 0) {// 有票可以卖
                      // 出票操作
                      // 使用sleep模拟一下出票时间
                      try {
                          Thread.sleep(100);
                      } catch (InterruptedException e) {
                          e.printStackTrace();
                      }
                      // 获取当前线程对象的名字
                      String name = Thread.currentThread().getName();
                      System.out.println(name + "正在卖:" + ticket--);
                  }
  			}
          }
  	}
  }
  ```
  {: id="20210313082711-hlhy0z4"}

  当使用了同步代码块后，上述的线程的安全问题，解决了。
  {: id="20210313082711-vdt36tj"}

  ```java
  class Ticket extends Thread{
  	private static int ticket = 100;

  	public Ticket() {
  		super();
  	}

  	public Ticket(String name) {
  		super(name);
  	}

  	/*
  	 * 执行卖票操作
  	 */
  	@Override
  	public void run() {
  		// 每个窗口卖票的操作
  		// 窗口永远开启
  		while (true) {
  			synchronized (Ticket.class) {//这里不能选用this作为锁，因为这几个线程的this不是同一个
  				if (ticket > 0) { // 有票可以卖
  	                // 出票操作
  	                // 使用sleep模拟一下出票时间
  	                try {
  	                    Thread.sleep(100);
  	                } catch (InterruptedException e) {
  	                    e.printStackTrace();
  	                }
  	                // 获取当前线程对象的名字
  	                System.out.println(getName() + "正在卖:" + ticket--);
  	            }
  			}
  		}
  	}
  }
  ```
  {: id="20210313082711-ip3qa3y"}
{: id="20210313082711-vwvxywt"}

### 9.4.3 同步方法
{: id="20210313082711-sq61s6h"}

* {: id="20210313082711-em48rqx"}同步方法:使用synchronized修饰的方法,就叫做同步方法,保证A线程执行该方法的时候,其他线程只能在方法外等着
  {: id="20210313082711-mmuf8ka" updated="20210313143812"}
{: id="20210313082711-rc1ohu3"}

格式：
{: id="20210313082711-77w3baz"}

```java
public synchronized void method(){
    可能会产生线程安全问题的代码
}
```
{: id="20210313082711-ieitthw"}

同步方法的锁对象：
{: id="20210313082711-p2ufu88"}

（1）静态方法：当前类的Class对象
{: id="20210313082711-7m1o9c4"}

（2）非静态方法：this
{: id="20210313082711-6nj84ec"}

使用同步方法代码如下：
{: id="20210313082711-zuv4r89"}

```java
public class Ticket implements Runnable{
	private int ticket = 100;   
	/*
	 * 执行卖票操作   
	 */  
	@Override 
	public void run() {	    
	//每个窗口卖票的操作 	        
	//窗口 永远开启 	        
		while(true){        
			sellTicket();            
		}        
	}
		        
		/*   
		 * 锁对象 是 谁调用这个方法 就是谁     
		 *   隐含 锁对象 就是  this    
		 *    	    
		 */
	    
	public synchronized void sellTicket(){
		if(ticket>0){//有票 可以卖   
		  //出票操作
		  //使用sleep模拟一下出票时间 
			try {              
				Thread.sleep(100);
			} catch (InterruptedException e) {
  				e.printStackTrace();
			}
        
            //获取当前线程对象的名字 
            String name = Thread.currentThread().getName();
            System.out.println(name+"正在卖:"+ticket‐‐);
        }
   }
}
```
{: id="20210313082711-9txgln0"}

```java
class Ticket extends Thread {
	private static int ticket = 100;

	public Ticket() {
		super();
	}

	public Ticket(String name) {
		super(name);
	}

	/*
	 * 执行卖票操作
	 */
	@Override
	public void run() {
		// 每个窗口卖票的操作
		// 窗口永远开启
		while (true) {
			sellTicket();
		}
	}
	//这里必须是静态方法，因为如果是非静态方法，隐含的锁对象是this，那么多个线程就不是同一个锁对象了
	//而静态方法隐含的锁对象是当前类的Class对象
	public synchronized static void sellTicket(){
		if(ticket>0){//有票可以卖 
			//出票操作
			//使用sleep模拟一下出票时间
			try {
				Thread.sleep(100);
			} catch(InterruptedException e) {
				e.printStackTrace();
			}
			//获取当前线程对象的名字
			String name = Thread.currentThread().getName();
			System.out.println(name + "正在卖：" + ticket--);
		}
	}

}
```
{: id="20210313082711-5w5yee2"}

### 9.4.4 练习
{: id="20210313082711-y4jcov1"}

1、要求两个线程，同时打印字母，每个线程都能连续打印3个字母。并且连续打印3个小写字母后，换成打印3个大写字母，再换成打印3个小写字母，以此类推。当字母循环到z之后，回到a。
{: id="20210313082711-wghl09y"}

![](imgs13/线程安全练习1.png)
{: id="20210313082711-9z4kweg"}

```java
public class TestExer {
    public static void main(String[] args) {
        PrintLetter p = new PrintLetter();

        new Thread(p).start();
        new Thread(p).start();
    }
}
class PrintLetter implements Runnable{
    private char letter = 'a';
    private boolean flag = true;
    public void run(){
        while(true){
            synchronized (this) {
                for (int i = 1; i <= 3; i++) {
                    if (flag) {
                        System.out.println(Thread.currentThread().getName() + "->" + letter);
                    } else {
                        System.out.println(Thread.currentThread().getName() + "->" + (char) (letter - 32));
                    }
                    letter++;
                    if(letter > 'z'){
                        letter = 'a';
                    }
                }
                flag = !flag;

                try {
                    Thread.sleep(100);//控制节奏
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```
{: id="20210313082711-lwylrpm"}

## 9.5 等待唤醒机制
{: id="20210313082711-4d4ei4b"}

### 9.5.1 线程间通信
{: id="20210313082711-g9q5v4a"}

**为什么要处理线程间通信：**
{: id="20210313082711-nkequr1"}

多个线程在处理同一个资源，但是处理的动作（线程的任务）却不相同。而多个线程并发执行时, 在默认情况下CPU是随机切换线程的，当我们需要多个线程来共同完成一件任务，并且我们希望他们有规律的执行, 那么多线程之间需要一些通信机制，可以协调它们的工作，以此来帮我们达到多线程共同操作一份数据。
{: id="20210313082711-swbyjl6"}

比如：线程A用来生成包子的，线程B用来吃包子的，包子可以理解为同一资源，线程A与线程B处理的动作，一个是生产，一个是消费，此时B线程必须等到A线程完成后才能执行，那么线程A与线程B之间就需要线程通信，即—— **等待唤醒机制。**
{: id="20210313082711-cmy8pn2"}

### 9.5.2 等待唤醒机制
{: id="20210313082711-pfl0w1j"}

**什么是等待唤醒机制**{: style="background-color: rgb(255, 253, 56);"}
{: id="20210313082711-kekbgbc"}

这是多个线程间的一种**协作**机制。谈到线程我们经常想到的是线程间的**竞争（race）**，比如去争夺锁，但这并不是故事的全部，线程间也会有协作机制。
{: id="20210313082711-oqkpda5"}

就是在一个线程满足某个条件时，就进入等待状态（**wait()**/**wait(time)**）， 等待其他线程执行完他们的指定代码过后再将其唤醒（**notify()**）;或可以指定wait的时间，等时间到了自动唤醒；在有多个线程进行等待时，如果需要，可以使用 notifyAll()来唤醒所有的等待线程。wait/notify 就是线程间的一种协作机制。
{: id="20210313082711-zgbvh9a"}

1. {: id="20210313082711-pt3afxl"}wait：线程不再活动，不再参与调度，进入 wait set 中，因此不会浪费 CPU 资源，也不会去竞争锁了，这时的线程状态即是 WAITING或TIMED_WAITING。它还要等着别的线程执行一个**特别的动作**，也即是“**通知（notify）**”或者等待时间到，在这个对象上等待的线程从wait set 中释放出来，重新进入到调度队列（ready queue）中
   {: id="20210313082711-c7dgg2n"}
2. {: id="20210313082711-7w7kcpy"}notify：则选取所通知对象的 wait set 中的一个线程释放；
   {: id="20210313082711-bfu0rq7"}
3. {: id="20210313082711-j1vurxk"}notifyAll：则释放所通知对象的 wait set 上的全部线程。
   {: id="20210313082711-3bg94au"}
{: id="20210313082711-w5917jj"}

> 注意：
> {: id="20210313082711-ky6rluw"}
>
> 被通知线程被唤醒后也不一定能立即恢复执行，因为它当初中断的地方是在同步块内，而此刻它已经不持有锁，所以她需要再次尝试去获取锁（很可能面临其它线程的竞争），成功后才能在当初调用 wait 方法之后的地方恢复执行。
> {: id="20210313082711-74yheam"}
>
> 总结如下：
> {: id="20210313082711-1vjymxo"}
>
> - {: id="20210313082711-7hplvnv"}如果能获取锁，线程就从 WAITING 状态变成 RUNNABLE（可运行） 状态；
>   {: id="20210313082711-avu9hwe"}
> - {: id="20210313082711-1pi3at4"}否则，线程就从 WAITING 状态又变成 BLOCKED（等待锁） 状态
>   {: id="20210313082711-vuxoe8g"}
> {: id="20210313082711-0qkzc26"}
{: id="20210313082711-pcsyheu"}

**调用wait和notify方法需要注意的细节**
{: id="20210313082711-roje5n2"}

1. {: id="20210313082711-seubgb6"}wait方法与notify方法必须要由同一个锁对象调用。因为：对应的锁对象可以通过notify唤醒使用同一个锁对象调用的wait方法后的线程。
   {: id="20210313082711-adxq6yn"}
2. {: id="20210313082711-b9mt2ks"}wait方法与notify方法是属于Object类的方法的。因为：锁对象可以是任意对象，而任意对象的所属类都是继承了Object类的。
   {: id="20210313082711-8hgdn8j"}
3. {: id="20210313082711-fcfh3e2"}wait方法与notify方法必须要在同步代码块或者是同步函数中使用。因为：必须要通过锁对象调用这2个方法。
   {: id="20210313082711-sp9p5lh"}
{: id="20210313082711-890j2yp"}

### 9.5.3 生产者与消费者问题
{: id="20210313082711-5g4imk3"}

等待唤醒机制可以解决经典的“生产者与消费者”的问题。
{: id="20210313082711-o8u4ttj"}

生产者与消费者问题（英语：Producer-consumer problem），也称有限缓冲问题（英语：Bounded-buffer problem），是一个多线程同步问题的经典案例。该问题描述了两个（多个）共享固定大小缓冲区的线程——即所谓的“生产者”和“消费者”——在实际运行时会发生的问题。生产者的主要作用是生成一定量的数据放到缓冲区中，然后重复此过程。与此同时，消费者也在缓冲区消耗这些数据。该问题的关键就是要保证生产者不会在缓冲区满时加入数据，消费者也不会在缓冲区中空时消耗数据。
{: id="20210313082711-61e8y7d"}

生产者与消费者问题中其实隐含了两个问题：
{: id="20210313082711-n5qh3a5"}

* {: id="20210313082711-amxpinx"}线程安全问题：因为生产者与消费者共享数据缓冲区，不过这个问题可以使用同步解决。
  {: id="20210313082711-wz6lcbs"}
* {: id="20210313082711-22iv2ap"}线程的协调工作问题：
  {: id="20210313082711-yj1dww5"}

  * {: id="20210313082711-lyvy607"}要解决该问题，就必须让生产者线程在缓冲区满时等待(wait)，暂停进入阻塞状态，等到下次消费者消耗了缓冲区中的数据的时候，通知(notify)正在等待的线程恢复到就绪状态，重新开始往缓冲区添加数据。同样，也可以让消费者线程在缓冲区空时进入等待(wait)，暂停进入阻塞状态，等到生产者往缓冲区添加数据之后，再通知(notify)正在等待的线程恢复到就绪状态。通过这样的通信机制来解决此类问题。
    {: id="20210313082711-izylmfm"}
  {: id="20210313082711-0wg1han"}
{: id="20210313082711-nvm8q2k"}

#### 一个厨师一个服务员问题
{: id="20210313082711-vng1vfm"}

案例：有家餐馆的取餐口比较小，只能放10份快餐，厨师做完快餐放在取餐口的工作台上，服务员从这个工作台取出快餐给顾客。现在有1个厨师和1个服务员。
{: id="20210313082711-rmclxu3"}

```java
package com.atguigu.test.thread;

public class TestThread {
	public static void main(String[] args) {
		Workbench bench = new Workbench();
		Cook c1 = new Cook("大拿",bench);
		Waiter w1 = new Waiter("翠花",bench);
	
		c1.start();
		w1.start();
	}

}
class Workbench {
	private static final int MAX_VALUE = 10;
	private int num;
	public synchronized void put() {
		if(num >= MAX_VALUE){
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		try {
			Thread.sleep(100);
			//加入睡眠时间是放大问题现象，去掉同步和wait等，可观察问题
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		num++;
		System.out.println(Thread.currentThread().getName()+ "厨师制作了一份快餐，现在工作台上有：" + num + "份快餐");
		this.notify();
	}
	public synchronized void take() {
		if(num <=0){
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		try {
			Thread.sleep(100);
			//加入睡眠时间是放大问题现象，去掉同步和wait等，可观察问题
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		num--;
		System.out.println(Thread.currentThread().getName()+"服务员取走了一份快餐，现在工作台上有：" + num + "份快餐");
		this.notify();
	}
}
class Waiter extends Thread{
	private Workbench workbench;

	public Waiter(String name,Workbench workbench) {
		super(name);
		this.workbench = workbench;
	}

	public void run(){
		while(true) {
			workbench.take();
		}
	}
}
class Cook extends Thread{
	private Workbench workbench;

	public Cook(String name,Workbench workbench) {
		super(name);
		this.workbench = workbench;
	}

	public void run(){
		while(true) {
			workbench.put();
		}
	}
}
```
{: id="20210313082711-0z2pfv9"}

#### 多个厨师多个服务员问题
{: id="20210313082711-1o1krlx"}

案例：有家餐馆的取餐口比较小，只能放10份快餐，厨师做完快餐放在取餐口的工作台上，服务员从这个工作台取出快餐给顾客。现在有多个厨师和多个服务员。
{: id="20210313082711-3xd7csf"}

```java
package com.atguigu.test.thread;

public class TestThread {
	public static void main(String[] args) {
		Workbench bench = new Workbench();
		Cook c1 = new Cook("大拿",bench);
		Waiter w1 = new Waiter("翠花",bench);
	
		c1.start();
		w1.start();
	}

}
class Workbench {
	private static final int MAX_VALUE = 10;
	private int num;
	public synchronized void put() {
		while(num >= MAX_VALUE){
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		try {
			Thread.sleep(100);
			//加入睡眠时间是放大问题现象，去掉同步和wait等，可观察问题
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		num++;
		System.out.println(Thread.currentThread().getName()+ "厨师制作了一份快餐，现在工作台上有：" + num + "份快餐");
		this.notifyAll();
	}
	public synchronized void take() {
		while(num <=0){
			try {
				this.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		try {
			Thread.sleep(100);
			//加入睡眠时间是放大问题现象，去掉同步和wait等，可观察问题
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		num--;
		System.out.println(Thread.currentThread().getName()+"服务员取走了一份快餐，现在工作台上有：" + num + "份快餐");
		this.notifyAll();
	}
}
class Waiter extends Thread{
	private Workbench workbench;

	public Waiter(String name,Workbench workbench) {
		super(name);
		this.workbench = workbench;
	}

	public void run(){
		while(true) {
			workbench.take();
		}
	}
}
class Cook extends Thread{
	private Workbench workbench;

	public Cook(String name,Workbench workbench) {
		super(name);
		this.workbench = workbench;
	}

	public void run(){
		while(true) {
			workbench.put();
		}
	}
}

```
{: id="20210313082711-3yme8ep"}

### 9.5.4 练习
{: id="20210313082711-jwjp98e"}

1、要求两个线程，同时打印字母，每个线程都能连续打印3个字母。两个线程交替打印，一个线程打印字母的小写形式，一个线程打印字母的大写形式，但是字母是连续的。当字母循环到z之后，回到a。
{: id="20210313082711-5h1x7k3"}

![](imgs13/线程安全练习2.png)
{: id="20210313082711-07glaud"}

```
public class TestExer {
    public static void main(String[] args) {
        PrintLetter p = new PrintLetter();

        new Thread(p).start();
        new Thread(p).start();
    }
}
class PrintLetter implements Runnable{
    private char letter = 'a';
    private boolean flag = true;
    public void run(){
        while(true){
            synchronized (this) {
                for (int i = 1; i <= 3; i++) {
                    if (flag) {
                        System.out.println(Thread.currentThread().getName() + "->" + letter);
                    } else {
                        System.out.println(Thread.currentThread().getName() + "->" + (char) (letter - 32));
                    }
                    letter++;
                    if(letter > 'z'){
                        letter = 'a';
                    }
                }
                flag = !flag;
                this.notify();
                try {
                    this.wait();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                try {
                    Thread.sleep(1000);//控制节奏
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```
{: id="20210313082711-fdscyt9"}

## 9.6 线程生命周期
{: id="20210313082711-uosy3dg"}

### 9.6.1 观点1:5种状态
{: id="20210313082711-o8grku3"}

简单来说，线程的生命周期有五种状态：新建（New）、就绪（Runnable）、运行（Running）、阻塞（Blocked）、死亡（Dead）。CPU需要在多条线程之间切换，于是线程状态会多次在运行、阻塞、就绪之间切换。
{: id="20210313082711-1i8o481"}

![](imgs13/1563282798989.png)
{: id="20210313082711-0ft1hjf"}

**1.** **新建**
{: id="20210313082711-6onwesi"}

当一个Thread类或其子类的对象被声明并创建时，新生的线程对象处于新建状。此时它和其他Java对象一样，仅仅由JVM为其分配了内存，并初始化了实例变量的值。此时的线程对象并没有任何线程的动态特征，程序也不会执行它的线程体run()。
{: id="20210313082711-qs2cu7h"}

**2.** **就绪**
{: id="20210313082711-p7n8dlb"}

但是当线程对象调用了start()方法之后，就不一样了，线程就从新建状态转为就绪状态。JVM会为其创建方法调用栈和程序计数器，当然，处于这个状态中的线程并没有开始运行，只是表示已具备了运行的条件，随时可以被调度。至于什么时候被调度，取决于JVM里线程调度器的调度。
{: id="20210313082711-lciuph8"}

> 注意：
> {: id="20210313082711-isi7h6n"}
>
> 程序只能对新建状态的线程调用start()，并且只能调用一次，如果对非新建状态的线程，如已启动的线程或已死亡的线程调用start()都会报错IllegalThreadStateException异常。
> {: id="20210313082711-8vzrbjm"}
{: id="20210313082711-hxtdlc5"}

**3.** **运行**
{: id="20210313082711-bx2idks"}

如果处于就绪状态的线程获得了CPU，开始执行run()方法的线程体代码，则该线程处于运行状态。如果计算机只有一个CPU，在任何时刻只有一个线程处于运行状态，如果计算机有多个处理器，将会有多个线程并行(Parallel)执行。
{: id="20210313082711-j2f3wcs"}

当然，美好的时光总是短暂的，而且CPU讲究雨露均沾。对于抢占式策略的系统而言，系统会给每个可执行的线程一个小时间段来处理任务，当该时间用完，系统会剥夺该线程所占用的资源，让其回到就绪状态等待下一次被调度。此时其他线程将获得执行机会，而在选择下一个线程时，系统会适当考虑线程的优先级。
{: id="20210313082711-sx1fn3q"}

**4.** **阻塞**
{: id="20210313082711-1t7nc0n"}

当在运行过程中的线程遇到如下情况时，线程会进入阻塞状态：
{: id="20210313082711-jw1bnd4"}

* {: id="20210313082711-g8jv0co"}线程调用了sleep()方法，主动放弃所占用的CPU资源；
  {: id="20210313082711-wvsh4k9"}
* {: id="20210313082711-gy1oni8"}线程试图获取一个同步监视器，但该同步监视器正被其他线程持有；
  {: id="20210313082711-ukkgnns"}
* {: id="20210313082711-oxm882t"}线程执行过程中，同步监视器调用了wait()，让它等待某个通知（notify）；
  {: id="20210313082711-w40eutu"}
* {: id="20210313082711-7zbcot6"}线程执行过程中，同步监视器调用了wait(time)
  {: id="20210313082711-73zhlqv"}
* {: id="20210313082711-0ud8978"}线程执行过程中，遇到了其他线程对象的加塞（join）；
  {: id="20210313082711-8ci8jv7"}
* {: id="20210313082711-ehbxtnr"}线程被调用suspend方法被挂起（已过时，因为容易发生死锁）；
  {: id="20210313082711-23750t4"}
{: id="20210313082711-6b34mqm"}

当前正在执行的线程被阻塞后，其他线程就有机会执行了。针对如上情况，当发生如下情况时会解除阻塞，让该线程重新进入就绪状态，等待线程调度器再次调度它：
{: id="20210313082711-zo0omyk"}

* {: id="20210313082711-gqx81fx"}线程的sleep()时间到；
  {: id="20210313082711-k4xq7xw"}
* {: id="20210313082711-frqsj1z"}线程成功获得了同步监视器；
  {: id="20210313082711-yddw540"}
* {: id="20210313082711-faxdxmn"}线程等到了通知(notify)；
  {: id="20210313082711-utxv58j"}
* {: id="20210313082711-wl56yl5"}线程wait的时间到了
  {: id="20210313082711-v7gyac5"}
* {: id="20210313082711-z2iffev"}加塞的线程结束了；
  {: id="20210313082711-mh31o8y"}
* {: id="20210313082711-wxruxq3"}被挂起的线程又被调用了resume恢复方法（已过时，因为容易发生死锁）；
  {: id="20210313082711-rrawyr0"}
{: id="20210313082711-h3n0l9b"}

**5.** **死亡**
{: id="20210313082711-m8j654e"}

线程会以以下三种方式之一结束，结束后的线程就处于死亡状态：
{: id="20210313082711-9807e0q"}

* {: id="20210313082711-7i4ryf2"}run()方法执行完成，线程正常结束
  {: id="20210313082711-ud2wirj"}
* {: id="20210313082711-zalvv7n"}线程执行过程中抛出了一个未捕获的异常（Exception）或错误（Error）
  {: id="20210313082711-tatabdf"}
* {: id="20210313082711-lzi1yj0"}直接调用该线程的stop()来结束该线程（已过时，因为容易发生死锁）
  {: id="20210313082711-rcjwnj2"}
{: id="20210313082711-33ymbp8"}

### 9.6.2 观点2:6种状态
{: id="20210313082711-3t7zg5z"}

在java.lang.Thread.State的枚举类中这样定义：
{: id="20210313082711-rhww6yj"}

```java
    public enum State {
        NEW,
        RUNNABLE,
        BLOCKED,
        WAITING,
        TIMED_WAITING,
        TERMINATED;
    }
```
{: id="20210313082711-467jaz2"}

* {: id="20210313082711-l0hek4e"}首先它没有区分：就绪和运行状态，因为对于Java对象来说，只能标记为可运行，至于什么时候运行，不是JVM来控制的了，是OS来进行调度的，而且时间非常短暂，因此对于Java对象的状态来说，无法区分。只能我们人为的进行想象和理解。
  {: id="20210313082711-vtusrkn"}
* {: id="20210313082711-7qnynsx"}其次根据Thread.State的定义，阻塞状态是分为三种的：BLOCKED、WAITING、TIMED_WAITING。
  {: id="20210313082711-5rqgadi"}
{: id="20210313082711-c0m79t8"}

![1563381997032](imgs13/1563381997032.png)
{: id="20210313082711-0sb7geh"}

说明：当从WAITING或TIMED_WAITING恢复到Runnable状态时，如果发现当前线程没有得到监视器锁，那么会立刻转入BLOCKED状态。
{: id="20210313082711-63nnvks"}

## 9.7 释放锁操作与死锁
{: id="20210313082711-aoo6l3x"}

任何线程进入同步代码块、同步方法之前，必须先获得对同步监视器的锁定，那么何时会释放对同步监视器的锁定呢？
{: id="20210313082711-nh7l10l"}

### **1、释放锁的操作**
{: id="20210313082711-5w86t8a"}

当前线程的同步方法、同步代码块执行结束。
{: id="20210313082711-9i4z7x8"}

当前线程在同步代码块、同步方法中出现了未处理的Error或Exception，导致当前线程异常结束。
{: id="20210313082711-jxl8ed2"}

当前线程在同步代码块、同步方法中执行了锁对象的wait()方法，当前线程被挂起，并释放锁。
{: id="20210313082711-2tlzo9e"}

### **2、不会释放锁的操作**
{: id="20210313082711-13niwy3"}

线程执行同步代码块或同步方法时，程序调用Thread.sleep()、Thread.yield()方法暂停当前线程的执行。
{: id="20210313082711-85zpxln"}

线程执行同步代码块时，其他线程调用了该线程的suspend()方法将该该线程挂起，该线程不会释放锁（同步监视器）。应尽量避免使用suspend()和resume()这样的过时来控制线程。
{: id="20210313082711-5zufqi9"}

### 3、死锁
{: id="20210313082711-j3i7ln6"}

不同的线程分别锁住对方需要的同步监视器对象不释放，都在等待对方先放弃时就形成了线程的死锁。一旦出现死锁，整个程序既不会发生异常，也不会给出任何提示，只是所有线程处于阻塞状态，无法继续。
{: id="20210313082711-cqy46m4"}

```java
public class TestDeadLock {
	public static void main(String[] args) {
		Object g = new Object();
		Object m = new Object();
		Owner s = new Owner(g,m);
		Customer c = new Customer(g,m);
		new Thread(s).start();
		new Thread(c).start();
	}
}
class Owner implements Runnable{
	private Object goods;
	private Object money;

	public Owner(Object goods, Object money) {
		super();
		this.goods = goods;
		this.money = money;
	}

	@Override
	public void run() {
		synchronized (goods) {
			System.out.println("先给钱");
			synchronized (money) {
				System.out.println("发货");
			}
		}
	}
}
class Customer implements Runnable{
	private Object goods;
	private Object money;

	public Customer(Object goods, Object money) {
		super();
		this.goods = goods;
		this.money = money;
	}

	@Override
	public void run() {
		synchronized (money) {
			System.out.println("先发货");
			synchronized (goods) {
				System.out.println("再给钱");
			}
		}
	}
}
```
{: id="20210313082711-fk01pbx"}

### 4、面试题：sleep()和wait()方法的区别
{: id="20210313082711-6iw090n"}

（1）sleep()不释放锁，wait()释放锁
{: id="20210313082711-kckvn1f"}

（2）sleep()指定休眠的时间，wait()可以指定时间也可以无限等待直到notify或notifyAll
{: id="20210313082711-w8rl0gc"}

（3）sleep()在Thread类中声明的静态方法，wait方法在Object类中声明
{: id="20210313082711-jilhwb9"}

因为我们调用wait（）方法是由锁对象调用，而锁对象的类型是任意类型的对象。那么希望任意类型的对象都要有的方法，只能声明在Object类中。
{: id="20210313082711-n2u84uo"}


{: id="20210313082711-7i0svmt" type="doc"}
