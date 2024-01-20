
工具类

```
public static <T> boolean addAll(Collection <? super T> c, T… elements) 

给 c 集合 批量添加元素

List<String> names = new ArrayList<>()

Collections.addAll（names，＂张三＂，＂王五＂，＂李四＂，＂张麻子＂)

```
[[wildcard 通配符]]

```
public static void shuffle(List<?> list) 洗牌
打乱List集合中的元素顺序
```

```
public static <T> void sort(List <T> list)  
对 List 集合中的元素进行升序排序
```

你必须让这个对象类实现是这个比较规则



public static` <T>` void sort(List`<T>` list, Comparator`<? super T>` c)  
对 List 集合中元素，按照比较器对象指定的规则进行排序

[[#方式二：使用重载的 sort 方法，创建 Comparator 接口的匿名内部类对象，然后自己制定比较规则]]

```
Arrays.sort(students, new Comparator<Student>(){
	
 	@Override
	public int compare(Student o1, Student o2) {

		return Double.compare（o1.getHeight（)，o2.getHeight（)) //升序
		 return Double.compare（o2.getHeight（)， 0o1.getHeight（)) //降序
 
}
})

```