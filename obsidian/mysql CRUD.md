
#### 数据类型

```
和常见的编程语言一样, 数据库中存储的数据也是区分类型的

MySQL中支持的数据类型大致可以分为三类: 数值类型、字符串类型和日期时间类型
```

```
double：浮点型，例如double(5,2)表示最多5位，其中必须有2位小数，即最大值为999.99；

char：固定长度字符串类型； char(3) 'lnj'

varchar：可变长度字符串类型；varchar(10) 'lnj'

text：字符串类型;

blob：二进制类型；

date：日期类型，格式为：yyyy-MM-dd；

time：时间类型，格式为：hh:mm:ss

datetime:日期时间类型 yyyy-MM-dd hh:mm:ss

注意点: 在mysql中，字符串类型和日期类型都要用单引号括起来。'lnj' '2022-02-02'
```

##### 整数类型

```
MySQL中有哪些数据类型?

- 整型类型/浮点类型/定点类型/字符类型/文本类型/枚举类型/集合类型/日期类型/布尔类型

3.整数类型 - 专门用来保存整数的

TINYINT 1 字节 (-128，127) (0，255) 小整数值

SMALLINT 2 字节 (-32 768，32 767) (0，65 535) 大整数值

MEDIUMINT 3 字节 (-8 388 608，8 388 607) (0，16 777 215) 大整数值

INT或INTEGER 4 字节 (-2 147 483 648，2 147 483 647) (0，4 294 967 295) 大整数值

BIGINT 8 字节 (-9,223,372,036,854,775,808，9 223 372 036 854 775 807) (0，18 446 744 073 709 551 615) 极大整数值
```

```
注意点:

- MySQL中的整型和其它编程语言的整型一样, 也区分有符号和无符号

+ 默认情况下整型就是有符号的

+ 我们可以在数据类型的后面加上 unsigned 来将数据类型变成无符号的

- 在设计数据库的时候一定要合理的使用数据类型

+ 例如: 我们要保存一个人的年龄 (整数)

+ 我们应该使用TINYINT类型, 因为人最多活到255岁已经上天了, 所以使用最小的整型即可

+ 如果使用其它的整型, 就会造成资源浪费, 数据库体积变大, 效率变低...

- 在保存数据的时候, 如果超出了当前数据类型的范围, 那么就会报错

- 在设置整型的时候, 还可以设置整型数据将来显示的位宽

+ 例如: 现在设置将来显示整型的位宽是2, 现在存储的数据1, 那么将来查询出来的数据就会显示成 1;

+ 2020-2-3 -- 2020-02-03

+ 注意点: 如果存储的数据没有指定的位宽, 那么就会自动补空格或者0, 如果大于或者等于了指定的位宽, 那么毛都不做

```

```
create table person(
id int,
age tinyint
);

insert into person values (1, -128);
insert into person values (1, 127);
insert into person values (1, 128); #报错

create table person2(

id int,

age tinyint unsigned

);
insert into person values (1, -128); #报错

insert into person values (1, 127);

insert into person values (1, 128);

create table person3(

id int,

age tinyint(2) zerofill

);
insert into person values (1, 1); #01
insert into person values (1, 12); #12
insert into person values (1, 123); #123
```

##### 浮点类型

```
浮点类型 - 专门用来保存小数的

FLOAT(m, d) 4 字节 单精度

DOUBLE(m, d) 8 字节 双精度

m总位数, d小数位数

  

- float和double的区别

+ 占用存储空间大小不一样

+ 默认保留的小数位数不同

+ 保存数据的有效精度也不同


- 浮点类型特点

+ 和其它编程语言中一样, 浮点类型是不准确的

+ 所以在企业开发中千万不要使用浮点数来保存用户的准确(珍贵)信息(RMB)
```

```
示例一: 默认保留的小数位数不同

create table person(

id int,

weight FLOAT,

height DOUBLE

);

insert into person values (1, 1.12345678901234567890, 1.12345678901234567890);

weight: 1.12346

height: 1.1234567890123457

  

示例二: 手动指定小数的总位数和小数部分的位数

create table person2(

id int,

weight FLOAT(10, 6),

height DOUBLE(10, 6)

);

insert into person2 values (1, 1.12345678901234567890, 1.12345678901234567890);

weight: 1.123457

height: 1.123457


示例三: 保存数据的有效精度也不同

create table person3(

id int,

weight FLOAT(20, 19),

height DOUBLE(20, 19)

);

insert into person3 values (1, 1.12345678901234567890, 1.12345678901234567890);

weight: 1.123456-8357467651000
height: 1.123456789012345-7000
```

##### 定点类型

