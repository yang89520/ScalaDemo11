

# JDBC定义

**独立于特定数据库管理系统**、**通用的SQL数据库存取和操作的公共接口**

# 获取数据库连接

- java.sql.Driver 接口是所有 JDBC 驱动程序需要实现的接口
- java.sql.DriverManager驱动程序管理器类

```java
// 读取配置文件
Properties properties = new Properties();
// load有几种方式
properties.load()
```



 ```java
// 两种连接方式
Connection connection = driver.connect(url,properties);

Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/myemployees",
 ```

# Preperedstatement预编译sql

```java
/*操作执行都在ps里
- set方法Int/String/Array
- excuteQruey/excuteUpdate qruey返回的是ResultSet对象 update返回int受影响条数
- ResultSet对象可以迭代取出
- 在使用qruey查询时
-- 使用ResultSet对象.get方法取出元素
-- 也可以使用getMetaData获取元数据 然后获取字段名和每行元素迭代
*/
PreparedStatement ps = connection.PreparedStatement(sql);
// ps 有set方法
```

```java
//占位符元素填充
//3.给占位符赋值
/*
     setInt(int parameterIndex, int x)
     parameterIndex : 占位符的索引位置
     x : 赋值的数据
*/
ps.setInt(1,1);
ps.setString(2,"abc");
```

```java
// 需要关闭资源
stream流、preparedstatement、connection
```

```java
//元素据迭代取出数据
    // 查询方法
    public JDBCUtils qurreyAll(String sql,String...param) throws SQLException {
        PreparedStatement ps=null;
        Connection conn=null;
        ResultSet resultSet=null;
        try {
            conn= conn();
            ps = conn.prepareStatement(sql);
            resultSet = ps.executeQuery();
            ResultSetMetaData metaData = resultSet.getMetaData();
            int count = metaData.getColumnCount();
            // 往集合中追加查询的对象越俗
            int m = 1;
            while (resultSet.next()) {
                String columnName = metaData.getColumnName(m++);
                map = new HashMap<>();
                for (int i = 0; i < count; i++) {
                    Object values = resultSet.getObject(columnName);
                    map.put(columnName, values);
                }
                cclist.add(map);
            }
        }catch (Exception e){
            e.printStackTrace();
        }finally {
            if (resultSet!=null){
                resultSet.close();
            }
            if (ps!=null){
                ps.close();
            }
            if (conn!=null){
                this.close();
            }
            return this;
        }
    }
```



# 封装JDBCUtils

```java
/*
- properties流
- conn连接
- DML
- DELETE
- UPDATE
- INSERT
- DDL
- QRUEY
*/
```

# 使用DBUtils

```java
//创建QueryRunner对象qr
QrueyRunner qr=new QrueyRunner();
//查询
qr.qruey(Connection,sql,Hander);
//更新
qr.update(Connection,sql,...params);
```



# 批处理

```java
/*
	ps.addBatch()
	ps.exceteBatch()
	ps.clearBatch()
*/
for (int i = 1; i <= 100000 ; i++) {
    ps.setInt(1,i);
    ps.setString(2,"aa" + i);
    //将数据添加到批处理中
    ps.addBatch();

    if (i % 1000 ==0) {
        //4.执行sql
        ps.executeBatch();
        //5.清空批处理
        ps.clearBatch();
    }
}
```



# 事务操作

```java
// 禁止自动提交
connection.setAutoCommit(false);
//事务提交
connection.commit();
//事务回滚
connection.rollback();
////允许自动提交
connection.setAutoCommit(True);
```



# Druid数据库连接池

```java
// 配置文件名字固定
/*
url=jdbc:mysql://localhost:3306/myemployees
username=root
password=*******
driverClassName=com.mysql.jdbc.Driver
*/

new DruidDataSource
// 第一种获取配置
datasource.setUrl/DriverClassName/Username/Password
// druid读取配置文件
DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);

datasource.getConnection
```

