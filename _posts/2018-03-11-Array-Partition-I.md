---
layout: post
title:  leetcode-561 Array-Partition-I
date:   2018-03-11 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given an array of **2n** integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

## Example：

```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```

## Note:

- n is a positive integer, which is in the range of [1, 10000].
- All the integers in the array will be in the range of [-10000, 10000].

## Solution：

```
class Solution:
    """
    思路：我的解法太。。。
    大神解法：sum(sorted(nums)[::2])
    """
    def sort(self, _list):
        if len(_list) <= 1:
            return _list
        pivot = _list[len(_list) // 2]
        left = [x for x in _list if x < pivot]
        middle = [x for x in _list if x == pivot]
        right = [x for x in _list if x > pivot]
        return self.sort(left) + middle + self.sort(right)
    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        new = self.sort(nums)
        return sum(new[::2])
```