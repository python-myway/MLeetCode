---
layout: post
title:  leetcode-728 Self-Dividing-Numbers
date:   2018-03-12 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible. 

## Example：

```
Input: 
left = 1, right = 22

Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```

## Note:

- The boundaries of each input argument are 1 <= left <= right <= 10000

## Solution：

```
class Solution:
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        count = []
        for num in range(left, right+1):
            if '0' in str(num):
                continue
            temp = [int(item) for item in str(num)]
            temp2 = list(filter(lambda x: num % x == 0, temp))
            if len(temp) == len(temp2):
                count.append(num)
        return count
```