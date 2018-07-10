---
layout: post
title:  Python String 学习笔记
date:   2018-07-10 00:00:00
categories: Python
tags: String
---

* content
{:toc}

对Python字符串的学习笔记

## 声明
- 单引号，双引号和双引号或者直接调用str()
- 特点：不可变序列
- 转义符和r''的使用

## 操作
- 索引和切片
- 常用内置操作方法
    - s.capitalize() s.lower() s.upper() s.swapcase() s.title()
    - s.count(sub, start=None, end=None)
    - s.endswith(suffix, start=None, end=None) s.startswith(suffix, start=None, end=None)
    - s.find(sub, start=None, end=None)
    - s.index(sub, start=None, end=None)
    - s.center(width, fillchar=None) # 'bar'.center(10, '-')
    - s.replace(old, new, count=None)
        - INPUT: 'foo bar foo baz foo qux'.replace('foo', 'grault', 2)
        - OUTPUT: 'grault bar grault baz foo qux'
    - s.zfill(width)
        - INPUT: '42'.zfill(5)
        - OUTPUT: '00042'
    - s.join(iterable)
    - s.split(sep=None, maxsplit=-1)

## FORMAT基本用法
- %-format

```python
errno = 50159747054
name = 'Bob'
'Hey %s, there is a 0x%x error!' % (name, errno)
# 'Hey Bob, there is a 0xbadc0ffee error!'
'Hey %(name)s, there is a 0x%(errno)x error!' % {"name": name, "errno": errno }
# 'Hey Bob, there is a 0xbadc0ffee error!'
```

- str.format()

```python
name = 'Bob'
errno = 50159747054
'Hello, {}'.format(name)
'Hey {name}, there is a 0x{errno:x} error!'.format(name=name, errno=errno)
```

- python 3.6+ f''

```python
name = 'Bob'
f'Hello, {name}!'
```

## encode & decode
- Python2中字符串的默认编码是Ascii，Python3中是utf-8
- 使用Python2时，经常会在模块的顶部添加 *# coding=uhf-8*, 避免出现编码错误
- unicode将所有的字符都对应上了相应的码点，而UTF-8或者ASCII码不过是对应从Unicode到字节的映射方式
- unicode到字节码(byte string)称之为encode，把从字节码(byte string)到unicode码称之为decode.

```python
s = '中国'    
s.encode('utf-8')
# b'\xe4\xb8\xad\xe5\x9b\xbd'
b'\xe4\xb8\xad\xe5\x9b\xbd'.decode('utf-8')
# '中国'
```

## 参考
- [Strings and Character Data in Python](https://realpython.com/python-strings/)
- [理解和解决Python2中的编码问题](https://blog.csdn.net/u010223750/article/details/56684096)
