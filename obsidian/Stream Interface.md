```
public interface Stream<T>{}
```

[07,JDK8新特性：Stream流入门,Stream流的创建\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1Cv411372m?p=149)

JDK8 新增的 API（java.util.stream)，操作集合或者数组

Stream 流大量结合了 Lambda 的语法风格来编程

[[Stream Example]]

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240113123345.png)

获取 Stream 流  
`default Stream<E> stream()` 获取当前集合对象的 Stream 流  
`public static <T> Stream<T> stream(T[] array)` 获取当前数组的 Stream 流

`public static<T> Stream<T> of(T…values)`  
获取当前接收数据的 stream 流
