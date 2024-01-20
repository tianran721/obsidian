
## Collection 的遍历方式
  
如果你要使用 for 循环遍历集合的话  
这个集合它必须是要支持索引的  
但 collection 它并没有规定集合的索引  
只有 list 系列集合才支持索引

### 迭代器 Iterator

迭代器是用来遍历集合的专用方式（数组没有迭代器)，

**Collection 集合的方法**

```
Iterator<E> iterator() 
//返回集合中的迭代器对象，该迭代器对象默认指向当前集合的第一个元素

Collection<String> c = new ArrayList<>() 
c.add（＂赵敏＂) 
c.add（＂小昭＂) 
c.add（＂素素＂)
c.add（＂灭绝＂) 
 
Iterator<String> it = c.iterator() 
 
```

### Iterator 中的常用方法

`boolean hasNext()`  
询问当前位置是否有元素存在，存在返回 true，不存在返回 false  

`E next()`

获取当前位置的元素，并同时将迭代器对象指向下一个元素处。  

我们可以通过它的 next 方法  
把当前位置处的元素值给取出来  
取出来之后呢迭代器对象指向下一个元素处

```
it.next()
it.next()
it.next()
it.next()
如果你在这个地方呢
你多取了一次的话
注意这是在取第五次
那此时it已经在这个位置
这个位置有没有数据
那这个时候它这个地方它就会出现异  (NoSuchElementException)

你在用迭代器取元素的时候不要越界了

```

我们应该使用循环结合迭代器遍历集合。

```
while(it.hasNext()){ 
	String ele =it.next() 
	System.out.println(ele) 
 }

你千万不要这样去调两次next
就相当于问了一次
同时取了两次就是会有bug的啊

```

### 增强 for

[11:03](https://www.bilibili.com/video/BV1Cv411372m/?p=137#t=663.985805)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240111230801.png)  


```
Collection<String> c = new ArrayList<>() 

for(String s : c) {
	System.out.println(s) 
}

```

增强 for 遍历集合，本质就是迭代器遍历集合的简化写法。

快捷键 : 你可以拿着这个集合对象  
然后点 for

### lambda ,forEach遍历集合 

[16:03](https://www.bilibili.com/video/BV1Cv411372m/?p=137#t=963.558139)

得益于 JDK8 开始的新技术 Lambda 表达式，提供了一种方式来遍历集合

 ```
default void forEach(Consumer<? super T> action) 
lambda遍历集合

collection它其实也有一个接口 Interface Iterable<T>
```

但是我告诉同学们  
这个 consumer 它是一个接口  
接口肯定不能直接创建对象的  
用接口的  一个匿名内部类的对象  
你可以直接去 new 一个匿名内部类的  
对象出来

```
c.forEach(new Consumer<String>(){ 
 @Override
 public void accept(String s) { {
 	System.out.println(s) 
}) 

它会让这个s先等于我们这个集合中
第一个数据
再等于第二个数据
...
```

```
内部其实还是用的增强for循环
对这个集合进行便利
这个this就代表主调
主调就是这个c集合


default void forEach(Consumer<? super T>action){ 
 Objects.requireNonNull(action) 
 for(T t:this){ 
 	action.accept(t) 
 }
}

```

Consumer 点进去有一个函数式注解的标记啊  
说明它的匿名内部类  可以用 lambda进行简化

```
c.forEach((String s) -> System.out.println(s)) 
 
c.forEach(s -> System.out.println(s) ) 
 
c.forEach(System.out::println ) 
 

```
