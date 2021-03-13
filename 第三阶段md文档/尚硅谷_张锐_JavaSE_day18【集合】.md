# JavaSE_day18【集合】
{: id="20210313082711-ox54ldh"}

## 主要内容
{: id="20210313082711-vz10eqz"}

* {: id="20210313082711-0922tfo"}Map
  {: id="20210313082711-asx3jct"}
{: id="20210313082711-md42dyd"}

## 学习目标
{: id="20210313082711-cp9r0qc"}

* {: id="20210313082711-035vfp0"}[ ] 掌握Map接口常见方法
  {: id="20210313082711-j8yprb2"}
* {: id="20210313082711-wic8qul"}[ ] 掌握Map常用实现类
  {: id="20210313082711-s97ftpr"}
{: id="20210313082711-o47xpt7"}

# 第十三章 Map接口
{: id="20210313082711-pounfzc"}

## 13.1Map
{: id="20210313082711-31nhg7t"}

### 13.1.1 概述
{: id="20210313082711-0mccmx1"}

现实生活中，我们常会看到这样的一种集合：IP地址与主机名，身份证号与个人，系统用户名与系统用户对象等，这种一一对应的关系，就叫做映射。Java提供了专门的集合类用来存放这种对象关系的对象，即`java.util.Map<K,V>`接口。
{: id="20210313082711-zxb174n"}

我们通过查看`Map`接口描述，发现`Map<K,V>`接口下的集合与`Collection<E>`接口下的集合，它们存储数据的形式不同。
{: id="20210313082711-al522yw"}

* {: id="20210313082711-aaygng2"}`Collection`中的集合，元素是孤立存在的（理解为单身），向集合中存储元素采用一个个元素的方式存储。
  {: id="20210313082711-9emrdfr"}
* {: id="20210313082711-yzr1ze8"}`Map`中的集合，元素是成对存在的(理解为夫妻)。每个元素由键与值两部分组成，通过键可以找对所对应的值。
  {: id="20210313082711-t84nqay"}
* {: id="20210313082711-offufjn"}`Collection`中的集合称为单列集合，`Map`中的集合称为双列集合。
  {: id="20210313082711-jxxbusz"}
* {: id="20210313082711-2kh884k"}需要注意的是，`Map`中的集合不能包含重复的键，值可以重复；每个键只能对应一个值（这个值可以是单个值，也可以是个数组或集合值）。
  {: id="20210313082711-d0gewql"}
{: id="20210313082711-jpa6509"}

![](D:/尚硅谷/备课资料/我的MD课件/part3/day17_note/imgs/Collection与Map.bmp)
{: id="20210313082711-cp03h9a"}

### 13.1.2 Map常用方法
{: id="20210313082711-kb4bmok"}

1、添加操作
{: id="20210313082711-ro6utmv"}

* {: id="20210313082711-6fwpkot"}V put(K key,V value)
  {: id="20210313082711-clavr5k"}
* {: id="20210313082711-byc0kci"}void putAll(Map<? extends K,? extends V> m)
  {: id="20210313082711-4wmrnub"}
{: id="20210313082711-gqr639k"}

2、删除
{: id="20210313082711-93r4fux"}

* {: id="20210313082711-5jcmbu0"}void clear()
  {: id="20210313082711-u7nl21i"}
* {: id="20210313082711-7lcqx15"}V remove(Object key)
  {: id="20210313082711-3hbxv84"}
{: id="20210313082711-aji0nww"}

3、元素查询的操作
{: id="20210313082711-t12aysp"}

* {: id="20210313082711-hcbh7mr"}V get(Object key)
  {: id="20210313082711-0gfmw47"}
* {: id="20210313082711-emejjv1"}boolean containsKey(Object key)
  {: id="20210313082711-nu7kd4h"}
* {: id="20210313082711-dzu8xt2"}boolean containsValue(Object value)
  {: id="20210313082711-oonqh3h"}
* {: id="20210313082711-ogw3vbo"}boolean isEmpty()
  {: id="20210313082711-xpq52s9"}
{: id="20210313082711-vhg1z4m"}

4、元视图操作的方法：
{: id="20210313082711-erpgr1g"}

* {: id="20210313082711-jglvwdy"}Set<K> keySet()
  {: id="20210313082711-fc5agdf"}
* {: id="20210313082711-1kornwu"}Collection<V> values()
  {: id="20210313082711-6h9bo5f"}
