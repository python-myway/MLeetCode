
---
layout: post
title:  leetcode-448 find-all-numbers-disappeared-in-an-array
date:   2018-02-02 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), 
some elements appear twice and others appear once.
Find all the elements of [1, n] inclusive that do not appear in this array.
Could you do it without extra space and in O(n) runtime? You may assume 
the returned list does not count as extra space.

## Example：

```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

## Solution：

```
class Solution:
    """
    思路：终于有一次超过80%的PY3的了，哈哈哈
    """
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        return list(set(range(1, len(nums)+1)) - set(nums))
        
# 还有一种思路是这样的：如果nums中存在，就把值设为0
class Solution:
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        d = [i for i in range(1, len(nums)+1)]
        for i in nums:
            d[i-1] = 0
        return [i for i in d if i>0]
```