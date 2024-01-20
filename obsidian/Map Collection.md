双列集合

脉劫 5 元  
康帅傅 5 元  
粤利粤 10 元

{key1=value1，key2=value2，key3=value3，…｝，一次需要存一对数据做为一个元素.

"key=value" 称为一个键值对／键值对对象／一个 Entry 对象

键是不允许重复的

# Map 集合业务场景下使用

shopping cart

# Map 集合体系

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240118150454.png)  
[[HashMap Class]]  
[[LinkedHashMap Class]]

[[TreeMap]]

#### method

public int size（）：获取集合的大小

```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
System.out.println(TreeMap1.size());//3
```
public void clear（）：清空集合
public boolean isEmpty(): 判断集合是否为空,为空返回true 
public V get(Object key)：根据键获取对应值

```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
System.out.println(TreeMap1.get(100));//asd
```
public V remove（Object key）：根据键删除整个元素（删除键会返回键的值）：
public boolean containsKey（Object key）：判断是否包含某个键，包含返回true
public boolean containsValue（Object value）： 判断是否包含某个值。
```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
System.out.println(TreeMap1.containsValue("a"));//false
```
public Set`<K>` keySet（）：获取Map集合的全部键。
```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
System.out.println(TreeMap1.keySet()); //[100, 120, 1340]
```

.public Collection`<V>` values（）； 获取Map集合的全部值。
```
Collection<String> values = TreeMap1.values(); //[asd, b, c]
```

putAll() 把map2 集合中的元素全部copy一份到map1集合中

```
Map<Integer,String> TreeMap1 = new TreeMap<>();  
TreeMap1.put(100,"a");  
TreeMap1.put(100,"asd");  
TreeMap1.put(120,"b");  
TreeMap1.put(1340,"c");  
  
Map<Integer,String> TreeMap2 = new TreeMap<>();  
TreeMap2.putAll(TreeMap1);  
System.out.println(TreeMap2);//{100=asd, 120=b, 1340=c}
```

[[Map traverasal]]