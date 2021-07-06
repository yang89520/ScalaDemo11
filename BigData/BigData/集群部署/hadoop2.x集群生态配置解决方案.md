**大数据环境安装和配置（Hadoop2.7.7，Hive2.3.4，Zookeeper3.4.10，Kafka2.1.0，Flume1.8.0，Hbase2.1.1，Spark2.4.0等）**

# 前言

本篇文章是以Hadoop为基础，搭建各种可能会用到的环境的基本步骤，包括：Hadoop，Hive，Zookeeper，Kafka，Flume，Hbase，Spark等。在实际应用中可能未必需要用到所有的这些，请读者们按需取舍。
注意：因为有些环境之间存在相互依赖，所以在搭建环境或者使用其的过程中要注意顺序。比如说Hive是依赖于Hadoop的，搭建使用Hive前，Hadoop集群肯定要提前搭建好并启动起来；搭建使用Hbase时，由于其依赖于Hadoop和Zookeeper，所以需要提前搭建并启动好Hadoop和ZooKeeper集群。
本篇文章搭建时涉及的安装包都下载好放入百度云
（ 百度云链接[https://pan.baidu.com/s/1jKgua2U1yacbrbgQk4-wFg](https://pan.baidu.com/s/1jKgua2U1yacbrbgQk4-wFg) 提取码：r93h）


# 系统说明
系统：CentOS 7.6
节点信息：

| 节点 | ip |
| --- | --- |
| master | 192.168.185.150 |
| slave1 | 192.168.185.151 |
| slave2 | 192.168.185.152 |

# 搭建步骤详述
## 一、节点基础配置
### 1、配置各节点网络
```shell
# 注意：centos自从7版本以后网卡名变成ens33而不是我这里的eth0了，我是习惯eth0了所以在安装的时候修改了网卡名，如果你的centos网卡名是ens33不要紧，就把我这里eth0的地方都换成你的ens33，对后面没影响。
# 注意：centos自从7版本以后网卡名变成ens33而不是我这里的eth0了，我是习惯eth0了所以在安装的时候修改了网卡名，如果你的centos网卡名是ens33不要紧，就把我这里eth0的地方都换成你的ens33，对后面没影响。
[root@master ~]# vim /etc/sysconfig/network-scripts/ifcfg-eth0
TYPE="Ethernet"
BOOTPROTO="static"
NAME="eth0"
DEVICE="eth0"
ONBOOT="yes"
IPADDR=192.168.185.150
NETMASK=255.255.255.0
GATEWAY=192.168.185.2
[root@master ~]# vim /etc/resolv.conf
nameserver 192.168.185.2
# 对其他两个slave节点也同样做上述操作，只不过在IPADDR值不一样，分别填其节点对应的ip
```
### 2、修改每个节点主机名，添加各节点映射

```shell
# 在其他两个子节点的hostname处分别填slave1和slave2
[root@master ~]# vim /etc/hostname
master
[root@master ~]# vim /etc/hosts
192.168.185.150 master
192.168.185.151 slave1
192.168.185.152 slave2
```
### 3、关闭防火墙

```shell
# 三个节点都要做
# 把SELINUX那值设为disabled
[root@master ~]# vim /etc/selinux/config
SELINUX=disabled
[root@master ~]# systemctl stop firewalld
[root@master ~]# systemctl disable firewalld
[root@master ~]# systemctl status firewalld
```
### 4、都重启以生效
```shell
[root@master ~]# reboot
[root@master ~]# ping www.baidu.com
# 注意下，重启后若ping百度不通，可能是因为namesever那重启后自动被改了，所以导致ping百度不通，如果这样的话就再重新写下上面的resolv.conf
[root@master ~]# vim /etc/resolv.conf
nameserver 192.168.185.2
# 这下应该就通了,ping下百度试试看
[root@master ~]# ping www.baidu.com
PING www.a.shifen.com (119.75.217.109) 56(84) bytes of data.
64 bytes from 119.75.217.109: icmp_seq=1 ttl=128 time=30.6 ms
64 bytes from 119.75.217.109: icmp_seq=2 ttl=128 time=30.9 ms
64 bytes from 119.75.217.109: icmp_seq=3 ttl=128 time=30.9 ms
```
### 5、配置节点间ssh免密登陆
```shell
[root@master ~]# ssh-keygen -t rsa
# 上面这条命令，遇到什么都别管，一路回车键敲下去
# 拷贝本密钥到三个节点上
[root@master ~]# ssh-copy-id master
[root@master ~]# ssh-copy-id slave1
[root@master ~]# ssh-copy-id slave2
# master节点上做完后，再在其他两个节点上重复上述操作
都做完后，用ssh命令节点间相互测试下：
[root@master ~]# ssh slave1
# 就会发现在master节点上免密登陆到了slave1，再敲logout就退出slave1了
```
### 6、安装java

```shell
# 之后我们所有的环境配置包都放到/usr/local/下
# 新建java目录，把下载好的jdk的二进制包拷到下面（你可以直接在centos里下载，或者在你主机下载好，上传到虚拟机的centos上）
[root@master ~]# cd /usr/local
[root@master local]# mkdir java
[root@master local]# cd java
[root@master java]# tar -zxvf jdk-8u191-linux-x64.tar.gz 
# 配置环境变量，在profile文件最后添加java的环境变量
[root@master ~]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
[root@master ~]# source /etc/profile
[root@master ~]# java -version
java version "1.8.0_191"
Java(TM) SE Runtime Environment (build 1.8.0_191-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)
# 在其他两个节点上重复上述操作
到此为止，基本配置就结束了。
```
## 二、Hadoop安装和配置
### 介绍
Hadoop是一个由Apache基金会所开发的分布式系统基础架构。Hadoop的框架最核心的设计就是：HDFS和MapReduce。HDFS为海量的数据提供了存储，而MapReduce则为海量的数据提供了计算。
HDFS，Hadoop Distributed File System，是一个分布式文件系统，用来存储 Hadoop 集群中所有存储节点上的文件，包含一个 NameNode 和大量 DataNode。NameNode，它在 HDFS 内部提供元数据服务，负责管理文件系统名称空间和控制外部客户机的访问，决定是否将文件映射到 DataNode 上。DataNode，它为 HDFS 提供存储块，响应来自 HDFS 客户机的读写请求。
MapReduce是一种编程模型，用于大规模数据集的并行运算。概念"Map（映射）“和"Reduce（归约）”，是它们的主要思想，即指定一个Map（映射）函数，用来把一组键值对映射成一组新的键值对，指定并发的Reduce（归约）函数，用来保证所有映射的键值对中的每一个共享相同的键组。
### 1、下载解压

```shell
# 在/usr/local下创建hadoop文件夹，将下载好的hadoop-2.7.7压缩包上传进去解压
[root@master ~]# cd /usr/local
[root@master local]# mkdir hadoop
[root@master local]# cd hadoop
[root@master hadoop]# tar -zxvf hadoop-2.7.7.tar
```
### 2、配置环境变量
```shell
[root@master hadoop]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
[root@master hadoop]# source /etc/profile
```
### 3、 配置core-site.xml
```shell
# 配置文件主要在hadoop-2.7.7/etc/hadoop下面
[root@master hadoop]# cd hadoop-2.7.7/etc/hadoop
# 把该文件<configuration>那块按如下修改
[root@master hadoop]# vim core-site.xml
<configuration>
<property>
  <name>fs.defaultFS</name>
  <value>hdfs://master:9000</value>
</property>
<property>
  <name>hadoop.tmp.dir</name>
  <value>/usr/local/data</value>
</property>
</configuration>
# 配置文件中的/usr/local/data是用来存储临时文件的，所以该文件夹需要手动创建
[root@master hadoop]# mkdir /usr/local/data
```
### 4、配置hdfs-site.xml
```shell
[root@master hadoop]# vim hdfs-site.xml
<configuration>
<property>
  <name>dfs.name.dir</name>
  <value>/usr/local/data/namenode</value>
</property>
<property>
  <name>dfs.data.dir</name>
  <value>/usr/local/data/datanode</value>
</property>
<property>
  <name>dfs.replication</name>
  <value>2</value>
</property>
</configuration>
```
### 5、配置mapred-site.xml
```shell
# 先修改文件名字
[root@master hadoop]# mv mapred-site.xml.template mapred-site.xml
[root@master hadoop]# vim mapred-site.xml
<configuration>
<property>
  <name>mapreduce.framework.name</name>
  <value>yarn</value>
</property>
</configuration>
```
### 6、配置yarn-site.xml
```shell
[root@master hadoop]# vim yarn-site.xml
<configuration>
<!-- Site specific YARN configuration properties -->
<property>
  <name>yarn.resourcemanager.hostname</name>
  <value>master</value>
</property>
<property>
  <name>yarn.nodemanager.aux-services</name>              
  <value>mapreduce_shuffle</value>     
</property>
</configuration>
```
### 7、修改slaves
```shell
[root@master hadoop]# vim slaves
slave1
slave2
```
### 8、修改hadoop-env.sh文件

```shell
# 在“export JAVA_HOME=”那一行把java环境修改成自己的路径
[root@master hadoop]# vim hadoop-env.sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
```
### 9、直接把配置好的hadoop包传到剩下两个子节点同样的位置下
```shell
[root@master hadoop]# cd /usr/local
[root@master local]# scp -r hadoop root@192.168.185.151:/usr/local/
[root@master local]# scp -r hadoop root@192.168.185.152:/usr/local/
```
### 10、在其他两个子节点别漏掉的操作

```shell
# 别忘了！在两个子节点/usr/local/下也要创建好data目录。
# 别忘了！在两个子节点重复下步骤2， 配置好hadoop环境变量。
```
### 11、测试是否成功

```shell
# 只要在主节点上启动，执行过程可能稍慢，耐心等待
# 先格式化
[root@master ~]# hdfs namenode -format
# 启动hdfs
[root@master ~]# cd /usr/local/hadoop/hadoop-2.7.7/
[root@master hadoop-2.7.7]# sbin/start-dfs.sh
# 启动yarn
[root@master hadoop-2.7.7]# sbin/start-yarn.sh
```
在主节点上输入jps命令查看，以下就对了：
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617767211772-747eb527-909c-44ea-9864-9589687bb329.png#align=left&display=inline&height=78&margin=%5Bobject%20Object%5D&originHeight=78&originWidth=318&size=0&status=done&style=none&width=318)
在子节点上输入jps命令查看，以下就对了：
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617767207703-c8248348-ac5e-4e75-9bb4-f34682e7dab1.png#align=left&display=inline&height=65&margin=%5Bobject%20Object%5D&originHeight=65&originWidth=268&size=0&status=done&style=none&width=268)
在浏览器上访问可视化页面：[http://192.168.185.150:50070](http://192.168.185.150:50070)
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617767212417-192b2cd9-8863-4c40-b8e6-9824abdb5c84.png#align=left&display=inline&height=927&margin=%5Bobject%20Object%5D&originHeight=927&originWidth=1381&size=0&status=done&style=none&width=1381)
到此为止，hadoop配置就结束了。


## 三、Hive安装和配置
### 介绍
Hive是基于Hadoop的一个数据仓库工具，可以将结构化的数据文件映射为一张数据库表，并提供简单的sql查询功能，可以将sql语句转换为MapReduce任务进行运行。 其优点是学习成本低，可以通过和SQL类似的HiveQL语言快速实现简单的MapReduce统计,不必开发专门的MapReduce应用，十分适合数据仓库的统计分析。同时，这个语言也允许熟悉 MapReduce 开发者的开发自定义的 mapper 和 reducer 来处理内建的 mapper 和 reducer 无法完成的复杂的分析工作。
Hive 没有专门的数据格式。所有Hive 的数据都存储在Hadoop兼容的文件系统（例如HDFS）中。Hive 在加载数据过程中不会对数据进行任何的修改，只是将数据移动到HDFS中Hive 设定的目录下，因此，Hive 不支持对数据的改写和添加，所有的数据都是在加载的时候确定的。
### 1、环境配置

```shell
# 注意：Hive只需要在master节点上安装配置
[root@master ~]# cd /usr/local
[root@master local]# mkdir hive
[root@master local]# cd hive
[root@master hive]# tar -zxvf apache-hive-2.3.4-bin.tar.gz 
[root@master hive]# mv apache-hive-2.3.4-bin hive-2.3.4
# 添加Hive环境变量
[root@master hive]# vim /etc/profile        
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin
[root@master hive]# source /etc/profile
```
### 2、修改 hive-site.xml
```shell
[root@master hive]# cd hive-2.3.4/conf
[root@master conf]# mv hive-default.xml.template  hive-site.xml
# 在hive-site.xml中找到下面的几个对应name的property,然后把value值更改
# 这里提醒一下，因为hive-site.xml几千多行，根据name找property的话不太方便，有两种建议：
# 1、把这个xml文件弄到你自己的主机上，用软件（比如notepad++）修改好，在上传回centos上相应位置
# 2、在之前给你的百度云链接里，我也上传了修改好的hive-site.xml文件，如果你版本跟我用的一样，可以直接拿去用
[root@master conf]# vim hive-site.xml 
<property>
<name>javax.jdo.option.ConnectionURL</name>
<value>jdbc:mysql://master:3306/hive_metadata?createDatabaseIfNotExist=true</value>
<description>
   JDBC connect string for a JDBC metastore.
   To use SSL to encrypt/authenticate the connection, provide database-specific SSL flag in the connection URL.
   For example, jdbc:postgresql://myhost/db?ssl=true for postgres database.
</description>
</property>
<property>
<name>javax.jdo.option.ConnectionDriverName</name>
<value>com.mysql.jdbc.Driver</value>
<description>Driver class name for a JDBC metastore</description>
</property>
<property>
<name>javax.jdo.option.ConnectionUserName</name>
<value>hive</value>
<description>Username to use against metastore database</description>
</property>
<property>
<name>javax.jdo.option.ConnectionPassword</name>
<value>hive</value>
<description>password to use against metastore database</description>
</property>
<property>
<name>hive.querylog.location</name>
<value>/usr/local/hive/hive-2.3.4/tmp/hadoop</value>
<description>Location of Hive run time structured log file</description>
</property>
<property>
<name>hive.server2.logging.operation.log.location</name>
<value>/usr/local/hive/hive-2.3.4/tmp/hadoop/operation_logs</value>
<description>Top level directory where operation logs are stored if logging functionality is enabled</description>
</property>
<property>
<name>hive.exec.local.scratchdir</name>
<value>/usr/local/hive/hive-2.3.4/tmp/hadoop</value>
<description>Local scratch space for Hive jobs</description>
</property>
<property>
<name>hive.downloaded.resources.dir</name>
<value>/usr/local/hive/hive-2.3.4/tmp/${hive.session.id}_resources</value>
<description>Temporary local directory for added resources in the remote file system.</description>
</property>
<property>
<name>hive.metastore.schema.verification</name>
<value>false</value>
<description>
   Enforce metastore schema version consistency.
   True: Verify that version information stored in is compatible with one from Hive jars. Also disable automatic
      schema migration attempt. Users are required to manually migrate schema after Hive upgrade which ensures
      proper metastore schema migration. (Default)
   False: Warn if the version information stored in metastore doesn't match with one from in Hive jars.
</description>
</property>
```
### 3、修改hive-env.sh文件
```shell
[root@master conf]# mv hive-env.sh.template hive-env.sh
# 找到下面的位置，做对应修改
[root@master conf]# vim hive-env.sh 
# Set HADOOP_HOME to point to a specific hadoop install directory
HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
# Hive Configuration Directory can be controlled by:
export HIVE_CONF_DIR=/usr/local/hive/hive-2.3.4/conf
# Folder containing extra libraries required for hive compilation/execution can be controlled by:
# export HIVE_AUX_JARS_PATH=
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HIVE_HOME=/usr/local/hive/hive-2.3.4
```
### 4、把下载好的mysql-connector-java.jar这个jar包拷到/usr/local/hive/hive-2.3.4/lib/下面


### 5、安装并配置mysql（因为hive的元数据是存储在mysql里的）
```shell
[root@master ~]# cd /usr/local/src/
[root@master src]# wget http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
[root@master src]# rpm -ivh mysql-community-release-el7-5.noarch.rpm
[root@master src]# yum install mysql-community-server
# 这里时间较长，耐心等待...
# 安装完成后，重启服务
[root@master src]# service mysqld restart
[root@master src]# mysql
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.6.42 MySQL Community Server (GPL)
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective owners.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql>
# mysql安装成功
```
### 6、在mysql上创建hive元数据库，创建hive账号，并进行授权
```shell
# 在mysql上连续执行下述命令:
# create database if not exists hive_metadata;
# grant all privileges on hive_metadata.* to 'hive'@'%' identified by 'hive';
# grant all privileges on hive_metadata.* to 'hive'@'localhost' identified by 'hive';
# grant all privileges on hive_metadata.* to 'hive'@'master' identified by 'hive';
# flush privileges;
# use hive_metadata;
[root@master src]# mysql
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.6.42 MySQL Community Server (GPL)
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql> create database if not exists hive_metadata;
Query OK, 1 row affected (0.00 sec)
mysql> grant all privileges on hive_metadata.* to 'hive'@'%' identified by 'hive';
Query OK, 0 rows affected (0.00 sec)
mysql> grant all privileges on hive_metadata.* to 'hive'@'localhost' identified by 'hive';
Query OK, 0 rows affected (0.00 sec)
mysql> grant all privileges on hive_metadata.* to 'hive'@'master' identified by 'hive';
Query OK, 0 rows affected (0.00 sec)
mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)
mysql> use hive_metadata;
Database changed
mysql> exit
Bye
```
### 7、初始化
```shell
[root@master src]# schematool -dbType mysql -initSchema
```
### 8、测试验证hive
```shell
# 我们先创建一个txt文件存点数据等下导到hive中去
[root@master src]# vim users.txt
1,浙江工商大学
2,杭州
3,I love
4,ZJGSU
5,加油哦
# 进入hive，出现命令行就说明之前搭建是成功的
[root@master src]# hive
hive>
# 创建users表，这个row format delimited fields terminated by ','代表我们等下导过来的文件中字段是以逗号“，”分割字段的
# 所以我们上面users.txt不同字段中间有逗号
hive> create table users(id int, name string) row format delimited fields terminated by ',';
OK
Time taken: 7.29 seconds
# 导数据
hive> load data local inpath '/usr/local/src/users.txt' into table users;
Loading data to table default.users
OK
Time taken: 1.703 seconds
# 查询
hive> select * from users;
OK
1    浙江工商大学
2    杭州
3    I love
4    ZJGSU
5    加油哦
Time taken: 2.062 seconds, Fetched: 5 row(s)
# ok,测试成功！
```
到此为止，hive配置就结束了，其实hive的配置挺繁琐的，不要急慢慢来，加油！


## 四、ZooKeeper安装和配置
### 介绍
ZooKeeper是一个分布式的应用程序协调服务，是Hadoop和Hbase的重要组件。它是一个为分布式应用提供一致性服务的软件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。其目标就是封装好复杂易出错的关键服务，将简单易用的接口和性能高效、功能稳定的系统提供给用户。
那么Zookeeper能做什么事情呢？举个简单的例子：假设我们有20个搜索引擎的服务器(每个负责总索引中的一部分的搜索任务)和一个总服务器(负责向这20个搜索引擎的服务器发出搜索请求并合并结果集)，一个备用的总服务器(负责当总服务器宕机时替换总服务器)，一个web的cgi(向总服务器发出搜索请求)。搜索引擎的服务器中的15个服务器提供搜索服务，5个服务器正在生成索引。这20个搜索引擎的服务器经常要让正在提供搜索服务的服务器停止提供服务开始生成索引，或生成索引的服务器已经把索引生成完成可以提供搜索服务了。使用Zookeeper可以保证总服务器自动感知有多少提供搜索引擎的服务器并向这些服务器发出搜索请求，当总服务器宕机时自动启用备用的总服务器。


### 1、环境配置
```shell
[root@master local]# mkdir zookeeper
[root@master local]# cd zookeeper
# 将下载好的zookeeper压缩包上传进来解压
[root@master zookeeper]# tar -zxvf zookeeper-3.4.10.tar.gz 
# 配置zookeeper环境变量
[root@master zookeeper]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin
[root@master zookeeper]# source /etc/profile
```
### 2、配置zoo.cfg文件
```shell
[root@master zookeeper]# cd zookeeper-3.4.10/conf
[root@master conf]# mv zoo_sample.cfg zoo.cfg
# 把 dataDir 那一行修改成自己的地址，在文件最后再加上三行server的配置
[root@master conf]# vim zoo.cfg 
dataDir=/usr/local/zookeeper/zookeeper-3.4.10/data
server.0=master:2888:3888 
server.1=slave1:2888:3888 
server.2=slave2:2888:3888
```
### 3、配置myid文件
```shell
[root@master conf]# cd ..
[root@master zookeeper-3.4.10]# mkdir data
[root@master zookeeper-3.4.10]# cd data
[root@master data]# vim myid
```
### 4、配置另外两个节点
```shell
# 把上面配置好的zookeeper文件夹直接传到两个子节点
[root@master data]# cd ../../..
[root@master local]# scp -r zookeeper root@192.168.185.151:/usr/local/
[root@master local]# scp -r zookeeper root@192.168.185.152:/usr/local/
# 注意在两个子节点上把myid文件里面的 0 给分别替换成 1 和 2
# 注意在两个子节点上像步骤1一样，在/etc/profile文件里配置zookeeper的环境变量，保存后别忘source一下
```
### 5、测试一下
```shell
# 在三个节点上分别执行命令，启动服务： zkServer.sh start
# 在三个节点上分别执行命令，查看状态： zkServer.sh status 
# 正确结果应该是：三个节点中其中一个是leader，另外两个是follower
# 在三个节点上分别执行命令： jps
# 检查三个节点是否都有QuromPeerMain进程
```


到此为止，zookeeper配置就结束了，这个应该不难。


## 五、Kafka安装和配置
### 介绍
Kafka是一种高吞吐量的分布式发布订阅消息系统，它可以处理消费者规模的网站中的所有动作流数据。Producer即生产者，向Kafka集群发送消息，在发送消息之前，会对消息进行分类，即主题（Topic），通过对消息指定主题可以将消息分类，消费者可以只关注自己需要的Topic中的消息。Consumer，即消费者，消费者通过与kafka集群建立长连接的方式，不断地从集群中拉取消息，然后可以对这些消息进行处理。


### 1、安装Scala


Kafka由Scala和Java编写，所以我们先需要安装配置Scala：
```shell
[root@master ~]# cd /usr/local
[root@master local]# mkdir scala
[root@master local]# cd scala/
# 下载好的scala压缩包上传进去解压
[root@master scala]# tar -zxvf scala-2.11.8.tgz

# 配置环境变量
[root@master scala]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin:$SCALA_HOME/bin
[root@master scala]# source /etc/profile
# 验证
[root@master scala-2.11.8]# scala -version
Scala code runner version 2.11.8 -- Copyright 2002-2018, LAMP/EPFL and Lightbend, Inc.
# 然后在剩下两个子节点中重复上述步骤！
```
### 2、安装配置Kafka
```shell
# 创建目录，把下载好的压缩包上传解压
[root@master local]# mkdir kafka
[root@master local]# cd kafka
[root@master kafka]# tar -zxvf kafka_2.11-2.1.0.tgz 
[root@master kafka]# mv kafka_2.11-2.1.0 kafka-2.1.0
# 配置环境变量
[root@master kafka]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export KAFKA_HOME=/usr/local/kafka/kafka-2.1.0
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin:$KAFKA_HOME/bin:$SCALA_HOME/bin
[root@master kafka]# source /etc/profile
# 修改server.properties文件，找到对应的位置，修改如下
[root@master kafka]# vim kafka-2.1.0/config/server.properties
broker.id=0
listeners=PLAINTEXT://192.168.185.150:9092
advertised.listeners=PLAINTEXT://192.168.185.150:9092
zookeeper.connect=192.168.185.150:2181,192.168.185.151:2181,192.168.185.152:2181
# 把master节点上修改好的kafka整个文件夹传到其余两个子节点
[root@master kafka]# cd /usr/local
[root@master local]# scp -r kafka root@192.168.185.151:/usr/local/
[root@master local]# scp -r kafka root@192.168.185.152:/usr/local/
# 在另外两个节点上，对server.properties要有几处修改
# broker.id 分别修改成： 1 和 2
# listeners 在ip那里分别修改成子节点对应的，即 PLAINTEXT://192.168.185.151:9092 和 PLAINTEXT://192.168.185.152:9092
# advertised.listeners 也在ip那里分别修改成子节点对应的，即 PLAINTEXT://192.168.185.151:9092 和 PLAINTEXT://192.168.185.152:9092
# zookeeper.connect 不需要修改
# 另外两个节点上也别忘了配置kafka环境变量
```
### 3、测试
```shell
# 在三个节点都启动kafka
[root@master local]# cd kafka/kafka-2.1.0/
[root@master kafka-2.1.0]# nohup kafka-server-start.sh /usr/local/kafka/kafka-2.1.0/config/server.properties & 
# 在主节点上创建主题TestTopic
[root@master kafka-2.1.0]# kafka-topics.sh --zookeeper 192.168.185.150:2181,192.168.185.151:2181,192.168.185.152:2181 --topic TestTopic --replication-factor 1 --partitions 1 --create
# 在主节点上启动一个生产者
[root@master kafka-2.1.0]# kafka-console-producer.sh --broker-list 192.168.185.150:9092,192.168.185.151:9092,192.168.185.152:9092 --topic TestTopic
# 在其他两个节点上分别创建消费者
[root@slave1 kafka-2.1.0]# kafka-console-consumer.sh --bootstrap-server 192.168.185.151:9092 --topic TestTopic --from-beginning
[root@slave2 kafka-2.1.0]# kafka-console-consumer.sh --bootstrap-server 192.168.185.152:9092 --topic TestTopic --from-beginning
# 在主节点生产者命令行那里随便输入一段话：
> hello world
# 然后你就会发现在其他两个消费者节点那里也出现了这句话，即消费到了该数据
```


到此为止，kafka配置就结束了。


## 六、Flume安装和配置
### 介绍
Flume是Cloudera提供的一个高可用的，高可靠的，分布式的海量日志采集、聚合和传输的系统，Flume支持在日志系统中定制各类数据发送方，用于收集数据；同时，Flume提供对数据进行简单处理，并写到各种数据接受方（可定制）的能力。Flume提供了从console（控制台）、RPC（Thrift-RPC）、text（文件）、tail（UNIX tail）、syslog（syslog日志系统），支持TCP和UDP等2种模式），exec（命令执行）等数据源上收集数据的能力。
使用Flume，我们可以将从多个服务器中获取的数据迅速的移交给Hadoop中，可以高效率的将多个网站服务器中收集的日志信息存入HDFS/HBase中。


注意：flume只需要在主节点配置，不需要在其他节点配置


### 1、环境配置
```shell
# 创建目录，将下载好的压缩包上传并解压
[root@master local]# mkdir flume
[root@master local]# cd flume/
[root@master flume]# tar -zxvf apache-flume-1.8.0-bin.tar.gz
[root@master flume]# mv apache-flume-1.8.0-bin flume-1.8.0
# 环境变量
[root@master flume]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export KAFKA_HOME=/usr/local/kafka/kafka-2.1.0
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export FLUME_HOME=/usr/local/flume/flume-1.8.0
export FLUME_CONF_DIR=$FLUME_HOME/conf
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin:$KAFKA_HOME/bin:$SCALA_HOME/bin:$FLUME_HOME/bin
[root@master flume]# source /etc/profile
```
### 2、修改flume-conf.properties文件
```shell
[root@master flume]# cd flume-1.8.0/conf
[root@master conf]# mv flume-conf.properties.template flume-conf.properties
# 在文件最后加上下面的内容
[root@master conf]# vim flume-conf.properties 
#agent1表示代理名称
agent1.sources=source1
agent1.sinks=sink1
agent1.channels=channel1
#配置source1
agent1.sources.source1.type=spooldir
agent1.sources.source1.spoolDir=/usr/local/flume/logs
agent1.sources.source1.channels=channel1
agent1.sources.source1.fileHeader = false
agent1.sources.source1.interceptors = i1
agent1.sources.source1.interceptors.i1.type = timestamp
#配置channel1
agent1.channels.channel1.type=file
agent1.channels.channel1.checkpointDir=/usr/local/flume/logs_tmp_cp
agent1.channels.channel1.dataDirs=/usr/local/flume/logs_tmp
#配置sink1
agent1.sinks.sink1.type=hdfs
agent1.sinks.sink1.hdfs.path=hdfs://master:9000/logs
agent1.sinks.sink1.hdfs.fileType=DataStream
agent1.sinks.sink1.hdfs.writeFormat=TEXT
agent1.sinks.sink1.hdfs.rollInterval=1
agent1.sinks.sink1.channel=channel1
agent1.sinks.sink1.hdfs.filePrefix=%Y-%m-%d
# 我们看到上面的配置文件中代理 agent1.sources.source1.spoolDir 监听的文件夹是/usr/local/flume/logs，所以我们要手动创建一下
[root@master conf]# cd ../..
[root@master flume]# mkdir logs
# 上面的配置文件中 agent1.sinks.sink1.hdfs.path=hdfs://master:9000/logs下，即将监听到的/usr/local/flume/logs下的文件自动上传到hdfs的/logs下，所以我们要手动创建hdfs下的目录
[root@master flume]# hdfs dfs -mkdir /logs
```
### 3、测试
```shell
# 启动服务
[root@master flume]# flume-ng agent -n agent1 -c conf -f /usr/local/flume/flume-1.8.0/conf/flume-conf.properties -Dflume.root.logger=DEBUG,console
# 先看下hdfs的logs目录下，目前什么都没有
[root@master flume]# hdfs dfs -ls -R /
```
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617774336813-3778c8ee-5aff-4f45-a19c-6876a018bf2a.png#align=left&display=inline&height=41&margin=%5Bobject%20Object%5D&originHeight=41&originWidth=784&size=0&status=done&style=none&width=784)
```shell
# 我们在/usr/local/flume/logs随便创建个文件
[root@master flume]# cd logs
[root@master logs]# vim flume_test.txt
hello world !
guang
浙江工商大学
# 然后我们发现hdfs的logs下自动上传了我们刚刚创建的文件
[root@master logs]# hdfs dfs -ls -R /
```
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617774337105-69090f77-94ee-4a67-b27d-123372fbd4b9.png#align=left&display=inline&height=50&margin=%5Bobject%20Object%5D&originHeight=50&originWidth=896&size=0&status=done&style=none&width=896)
```shell
[root@master logs]# hdfs dfs -cat /logs/2018-12-31.1546242551842
hello world !
guang
浙江工商大学
```


到此为止，flume配置就结束了。


## 七、Hbase安装和配置
### 介绍
HBase – Hadoop Database，是一个高可靠性、高性能、面向列、可伸缩的分布式存储系统。Hadoop HDFS为HBase提供了高可靠性的底层存储支持，Hadoop MapReduce为HBase提供了高性能的计算能力，Zookeeper为HBase提供了稳定服务和failover机制。


### 1、环境配置
```shell
创建目录，将下载好的压缩包上传并解压
[root@master local]# mkdir hbase
[root@master local]# cd hbase
[root@master hbase]# tar -zxvf hbase-2.1.1-bin.tar.gz
# 环境变量
[root@master hbase]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export KAFKA_HOME=/usr/local/kafka/kafka-2.1.0
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export FLUME_HOME=/usr/local/flume/flume-1.8.0
export FLUME_CONF_DIR=$FLUME_HOME/conf
export HBASE_HOME=/usr/local/hbase/hbase-2.1.1
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin:$KAFKA_HOME/bin:$SCALA_HOME/bin:$FLUME_HOME/bin:$HBASE_HOME/bin
[root@master hbase]# source /etc/profile
```
### 2、修改hbase-env.sh文件
```shell
[root@master hbase]# cd hbase-2.1.1/conf
[root@master conf]# vim hbase-env.sh 
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HBASE_LOG_DIR=${HBASE_HOME}/logs 
export HBASE_MANAGES_ZK=false
```
### 3、修改hbase-site.xml 文件
```shell
[root@master conf]# vim hbase-site.xml 
<configuration>
<property>
<name>hbase.rootdir</name>
<value>hdfs://master:9000/hbase</value>
</property>
<property>
<name>hbase.cluster.distributed</name>
<value>true</value>
</property>
<property>
<name>hbase.zookeeper.quorum</name>
<value>master,slave1,slave2</value>
</property>
<property>
<name>hbase.zookeeper.property.dataDir</name>
<value>/usr/local/zookeeper/zookeeper-3.4.10/data</value>
</property>
<property>
<name>hbase.tmp.dir</name>
<value>/usr/local/hbase/data/tmp</value>
</property>
<property>
<name>hbase.master</name>
<value>hdfs://master:60000</value>
</property>
<property>
<name>hbase.master.info.port</name>
<value>16010</value>
</property>
<property>
<name>hbase.regionserver.info.port</name>
<value>16030</value>
</property>
</configuration>
```
### 4、修改regionservers文件
```shell
[root@master conf]# vim regionservers 
master
slave1
slave2
```
### 5、其他两个子节点的配置
```shell
# 把上面配置好的hbase整个文件夹传过去
[root@master conf]# cd ../../..
[root@master local]# scp -r hbase root@192.168.185.151:/usr/local/
[root@master local]# scp -r hbase root@192.168.185.152:/usr/local/
# 别忘在另外两个节点也要在/etc/profile下配置环境变量并source一下使生效！
# 在所有节点上都手动创建/usr/local/hbase/data/tmp目录，也就是上面配置文件中hbase.tmp.dir属性的值，用来保存临时文件的。
```
### 6、测试
```shell
# 注意：测试Hbase之前，zookeeper和hadoop需要提前启动起来
[root@master local]# cd hbase/hbase-2.1.1
[root@master hbase-2.1.1]# bin/start-hbase.sh  
[root@master hbase-2.1.1]# jps
# 正确结果：主节点上显示：HMaster / 子节点上显示：HRegionServer
```
在主机浏览器上访问：[http://192.168.185.150:16010](http://192.168.185.150:16010)
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617774349370-098627a6-55e9-4506-8b20-592cac61e1a8.png#align=left&display=inline&height=488&margin=%5Bobject%20Object%5D&originHeight=488&originWidth=1260&size=0&status=done&style=none&width=1260)
到此为止，Hbase配置就结束了。


## 八、Spark安装和配置
### 介绍
Apache Spark 是专为大规模数据处理而设计的快速通用的计算引擎，是类似于Hadoop MapReduce的通用并行框架。Spark拥有Hadoop MapReduce所具有的优点，但不同于MapReduce的是——Job中间输出结果可以保存在内存中，从而不再需要读写HDFS，因此Spark能更好地适用于数据挖掘与机器学习等需要迭代的MapReduce的算法。Spark实际上是对Hadoop的一种补充，可以很好的在Hadoop 文件系统中并行运行。
### 1、环境配置
```shell
# 创建目录，将下载好的压缩包上传并解压
[root@master local]# mkdir spark
[root@master local]# cd spark
[root@master spark]# tar -zxvf spark-2.4.0-bin-hadoop2.7.tgz 
[root@master spark]# mv spark-2.4.0-bin-hadoop2.7 spark-2.4.0
# 配置环境变量
[root@master spark]# vim /etc/profile
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
export HIVE_HOME=/usr/local/hive/hive-2.3.4
export ZOOKEEPER_HOME=/usr/local/zookeeper/zookeeper-3.4.10
export KAFKA_HOME=/usr/local/kafka/kafka-2.1.0
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export FLUME_HOME=/usr/local/flume/flume-1.8.0
export FLUME_CONF_DIR=$FLUME_HOME/conf
export HBASE_HOME=/usr/local/hbase/hbase-2.1.1
export SPARK_HOME=/usr/local/spark/spark-2.4.0
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HIVE_HOME/bin:$ZOOKEEPER_HOME/bin:$KAFKA_HOME/bin:$SCALA_HOME/bin:$FLUME_HOME/bin:$HBASE_HOME/bin:$SPARK_HOME/bin
[root@master spark]# source /etc/profile
```
### 2、修改spark-env.sh文件
```shell
[root@master spark]# cd spark-2.4.0/conf/
[root@master conf]# mv spark-env.sh.template spark-env.sh
[root@master conf]# vim spark-env.sh 
export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export SCALA_HOME=/usr/local/scala/scala-2.11.8
export HADOOP_HOME=/usr/local/hadoop/hadoop-2.7.7
export HADOOP_CONF_DIR=/usr/local/hadoop/hadoop-2.7.7/etc/hadoop
```
### 3、修改slaves文件
```shell
[root@master conf]# mv slaves.template slaves
[root@master conf]# vim slaves 
master
slave1
slave2
```
### 4、在其余两个子节点上操作
```shell
# 把上面配置好的spark整个文件夹传过去
[root@master conf]# cd ../../..
[root@master local]# scp -r spark root@192.168.185.151:/usr/local/
[root@master local]# scp -r spark root@192.168.185.152:/usr/local/
# 别忘在另外两个节点也要在/etc/profile下配置环境变量并source一下使生效！
```
### 5、启动
```shell
[root@master local]# cd spark/spark-2.4.0/         
[root@master spark-2.4.0]# sbin/start-all.sh
```


启动完毕后在主机浏览器访问界面：[http://192.168.185.150:8080/](http://192.168.185.150:8080/)
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617774455414-f8227045-a53a-4dd3-b032-e11700f4105a.png#align=left&display=inline&height=594&margin=%5Bobject%20Object%5D&originHeight=594&originWidth=1805&size=0&status=done&style=none&width=1805)
OK成功，到此为止，Spark配置就结束了！现在我们来测试运行一个spark内部自带的计算圆周率的例子代码：
```shell
[root@master spark-2.4.0]# ./bin/spark-submit \
--class org.apache.spark.examples.SparkPi \
--master local \
examples/jars/spark-examples_2.11-2.4.0.jar
```
在控制台输出中我们可以找到计算结果：
![](https://cdn.nlark.com/yuque/0/2021/png/1471886/1617774479762-a1692e00-3a1b-4c11-bdf2-73376fd85b78.png#align=left&display=inline&height=23&margin=%5Bobject%20Object%5D&originHeight=23&originWidth=377&size=0&status=done&style=none&width=377)


