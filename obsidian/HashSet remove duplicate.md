```
深入理解HashSet集合去重复的机制

HashSet集合默认不能对内容一样的两个不同对象去重复
比如内容一样的两个学生对象存入到HashSet集合中去，HashSet集合是不能去重复的

Set<Student> studentOfhashset = new HashSet<>();  
  
var stu1 = new Student("tony");  
var stu2 = new Student("tony");  
  
studentOfhashset.add(stu1);  
studentOfhashset.add(stu2);  
//[Student{name='tony', age=13, height=134.0}, Student{name='tony', age=13, height=134.0}]  
System.out.println(studentOfhashset);
```

```
HashSet集合 实现对内容一样的两个不同对象也能去重复

结论：如果希望Set集合认为2个内容一样的对象是重复的，
必须重写对象的hashCode（）和equals（）方法

idea -> gene -> hash and equals

@Override  
public boolean equals(Object o) {  
    if (this == o) return true;  
    if (o == null || getClass() != o.getClass()) return false;  
    Student student = (Student) o;  
    return age == student.age && Double.compare(student.height, height) == 0 && Objects.equals(name, student.name);  
}  
  
// 只要两个对象内容一样，返回的哈希值就是一样的。  
@Override  
public int hashCode() {  
    // Objects.hash according to 姓名 年龄 身高计算哈希值的  
    return Objects.hash(name, age, height);  
}

```