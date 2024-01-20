[[USB]]
Java Database Connectivity

DBMS database manager software
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118211019.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118211202.png)
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118211327.png)


jdbc interface 存储在java.sql和javax.sql 包中的 api

#### jar包是什么？
java程序打成的一种压缩包格式，你可以将这些jar包引入你的项目中，然后你可以使用这个java程序中类和方法以及属性了

#### 核心类和接口

DriverManager
```
将第三方数据库厂商的实现驱动jar注册到程序中.
可以根据数据库连接信息获取 connection
```

Connection

```
和数据库建立的连接，在连接对象上，可以多次执行数据库curd动作

可以获取 statement和 preparedstatement，callablestatement 对象
```

Statement | 
PreparedStatement |预编译SQL（有动态值语句）
CallableStatement
```
具体发送SQL语句到数据库管理软件的对象
不同发送方式稍有不同！preparedstatement 使用为重点！
```

Result
#### 选择全新8＋版本mysql-jdbc驱动

驱动jar版本选择 :我们选择版本 8.0.27 版本
(8.0.25+ ,省略时区设置)
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118213225.png)

```
drag jdbc jar package into lib
Mark package as...

```


#### 导入依赖
```
项目创建lib文件夹
导入驱动依赖jar包
jar 包右键—添加为项目依赖
```
#### jdbc 基本使用步骤分析
```
注册驱动
获取连接
创建发送sql语句对象
发送sql语句，并获取返回结果
结果集解析
资源关闭
```

#### 准备数据库数据
```
CREATE DATABASE atguigu;

USE atguigu;

CREATE TABLE t_user(
   id INT PRIMARY KEY AUTO_INCREMENT COMMENT '用户主键',
   account VARCHAR(20) NOT NULL UNIQUE COMMENT '账号',
   PASSWORD VARCHAR(64) NOT NULL COMMENT '密码',
   nickname VARCHAR(20) NOT NULL COMMENT '昵称');
   
INSERT INTO t_user(account,PASSWORD,nickname) VALUES
  ('root','123456','经理'),('admin','666666','管理员');
```

properties配置文件
```
atguigu.jdbc.url=jdbc:mysql://localhost:3306/atguigu
atguigu.jdbc.driver=com.mysql.cj.jdbc.Driver
atguigu.jdbc.username=root
atguigu.jdbc.password=root

```