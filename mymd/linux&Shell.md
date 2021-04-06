

# Linux基础

## vim

```shell
#一般模式
	# 复制一行多行 yy ydy
	# 删除一行多行 dd d2d
	# 撤销 u
	# 粘贴 p
	# 复制一个字 yw
	# 向后删除一个词 x
	#向前删 X
	
	# 移动到行头 shift+^
	# 移动到行位 shift+$


#编辑模式
	# aoi
	# 当前位置 i
	# 当前单词后 a
	# 当前行后一行 o
	# AOI
	# 当前行头 I
	# 行前行尾 A
	# 上一行 O
	
#命令模式
	# set su /nosu 显示行号、取消显示
	# nohl 取消高亮
	#/搜索 u下一个词 U上一个词
```



## 文件类

目录层级

```shell
./
../
../../
```



```shell
#cd
相对绝对路径 cd opt || cd /opt
上一步操作位置 cd -
家目录 cd ~
跳转链接目录源目录 cd -P
```

```shell
#ls
查看所有文件目录 ls -a
查看详细信息 ls -l 
综合显示 ls-al
```

```shell
#mkdir/deldir
mkdir 【-P】 多级目录
deldir 删除目录

#pwd
显示当前目录 pwd

#创建文件
touch vim

#复制文件目录
cp -r 原 新
cp -r 原 /. 当前目录

#移除文件目录
rm -rfv 目录/文件

#移动文件目录重命名
mv /目录或文件 移动到的目录
-f 覆盖不提示
mv 文件或目录 新名


#查看文件
cat -n
more
#打印
echo -e 使用\符匹配模式

# 打印头尾
head -n
tail -n/-f f实时显示追加

#文件插入内容
ls -l > mytest.txt  覆盖
ls -l >> mytest.txt  追加

#路径目录名和文件名
dirname
basename
```





## 时间类

```shell
#date当前时间
#date -s 设置时间
#date -d ‘1 day ago’
```



## 用户管理

```shell
#增加用户
useradd atguigu 普通创建
useradd -g 1001 atguigu 将atguigu用户放到1001组
passwd atguigu

#查看用户
id atguigu

#查看所有用户
cat /etc/passwd

#切换用户
su
切用户并获取环境变量 su - atguigu
每个用户是一个进程，不exit退出用户进程一直会存在

#删除用户
userdel

#查看登录信息
whoami 当前用户
who am i 系统的登录用户

#修改用户
usermod -g 新组名 用户 


# 借用root权限
sudo
visudo默认编辑的是/etc/sudoers 权限是440的文件可以用visudo编辑
visudo是安全的，语法错误编辑会失败
```



## 用户组管理

```shell
#增加删除组
groupadd
groupdel
#修改组名
groupmod 新组名 老组名
#查看所有组
cat /etc/group
```



## 文件权限

```shell
#第一位 文件类型组 d目录 -文件 l链接 
#2-4位 所有者组 rwx u
#5-7位 root组 rwx g
#8-10位 其他用户组 rwx o
#2-10位 a
#文件能否被操作，取决于上一级文件夹权限 和 当前文件用户/用户组的权限

#更改文件权限
-R 递归全修改
chmod a+rwx 文件或目录

#更改文件、目录所有者
-R 递归全修改
chown 777 文件或目录
chown 最终用户 文件目录
chown 组名:用户名 文件目录
```



## 搜索类

搜索 遍历 类都可使用正则

```shell
#find 查找匹配 
-name
-user
-group
-size kb为最小单位
-type TYPE:
    f: 普通文件
    d: 目录文件
    l: 符号链接文件
    s：套接字文件
    b: 块设备文件
    c: 字符设备文件
    p: 管道文件   
#--------------------------------
find ~ $HOME目录下的文件
find . 当前目录
find / 根目录
#grep 筛选
-n显示行号
-v过滤去掉 不包含

#which 查看命令路径
which 命令

#搜索匹配符
#grep/set/awk
#grep
. 匹配代表一个字符 grep -n a.a test.txt
* 匹配1或任意个重复*前面的字符 
	grep -n a*a mytest02.txt 匹配a字符
    grep -n aa*a mytest02.txt 匹配aa字符
    grep -n aba*a mytest02.txt 匹配ab中的任意字符
    grep -n a...a mytest02.txt 匹配a和a中间三个任意字符
    grep -n a.*c mytest02.txt 匹配a和c中间任意字符
.* 匹配0个或任意字符
```



