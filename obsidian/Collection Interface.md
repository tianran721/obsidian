## 概述 Collection

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111154605.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111164312.png)

Collection 代表单列集合，每个元素只包含一个值。

Map 代表双列集合，键值对

首先 collection 实际上是一个接口  并且它是支持泛型的

而 collection 下面呢它又分了很多的子接口  
比如说一个 list 的接口  
还有一个是 set 接口  也是支持泛型的

### Collection 集合体系

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111155033.png)

List 接口的实现类: ArrayList,LinkedList


**List 系列集合**：添加的元素是有序,可重复,有索引。


**Set 系列集合**：添加的元素是无序,不重复,无索引。

[[HashSet Collection]]



[[TreeSet]]

# Collection 的方法

Collection 是单列集合的祖宗

  
```
public Object［］ toArray（)：集合转成数组
 
Object[] arr = collection.toArray();

```


为什么返回的是 Object 类型?
原因:集合里面 泛型  
在运行阶段的时候**已经擦除**了  


**集合转成字符串数组**

```
String[] arr2 = c.toArray(new String[c.size()]); System.out.println(Arrays.toString(arr2));

指定的一个String 类型的数组给到底层  
```


```
public boolean addAll(Collection<? extends E> c)

一个集合的全部数据倒入到另一个集合中去
```

`public boolean add(E e)`  
把给定的对象添加到当前集合中

`public void clear()`  
清空集合中所有的元素

`public boolean remove(E e)`  
把给定的对象 from 当前集合中删除

`public boolean contains(Object obj)`  
判断当前集合中是否包含给定的对象

`public boolean isEmpty()`  
判断当前集合是否为空

`public int size()`  
返回集合中元素的个数。

[[Collection traverse]]

[[method reference]]


### 案例:遍历集合中的自定义对象

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117223101.png)
需求  : 展示多部电影信息  
①：每部电影都是一个对象，多部电影要使用集合  
②：遍历集合中的 3 个电影对象，输出每部电影的详情信息。

你将来做前端的时候呢
它实际上也是把后台的这些对象  扔到一个集合里面 
然后把这个集合扔到前端  
前端 再把集合中的这些对象都遍历出来  展示一下

集合存储对象是存对象的地址信息  
他到时候根据地址  
再去堆内存中找这些对象  


### 集合存储对象的原理

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113091219.png)


