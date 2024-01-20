```
//1,创建一个Set集合的对象

Set<Integer> hashset = new HashSet<>()
  
// 无序 不重复  
hashset.add(333)
hashset.add(333)
hashset.add(666)
hashset.add(666)
hashset.add(777)

```

```
Set<Integer> Linkedhashset = new LinkedHashSet<>()
  
// 有序 不重复   [333, 666, 777]
Linkedhashset.add(333)
Linkedhashset.add(333)
Linkedhashset.add(666)
Linkedhashset.add(666)
Linkedhashset.add(777)

```

```
Set<Integer> treeset = new TreeSet<>()
  
// [333, 666, 777] 升序
treeset.add(777)
treeset.add(333)
treeset.add(666)
treeset.add(333)
treeset.add(666)
  
System.out.println(treeset)

```

[[Hash]]

[[Hash table,HashSet principle]]

[[binary tree]]

[[HashSet remove duplicate]]

[[LinkedHashSet原理]]

[[TreeSet]]