## 解压/压缩

```shell
#zip/unzip
zip -r 压缩目录
unzip -d 解压到指定目录
#gzip/gunzip
压缩解压gz文件
#tar
	-z 打包同时压缩
	-f 指定压缩后的文件名
	-v 显示详细信息
	-c 生成tar包
	-x 解压tar包
```

## 远程分发指令

```shell
#scp （secure copy）
之前都是sudo scp /opt/hello.txt atguigu@hadoop103:/opt/
也可以：sudo scp /opt/hello.txt hadoop103:/opt/
#	rsync
主要用于备份和镜像，速度快，只对差异文件更新。
sudo rsync -av hadoop hadoop:/opt/
```





## 自定义命令

```shell
#alias
alias显示所有别名
#创建别名
alias l.='ls -d .* --color=auto'
#删除别名
unalias  别名  
#使用原生的命令不用别名
\cp就是原生cp 不是别名的cp -i
```





## 进程管理



```shell
#查看进程 ps
-aux 全部
-ef 父子进程
#杀死进程 kill
kill -9
#查看进程树 pstree
-p显示进程号
-u显示所属用户
```



## 磁盘

```shell
# 查看磁盘详细信息 df -h
```

# Shell编程

## 变量

```shell
#特殊变量 --脚本专用
-$n 1-9
-$# 参数个数
----------------------
-$* 参数作为整体 无法迭代---/""包括
-$@ 逐个参数列表 可迭代　--/如果不包括两种写法都是逐个参数列表
----------------------
-$? 状态码 上个程序运行状态 0正确 1错误
```

$*和$@区别

