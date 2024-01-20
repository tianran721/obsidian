### ArrayList 集合的底层原理

TODO

ArrayList 基于数组实现的
[[Array]]

==ArrayList 集合的底层原理==

1. 利用无参构造器创建的ArrayList集合，会在底层创建一个默认长度为 0 的数组



会用一个 size 来记录这个数 组的大小  


2. 添加第一个元素时，底层会创建一个新的长度为 10 的数组

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113094123.png)

当你第一次添加数据到里面   
他就会把这个数组呢  
扩容成一个长度为十的新数组  
交给这个 element date 来记住啊

然后把数据 a 加到 第一个位置  
接着让 size 呢指向他的第二个索引  
第二索引位置正好就是它的元素个数  
同时也是下次存入的位置

如果你再加上数据是 b 的话呢  
那么它会让这个 size 又往后移  
相当于指向二  
代表有两个数据  
也是下次存入数据的位置

3. 存满时，会扩容 1.5 倍


![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113094321.png)

4. 如果一次添加多个元素，1.5 倍还放不下，则新创建数组的长度以实际为准

```
List<string> list1 = new ArrayList<>() 

 list1.add("a") 
List<String> list2 = new ArrayList<>() 

 list2.add("a11") 
list1.addAll（list2) 
 
 
//把集合list2的数据全部倒入到List1集合
```

你比如说我前面教过同学们一种 api  
你可以把某一个集合里的数据  
全部倒到这个集合里面去  
那假如说啊我现在这个集合里面的数  
据呢  
它是 11 个数据  
我把这 11 个数据一下子往这个集合里  
面去倒

它会创建一个数组  
长度以实际为准的数组  
也就是说它会创建一个新的数组  
长度为 21 的  
就是原来这十个数据呢  
加上你新加的这 11 个数据  
创建一个长度为 21 的速度出来  
再把你的数据呢全部存进去啊

特定: 查询快,增删慢  
ArrayList 不适合：数据量  
大的同时 又要频繁的进行增删操作！
