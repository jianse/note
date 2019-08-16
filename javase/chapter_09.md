

# 第九章 集合框架 

像C++的STL一样, java也有提供给我们的容器. 它存放在java.util包下, 以Collection和Map为根的两族接口和他们的实现类为主的泛型容器

如下图:

![collection_framework](https://s2.ax1x.com/2019/08/16/mZ0zgU.png)

## 9.1 Collection

Collection接口定义了所有Collection的公共行为

主要的方法有:
- 判断Collection是否为空
```
isEmpty()
```

- 向Collection中添加元素
```
add(T item);
```

- 移除Collection中的元素
```
remove(T item)
```

- 获得Collection的迭代器
```
iterate();
```

## 9.2 List

List接口是Collection接口下的一支,List是Collection的更具体的一类

### 9.2.1 List的特点

1. 元素(逻辑上)以线性方式存储
2. 可以存放重复对象
3. 元素是有序的
4. 可以进行随机存取

### 9.2.2 Vector

Vector是java 1.0 版本时就引入的集合实现类,它实现了一个可以同台增长的数组,可以根据所存入的元素动态的伸缩.

Vector是线程安全的,所以Vector可以在多线程场景下安全的使用,但也因为线程安全使其效率有所限制

如果不需要线程安全的使用可伸缩的数组可以使用[ArrayList](#arraylist)

### 9.2.3 Stack

Stack是一种先进后出(LIFO)的容器,它是Vector的子类,这意味着Stack也是线程安全的.

Stack类为自身提供独立的操作方法

- 判断栈是否为空
```
empty()
```
- 查看栈顶元素并且不出栈
```
peek()
```
- 弹栈 : 出栈栈顶元素
```
pop()
```
- 压栈 : 将元素压入栈顶
```
push(E item)
```
- 查询元素与栈顶的距离
```
search(Object o)
```

Stack也是java 1.0 时引入的 , java 1.2 时引入了[Deque](#deque)接口,Deque接口及其实现提供了更完整和一致的LIFO堆栈操作集，应优先使用此类。

### 9.2.4 ArrayList :id=arraylist

ArrayList顾名思义就是内部有数组实现的List,它为我们封装了一系列数组操作,让我们不必考虑增删改查时数组怎样变化,数组如何扩展,如何缩小,然后向我们提供增删改查的接口.

ArrayList实现了RandomACcess接口,这是一个标记接口(没有方法的接口),这意味着ArrayList支持常数时间复杂度的随机访问.

ArrayList的访问效率较高,插入删除效率较低,适用于多访问少修改的使用场景.

### 9.2.5 LinkedList

LiskedList是List的链表实现

## 9.3 Set

### 9.3.1 Set的特点

### 9.3.2 HashSet

### 9.3.3 LinkedHashSet

### 9.3.4 TreeSet

## 9.4 Queue

### 9.4.1 Queue的特点

### 9.4.2 PriorityQueue

### 9.4.3 Deque :id=deque

### 9.4.4 ArrayDeque

## 9.5 Map

### 9.5.1 Map特点

### 9.5.2 HashMap

### 9.5.3 LinkedHashMap

### 9.5.4 HashTable

### 9.5.5 Properties

## 9.6 集合、泛型、多态与面向接口

## 9.7 Collections和Arrays工具类

## 9.8 Iterator 迭代器

## 9.9 java.util.concurrent包