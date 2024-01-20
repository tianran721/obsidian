# List 遍历方式

 ①for 循环（因为 List 集合有索引)

```
你直接用 list 这个集合对象  
再点 fori 一回车  
他就可以把这个 for 循环的架子写好

//（1)for循环
for(int i= 0
 i < list.size()
 i++) { 
	String s = list.get(i) 
 	System.out.println(s) 
}

```

 ② 迭代器  

```
 //（2)迭代器。
Iterator<String> it = list.iterator()  
while(it.hasNext()){
	System.out.println(it.next()) 
 }
```

③增强 for 循环 

```
增强for循坏
for (String s:list){ 		    		
    System.out.println(s) 
 }
```

④Lambda 表达式

```
// JDK 1.8开始之后的Lambda表达式 
list.forEach(s->{ System.out.println(s) }) 
```
