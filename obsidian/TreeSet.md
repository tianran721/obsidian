```
底层是基于红黑树实现的排序


Set<Integer> treeset1 = new TreeSet<>();  
treeset1.add(3);  
treeset1.add(1);  
treeset1.add(0);  
System.out.println(treeset1);//[0, 1, 3]
```
[[Excalidraw/treeset|treeset]]


```
对于字符串类型：默认按照首字符的编号升序排序。
对于自定义类型如Student对象，TreeSet默认是无法直接排序的。
```

## TreeSet集合存储自定义类型的对象时，必须指定排序规则

```
方式一
让自定义的类（如学生类）实现Comparable接口，重写里面的compareTo方法来指定比较规则。
// generics require declaring what to be compared
public class Student implements Comparable<Student>{
	// in ascending order by age 
	@Override  
	public int compareTo(Student o) {  
	 return this.age - o.age;  
	}
}

===
Set<Student> students = new TreeSet<>();  
students.add(new Student("bob",23, 1.7));  
students.add(new Student("tom",22, 1.8));  
students.add(new Student("june",26, 1.5));  
students.add(new Student("tim",22, 1.5));


//[Student{name='tom', age=22, height=1.8}, Student{name='bob', age=23, height=1.7}, Student{name='june', age=26, height=1.5}]  

System.out.println(students);

```

```
方式二
通过调用TreeSet集合有参数构造器，可以设置Comparator对象（比较器对象，用于指定比较规则。

public TreeSet (Comparator<? super E> comparator)




Set<Student> students = new TreeSet<>(new Comparator<Student>() {  
    @Override  
    public int compare(Student o1, Student o2) { 
    	// compare will return -1 , 1 , 0 
        return Double.compare(o1.getHeight() , o2.getHeight());  
    }  
});  
	students.add(new Student("bob", 1.7));  
	students.add(new Student("tom", 1.8));  
	students.add(new Student("june", 1.5));  
	students.add(new Student("tim", 1.5));
	  
//[Student{name='june', age=26, height=1.5}, Student{name='bob', age=23, height=1.7}, Student{name='tom', age=22, height=1.8}]  
	System.out.println(students);
 

```


```
注意：如果类本身有实现Comparable接口，TreeSet集合同时也自带比较器，默认使用集合自带的比较器排序。

lambda simplify Comparator

Set<Student> students = new TreeSet<>(( o1,  o2)-> Double.compare(o1.getHeight() , o2.getHeight()));

```