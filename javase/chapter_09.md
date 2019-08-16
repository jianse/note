

# 第九章 集合框架 

像C++的STL一样, java也有提供给我们的容器. 它存放在java.util包下, 以Collection和Map为根的两族接口和他们的实现类为主的泛型容器

如下图:

![collection_framework](https://s2.ax1x.com/2019/08/16/mZliKf.png)

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

### 9.2.2 ArrayList实现类

### 9.2.3 LinkedList实现类

## 9.3 Set

## 9.4 Queue

## 9.5 Map

## 9.6 集合与泛型

## 9.7 Collections和Arrays工具类


## 9.8 Iterator 迭代器

## 9.9 java.util.concurrent包