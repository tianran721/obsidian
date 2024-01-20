Objects 是一个工具类，提供了很多操作对象的静态方法给我们使用。

# static method

public static boolean equals(Object a, Object b)  
先做非空判断，再比较两个对象

字符串重写了 equals() 比较的是字符串内容

public static boolean isNull(Object obj)

判断对象是否为 null，为 null 返回 true

public static boolean nonNull(Object obj)  
判断对象是否不为 null，不为 null 则返回 true
