---
layout: post
title:  leetcode-283 Move Zeroes
date:   2019-03-18 00:00:00
categories: LeetCode
tags: LeetCode-Easy Array TwoPointers
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Easy**

## Description

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

## Example

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

## Note

You must do this in-place without making a copy of the array.
Minimize the total number of operations.

## Solution

```
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = nums.count(0)
        m = len(nums)
        i = 0
        while 0 in nums:
            if nums[i] == 0:
                nums.remove(nums[i])  
            else:
                i=i+1
        for j in range(n):
            nums.append(0)
```

## [More](https://leetcode.com/problems/move-zeroes/)