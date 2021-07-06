## 软硬件环境

[软硬件环境建议配置](https://dolphinscheduler.apache.org/zh-cn/docs/latest/user_doc/hardware-environment.html)

## 集群部署(Cluster)

### 基础配置

```shell
# software和module 创建dolphinscheduler 上传安装包
mkdir dolphinscheduler
cd dolphinscheduler/
mkdir /opt/module/dolphinscheduler
tar -zxf apache-dolphinscheduler-1.3.6-bin.tar.gz -C /opt/module/dolphinscheduler/

cd /opt/module/dolphinscheduler/apache-dolphinscheduler-1.3.6-bin/

# 初始化mysql数据库 {user} {password} 登录dolphinscheduler的用户名密码
mysql -uroot -p
    mysql> CREATE DATABASE dolphinscheduler DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
    mysql> GRANT ALL PRIVILEGES ON dolphinscheduler.* TO 'yiran'@'%' IDENTIFIED BY 'Yang89520..';
    mysql> GRANT ALL PRIVILEGES ON dolphinscheduler.* TO 'yiran'@'localhost' IDENTIFIED BY 'Yang89520..';
    mysql> flush privileges;

# 配置conf设置
vim conf/datasource.properties
    # mysql
    spring.datasource.driver-class-name=com.mysql.jdbc.Driver
    spring.datasource.url=jdbc:mysql://hadoop102:3306/dolphinscheduler?useUnicode=true&characterEncoding=UTF-8&allowMultiQueries=true     
    spring.datasource.username=yiran						
    spring.datasource.password=Yang89520..
  
# 拷贝mysql jar包到 lib
cp /opt/module/hive/lib/mysql-connector-java-5.1.27-bin.jar /opt/module/dolphinscheduler/apache-dolphinscheduler-1.3.6-bin/lib/

# 将hdfs-site.xml、core-site.xml 拷贝至ds的 conf 目录下
cp /opt/module/hadoop-3.1.3/etc/hadoop/hdfs-site.xml /opt/module/dolphinscheduler-woker/conf/
cp /opt/module/hadoop-3.1.3/etc/hadoop/core-site.xml /opt/module/dolphinscheduler-woker/conf/

# 配置依赖环境变量
vim conf/env/dolphinscheduler_env.sh
    export HADOOP_HOME=/opt/module/hadoop-3.1.3
    export HADOOP_CONF_DIR=/opt/module/hadoop-3.1.3/etc/hadoop
    #export SPARK_HOME1=/opt/soft/spark1
    export SPARK_HOME2=/opt/module/spark/spark-3.0.0-yarn
    #export PYTHON_HOME=/opt/soft/python
    export JAVA_HOME=/opt/module/jdk1.8.0_212
    export HIVE_HOME=/opt/module/hive
    #export FLINK_HOME=/opt/soft/flink
    #export DATAX_HOME=/opt/soft/datax

    export PATH=$HADOOP_HOME/bin:$SPARK_HOME2/bin:$JAVA_HOME/bin:$HIVE_HOME/bin:$PATH

    #export PATH=$HADOOP_HOME/bin:$SPARK_HOME1/bin:$SPARK_HOME2/bin:$PYTHON_HOME:$JAVA_HOME/bin:$HIVE_HOME/bin:$FLINK_HOME/bin:$DATAX_HOME/bin:$PATH

# 修改一键启动脚本
vim conf/config/install_config.conf
```

> 集群分配

| 进程                 | 服务       | 节点                |
| -------------------- | ---------- | ------------------- |
| MasterServer         | master服务 | hadoop102,hadoop104 |
| WorkerServer         | worker服务 | hadoop103,hadoop104 |
| LoggerServer         | logger服务 | hadoop103           |
| ApiApplicationServer | api服务    | hadoop103           |
| AlertServer          | alert服务  | hadoop104           |



### 一键启动配置

> 编写一键启动脚本
>
> `vim  conf/config/install_config.conf`

```properties
# 这里填 mysql or postgresql
dbtype="mysql"

# 数据库连接地址
dbhost="hadoop102:3306"

# 数据库名
dbname="dolphinscheduler"

# 数据库用户名，此处需要修改为上面设置的{user}具体值
username="yiran"

# 数据库密码, 如果有特殊字符，请使用\转义，需要修改为上面设置的{password}具体值
password="Yang89520.."

#Zookeeper地址
zkQuorum="hadoop102:2181,hadoop103:2181,hadoop104:2181"

#将DS安装到哪个目录，如: /opt/soft/dolphinscheduler，不同于现在的目录
installPath="/opt/module/dolphinscheduler-woker"

#使用哪个用户部署，使用第3节创建的用户
deployUser="yiran"

# 邮件配置，以qq邮箱为例
# 邮件协议
mailProtocol="SMTP"

# 邮件服务地址
mailServerHost="smtp.qq.com"

# 邮件服务端口
mailServerPort="25"

# mailSender和mailUser配置成一样即可
# 发送者
mailSender="2541060688@qq.com"

# 发送用户
mailUser="2541060688@qq.com"

# 邮箱密码
mailPassword="yang89520"

# TLS协议的邮箱设置为true，否则设置为false
starttlsEnable="true"

# 开启SSL协议的邮箱配置为true，否则为false。注意: starttlsEnable和sslEnable不能同时为true
sslEnable="false"

# 邮件服务地址值，参考上面 mailServerHost
sslTrust="smtp.qq.com"

# 业务用到的比如sql等资源文件上传到哪里，可以设置：HDFS,S3,NONE，单机如果想使用本地文件系统，请配置为HDFS，因为HDFS支持本地文件系统；如果不需要资源上传功能请选择NONE。强调一点：使用本地文件系统不需要部署hadoop
resourceStorageType="HDFS"

#如果上传资源保存想保存在hadoop上，hadoop集群的NameNode启用了HA的话，需要将hadoop的配置文件core-site.xml和hdfs-site.xml放到安装路径的conf目录下，本例即是放到/opt/soft/dolphinscheduler/conf下面，并配置namenode cluster名称；如果NameNode不是HA,则只需要将mycluster修改为具体的ip或者主机名即可
defaultFS="hdfs://hadoop102:9820"


# 如果没有使用到Yarn,保持以下默认值即可;如果ResourceManager是HA，则配置为ResourceManager节点的主备ip或者hostname,比如"192.168.xx.xx,192.168.xx.xx";如果是单ResourceManager请配置yarnHaIps=""即可
yarnHaIps=""

# 如果ResourceManager是HA或者没有使用到Yarn保持默认值即可；如果是单ResourceManager，请配置真实的ResourceManager主机名或者ip
singleYarnIp="hadoop103"

# 资源上传根路径,主持HDFS和S3,由于hdfs支持本地文件系统，需要确保本地文件夹存在且有读写权限
resourceUploadPath="/dolphinscheduler"

# 具备权限创建resourceUploadPath的用户
hdfsRootUser="yiran"



#在哪些机器上部署DS服务，本机选localhost
ips="hadoop102,hadoop103,hadoop104"

#ssh端口,默认22
sshPort="22"

#master服务部署在哪台机器上
masters="hadoop102,hadoop104"

#worker服务部署在哪台机器上,并指定此worker属于哪一个worker组,下面示例的default即为组名
workers="hadoop103:default,hadoop104:default"

#报警服务部署在哪台机器上
alertServer="hadoop104"

#后端api服务部署在在哪台机器上
apiServers="hadoop102"
```



> 一键部署

切换到部署用户yiran，然后执行一键部署脚本

`sh install.sh`

```
注意：
第一次部署的话，在运行中第3步`3,stop server`出现5次以下信息，此信息可以忽略
sh: bin/dolphinscheduler-daemon.sh: No such file or directory
```

如果以上服务都正常启动，说明自动部署成功

部署成功后，可以进行日志查看，日志统一存放于logs文件夹内

```日志路径
 logs/
    ├── dolphinscheduler-alert-server.log
    ├── dolphinscheduler-master-server.log
    |—— dolphinscheduler-worker-server.log
    |—— dolphinscheduler-api-server.log
    |—— dolphinscheduler-logger-server.log
```

### 手动配置

> alert.properties

```properties
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#alert type is EMAIL/SMS
alert.type=EMAIL

# mail server configuration
mail.protocol=SMTP
mail.server.host=smtp.qq.com
mail.server.port=25
mail.sender=2541060688@qq.com
mail.user=2541060688@qq.com
mail.passwd=yang89520
# TLS
mail.smtp.starttls.enable=true
# SSL
mail.smtp.ssl.enable=false
mail.smtp.ssl.trust=smtp.qq.com

#xls file path,need create if not exist
#xls.file.path=/tmp/xls

# Enterprise WeChat configuration
enterprise.wechat.enable=false
#enterprise.wechat.corp.id=xxxxxxx
#enterprise.wechat.secret=xxxxxxx
#enterprise.wechat.agent.id=xxxxxxx
#enterprise.wechat.users=xxxxxxx
#enterprise.wechat.token.url=https://qyapi.weixin.qq.com/cgi-bin/gettoken?corpid=$corpId&corpsecret=$secret
#enterprise.wechat.push.url=https://qyapi.weixin.qq.com/cgi-bin/message/send?access_token=$token
#enterprise.wechat.team.send.msg={\"toparty\":\"$toParty\",\"agentid\":\"$agentId\",\"msgtype\":\"text\",\"text\":{\"content\":\"$msg\"},\"safe\":\"0\"}
#enterprise.wechat.user.send.msg={\"touser\":\"$toUser\",\"agentid\":\"$agentId\",\"msgtype\":\"markdown\",\"markdown\":{\"content\":\"$msg\"}}

plugin.dir=/Users/xx/your/path/to/plugin/dir

```

> application-api.properties
>
> 修改web访问端口

```properties
# 主要修改这几个配置
# server port   
server.port=16888
#--------------------------------完整配置--------------------------
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

# server.port=
server.port=16888

# session config
server.servlet.session.timeout=7200

# servlet config
server.servlet.context-path=/dolphinscheduler/

# time zone
spring.jackson.time-zone=GMT+8

# file size limit for upload
spring.servlet.multipart.max-file-size=1024MB
spring.servlet.multipart.max-request-size=1024MB

# enable response compression
server.compression.enabled=true
server.compression.mime-types=text/html,text/xml,text/plain,text/css,text/javascript,application/javascript,application/json,application/xml

# max http post size
server.jetty.max-http-form-post-size=5000000

# messages encoding
spring.messages.encoding=UTF-8

# i18n classpath folder, file prefix messages. if have many files, use "," seperator
spring.messages.basename=i18n/messages

# Authentication types (supported types: PASSWORD)
security.authentication.type=PASSWORD
```

> common.properties

```properties
# 主要修改这几个配置
resource.storage.type=HDFS  
fs.defaultFS=hdfs://hadoop102:9820
yarn.application.status.address=http://hadoop103:8088/ws/v1/cluster/apps/%s

#--------------------------------完整配置--------------------------
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

data.basedir.path=/tmp/dolphinscheduler


resource.upload.path=/dolphinscheduler

# whether to startup kerberos
hadoop.security.authentication.startup.state=

# java.security.krb5.conf.path=
java.security.krb5.conf.path=

# login user from keytab username
login.user.keytab.username=

# login user from keytab path
login.user.keytab.path=

# kerberos expire time, the unit is hour
kerberos.expire.time=2

# resource view suffixss
#resource.view.suffixs=txt,log,sh,bat,conf,cfg,py,java,sql,xml,hql,properties,json,yml,yaml,ini,js

# if resource.storage.type=HDFS
hdfs.root.user=yiran

# if resource.storage.type=HDFS
fs.defaultFS=hdfs://hadoop102:9820

# if resource.storage.type=HDFS
fs.s3a.endpoint=

# if resource.storage.type=HDFS
fs.s3a.access.key=

# if resource.storage.type=HDFS
fs.s3a.secret.key=

# if resourcemanager HA is enabled, please set the HA IPs; if resourcemanager is single, keep this value empty
yarn.resourcemanager.ha.rm.ids=

# if resourcemanager HA is enabled or not use resourcemanager, please keep the default value; If resourcemanager is single, you only need to replace ds1 to actual resourcemanager hostname
yarn.application.status.address=http://hadoop103:8088/ws/v1/cluster/apps/%s

# system env path
#dolphinscheduler.env.path=env/dolphinscheduler_env.sh

# development state
development.state=false
```

> master.properties
>
> 可改可不改

```properties
master.listen.port=8787 #默认5678
```

> worker.properties
>
> 可改可不改

```properties
worker.listen.port=7878  #默认1234
worker.groups=hadoop  #default
```

> zookeeper.properties

```properties
zookeeper.quorum=hadoop102:2181,hadoop103:2181,hadoop104:2181
```

> xsync分发

> 启动

各节点用`bin/dolphinscheduler-daemon.sh start|stop xxx-server `启停

或者用`bin/start-all.sh`和`bin/stop-all.sh`

```shell
===============hadoop102==============
4880 DataNode
5921 HistoryServer
4689 NameNode
22117 Jps
10021 AzkabanExecutorServer
28584 RunJar
5209 NodeManager
28379 RunJar
10604 AzkabanWebServer
32718 JobHistoryServer
4943 QuorumPeerMain
===============hadoop103==============
1764 ResourceManager
21477 DataNode
2053 NodeManager
2342 QuorumPeerMain
20264 Jps
24125 AzkabanExecutorServer
2766 Kafka
===============hadoop104==============
29953 SecondaryNameNode
29810 DataNode
27012 Jps
30073 NodeManager
22284 LoggerServer
14061 Kafka
22397 AlertServer
22173 AzkabanExecutorServer
22046 MasterServer
13646 QuorumPeerMain
```

### 访问验证

访问[http://hadoop103:16888/dolphinscheduler](http://hadoop102:16888/dolphinscheduler)【哪台节点起api-server就在哪台访问】

输入默认用户名密码

- 默认用户：admin
- 默认密码：dolphinscheduler123



### 调优配置

生产环境上建议，worker.properties里设置的cpu和内存调一下就可以保护worker不至于挂掉，一般别超过cpu核数的2倍，内存留上1~2G（当然如果比较豪，可以预留更多资源），线程数别超过cp倍。

```
例如：8c16G机器 worker.exec.threads=20  worker.max.cpuload.avg=16   worker.reserved.memory=1

同理对于master调优配置 8c16G机器   master.properties文件  master.max.cpuload.avg=16  master.reserved.memory=1
```



## 功能使用

### 主要功能

- 首页：主要显示状态统计，查看任务是否繁忙

![image-20210624220024135](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624220024135.png)

- 项目管理：
- 资源中心：对上传和创建的资源进行管理，主要是文件夹和udf函数
- 数据源中心：

![image-20210624220422253](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624220422253.png)

- 监控中心

![image-20210624220836414](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624220836414.png)

- 安全中心

![image-20210624220927600](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624220927600.png)

### 安全中心配置

#### 创建队列

![image-20210624215503006](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624215503006.png)

#### 创建租户

![image-20210624221158468](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624221158468.png)

#### 创建用户

![image-20210624221308039](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624221308039.png)

#### 创建告警组

- 可选邮件、短信

![image-20210624221435787](dolphinscheduler集群部署.assets/image-20210624221435787.png)

#### 创建Worker分组

- 对所有可供调度的节点进行分组
- 以后可以将任务放到指定分组的节点上跑

![image-20210624221941161](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624221941161.png)

#### 令牌管理

- 开发和DS api交互的时候使用的Token



### 快速上手

- 创建项目
- 将项目需要的脚本和脚本依赖的资源都放到资源中心，可以创创建一个专用的目录存放
- 定义工作流
- 创建一个shell脚本调用资源里的启动脚本

#### shell脚本

- 设置自定义参数变量传参

![image-20210624224731878](https://gitee.com/Mryang_bast/typera/raw/master/hive_imgs/image-20210624224731878.png)

添加job先后【依赖】顺序











## 参考文献

[配置邮箱报警](https://www.cnblogs.com/tenic/p/14897570.html)

## FAQ

> 创建文件错误 没有权限创建文件|上传文件

这种情况一般是三个方面

- 没有操作hdfs的权限`dolphinscheduler`

- 没有读写本地资源目录的权限`tmp/dolphinscheduler`

- 免密sudo没配好

- ```shell
  echo 'dolphinscheduler  ALL=(userA,userB,userC)  NOPASSWD: NOPASSWD: ALL' >> /etc/sudoers
  sed -i 's/Defaults    requirett/#Defaults    requirett/g' /etc/sudoers
  ```

- 三个都配好后重启ds，就行了