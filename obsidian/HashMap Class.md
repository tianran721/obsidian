 无序,不重复,无索引  
（用的最多)

# method

put 

```
Map<String,Integer> hashMap1 = new HashMap<>();
        hashMap1.put("tony",100);
        hashMap1.put("tony",110);
        // 后面重复的数据会覆盖前面的数据（键)
        hashMap1.put("bob",120);
        hashMap1.put("dony",1340);
        System.out.println(hashMap1);//{tony=110, bob=120, dony=1340}


```
