```
每个表都是独立的
表与表之间通过公共字段来建立关系（例如ID字段）多表查询效率低
SQL Server/Oracle/MySQL
```


#### 配置环境变量

```
将安装目录中bin文件夹的地址放到环境变量path中
```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118160044.png)

环境变量


#### cmd mysql服务器
```
 (default no pass)
mysql -h127.0.0.1 -P3306 -uroot

-h 主机地址

-P 端口号

-u 用户名

-p 用户密码
MySQL服务器在本地, 主机地址可以省略
服务器使用默认3306端口, 端口号可以省略

mysql -uroot -p 密码采用暗文input

```

```
显示数据库

show databases;


```


![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118221620.png)
```
information_schema

保存着关于MySQL服务器所维护的所有其他数据库的信息。

如数据库名，数据库的表，表栏的数据类型与访问权限等
```

```
mysql

MySQL系统数据库, 保存了登录用户名,密码,以及每个用户的权限等等
```

```
performance_schema

用来保存数据库服务器性能的参数
```

```
sys

这个库是通过视图的形式把information_schema和performance_schema结合起来，查询出更加令人容易理解的数据
```

#### CRUD
```
数据库的增删改查
表的增删改查
数据的增删改查
```
