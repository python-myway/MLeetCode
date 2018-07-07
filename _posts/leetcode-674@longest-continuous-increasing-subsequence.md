
---
layout: post
title:  leetcode-674 longest-continuous-increasing-subsequence
date:   2018-02-12 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an unsorted array of integers, find the length of longest continuous increasing subsequence (subarray).

## Example1：

```
Input: [1,3,5,4,7]

Output: 3

Explanation: The longest continuous increasing subsequence is [1,3,5], its length is 3. 
Even though [1,3,5,7] is also an increasing subsequence, it's not a continuous one where 5 and 7 are separated by 4.
```

## Example2：

```
Input: [2,2,2,2,2]

Output: 1

Explanation: The longest continuous increasing subsequence is [2], its length is 1.
```

## Solution：

```
class Solution:
    def findLengthOfLCIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l_m = []
        max_l = [nums.pop(0)]
        for num in nums:
            if num > max_l[-1]:
                max_l.append(num)
            else:
                l_m.append(max_l)
                max_l = []
                max_l.append(num)
        return max(l_m, key=len)
```
