
---
layout: post
title:  leetcode-504 base-7
date:   2018-03-26 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an integer, return its base 7 string representation.

## Example1：

```
Input: 100

Output: "202"
```

## Example2：

```
Input: -7

Output: "-10"
```

## Solution：

```
class Solution:
    def convertToBase7(self, num):
        """
        :type num: int
        :rtype: str
        """
        
        if num == 0: 
            return '0'
        n, res = abs(num), ''
        while n:
            res = str(n % 7) + res
            n //= 7
        return res if num > 0 else '-' + res
```