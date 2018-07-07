
---
layout: post
title:  leetcode-136 Single-Number
date:   2018-03-19 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an array of integers, every element appears twice except for one. Find that single one.

## Note :

- Your algorithm should have a linear runtime complexity. 
Could you implement it without using extra memory? 

## Solution：

```
class Solution:
    """
    提交了几次都是因为时间问题被打回了
    """
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        from collections import Counter
        temp = Counter(nums)
        for key, value in temp.items():
            if value == 1:
                return key
                
# 大神的这个写法很强啊
class Solution:
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        cal=0
        for i in nums:
            cal ^= i
        return cal
```