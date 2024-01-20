![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110224807.png)

# 把集合中所有以 " 张 " 开头，且是 3 个字的元素存储到一个新的集合

```
List<String> list = new ArrayList<>() 
// names : old Collections
for (String name : names){
	 if（name.startsWith（＂张＂)＆＆name.length（)==3){
		 list.add(name)
	 }		  	    
}

```

使用 Stream 流来解决这个需求

```
steam 是支持链式编程的

(lambda已经成为java代码的一种书写标准)

List<String> list2 = names.stream().filter(s -> s.startsWith("张")&&s.length()==3).collect(Collectors.tolist()) 
 
再调它的一个方法叫collect

这个参数呢他叫collectors to list
就是别人已经设计好的你可以把它记住

```
