[Effective Java - Still Effective After All These Years - YouTube](https://www.youtube.com/watch?v=V1vQf4qyMXg&t=1344s)

subtype 子类

Unlike arrays, generic types are invariant  不变的
— That is, List<string> is not a subtype of List<object> 

-Good for compile-time type safety, but inflexible
Wildcard types provide additional API flexibility

List<string> is a subtype of List<? extends object> 

List<object> is a subtype of List<? super string>