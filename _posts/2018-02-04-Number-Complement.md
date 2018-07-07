---
layout: post
title:  leetcode-476 Number-Complement
date:   2018-02-04 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a positive integer, output its complement number. 
The complement strategy is to flip the bits of its binary representation.

## Example1：

```
Input: 5

Output: 2

Explanation: The binary representation of 5 is 101 (no leading zero bits), 
and its complement is 010. So you need to output 2.
```

## Example2：

```
Input: 1

Output: 0

Explanation: The binary representation of 1 is 1 (no leading zero bits), 
and its complement is 0. So you need to output 0.
```

## Note :

- The given integer is guaranteed to fit within the range of a 32-bit signed integer.
- You could assume no leading zero bit in the integer’s binary representation.

## Solution：

```
class Solution:
    """
    思路：这题和#627很像，都是找到一个数使m^x = n,我的思路就是普通取反
    """
    def findComplement(self, num):
        """
        :type num: int
        :rtype: int
        """
        l = []
        for item in list(bin(num))[2:]:
            if item == '1':
                l.append('0')
            else:
                l.append('1')
        l.insert(0, '0b')
        return int(''.join(l), n=2)

# 大神解法
class Solution(object):
    def findComplement(self, num):
        i = 1
        while i <= num:
            i = i << 1
        return (i - 1) ^ num
```