* {: id="20210313082711-vvpicbp"}Set<Map.Entry<K,V>> entrySet()
  {: id="20210313082711-3uyuv8x"}
{: id="20210313082711-hnqwsz7"}

5、其他方法
{: id="20210313082711-q727o1y"}

* {: id="20210313082711-ipohmyn"}int size()
  {: id="20210313082711-k07ia4v"}
{: id="20210313082711-4kffk0x"}

```java
public class MapDemo {
    public static void main(String[] args) {
        //创建 map对象
        HashMap<String, String>  map = new HashMap<String, String>();

        //添加元素到集合
        map.put("黄晓明", "杨颖");
        map.put("文章", "马伊琍");
        map.put("邓超", "孙俪");
        System.out.println(map);

        //String remove(String key)
        System.out.println(map.remove("邓超"));
        System.out.println(map);

        // 想要查看 黄晓明的媳妇 是谁
        System.out.println(map.get("黄晓明"));
        System.out.println(map.get("邓超"));    
    }
}
```
{: id="20210313082711-k5kcwqu"}

> tips:
> {: id="20210313082711-dy6nfpt"}
>
> 使用put方法时，若指定的键(key)在集合中没有，则没有这个键对应的值，返回null，并把指定的键值添加到集合中；
> {: id="20210313082711-ku0oai0"}
>
> 若指定的键(key)在集合中存在，则返回值为集合中键对应的值（该值为替换前的值），并把指定键所对应的值，替换成指定的新值。
> {: id="20210313082711-uwei9xt"}
{: id="20210313082711-yz6okz1"}

### 13.1.3  Map集合的遍历
{: id="20210313082711-ggou13w"}

Collection集合的遍历：（1）foreach（2）通过Iterator对象遍历
{: id="20210313082711-l9jgfv0"}

Map的遍历，不能支持foreach，因为Map接口没有继承java.lang.Iterable<T>接口，也没有实现Iterator iterator()方法。只能用如下方式遍历：
{: id="20210313082711-cc7wlbz"}

（1）分开遍历：
{: id="20210313082711-2t5wlnj"}

* {: id="20210313082711-01vbequ"}单独遍历所有key
  {: id="20210313082711-4lplow2"}
* {: id="20210313082711-pu1bcpt"}单独遍历所有value
  {: id="20210313082711-74lzjfn"}
{: id="20210313082711-c2nj1k5"}

（2）成对遍历：
{: id="20210313082711-74xebk5"}

* {: id="20210313082711-jrrxly6"}遍历的是映射关系Map.Entry类型的对象，Map.Entry是Map接口的内部接口。每一种Map内部有自己的Map.Entry的实现类。在Map中存储数据，实际上是将Key---->value的数据存储在Map.Entry接口的实例中，再在Map集合中插入Map.Entry的实例化对象，如图示：
  {: id="20210313082711-q1j0mka"}
{: id="20210313082711-r01a4o5"}

![1563725601891](D:/尚硅谷/备课资料/我的MD课件/part3/day17_note/imgs/1563725601891.png)
{: id="20210313082711-f19dn0p"}

```java
public class TestMap {
	public static void main(String[] args) {
		HashMap<String,String> map = new HashMap<>();
		map.put("许仙", "白娘子");
		map.put("董永", "七仙女");
		map.put("牛郎", "织女");
		map.put("许仙", "小青");
		
		System.out.println("所有的key:");
		Set<String> keySet = map.keySet();
		for (String key : keySet) {
			System.out.println(key);
		}
		
		System.out.println("所有的value：");
		Collection<String> values = map.values();
		for (String value : values) {
			System.out.println(value);
		}
		
		System.out.println("所有的映射关系");
		Set<Map.Entry<String,String>> entrySet = map.entrySet();
		for (Map.Entry<String,String> entry : entrySet) {
//			System.out.println(entry);
			System.out.println(entry.getKey()+"->"+entry.getValue());
		}
	}
}
```
{: id="20210313082711-s3nggcl"}

### 13.1.4 Map的实现类们
{: id="20210313082711-j1iu2ub"}

Map接口的常用实现类：HashMap、TreeMap、LinkedHashMap和Properties。其中HashMap是 Map 接口使用频率最高的实现类。
{: id="20210313082711-umabozd"}

#### **1、HashMap和Hashtable的区别与联系**
{: id="20210313082711-8nfqx8t"}

