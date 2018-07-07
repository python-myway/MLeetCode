---
layout: post
title:  leetcode-461 Hamming-Distance
date:   2018-02-16 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

The **Hamming distance**(汉明距离是一个概念，它表示两个（相同长度）字对应位不同的数量，我们以d（x,y）表示两个字x,y之间的汉明距离。对两个字符串进行异或运算，并统计结果为1的个数，那么这个数就是汉明距离) between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

## Example：

```
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

## Note:

- 0 ≤ x, y < 2^31

## Solution：

```
class Solution:
    """
    思路：先将x，y转换成二进制，再进行异或运算
    """
    def hammingDistance(self, x, y):
        """
        :type x: int
        :type y: int
        :rtype: int
        """
        list_x = list(bin(x))[2:]
        list_y = list(bin(y))[2:]
        len_x = len(list_x)
        len_y = len(list_y)
        temp = ['0'] * abs(len_x - len_y)
        if len_x > len_y:
            temp.extend(list_y)
            list_y = temp
        else:
            temp.extend(list_x)
            list_x = temp
        l = list(map(lambda a: a[0] + a[1], zip(list_x, list_y)))
        return l.count('10') + l.count('01')
```