```
定点类型 - 也是用于存储小数的

decimal(M, D)

m总位数, d小数位数

定点类型的本质: 是将数据分为两个部分来存储, 每个部分都是整数

所以定点数不要滥用, 因为非常消耗资源

create table person4(

id int,

weight decimal(21, 20),

height decimal(21, 20)

);

insert into person4 values (1, 1.12345678901234567890, 1.12345678901234567890);

weight: 1.12345678901234567890

height: 1.12345678901234567890
```

##### 字符类型

```
4.字符类型 - 专门用来存储字符的

CHAR(size) 0-255 字节 定长字符串 (未指定默认255)

VARCHAR(size) 0-65535字节 变长字符串

- char和varchar区别

+ 能够保存数据的容量不一样

+ char不会回收多余的字符, 要多少给多少

+ varchar会回收多余的字符, 用多少给多少

+ 例如: 通过 char(2)存储存储数据'a', 存储的结果是' a';

+ 例如: 通过 varchar(2)存储存储数据'a', 存储的结果是'a';
```

```
示例一:

create table person(

id int,
name1 char(2),
name2 varchar(2)

);

insert into person values (1, 'a', 'b');

insert into person values (1, '12', '34');

insert into person values (1, 'abc', 'def'); #只要超出申请的范围就会报错

  

示例二:

注意点: 由于是字符类型, 所以传递值建议用单引号''

注意点: VARCHAR理论上可以存储65535个字符, 但是实际会随着当前数据库的字符集改变

create table person2(

id int,

name1 char(255),

name2 varchar(255)

);

# 65535 / 3 = 21845, 由于utf8一个字符占用3个字节, 所以varchar在utf8的表中最多只能存储21845个字符

# 65535 / 2 = 32767, 由于gbk一个字符占用2个字节,所以varchar在gbk的表中最多只能存储32767个字符

create table person3(

id int,

name1 char(255),

name2 varchar(65535)

)charset=gbk;

Column length too big for column 'name2' (max = 21845); use BLOB or TEXT instead

Column length too big for column 'name2' (max = 32767); use BLOB or TEXT instead
```

##### 大文本类型

```
5.大文本类型

5.1.MySQL中每一行存储的数据是有大小限制的, 每一行最多只能存储65534个字节

create table person(

#name1 char(3),

name2 varchar(21844) #在UTF8中相当于65535个字节

)charset=utf8;

# Row size too large. The maximum row size for the used table type, not counting BLOBs, is 65535. This includes storage overhead, check the manual. You have to change some columns to TEXT or BLOBs
```

```
5.2.大文本类型

TINYTEXT 0-255字节 短文本字符串

TEXT 0-65535字节 长文本数据

MEDIUMTEXT 0-16777215字节 中等长度文本数据

LONGTEXT 0-4294967295字节 极大文本数据

create table person2(

name1 char(3),

name2 TEXT #不会报错, 因为没有超出显示, 实际只占用10个字节

)charset=utf8;

注意点:

大文本类型在表中并不会实际占用所能保存的字节数, 而是利用10个字节引用了实际保存数据的地址
```

##### 枚举类型

```
6.枚举类型

和其它编程语言一样, 如果某个字段的取值只能是几个固定值中的一个, 那么就可以使用枚举

enum(值1, 值2, ...);
create table person(

id int,

gender enum('男', '女', '妖')

);

insert into person values (1, '火'); #会报错

insert into person values (1, '男'); #不会报错

insert into person values (2, '女'); #不会报错

insert into person values (3, '妖'); #不会报错
```

```
注意点:

- MySQL中的枚举类型和其它的编程语言一样, 底层都是使用整型来实现的

+ 和其它编程语言不太一样的是, 其它编程语言的枚举都是从0开始的, 而MySQL的枚举是从1开始的

select gender+0 from person;

- 由于MySQL的枚举底层是使用整型实现的, 所以我们在赋值的时候除了可以赋值固定的几个值其中的一个以外

我们还可以赋值对应的整数

insert into person values (4, 1); #不会报错

insert into person values (4, 4); #会报错
```
##### 集合类型