* {: id="20210313082711-q805xq4"}HashMap和Hashtable都是哈希表。
  {: id="20210313082711-dp4bni2"}
* {: id="20210313082711-mvai1l7"}HashMap和Hashtable判断两个 key 相等的标准是：两个 key 的hashCode 值相等，并且 equals() 方法也返回 true。因此，为了成功地在哈希表中存储和获取对象，用作键的对象必须实现 hashCode 方法和 equals 方法。
  {: id="20210313082711-sbo41bi"}
* {: id="20210313082711-czjxo1j"}Hashtable是线程安全的，任何非 null 对象都可以用作键或值。
  {: id="20210313082711-f7tug98"}
* {: id="20210313082711-d0wu6ca"}HashMap是线程不安全的，并允许使用 null 值和 null 键。
  {: id="20210313082711-rgp7lka"}
{: id="20210313082711-nvicyub"}

示例代码：添加员工姓名为key，薪资为value
{: id="20210313082711-fxsohat"}

```java
	public static void main(String[] args) {
		HashMap<String,Double> map = new HashMap<>();
		map.put("张三", 10000.0);
		//key相同，新的value会覆盖原来的value
		//因为String重写了hashCode和equals方法
		map.put("张三", 12000.0);
		map.put("李四", 14000.0);
		//HashMap支持key和value为null值
		String name = null;
		Double salary = null;
		map.put(name, salary);
		
		Set<Entry<String, Double>> entrySet = map.entrySet();
		for (Entry<String, Double> entry : entrySet) {
			System.out.println(entry);
		}
	}
```
{: id="20210313082711-yo74ngb"}

#### **2、LinkedHashMap**
{: id="20210313082711-28wn3ij"}

LinkedHashMap 是 HashMap 的子类。此实现与 HashMap 的不同之处在于，后者维护着一个运行于所有条目的双重链接列表。此链接列表定义了迭代顺序，该迭代顺序通常就是将键插入到映射中的顺序（插入顺序）。
{: id="20210313082711-qrbs9ck"}

示例代码：添加员工姓名为key，薪资为value
{: id="20210313082711-6cliyna"}

```java
	public static void main(String[] args) {
		LinkedHashMap<String,Double> map = new LinkedHashMap<>();
		map.put("张三", 10000.0);
		//key相同，新的value会覆盖原来的value
		//因为String重写了hashCode和equals方法
		map.put("张三", 12000.0);
		map.put("李四", 14000.0);
		//HashMap支持key和value为null值
		String name = null;
		Double salary = null;
		map.put(name, salary);
		
		Set<Entry<String, Double>> entrySet = map.entrySet();
		for (Entry<String, Double> entry : entrySet) {
			System.out.println(entry);
		}
	}
```
{: id="20210313082711-2zgr9cy"}

#### **3、TreeMap**
{: id="20210313082711-e5sgkf2"}

基于红黑树（Red-Black tree）的 NavigableMap 实现。该映射根据其键的自然顺序进行排序，或者根据创建映射时提供的 Comparator 进行排序，具体取决于使用的构造方法。
{: id="20210313082711-3gsx6oe"}

代码示例：添加员工姓名为key，薪资为value
{: id="20210313082711-7xrtk5p"}

```java
package com.atguigu.map;

import java.util.Comparator;
import java.util.Map.Entry;
import java.util.Set;
import java.util.TreeMap;

import org.junit.Test;

public class TestTreeMap {
	@Test
	public void test1() {
		TreeMap<String,Integer> map = new TreeMap<>();
		map.put("Jack", 11000);
		map.put("Alice", 12000);
		map.put("zhangsan", 13000);
		map.put("baitao", 14000);
		map.put("Lucy", 15000);
		
		//String实现了Comparable接口，默认按照Unicode编码值排序
		Set<Entry<String, Integer>> entrySet = map.entrySet();
		for (Entry<String, Integer> entry : entrySet) {
			System.out.println(entry);
		}
	}
	@Test
	public void test2() {
		//指定定制比较器Comparator，按照Unicode编码值排序，但是忽略大小写
		TreeMap<String,Integer> map = new TreeMap<>(new Comparator<String>() {

			@Override
			public int compare(String o1, String o2) {
				return o1.compareToIgnoreCase(o2);
			}
		});
		map.put("Jack", 11000);
		map.put("Alice", 12000);
		map.put("zhangsan", 13000);
		map.put("baitao", 14000);
		map.put("Lucy", 15000);
		
		Set<Entry<String, Integer>> entrySet = map.entrySet();
		for (Entry<String, Integer> entry : entrySet) {
			System.out.println(entry);
		}
	}
}
```
{: id="20210313082711-le2e9rg"}

