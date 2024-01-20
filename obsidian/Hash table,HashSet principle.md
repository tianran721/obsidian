# 哈希表

```
 哈希表是一种增删改查数据性能都较好的结构
 查:使用元素的哈希值对数组的长度求余计算出数组索引,然后根据链表找到数据
```
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117131442.png)  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117131635.png)  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117131821.png)  
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117131953.png)
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117133047.png)

```
JDK8之前: 哈希表:数组+链表


1.第一次创建一个默认长度16的数组，默认加载因子为0.75，数组名table
2.使用元素的哈希值对数组的长度求余计算出当前元素应存入的位置
(如:163对16求余数=3)
3.判断当前位置是否为null，如果是null直接存入

(如:1603对16求余数=3)
4.如果不为null，表示有元素，则调用equals方法比较 相等，则不存数据
不相等，则存入数组
	JDK8之前，新元素存入数组，占老元素位置，老元素挂下面
	JDK8开始之后，新元素直接挂在老元素下面

5.链表会过长，导致查询性能降低,
6.一旦数组占满12个就会扩容(16*0.75=12)
7.JDK8开始，当链表长度超过8，且数组长度＞＝64时，自动将链表转成红黑树
```
