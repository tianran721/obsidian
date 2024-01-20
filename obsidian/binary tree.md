## 二叉树

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117133337.png)
```
普通二叉树(没什么用)
每个节点包含: 值,父节点地址,左子节点地址,右子节点地址

度：每一个节点的子节点数量

树高：树的总层数

根节点：最顶层的节点

左子树: 
右子树: 9的右子树(2-1-10)
```
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117133741.png)
```
二叉查找树（二叉排序树）开发中使用
规则：
 小的存左边
 大的存右边
 一样的不存

查找: 如找 11 , 和7比大,往右边 , 和10比 大 ,往右边,找到11
排序: 从最左边开始,1-2-3...12

```
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117134208.png)

```
二叉查找树存在的问题

当数据已经是排好序的，导致查询的性能与单链表一样，查询速度变慢！


```
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117134325.png)

```
平衡二叉树: (java中使用)
左边树和右边树高度差不超过1的树

在满足查找二叉树的大小规则下，让树尽可能矮小


```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240117134544.png)

```
红黑树: 可以自平衡的二叉树
红黑树是一种增删改查数据性能相对都较好的结构。
```