```
7.集合类型

和编程开发中一样, 如果某个字段的取值只能是几个固定值中的几个, 那么就可以使用集合类型

set(值1, 值2, ...)

  

create table person(

id int,

hobby set('篮球','足球','高尔夫球','足浴')

);

insert into person values (1, '篮球,足球,高尔夫球'); #不会报错

insert into person values (1, '橄榄球'); #会报错

  

insert into person values (2, '篮球'); #不会报错 1

insert into person values (3, '足球'); #不会报错 2

insert into person values (4, '高尔夫球'); #不会报错 4

insert into person values (5, '足浴'); #不会报错 8

注意点:

- MySQL的集合类型也是使用整型来实现的

select hobby+0 from person;

- MySQL的集合类型是按照2(n)的方式来实现的

2(0) = 1

2(1) = 2

2(2) = 4

2(3) = 8
```
##### 布尔类型
```
布尔类型 - 专门用来保存真假的

create table person(
id int,
flag boolean
);

insert into person values (1, '男'); #会报错

insert into person values (1, true); #不会报错

insert into person values (2, false); #不会报错

注意点:

- MySQL中的布尔类型也是使用整型来实现的, 0就表示假, 1就表示真

+ 底层的本质是因为MySQL是使用C/C++来实现的, 所以就是'非零即真'

insert into person values (3, 1); #不会报错

insert into person values (4, 0); #不会报错

insert into person values (5, 2); #不会报错
```
##### 日期类型
```
8.日期类型 - 专门用来保存时间的

DATE 3字节 YYYY-MM-DD 日期值

TIME 3字节 HH:MM:SS 时间值或持续时间

DATETIME 8字节 YYYY-MM-DD HH:MM:SS 混合日期和时间值

注意点: 在存储时间的时候, 需要用单引号将时间括起来

create table person(
id int,
filed1 DATE,
filed2 TIME,
filed3 DATETIME
);

insert into person values (1, '2020-02-02', '14:18:23', '2020-02-02 14:18:23');
```
#### 数据库增删改查

```
1.创建数据库
create database [if not exists] 数据库名称 [charset=字符集];
示例一:
create database stu;
注意点: 以上语句, 如果MySQL中已经有了名称叫做stu的数据库, 再执行就会报错

示例二:

create database if not exists person;
注意点: 以上语句, 如果MySQL中已经有了名称叫做person的数据库, 并不会报错, 而是跳过这条语句

示例三:
create database if not exists it666 charset=utf8;
注意点: 为了避免将来读取的字符集和存储的字符集不一样导致乱码问题,

在创建数据库的时候, 我们还需要指定当前创建的数据库将来使用什么编码方式存储数据
2.如何查看数据库全局默认的编码
show variables like 'character_set_%';

3.如果查看某个数据库的编码
show create database person;

4.特殊的数据库名称处理

create database if not exists `create` charset=utf8;

注意点: 如果数据库的名称是SQL的关键字或者是一些特殊字符#~@*&.., 这个时候就需要用反引号括起来
```

```
1.如何删除数据库

drop database [if exists] 数据库名称;
示例一:

drop database stu;

注意点: 以上语句, 如果MySQL中没有要删除的数据库, 那么就会报错 

示例二:

drop database if exists person;

注意点: 以上语句, 如果MySQL中没有要删除的数据库, 那么就会跳过, 并不会报错
```

```
1.如何修改数据库

alter database 数据库名称 charset=字符集;

alter database it666 charset=utf8;

1.如何查看数据库

show create database 数据库名称;

show databases;

```


#### 表增删改查

在对数据库的表进行操作的时候(增删改查), 都必须先告诉MySQL我们要操作的是哪一个数据库
```
use 数据库名称;

1.如何查看数据库中有哪些表?

show tables;
2.如何查看指定表的结构
desc 表名;
```

```
1.创建表

create table 表名(

	字段名称 数据类型,
	
	字段名称 数据类型,
	
	字段名称 数据类型,
	
	字段名称 数据类型,

);

示例一:

create table stu(
	id int,
	name text
);

注意点: 以上代码创建表, 如果表已经存在了, 那么就会报错

示例二:

create table if not exists person(
id int,
name text
);

注意点: 以上代码创建表, 没有就会创建一个新的, 有就会自动跳过
```

```
删除表

drop table 表名;

示例一:

drop table stu;

注意点: 以上语句, 如果删除的表不存在, 那么就会报错

示例二:

drop table if exists person;

注意点: 以上语句, 如果需要删除的表存在, 那么就直接删除, 如果不存在就跳过
```

```
6.1添加字段

alter table 表名 add 新增字段名称 新增字段数据类型 [位置];

alter table person add age int;

注意点: 默认情况下会将新增的字段放到原有字段的后面

  
alter table person add score float first;

注意点: 我们可以通过指定first将新增的字段放到原有字段的前面

  
alter table person add phone int after name;

注意点: 我们可以通过after指定将新增的字段放到哪个字段的后面
```

```
6.3修改字段

6.3.1修改字段的数据类型

alter table 表名 modify 需要修改的字段名称 新的数据类型

alter table person modify score double;


6.3.2修改字段的名称和数据类型

alter table 表名 change 原始字段名称 新的字段名称 新的数据类型;

alter table person change age addr text;
```


