# String类

## 增

### 字符串的拼接

字符串直接拼接产生大量对象，产生不必要消耗

一般使用StringBuilder

```java
String a="hello world";
String b="world hello!";
String c=a+b;
// StringBuilder
```

### 字符串转数组

```java
// 将字符串变成char型数组
word.toCharArray();
// 指定字符分割成String数组
word.split(" ");
```



### 字符串插值

insert在索引前面添加字符串

```java
StringBuffer stringBuilder1=new StringBuffer("20180918");
stringBuilder1.insert(6,"-");
stringBuilder1.insert(4,"-");
```

### 字符串追加

```java
StringBuffer stringBuilder1=new StringBuffer("20180918");
stringBuilder1.append("aa")
    .append("bb")
    .append("cc");
```



## 删

### 除去字符串的空白字符

```java
// 除去字符串的空白字符
word.trim();
// 移除末尾空白符（可以移除中文空格）
word.strip();
// 移除开始空白符
word.stripLeading();
// 移除末尾空白符（非中文空白符）
word.stripTrailing();
```



## 查

### 获取字符串长度

```java
word.length();
```



### 字符串比较

```java
String str1 = "Hello World";
String str2 = "Hello World";
//因为字符串实现了compare接口，所以能比较对象
str1.compareTo(str2)
//忽略大小写
str1.compareToIgnoreCase(str3)
```

### 字符串查找

```java
// 返回索引的char
word.charAt(0);
// 查找第一次出现的索引
str1.indexOf("o");
// 查找字符串最后一次出现的索引
str1.lastIndexOf("o");
// 从指定位置起查找
str1.indexOf("o",3);
str1.lastIndexOf("e",15);
// 查找第2次出现的索引
str1.indexOf("o",str1.indexOf("o",3));// n次嵌套
// 查找两索引间的字符串（左闭又开）
str1.substring(0, 5);
// 查找从某位置到末尾的字符串
str1.substring(6);

```

### 字符串匹配

```java
// 是否以字符串开头
word.startsWith("hel");
// 是否以字符串结尾
word.endsWith("ld!");
// 在第二个参数指定位置开始字符串是否以第一个参数开始
word.startsWith("llo",2);
```

### 字符串比较

```java
// 比较相等
word.equals("hello world!"); // 考虑大小写
word.equalsIgnoreCase("hello world!"); // 忽略
word.toUpperCase().equals("hEllO wOrld!".toUpperCase())
// 比较大小
str1.compareTo(str2);
```



### 

## 改

### 字符串替换

```java
str1.replace("o", "h");
str1.replaceAll("o", "h");// 替换全部
str1.replaceFirst("o", "h");// 替换出现的第一个
```



### 字符串反转

```java
new StringBuffer(str1).reverse()
```

### 字符串分割

```java
String [] temp = str1.split("\\ ");
```



### 字符串大小写

```java
str1.toUpperCase();
str1.toLowerCase();
```

### 字符串删除

```java
new StringBuffer delete(int start,int end);
```



## 转

字符串和其它数据类型的转换

### 基本数据类型和字符串的转换

```java
int a=1;  a+"";
String b=String.valueOf(a);
```

## 格式化

####  格式化匹配表

![image-20210316165759326](https://gitee.com/Mryang_bast/typera/raw/master/java_imgs/image-20210316165759326.png)

## 正则

### 正则应用方法

#### 匹配

boolean matchs(正则表达式)：判断当前字符串是否匹配某个正则表达式

#### 替换

String replace(xx,xx)：不支持正则

String replaceFirst(正则，value)：替换第一个匹配部分

String repalceAll(正则， value)：替换所有匹配部分

#### 拆分

String[] split(正则)：按照某种规则进行拆分



### 常用正则表达式：

####  符类

`[abc]`：`a`、`b` 或 `c`（简单类）

`[^abc]`：任何字符，除了 `a`、`b` 或 `c`（否定）

`[a-zA-Z]`：`a` 到 `z` 或 `A` 到 `Z`，两头的字母包括在内（范围）

#### 预定义字符类

`.`：任何字符（与[行结束符](#lt)可能匹配也可能不匹配）

`\d`：数字：`[0-9]`

`\D`：非数字： `[^0-9]`

`\s`：空白字符：`[ \t\n\x0B\f\r]`

`\S`：非空白字符：`[^\s]`

`\w`：单词字符：`[a-zA-Z_0-9]`

`\W`：非单词字符：`[^\w]`

#### POSIX 字符类（仅 US-ASCII）

``\p{Lower} ``小写字母字符：[a-z]

``\p{Upper} ``大写字母字符：[A-Z]

``\p{ASCII} ``所有 ASCII：[\x00-\x7F]

``\p{Alpha} ``字母字符：[\p{Lower}\p{Upper}]

``\p{Digit}`` 十进制数字：[0-9]

``\p{Alnum} ``字母数字字符：[\p{Alpha}\p{Digit}]

``\p{Punct}`` 标点符号：!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~

``\p{Blank}`` 空格或制表符：[ \t]

#### 边界匹配器

`^`：行的开头

`$`：行的结尾

#### Greedy 数量词

*X*`?`：*X*，一次或一次也没有

*X*`*`：*X*，零次或多次

*X*`+`：*X*，一次或多次

*X*`{`*n*`}`：*X*，恰好 *n* 次

*X*`{`*n*`,}`：*X*，至少 *n* 次

*X*`{`*n*`,`*m*`}`：*X*，至少 *n* 次，但是不超过 *m* 次

#### Logical 运算符

*XY*：*X* 后跟 *Y*

*X*`|`*Y*：*X* 或 *Y*

`(`*X*`)`：X，作为捕获组

#### 特殊构造（非捕获）

(?:X) X，作为非捕获组

(?=X) X，通过零宽度的正 lookahead

(?!X) X，通过零宽度的负 lookahead

(?<=X) X，通过零宽度的正 lookbehind

(?<!X) X，通过零宽度的负 lookbehind

(?>X) X，作为独立的非捕获组

#### 常见应用

1.验证用户名和密码，要求第一个字必须为字母，一共6~16位字母数字下划线组成：**（^[a-zA-Z]\w{5,15}$）**

2.验证电话号码：xxx/xxxx-xxxxxxx/xxxxxxxx：**（^(\d{3,4}-)\d{7,8}$）**

3.验证手机号码：**( ^(13[0-9]|14[5|7]|15[0|1|2|3|5|6|7|8|9]|18[0|1|2|3|5|6|7|8|9])\d{8}$ )**

4.验证身份证号： **(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)**

5.验证Email地址：**(^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$)**

6.只能输入由数字和26个英文字母组成的字符串：**(^[A-Za-z0-9]+$)**

7.整数或者小数：**(^[0-9]+(\.\[0-9\]+){0,1}$)**

8.中文字符的正则表达式：**([\u4e00-\u9fa5])**

9.金额校验(非零开头的最多带两位小数的数字)：**(^(\[1-9\][0-9]*)+(.[0-9]{1,2})?$)**

10.IPV4地址：**(((\\d{1,2})|(1\\d{1,2})|(2[0-4]\\d)|(25[0-5]))\\.){3}((\\d{1,2})|(1\\d{1,2})|(2[0-4]\\d)|(25[0-5]))**