![$*和$@区别](https://gitee.com/Mryang_bast/typera/raw/master/linux_imgs/20210404172309.png)

## 运算符

```shell
#算数运算符 + - \* / % 
a=1
b=2
echo $[$a+$b]
echo $(($a+$b))
#逻辑运算符 && ||
```



## 条件语句

```shell
#条件
数值比较
	-= 比较字符串时候相同
	-eq 数值相同
	-lt 小于
	-le 小于等于
	-gt 大于
	-ge 大于等于
	-ne 不等于
	---------
	a=5
	[ a -lt 6 ]
权限比较
	-r
	-w
	-x
	---------
	[ -x a.sh ]
文件类型比较
	-f 文件
	-d 目录
	-e 存在
	----------
	[ -e /opt/module ]
```



## 循环判断语句

循环语句：

- break：跳出整个循环
- exit：跳出脚本
- continue：跳出本次循环，接着执行下一次循环

```shell
# if语句
if [ 条件 ]
then
elif [  ]
then
fi

# case语句
case $变量名 in

"值")
	...
	;;
"值")
	...
	;;
*)
	...
	;;
esac
```

```shell
#for循环
for i in “file1” “file2” “file3”
for i in $(seq -w 10) --》等宽的01-10
for i in {1…10}
for i in $( ls )  从流获取
for I in $(<                                                                             file)
for i in “$@” --》取所有位置参数，可简写为for i

----------------------
--基本写法
for ((i=1;i<10;++1))//i++

for ex in ex1,ex2,ex3

----------------------
--迭代参数
for ex in "$@"
----------------------
--迭代0-9
for i in {0..9};
----------------------
--迭代标准输出 
# 默认以空格分隔
for i in $(cat /root/users.txt)
```





## read读取控制台

```shell

```



## 函数

```shell
# 基本结构
[ function ] 函数名[()]
{
	# 如何给函数传参?

	if [ $#=0 ] | [ $# -lt 2 ] then
		echo "请输入两个数值参数"
		exit
	elif [ $# -ge 2 ] then 
		echo $[$1+$2]
	#----------------------
	[return 0-255]  #return的是状态码
	
}
# 使用注意：
	-函数function和()不能同时省略
	-参数是由$n传递的
	-return可省略
	-return返回的是状态码0-255
```



## shell工具四剑客

### cut



### sed

sed是一种流编辑器，它一次处理一行内容。

```shell
#sed 文本操作
sed -n打印模式 默认
sed -i修改模式
-p打印行
	sed -n 'p' echoPath.list # 全部
    sed -n '3p' echoPath.list # 打印文件第三行
    sed -n '3!p' echoPath.list # 打印文件除了第三行
-a追加行
	sed '1,4a 123' # 1-4行后面追加123
	#文件最后追加并打印文件 \代表行开头之后有空格也会被输入
	sed '$a \ aa:123 \n bb:123' echoPath.list
-i插入行
	sed '5i 123' aa.txt # 5行前插入 
-c替换行
	sed '5c 123' aa.txt # 第五行替换成123
	sed '1,5c 123' aa.txt # 1-5行替换成123
-d删除行
-s替换字符串 类似vim的用法
	sed 's/aa/bb' aa.text # 每行第一个
	sed 's/aa/bb/g' aa.txt # 全部

```



### awk

文本分析工具，把文件逐行的读入

```shell
#awk 行列可迭代文本操作
#基本语法

#三种简单格式分别是：
    awk 'pattern' filename
    awk '{action}' filename
    awk 'pattern {action}' filename
    #多条条件顺序执行，非阻塞
    awk 'pattern{action}  pattern1{action1} ...' filename
    
#BEGIN{}{} END{} 处理数据前执行begin 处理完执行end
	awk [-F|-f] 'BEGIN{}{command1; command2} END{}' filename
	- [-F|-f]      大参数，-F指定分隔符，-f调用脚本
    - ' '          引用代码块
    - //           匹配代码块，可以是字符串或正则表达式
    - {}           命令代码块，包含一条或多条命令
    - ;            多条命令使用分号分隔
    cat /etc/passwd|awk -F: 'BEGIN{SUM=0} /^a/{print;sum+=$3} END{print sum}'
参数
	-F
	-v 定义一个用户变量 和变量定义在begin里没区别
#内置变量
    - $0:表示整个当前行
    - $1:表示每行第一个字段
    - $2:表示每行第二个字段
    ....以此类推
    - NR:每行的记录号(行号) num record
    - NF:每行的字段数 num field
    - FILENAME:正在处理的文件名

    awk -F '=' '{if($1!='user')print $1,$2,
        "行号:"NR,"文件名:" FILENAME,
        "字段数:" "NF","User:"1,
        "hah:" "dog"}' ./echoPath.list
    输出||-------------------------------------------------------------
    shell  $SHELL 行号:1 文件名:./echoPath.list 字段数:NF User:1 hah:dog
    pwd  $PWD 行号:2 文件名:./echoPath.list 字段数:NF User:1 hah:dog
    home  $HOME 行号:3 文件名:./echoPath.list 字段数:NF User:1 hah:dog
    user  $USER 行号:4 文件名:./echoPath.list 字段数:NF User:1 hah:dog
#-----
#内置函数
    print()
    printf()
    getline()

#F指定分隔符
awk -F '=' '{print $1,$2}' ./echoPath.list #打印出符合分隔符的元素
#拿到ifconfig的ip地址
ifconfig|grep 'inet'|grep 'bro'|awk '{print($2)}'
#遍历文件

#匹配操作符（~） 对记录或字段的表达式进行匹配。例如，找出当前目录下文件所有者为atguigu的文件：
ll|awk '$3~/atguigu/{print}'
```

```shell
#awk的正则
1）正则放在pattem位置
2）正则放在/gexp/的中间
3）遇到符号冲突使用转义符\
正则元字符语法
	-^ 开头 /^a/
	-$ 末尾 /L$/
	-. 一个字符
	-* 0个及以上前置字符
	-+ 1个及以上前置字符
	-? 0或1个前置字符
	-[ABC] ABC任意字符
	-[^ABC] 非任何ABC字符
	-[a-z]
	-a|b a或b
	-(ab) 匹配ab组合 可接*+？
	-\转义
	-& 替代
```



### sort

它将文件进行排序，并将排序结果标准输出。

```shell
#sort文件排序
-n	依照数值的大小排序
-r	以相反的顺序来排序
-t	设置排序时所用的分隔字符
-k	指定需要排序的列
```



### xargs

```shell
#xargs 标准输出作为参数 
#基础语法
xargs [选项] [被执行命令] [被执行命令初始化参数]
	-n 1 逐行传入
	-1.将标准输入中的空白符(空格、TAB、换行符)替换成空格，多个连续的空白符只替换成一个；
	-2.将替换后的标准输入内容，按空格切割成多个小块；
	-3.将切割后小块参数，按指定个数(-n选项)依次传递给被执行命令作为参数。
```

