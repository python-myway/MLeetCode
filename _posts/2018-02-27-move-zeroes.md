---
layout: post
title:  leetcode-283 move-zeroes
date:   2018-02-27 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given an array nums, write a function to move all 0's to the end of it 
while maintaining the relative order of the non-zero elements.
For example, given nums = [0, 1, 0, 3, 12], after calling your function, 
nums should be [1, 3, 12, 0, 0].

## Note :

- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.

## Solution：

```
class Solution:
    """
    思路：这个解法很有意思啊，不是我想的：（
    """
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        length = len(nums)
        lastIndex = 0
        for p1 in range(0,length):
            if nums[p1] != 0:
                nums[lastIndex] = nums[p1]
                lastIndex  = lastIndex + 1
        while lastIndex < length:
            nums[lastIndex] = 0
            lastIndex = lastIndex + 1
```