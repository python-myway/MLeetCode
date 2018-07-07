
---
layout: post
title:  leetcode-628 maximum-product-of-three-numbers
date:   2018-03-16 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an integer array, find three numbers whose product is maximum 
and output the maximum product.

## Example1：

```
Input: [1,2,3]

Output: 6
```

## Example2：

```
Input: [1,2,3,4]

Output: 24
```

## Note :

- The length of the given array will be in range [3,104] and all elements are in the range [-1000, 1000].
- Multiplication of any three numbers in the input won't exceed the range of 32-bit signed integer.

## Solution：

```
class Solution:
    def maximumProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = sorted(nums)
        return max(nums[-1] * nums[-2] * nums[-3], nums[-1] * nums[0] * nums[1])

# 速度是我这个的一半，其实思路是一样的
class Solution:
    def maximumProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        a, b = heapq.nlargest(3, nums), heapq.nsmallest(2, nums)
        return max(a[0] * a[1] * a[2], b[0] * b[1] * a[0])
```