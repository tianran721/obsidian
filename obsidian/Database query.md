### 单表查询
#### 结果集
```
1.单表查询

select * from 表名; #查询表中所有数据

select 字段1, 字段2 from 表名; #查询表中指定字段数据

select [* || 字段] from 表名 [where 条件]; #查询表中满足条件的数据

2.什么是结果集?

通过查询语句查询出来的结果我们就称之为结果集

结果集以表的形式将查询的结果返回给我们

注意点:

结果集返回的表和查询的表不是同一张表

被查询的表是真实存在的, 是存储在磁盘上的

而结果集不是真实存在的, 是存储到内存中的
```
##### 结果集的字段别名
```
3.如何给结果集的字段别名?

- 查询指定字段数据时, 我们可以通过as给指定字段取别名

SELECT name as MyName, age as MyAge FROM stu;
```
##### 查询表达式
```
4.什么是字段表达式?

- 查询数据的时候, 除了可以查询指定字段的数据以外, 我们还可以查询表达式的结果

SELECT 6+6;
```
##### 伪表
```
5.什么是伪表?

- 字段表达式虽然能够查询出表达式的结果, 但是不符合MySQL的规范

- 所以我们可以通过伪表(dual)的方式让字段表达式符合MySQL的规范

SELECT 6+6 from dual;
```
#### 模糊查询 like
```
1.模糊查询

格式:

select 字段 from 表名 where 字段 like '条件';

_通配符: 表示任意一个字符

%通配符: 表示任意0~n个字符

  

a_c: abc / adc (匹配)

abc,adc,abbc,ac

_a_c: 1abc / 3adc (匹配)

1abc,abc1,2abbc,3adc

  

a%c:abc / adc / abbc / ac

abc,adc,abbc,ac

%a%c: 1abc / 2abbc / 3adc

1abc,abc1,2abbc,3adc

  

select * from stu where name like 'z_';

select * from stu where name like 'z__';

select * from stu where name like 'z_%';
```
#### 排序 order by
```
1.排序 order by

select 字段 from 表名 order by 字段 [asc | desc];

select * from stu order by age; #默认按照升序进行排序

select * from stu order by age asc; # 升序排序

select * from stu order by age desc; # 降序排序

  

select * from stu order by age desc, score asc; #如果年龄相同, 那么还可以继续按照其它字段来排序
```
#### 聚合函数
```
1.聚合函数:

count(); 统计

select count(*) from stu;

select count(*) from stu where score >= 60;

  

sum(); 求和

select sum(id) from stu;

  

avg(); 求平均值

select avg(id) from stu; # 21 / 6 = 3.5

select avg(score) from stu;

  

max(); 获取最大值

select max(score) from stu;

  

min(); 获取最小值

select min(score) from stu;
```
##### 数值类
```
2.数值类

rand(); #生成随机数

select rand() from dual;

select * from stu order by rand();

round()#四舍五入

select round(3.1) from dual;

select round(3.5) from dual;

ceil(); #向上取整

select ceil(3.1) from dual;

floor(); #向下取整

select floor(3.9) from dual;

truncate(); #截取小数位

select truncate(3.1234567, 2) from dual;
```
##### 字符串类
```
3.字符串类

ucase(); #转换为大写

select ucase('hello world') from dual;

lcase(); #转换为小写

select lcase('HELLO WORLD') from dual;

left(); #从左边开始截取到指定的位置

LEFT('Hello World', 5)，它将返回'Hello'

select left('1234567890', 3) from dual;

right();#从右边开始截取到指定的位置

select right('1234567890', 3) from dual;

substring(); #从指定位置开始截取指定个字符

select substring('1234567890', 3, 5) from dual;
```

#### 数据分组 group by TODO
某个员工信息表结构和数据如下：  
  id  name  dept  salary  edlevel  hiredate   
      1 张三 开发部 2000 3 2009-10-11  
      2 李四 开发部 2500 3 2009-10-01  
      3 王五 设计部 2600 5 2010-10-02  
      4 王六 设计部 2300 4 2010-10-03  
      5 马七 设计部 2100 4 2010-10-06  
      6 赵八 销售部 3000 5 2010-10-05  
      7 钱九 销售部 3100 7 2010-10-07  
      8 孙十 销售部 3500 7 2010-10-06   
