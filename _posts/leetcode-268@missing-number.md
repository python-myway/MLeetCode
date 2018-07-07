
---
layout: post
title:  leetcode-268 missing-number
date:   2018-02-17 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

## Example1：

```
Input: [3,0,1]

Output: 2
```

## Example2：

```
Input: [9,6,4,2,3,5,7,0,1]

Output: 8
```

## Note :

- Your algorithm should run in linear runtime complexity. Could you implement 
it using only constant extra space complexity?

## Solution：

```
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return  sum(range(len(nums) + 1)) - sum(nums)
        
        
# 速度快，法二是纯数学解法啊
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        """
        # 法一：
        for i, x in enumerate(nums):
            if abs(x) >= len(nums) or x < -len(nums):
                continue
            if nums[abs(x)] == 0:
                nums[abs(x)] = -len(nums) -1
                if x != 0:
                    nums[0] = -(abs(nums[0]))
            else:
                nums[abs(x)] *= -1
        for i in range(len(nums)):
            if nums[i] >= 0:
                return i
        else:
            return len(nums)
        """
        
        return len(nums) * (len(nums) + 1) // 2 - sum(nums)
```