有序,不重复,无索引。


#### method

```
Map<String,Integer> linkedhashMap1 = new LinkedHashMap<>();  
linkedhashMap1.put("tony",100);  
linkedhashMap1.put("tony",110);  
linkedhashMap1.put("bob",120);  
linkedhashMap1.put("dony",1340);  
System.out.println(linkedhashMap1);//{tony=110, bob=120, dony=1340}
```