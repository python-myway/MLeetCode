
---
layout: post
title:  leetcode-697 degree-of-an-array
date:   2018-04-10 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a non-empty array of non-negative integers nums, the degree of 
this array is defined as the maximum frequency of any one of its elements.

Your task is to find the smallest possible length of a (contiguous) subarray 
of nums, that has the same degree as nums.

## Example1：

```
Input: [1, 2, 2, 3, 1]

Output: 2

Explanation: 
The input array has a degree of 2 because both elements 1 and 2 appear twice.
Of the subarrays that have the same degree:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
The shortest length is 2. So return 2.
```

## Example2：

```
Input: [1,2,2,3,1,4,2]

Output: 6
```

## Note :

- nums.length will be between 1 and 50,000.
- nums[i] will be an integer between 0 and 49,999.

## Solution：

```
class Solution:
    def findShortestSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        from collections import Counter
        c = Counter(nums)       
        first, last = {}, {}
        for i, v in enumerate(nums):
            first.setdefault(v, i)
            last[v] = i
        degree = max(c.values())
        return min(last[v] - first[v] + 1 for v in c if c[v] == degree)
        
# 这个快了将近一半的时间
class Solution:
    def findShortestSubArray(self, nums):
        
        diction = {}
        
        for i in nums:
            if i not in diction:
                diction[i] = 1
            else:
                diction[i] += 1
            
        degree = max(list(diction.values()))
        
        if degree == 1:
            return 1
        
        max_value = []
        
        for i in diction:
            if diction[i] == degree:
                max_value.append(i)
        
        min_length = 10000000000
        
        for i in max_value:
            head = 0
            tail = 0
            for j in range(len(nums)):
                if nums[j] == i:
                    head = j
                    break
            for j in range(len(nums)-1,-1,-1):
                if nums[j] == i:
                    tail = j
                    break
            if min_length > tail - head + 1:
                min_length = tail - head + 1
        
        return min_length
```