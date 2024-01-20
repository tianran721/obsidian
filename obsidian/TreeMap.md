有序,不重复,无索引。


#### method

```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
System.out.println(TreeMap1);//{100=asd, 120=b, 1340=c}
```