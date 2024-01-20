# Set Collection

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113110114.png)

Set 系列集合特点：无序 不重复 无索引 

HashSet：无序,不重复,无索引。(用的是比较多)

LinkedHashSet：有序,不重复,无索引。

TreeSet：排序,不重复,无索引。  
默认是升序排序的

## method

```
Set<String> hashSet = new HashSet<>()
  
Collections.addAll(hashSet,"tom","bob")
  
Stream<String> stream1 = hashSet.stream()

```
