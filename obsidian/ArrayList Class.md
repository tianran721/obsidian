

### 数组和集合的区别

数组定义完成后，长度就固定了

集合大小可变

ArrayList `<E>` E 代表创建集合对象时可以指定具体的引用数据类型

不写<> 代表集合可以存储任意类型的数据

ArrayList `<String>` list = new ArrayList `<String>`()

JDK1.7 开始支持的简写法: ArrayList `<String>` list = new ArrayList `<>`()

### ArrayList 构造器

ArrayList() 构造一个初始容量为 10 的空列表。,超过 10 后会自动扩容

```
ArrayList(int length) 指定容器初始大小
```

#### ArrayList method

public boolean add(E e)  
将指定的元素添加到此集合的末尾

public void add(int index,E element)  
在此集合中的指定位置插入指定的元素

public E get(int index)  
返回指定索引处的元素

public int size()  
返回集合中的元素的个数

public E remove(int index)  
删除指定索引处的元素，返回被删除的元素

public boolean remove(Object o)  
删除指定的元素，返回删除是否成功

public E set(int index,E element)  
修改指定索引处的元素，返回被修改的元素 (当有二个相同数据时,默认删除第一次出现的数据)


打印集合时,会打印集合内容 (重写了 toString)