#### **4、Properties**
{: id="20210313082711-yihwqxt"}

Properties 类是 Hashtable 的子类，Properties 可保存在流中或从流中加载。属性列表中每个键及其对应值都是一个字符串。
{: id="20210313082711-kfvb276"}

存取数据时，建议使用setProperty(String key,String value)方法和getProperty(String key)方法。
{: id="20210313082711-ql0v4gh"}

代码示例：
{: id="20210313082711-biqy9ed"}

```java
	public static void main(String[] args) {
		Properties properties = System.getProperties();
		String p2 = properties.getProperty("file.encoding");//当前源文件字符编码
		System.out.println(p2);
	}
```
{: id="20210313082711-isc19m8"}

### 13.1.5 Set集合与Map集合的关系
{: id="20210313082711-4au4fcn"}

Set的内部实现其实是一个Map。即HashSet的内部实现是一个HashMap，TreeSet的内部实现是一个TreeMap，LinkedHashSet的内部实现是一个LinkedHashMap。
{: id="20210313082711-emdft8y"}

部分源代码摘要：
{: id="20210313082711-tivfz2r"}

HashSet源码：
{: id="20210313082711-hhrl97z"}

```java
    public HashSet() {
        map = new HashMap<>();
    }

    public HashSet(Collection<? extends E> c) {
        map = new HashMap<>(Math.max((int) (c.size()/.75f) + 1, 16));
        addAll(c);
    }

    public HashSet(int initialCapacity, float loadFactor) {
        map = new HashMap<>(initialCapacity, loadFactor);
    }

    public HashSet(int initialCapacity) {
        map = new HashMap<>(initialCapacity);
    }

	//这个构造器是给子类LinkedHashSet调用的
    HashSet(int initialCapacity, float loadFactor, boolean dummy) {
        map = new LinkedHashMap<>(initialCapacity, loadFactor);
    }
```
{: id="20210313082711-90u8qy0"}

LinkedHashSet源码：
{: id="20210313082711-x3aknx5"}

```java
    public LinkedHashSet(int initialCapacity, float loadFactor) {
        super(initialCapacity, loadFactor, true);//调用HashSet的某个构造器
    }

    public LinkedHashSet(int initialCapacity) {
        super(initialCapacity, .75f, true);//调用HashSet的某个构造器
    }

    public LinkedHashSet() {
        super(16, .75f, true);
    }

    public LinkedHashSet(Collection<? extends E> c) {
        super(Math.max(2*c.size(), 11), .75f, true);//调用HashSet的某个构造器
        addAll(c);
    }
```
{: id="20210313082711-j2rtaoj"}

TreeSet源码：
{: id="20210313082711-wlo0442"}

```java
    public TreeSet() {
        this(new TreeMap<E,Object>());
    }

    public TreeSet(Comparator<? super E> comparator) {
        this(new TreeMap<>(comparator));
    }

    public TreeSet(Collection<? extends E> c) {
        this();
        addAll(c);
    }

    public TreeSet(SortedSet<E> s) {
        this(s.comparator());
        addAll(s);
    }
```
{: id="20210313082711-gvd2020"}

但是，咱们存到Set中只有一个元素，又是怎么变成(key,value)的呢？
{: id="20210313082711-kig17rw"}

以HashSet中的源码为例：
{: id="20210313082711-kshjgo2"}

```java
private static final Object PRESENT = new Object();
public boolean add(E e) {
    return map.put(e, PRESENT)==null;
}
public Iterator<E> iterator() {
    return map.keySet().iterator();
}
```
{: id="20210313082711-bzfwk2k"}

原来是，把添加到Set中的元素作为内部实现map的key，然后用一个常量对象PRESENT对象，作为value。
{: id="20210313082711-4m0p2jk"}

这是因为Set的元素不可重复和Map的key不可重复有相同特点。Map有一个方法keySet()可以返回所有key。
{: id="20210313082711-bv4ppt1"}

## 13.2 集合框架
{: id="20210313082711-spfa761"}

![](D:/尚硅谷/备课资料/我的MD课件/part3/day17_note/imgs/1560348912361.png)
{: id="20210313082711-vmgj82p"}


{: id="20210313082711-303egni" type="doc"}
