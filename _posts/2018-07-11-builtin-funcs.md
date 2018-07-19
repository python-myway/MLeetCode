---
layout: post
title:  builtin-funcs-sorted
date:   2018-07-11 00:00:00
categories: Python
tags: Builtin functional-programming Lambda
---

* content
{:toc}

总结下编程中常用的内置函数sorted的使用
大部分翻译自[sortinghowto](https://docs.python.org/3/howto/sorting.html#sortinghowto)

## Lambda函数

lambda函数又称匿名函数，定义其的函数体比标准函数简单，但是用法和标准函数无差

```python
lambda x : x + 2

def test(x):
    return x + 2
    
# 上面的两个函数完全等价(当然这只是我现在的想法，以后我对Python理解更深，或许会有新的想法)

a = lambda x : x + 2
a(2) # 调用

lambda x, y : (x + 2, y + 2)
```

## sorted
Python的排序算法是[Timsort](https://en.wikipedia.org/wiki/Timsort)

sorted(iterable, *, key=None, reverse=False)

### 基本用法

```python
sorted([5, 2, 3, 1, 4])
# [1, 2, 3, 4, 5]

sorted({1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'})
# [1, 2, 3, 4, 5]

sorted("This is a test string from Andrew".split(), key=str.lower)
# ['a', 'Andrew', 'from', 'is', 'string', 'test', 'This']

student_tuples = [
        ('john', 'A', 15),
        ('jane', 'B', 12),
        ('dave', 'B', 10),
    ]
sorted(student_tuples, key=lambda student: student[2])
# [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]

class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age
    def __repr__(self):
        return repr((self.name, self.grade, self.age))

student_objects = [
        Student('john', 'A', 15),
        Student('jane', 'B', 12),
        Student('dave', 'B', 10),
    ]
sorted(student_objects, key=lambda student: student.age)
# [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]

```

### 使用标准库中的cmp_key

```python
student_tuples = [
        ('john', 'A', 15),
        ('jane', 'B', 12),
        ('dave', 'B', 10),
    ]
class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age
    def __repr__(self):
        return repr((self.name, self.grade, self.age))
student_objects = [
        Student('john', 'A', 15),
        Student('jane', 'B', 12),
        Student('dave', 'B', 10),
    ]    
from operator import itemgetter, attrgetter
sorted(student_tuples, key=itemgetter(2))
# [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
sorted(student_objects, key=attrgetter('age'))
# [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
sorted(student_tuples, key=itemgetter(1,2))
# [('john', 'A', 15), ('dave', 'B', 10), ('jane', 'B', 12)]
sorted(student_objects, key=attrgetter('grade', 'age'))
# [('john', 'A', 15), ('dave', 'B', 10), ('jane', 'B', 12)]
```

### 排序稳定性&连续排序

```python
class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age
    def __repr__(self):
        return repr((self.name, self.grade, self.age))
student_objects = [
        Student('john', 'A', 15),
        Student('jane', 'B', 12),
        Student('dave', 'B', 10),
    ]    
from operator import itemgetter, attrgetter
# 当被排序的数据的键值相等时，那么排序输出应该保留这些数据的原始顺序
data = [('red', 1), ('blue', 1), ('red', 2), ('blue', 2)]
sorted(data, key=itemgetter(0))
# [('blue', 1), ('blue', 2), ('red', 1), ('red', 2)]

# 利用这个特性可以对数据进行连续排序
# list也有一个sort方法，但是list.sort()补返回任何值，切记
s = sorted(student_objects, key=attrgetter('age'))
sorted(s, key=attrgetter('grade'), reverse=True)
# [('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```
