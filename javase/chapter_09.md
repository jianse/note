

# 第九章 集合框架 

像C++的STL一样, java也有提供给我们的容器. 它存放在java.util包下, 以Collection和Map为根的两族接口和他们的实现类为主的泛型容器

如下图:

![collection_framework](https://s2.ax1x.com/2019/08/16/mZ0zgU.png)

## 9.1 Collection

Collection接口定义了所有Collection的公共行为

主要的方法有:

方法名|操作
:--:|:--:
`isEmpty()`|判断Collection是否为空
`contains(Object o)`|判断元素是否在Collection中
`add(T item);`|向Collection中添加元素
`remove(T item)`|移除Collection中的元素
`iterate();`|获得Collection的迭代器


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

方法名|操作
:--:|:--:
`empty()`| 判断栈是否为空
`peek()`| 查看栈顶元素并且不出栈
`pop()`|弹栈 : 出栈栈顶元素
`push(E item)`|压栈 : 将元素压入栈顶
`search(Object o)`|查询元素与栈顶的距离


Stack也是java 1.0 时引入的 , java 1.2 时引入了[Deque](#deque)接口,Deque接口及其实现提供了更完整和一致的LIFO堆栈操作集，应优先使用此类。

### 9.2.4 ArrayList :id=arraylist

ArrayList顾名思义就是内部有数组实现的List,它为我们封装了一系列数组操作,让我们不必考虑增删改查时数组怎样变化,数组如何扩展,如何缩小,然后向我们提供增删改查的接口.

ArrayList实现了RandomACcess接口,这是一个标记接口(没有方法的接口),这意味着ArrayList支持常数时间复杂度的随机访问.

ArrayList的访问效率较高,插入删除效率较低,适用于多访问少修改的使用场景.

ArrayList 是 java 1.2 时集合框架引入的它与Vector的实现很相似 , 但是ArrayList时线程不安全的.所以相应的它的效率要比Vector高.

### 9.2.5 LinkedList

LiskedList是List的链表实现,链表解决了数组插入删除慢的缺点 , Java中所有链表实际上都是双向链接的,即每个节点同时存放着一个向前的和一个向后的引用 . 所以LinkedList也同时也是Deque接口的实现类.

LinkedList插入删除效率较高,但是不能进行常数复杂度的随机访问,所以适用于多增删,少随机访问的使用场景.

### 9.2.6 时间复杂度比较

操作|ArrayList时间复杂度|LinkedList时间复杂度
:--:|:--:|:--:
读取get(index)          |O(1)   |O(n)
添加add(E)              |O(1)   |O(1)
指定位置添加add(index,E)|O(n)   |O(n)
删除remove(E)           |O(n)   |O(1)

## 9.3 Set

Set是Collection接口下的另一支 , 代表了数学上的集合 , 元素是无序的 , 并且不包含重复的元素

### 9.3.1 Set的特点

1. 元素是无序的
2. 没有重复元素

### 9.3.2 HashSet

HashSet 是借助[HashMap](#_952-hashmap) 实现的,将要插入的值当作HashMap的键,值是一个固定的Object对象,因为HashMap的key不能重复所以HashSet的元素就不能重复 .

### 9.3.3 LinkedHashSet

LinkedHashSet继承自HashSet , 源码更少、更简单 , 与HashMap唯一的区别是LinkedHashSet内部使用的是[LinkedHashMap](#_953-linkedhashmap)。这样做的意义或者好处就是LinkedHashSet中的元素顺序是可以保证的 , 也就是说遍历序和插入序是一致的。

### 9.3.4 TreeSet

TreeSet实现了NavigableSet接口 , 该接口定义了一些搜索目标的方法 , 并且该接口扩展了 SortedSet接口 , 所以TreeSet是一个可排序并且可以搜索的集合.

TreeSet包装了一个TreeMap其中Set中的元素是[TreeMap](#_954-treemap)的键,而值是一个常量.所有的方法都委托给了TreeMap

因为TreeSet要实现对元素的排序所以元素必须实现Comparable接口以便对元素进行比较.

## 9.4 Queue

Queue接口是Collection接口的子类,也是集合框架的一员 . Queue接口通常(但不一定)定义了一种先进先出(LIFO)的数据结构

Queue提供了两种操作Queue的方式

1. 出错时抛出异常
2. 出错时返回特殊值

: **队列方法总结**

&nbsp;|抛出异常|返回特殊值
:--:|:--:|:--:
插入|add(e)|offer(e)
删除|remove()|poll()
检查|element()|peek()

Queue实现通常不允许插入`null`元素,即使允许也不应该被插入到Queue中,因为在poll()方法中返回null用来指示队列为空.

### 9.4.1 Queue的特点

1. 先进先出(LIFO)
2. 一般上不允许插入`null`
3. 一般不支持随机访问
 
### 9.4.2 PriorityQueue

基于优先级堆的无界优先级队列。优先级队列的元素根据其 自然顺序排序，或者根据使用的Comparator 构造函数在队列构造时提供。优先级队列不允许null元素。依赖于自然排序的优先级队列也不允许插入不可比较的对象（这样做可能导致 ClassCastException）。

!> **此实现不是同步的** , PriorityQueue 如果任何线程修改队列，则多个线程不应同时访问实例。相反，使用线程安全PriorityBlockingQueue类。

### 9.4.3 Deque :id=deque

Deque接口扩展了Queue接口提供了一个双端队列,即既可以从队列的两端出入队的队列

<table>
 <caption>Summary of Deque methods</caption>
  <thead>
  <tr>
    <td rowspan="2"></td>
    <th scope="col" colspan="2"> First Element (Head)</th>
    <th scope="col" colspan="2"> Last Element (Tail)</th>
  </tr>
  <tr>
    <th scope="col" style="font-weight:normal; font-style:italic">Throws exception</th>
    <th scope="col" style="font-weight:normal; font-style:italic">Special value</th>
    <th scope="col" style="font-weight:normal; font-style:italic">Throws exception</th>
    <th scope="col" style="font-weight:normal; font-style:italic">Special value</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <th scope="row">Insert</th>
    <td><code>addFirst(e)</code></td>
    <td><code>offerFirst(e)</code></td>
    <td><code>addLast(e)</code></a></td>
    <td><code>offerLast(e)</code></td>
  </tr>
  <tr>
    <th scope="row">Remove</th>
    <td><code>removeFirst()</code></td>
    <td><code>pollFirst()</code></td>
    <td><code>removeLast()</code></td>
    <td><code>pollLast()</code></td>
  </tr>
  <tr>
    <th scope="row">Examine</th>
    <td><code>getFirst()</code></td>
    <td><code>peekFirst()</code></td>
    <td><code>getLast()</code></td>
    <td><code>peekLast()</code></td>
  </tr>
  </tbody>
 </table>

Deque扩展了Queue.当deque用作队列时，会产生FIFO（先进先出）行为。元素在双端队列的末尾添加并从头开始删除。从Queue接口继承的Deque方法与下表中指示的方法完全等效 ：

**Queue与Deque方法比较**

Queue方法|Deque方法
:--:|:--:
add(e)      |addLast(e)
offer(e)    |offerLast(e)
remove()    |removeFirst()
poll()      |pollFirst()
element()   |getFirst()
peek()      |peekFirst()

同时Deque也可以当作Stack使用

**Stack与Deque方法比较**

Stack方法|Deque方法
:--:|:--:
push(e)     |addFirst(e)
pop()       |removeFirst()
peek()      |peekFirst()

### 9.4.4 ArrayDeque

## 9.5 Map

### 9.5.1 Map特点

### 9.5.2 HashMap

### 9.5.3 LinkedHashMap

### 9.5.4 TreeMap

### 9.5.5 HashTable

### 9.5.6 Properties

## 9.6 集合、泛型、多态与面向接口

## 9.7 Collections和Arrays工具类

## 9.8 Iterator 迭代器

## 9.9 java.util.concurrent包