#### 插入数据
```
insert into 表名 (字段名称1, 字段名称2) values (值1, 值2);

  

示例:

create table if not exists stu(

id int,

name varchar(20)

);

insert into stu (id, name) values (1, 'lnj');

# 注意点: 在插入数据的时候指定的字段名称的顺序不用和表中的字段名称的顺序一致

insert into stu (name, id) values ('zs', 2);

# 注意点: 在插入数据的时候指定的取值顺序必须和指定的字段名称顺序一致

insert into stu (name, id) values (3, 'ls');

# 注意点: 如果插入数据时指定的取值顺序和表中的字段顺序是一致的, 那么可以不指定字段名称

insert into stu values (3, 'ls');

# 注意点: 我们可以通过values同时插入多条数据

insert into stu values (4, 'ww'), (5, 'zl');
```

#### 更新数据

```

update 表名 set 字段名称=值 [where 条件];

示例:

# 注意点: 如果在更新数据的时候没有指定条件, 那么就会更新整张表中的数据

update stu set score=77;

# 注意点: 如果在更新数据的时候指定了条件, 那么只会更新满足条件的数据

update stu set score=88 where name='ls';

# 注意点: 在指定条件的时候, 我们可以通过AND来指定多个条件, AND===&&

update stu set score=100 where name='lnj' AND id=5;

# 注意点: 在指定条件的时候, 我们可以通过OR来指定多个条件, OR===||

update stu set score=66 where name='zs' OR name='ww';

# 注意点: 在更新数据的时候是可以同时更新多个字段的

update stu set name='it666', score=33 where id=5;
```

#### 查询表

```
# 注意点: 以下方式会将表中所有的数据都查询出来, 所以性能比较差

# 注意点: 以下方式会将表中所有的数据都查询出来, 不能查询特定字段的值

select * from 表名;
# 以下才是查询数据完整的写法

select 字段名称1, 字段名称2 from 表名 [where 条件];

# 查询特定字段的数据

select name from stu;

# 查询满足条件的数据

select * from stu where score > 60;

select id, name from stu where score > 60;

select * from stu where score = 77 || score = 88;

以下SQL语句查询所有ID为1、2、3的订单：

SELECT * FROM orders WHERE order_id IN (1, 2, 3);

select * from stu where score in (77, 88);

select * from stu where score BETWEEN 77 AND 88;

select * from stu where score IS NOT NULL;

select * from stu where score IS NULL;
```

#### where支持的运算符

```
=（等于）、!=（不等于）、<>（不等于）、<（小于）、<=（小于等于）、>（大于）、>=（大于等于）；

IN(set)；固定的范围值

BETWEEN…AND；值在什么范围

IS NULL；（为空） IS NOT NULL（不为空）

AND；与

OR；或

NOT；非

LIKE: 模糊查询
```

#### 删除数据
```
删除数据

delete from 表名 [where 条件];
# 删除满足条件的数据
delete from stu where score > 60;
$ 删除所有的数据

delete from stu;
```
#### MySQL存储引擎

MySQL中的存储引擎就好比我们现实生活中的银行, 不同的银行提供的安全级别、服务水平、存储功能不一样

```
+ MyISAM: 安全性低, 但不支持事务和外键, 适合频繁插入和查询的应用

+ InnoDB(默认): 安全性高, 支持事务和外键, 适合对安全性, 数据完整性要求较高的应用

+ Memory: 访问速度极快, 但不会永久存储数据, 适合对读写速度要求较高的应用

create table stu(
	id int,
	name text
)engine=引擎名称;
```
不同引擎本质
```
- 前面我们说过数据库的本质就是文件
- 通过我们的观察, 我们发现只要创建一个数据库就会自动创建一个文件夹
- 通过我们的观察, 我们发现只要创建一张表就会在指定的数据库文件夹中创建一个文件
- 创建表的时候自动创建的这个文件就保存了这张表的结构

create table stu(
	id int,
	name varchar(20)
)engine=Memory;
```

```
InnoDB:

- 如果表的存储引擎是InnoDB, 那么只要创建表就会自动创建一个文件, 这个文件就保存了这张表的结构

- 如果往InnoDB的表中存储数据, 那么数据会被存储到ibdata1的文件中, 如果存储的数据比较多, 那么系统会自动再创建ibdata2, ibdata3, ...文件

MyISAM:
- 如果表的存储引擎是MyISAM, 那么只要创建表就会自动创建三个文件
+ .sdi这个文件就保存了这张表的结构
+ .MYD这个文件就保存了这张表中存储的数据
+ .MYI这个文件就保存了这张表中的索引

Memory:

- 如果表的存储引擎是Memory, 那么只要创建表就会自动创建一个文件, 这个文件就保存了这张表的结构

- 注意点: 如果表的存储引擎是Memory, 那么就不会像InnoDB/MyISAM将数据保存到文件中了, 而是直接保存到内存中

alter table 表名 engine=引擎名称;
alter table stu engine=MyISAM;

```



[[Database key]]