例如，我想列出每个部门最高薪水的结果，sql语句如下：  
**SELECT DEPT, MAX(SALARY) AS MAXIMUM FROM STAFF GROUP BY DEPT**  
查询结果如下：  
      DEPT  MAXIMUM   
      开发部 2500  
      设计部 2600  
      销售部 3500
```
1. 数据分组 group by

select 分组字段 || 聚合函数 from 表名 group by 分组字段;

- 需求: 要求统计表中一共有多少个城市
select city from stu;
select city from stu group by city;

- 需求: 要求统计每个城市中有多少个人
select city, count(*) from stu group by city;

注意点:
- 在对数据进行分组的时候, select 后面必须是分组字段或者聚合函数, 否则就只会返回第一条数据

select city from stu group by city;

select name from stu group by city;

select city, group_concat(name) from stu group by city;
```
#### 条件查询 having TODO

```
1.条件查询 having:

- having和where很像都是用来做条件查询的

- 但是where是去数据库中查询符合条件的数据, 而having是去结果集中查询符合条件的数据

select * from stu where city='北京';

select * from stu having city='北京';

select name, age from stu where city='北京';

select name, age from stu having city='北京';

#Unknown column 'city' in 'having clause'

需求: select city from stu group by city;

需求: select city, avg(score) from stu group by city;

需求: select city, avg(score) as average from stu group by city;

需求: select city, avg(score) as average from stu group by city having average>=60;
```
#### 分页 limit
```
代码示例:
语句1：select * from student limit 9,4
语句2：slect * from student limit 4 offset 9
// 语句1和2均返回表student的第10、11、12、13行  
//语句2中的4表示返回4行，9表示从表的第十行开始

select 字段 from 表 limit 索引, 个数;

select * from stu limit 0, 3;

select * from stu limit 3, 3;
```
#### 查询选项 all distinct
```
1. 查询选项

select [查询选项] 字段名称 from 表名;

all: 显示所有查询出来的数据[默认]

distinct: 去除结果集中重复的数据之后再显示

select name from stu;

select all name from stu;

select distinct name from stu;

注意点:

如果是通过distinct来对结果集中重复的数据进行去重

那么只有所有列的数据都相同才会去重

select name, score from stu;

select distinct name, score from stu;
```
#### 完整的查询语句
```
完整的查询语句

select [查询选项] 字段名称 [from 表名] [where 条件] [order by 排序] [group by 分组] [having 条件] [limit 分页];
```

### 多表查询

```
- 多表查询只需要在单表查询基础上增加一张表即可

select * from 表名1, 表名2;

select * from stu, grade;

注意点:

- 默认情况下多表查询的结果是笛卡尔集
```
#### union
```
2. union作用

在纵向上将多张表的结果结合起来返回给我们

select * from 表名1 union select * from 表名2;

  

select id, name from stu union select id, score from grade;

注意点:

- 使用union进行多表查询, 返回的结果集的表头的名称是第一张表的名称

- 使用union进行多表查询, 必须保证多张表查询的字段个数一致

#select id, name from stu union select id, score, stuId from grade;

#The used SELECT statements have a different number of columns

- 使用union进行多表查询, 默认情况下会自动去重

#select id, name from stu union select id, name from person;

- 使用union进行多表查询, 如果不想自动去重, 那么可以在union后面加上all

#select id, name from stu union all select id, name from person;
```
#### 表的连接查询
```
1.表的连接查询

- 将多张表中'关联的字段''连接'在一起查询我们称之为'表的连接查询'

- 大白话: 查询多张表中满足条件的数据
```

##### 内连接inner join TODO
```
1.1内连接 inner join

select * from stu, grade where stu.id = grade.stuId;

select * from 表名1 inner join 表名2 on 条件;

select * from stu inner join grade on stu.id = grade.stuId;

注意点:

- 在进行多表查询的时候, 如果想查询指定的字段, 那么必须在字段名称前面加上表名才行

#select stu.id, stu.name, grade.score from stu inner join grade on stu.id = grade.stuId;

- 在内连接中只会返回满足条件的数据
```