---
layout: post
title:  leetcode-693 Binary-Number-with-Alternating-Bits
date:   2018-03-19 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a positive integer, check whether it has alternating bits: namely, 
if two adjacent bits will always have different values.

## Example1:
```
Input: 5

Output: True

Explanation:
The binary representation of 5 is: 101
```

## Example2:
```
Input: 7

Output: False

Explanation:
The binary representation of 7 is: 111.
```

## Example3:
```
Input: 11

Output: False

Explanation:
The binary representation of 11 is: 1011.
```

## Example4:
```
Input: 10

Output: True

Explanation:
The binary representation of 10 is: 1010.
```

## Solution：

```
class Solution:
    def hasAlternatingBits(self, n):
        """
        :type n: int
        :rtype: bool
        """
        temp = n >> 1
        if '0' in bin(n ^ temp)[2:]:
            return False
        return True

# 这个是Python3中最快的答案
class Solution:
    def hasAlternatingBits(self, n):
        """
        :type n: int
        :rtype: bool
        """
        x = 1
        w = -1
        while x<=n:
            if n&1 == 1:
                if w == 1:
                    return False
                else:
                    w = 1
            else:
                if w == 0:
                    return False
                else:
                    w = 0
            n=n>>1
        return True
```