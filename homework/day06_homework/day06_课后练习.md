# day06_课后练习
{: id="20210309203838-twxzbjs"}

# 成员变量基础练习
{: id="20210309203838-e4j2tu1"}

## 第1题
{: id="20210309203838-8pdaygt"}

案例：
{: id="20210309203838-wd4m59c"}

​	声明员工类Employee，包含属性：编号、姓名、年龄、薪资，
{: id="20210309203838-8ua3ual"}

​	声明Test01测试类，并在main方法中，创建2个员工对象，并为属性赋值，并打印两个员工的信息。
{: id="20210309203838-fr5306n"}

![1558849379468](imgs/1558849379468.png)
{: id="20210309203838-w5x89iw"}

## 第2题
{: id="20210309203838-yekb2uk"}

案例：
{: id="20210309203838-188xnp4"}

​	声明一个日期类MyDate，包含属性：年、月、日
{: id="20210309203838-xgmpm0o"}

​	声明一个Test02测试类，并在main方法中，创建3个日期对象，一个是你的出生日期，一个是来尚硅谷的日期，一个是毕业的日期，并打印显示
{: id="20210309203838-kaz7ulk"}

## 第3题
{: id="20210309203838-yjzxwyq"}

案例：
{: id="20210309203838-o3zayoz"}

​	声明公民类Citizen，包含属性：姓名，生日，身份证号，其中姓名是String类型，生日是MyDate类型，身份证号也是String类型。
{: id="20210309203838-ap066xx"}

​	声明Test03测试类，在main方法中创建你们家庭成员的几个对象，并打印信息。
{: id="20210309203838-forqy99"}

# 成员方法基础练习
{: id="20210309203838-mngcl06"}

## 第4题
{: id="20210309203838-75tgiad"}

案例：
{: id="20210309203838-x7xukom"}

​	声明一个日期类MyDate，包含属性：年、月、日，并在MyDate类中声明几个方法：
{: id="20210309203838-psa77rf"}

1、boolean isLeapYear()：判断当前日期的是闰年吗？
{: id="20210309203838-l05zq62"}

2、void set(int y, int m, int d)：修改年，月，日为新日期
{: id="20210309203838-01gh9ss"}

3、void puls(int years, int months, int days)：加上years年，months月，days天后的日期
{: id="20210309203838-nbwlpv3"}

​	并在测试类Test04的main方法中创建对象，并调用测试
{: id="20210309203838-umtms09"}

## 第5题
{: id="20210309203838-wu9kxe1"}

案例：
{: id="20210309203838-ik73nsn"}

​	声明一个三角形类Triangle，包含属性：a,b,c，表示三条边，包含几个方法：
{: id="20210309203838-36yrt77"}

1、boolean  isRightTriangle()：判断是否是一个直角三角形
{: id="20210309203838-shdebp9"}

2、boolean isIsoscelesTriangle()：判断是否是一个等腰三角形
{: id="20210309203838-yxktgmp"}

3、boolean isEquilateralTriangle()：判断是否是一个等边三角形
{: id="20210309203838-adwz481"}

4、double getArea()：根据三条边，用海伦公式求面积
{: id="20210309203838-sonhrc2"}

5、double getLength()：求周长
{: id="20210309203838-mep4rxg"}

​	并在测试类Test05的main方法中调用测试
{: id="20210309203838-fpki727"}

## 第6题
{: id="20210309203838-65se94k"}

案例：
{: id="20210309203838-xzn7o22"}

​	声明一个数学计算工具类MathTools，包含如下方法：
{: id="20210309203838-hylnul3"}

1、int add(int a, int b)：求a+b
{: id="20210309203838-dwc3f9d"}

2、int subtract(int a,int b)：求a-b
{: id="20210309203838-qe6s2on"}

3、int mutiply(int a, int b)：求a*b
{: id="20210309203838-1g91vd5"}

4、int divide(int a, int b)：求a/b
{: id="20210309203838-kqqy6w8"}

5、int remainder(int a, int b)：求a%b
{: id="20210309203838-std7uy9"}

6、int max(int a, int b)：求a和b中的最大值
{: id="20210309203838-2b6ua0f"}

7、int min(int a, int b)：求a和b中的最小值
{: id="20210309203838-xybwmo7"}

8、boolean equals(int a, int b)：判断a和b是否相等
{: id="20210309203838-oewzan5"}

9、boolean isEven(int a)：判断a是否是偶数
{: id="20210309203838-0hccyii"}

10、boolean isPrimeNumer(int a)：判断a是否是素数
{: id="20210309203838-7oudodp"}

11、int round(double d)：返回d的四舍五入后的整数值
{: id="20210309203838-rvgfv0n"}

​	声明一个Test06测试类，并在main方法中调用测试
{: id="20210309203838-b3y2ac4"}

## 第7题
{: id="20210309203838-w3si4c7"}

案例：
{: id="20210309203838-60zbr05"}

​	声明一个数组管理工具类MyArrays，包含如下方法：
{: id="20210309203838-kqfuvjs"}

1、void sort(int[] arr)：可以为任意一维整型数组arr实现从小到大排序
{: id="20210309203838-wle138z"}

2、int indexOf(int[] arr, int value)：可以在任意一维整型数组arr中查找value值的下标，如果不存在返回-1
{: id="20210309203838-nki7u7c"}

3、int[] copy(int[] arr, int len)：可以实现从任意一维数组arr中复制一个新数组返回，新数组的长度为len，从arr[0]开始复制
{: id="20210309203838-b56nqhs"}

​	声明一个Test07测试类，并在main方法中调用测试
{: id="20210309203838-qy62561"}

## 第8题
{: id="20210309203838-wtwga1i"}

案例：
{: id="20210309203838-hresd84"}

​	声明一个常识工具类DateCommonsTools，包含如下方法：
{: id="20210309203838-7xldme4"}

1、String getWeekName(int week)：根据星期值，返回对应的英语单词
{: id="20210309203838-cbjy6e5"}

2、String getMonthName(int month)：根据月份值，返回对应的英语单词
{: id="20210309203838-kh8e1i9"}

3、int getTotalDaysOfMonth(int year, int month)：返回某年某月的总天数
{: id="20210309203838-7pfoe07"}

4、int getTotalDaysOfYear(int year)：获取某年的总天数
{: id="20210309203838-4xgu34w"}

5、boolean isLeapYear(int year)：判断某年是否是闰年
{: id="20210309203838-rsg3vzx"}

​	声明一个Test08测试类，并在main方法中调用测试
{: id="20210309203838-lkot5cb"}


{: id="20210309203838-gfwd6yv" type="doc"}
