List 系列集合特点：有序，可重复，有索引  
ArrayList：有序，可重复，有索引。  
LinkedList：有序，可重复，有索引。

[[List traversal]]

# method

```
void add(int index,E element)
在此集合中的指定位置插入指定的元素

List＜String＞ list = new ArrayList<>（) 

list.add（＂蜘蛛精＂) 
list.add（＂至尊宝＂) 
list.add（＂至尊宝＂) 
list.add（＂牛夫人＂) 
list.add（2,＂紫霞仙子＂)

```

```
E remove(int index)
删除指定索引处的元素，返回被删除的元素
E set(int index,E element)
修改指定索引处的元素，返回被修改的元素
E get(int index)
返回指定索引处的元素
```

获取 List 集合的 Stream 流

```
List<String> arrayListOfName = new ArrayList<>()
  
Collections.addAll(arrayListOfName,"tom","bob","tony")
  
Stream<String> stream = arrayListOfName.stream()
  
System.out.println(stream)

stream.filter(name->name.startsWith("t")).forEach(item-> System.out.println(item))

  
//java.util.stream.ReferencePipeline$Head@35bbe5e8
```

TODO:[07,JDK8新特性：Stream流入门,Stream流的创建\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1Cv411372m?p=149)
