## Arrays 类

Arrays 用来操作数组的一个工具类。

```
public static String toString（类型［］arr)  
返回数组的内容

int[] arr = {10, 20, 30, 40, 50, 60} 

System.out.println(Arrays.toString(arr))
```


```
public static 类型［］ copyOfRange（类型［］arr，起始索引，结束索引)(包前不包后)  
拷贝数组（指定范围)
```

1. public static copyOf（类型［］arr，int newLength)  
拷贝数组 ,比原数组长 补的是 0

可以指定新数组的长度。

1. public static setAll(double[] array, IntToDoubleFunction generator)

把数组中的原数据改为新数据又存回原数组

IntToDoubleFunction: 函数接口,接受匿名内部类对象

把所有的价格都打八折，然后又存进去。

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110144033.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240110144620.png)

1. public static void sort（类型［］arr ) 对数组进行排序（默认是升序排序)

[[sorting objects stored in array]]