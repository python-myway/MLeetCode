---
layout: post
title:  leetcode-374 guess-number-higher-or-lower
date:   2018-07-12 00:00:00
categories: LeetCode
tags: LeetCode-Easy BinarySearch
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Easy**

## Description

We are playing the Guess Game. The game is as follows:
I pick a number from 1 to n. You have to guess which number I picked.
Every time you guess wrong, I'll tell you whether the number is higher 
or lower.
You call a pre-defined API **guess(int num)** which returns 3 possible 
results (-1, 1, or 0):

```
-1 : My number is lower
 1 : My number is higher
 0 : Congrats! You got it!
```

## Example

n = 10, I pick 6.
Return 6.

## Solution

```
# 这道题还是很简单的，使用二分的思想，但是题目描述不太清楚，我猜可能这就是很多不喜欢的原因
# The guess API is already defined for you.
# @param num, your guess
# @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
# def guess(num):

class Solution(object):
    def guessNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        left = 1
        right = n
        while left <= right:
            mid = (left + right) // 2
            if guess(mid) == 1:
                left = mid + 1
            elif guess(mid) == -1:
                right = mid - 1
            else:
                return mid
```

## [More](https://leetcode.com/problems/guess-number-higher-or-lower/description/)