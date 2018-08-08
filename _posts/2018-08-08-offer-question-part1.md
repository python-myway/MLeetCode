---
layout: post
title:  offer-question part1
date:   2018-08-08 00:00:00
categories: 剑指offer
tags: 剑指offer
---

* content
{:toc}

将剑指offer的题目用Python实现

## Question-2
- 问题：设置单例模式：设计一个类，只能生成该类的一个实例

- 装饰器模式，仅适用单线程环境

```python
def singleton(cls):
    instance_ = {}
    def wrapper(*args, **kwargs):
        if not instance_[cls]:
            instance_[cls] = cls(*args, **kwargs)
        return instance_[cls]
    return wrapper
```

- 装饰器模式，添加线程锁

```python
import threading

def singleton(cls):
    instance_ = {}
    def wrapper(*args, **kwargs):
        if not instance_[cls]:
            with threading.Lock:
                instance_[cls] = cls(*args, **kwargs)
        return instance_[cls]
    return wrapper
```

- 利用类的构造函数
```python
class Singleton:
    Instance_ = None
    def __new__(cls, *args, **kwargs):
        if not Singleton.Instance_:
            Singleton.Instance_ = super().__new__(cls, *args, **kwargs)
        return Singleton.Instance_
```

- 考点：对单例模式的理解，对多线程编程的理解

- 扩展：定义一个表示总统的类型President，可以从该类型继承出FrancePresident/AmericanPresident等类型，
这些派生类型都只能产生一个实例

```python
class MataPresident(type):
    def __call__(self, *args, **kwargs):
        pass
```

## Question-3

- 问题：找出数组中重复的数字
在一个长度为n的数组里的所有数字都在0～n-1的范围内，数组中某些数字是重复的，请找出任意一个重复的数字
例如[2, 3, 1, 0, 2, 5, 3],则输出2或者3

- 排序后遍历，时间复杂度O(nlogn)，空间复杂度O(1)

```python
def find_repeat(list_):
    list_.sort()
    cmp = None
    for num in list_:
        if num != cmp:
            cmp = num
        else:
            return cmp
```

- 利用字典，时间复杂度O(n)，空间复杂度O(n)

```python
def find_repeat(list_):
    dict_ = {}
    for num in list_:
        if not dict_[num]:
            dict_[num] = num
        else:
            return num
```

- 时间复杂度O(n)，空间复杂度O(1)

```python
def find_repeat(list_):
    for i, num in enumerate(list_):
        while list_[i] != i:
            if list_[num] == num:
                return num
            else:
                list_[i], list_[num] = list_[num], list_[i]
```

- 扩展：不改变数组找出重复的数字

```python
def find_repeat(list_):
    start, end = 0, len(list_)
    while end >= start:
        middle = (end - start) // 2
        count = counter(list_, start, middle)
        if count > middle - start + 1:
            end = middle
            continue
        else:
            start = middle
            continue
                
def counter(list_, start, end):
    cnt = 0
    for num in list_:
        if start <= num <= end:
            cnt += 1
    return cnt
```

## Question-4

- 问题：在一个二维数组中，每一行从左至右递增排序，每一列从上之下递增排序，
输入这样的数组和一个整数，判断该整数是否在数组中

```python
def find_num(list_, num):
    row = 0
    col = len(list_[0]) - 1
    while row <= len(list_) - 1 and col >= 0:
        if num == list_[row][col]:
            return True
        if num >= list_[row][col]:
            row += 1
            continue
        if num <= list_[row][col]:
            col -= 1
            continue
    else:
        return False
```