---
layout: post
title:  leetcode-594 longest-harmonious-subsequence
date:   2018-03-04 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

We define a harmonious array is an array where the difference 
between its maximum value and its minimum value is exactly 1.
Now, given an integer array, you need to find the length of its 
longest harmonious subsequence among all its possible subsequences.

## Example1：

```
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
```

## Note:

```
The length of the input array will not exceed 20,000.
```

## Solution：

```
# 这个是盗用别人的，这个思路简直不要太棒
from collections import Counter
class Solution:
    def findLHS(self, nums):
        c_n = Counter(nums)
        max_l = 0
        for k, v in c_n.items():
            if (k+1) in c_n and v+c_n[k+1] > max_l:
                max_l = v+c_n[k+1]
        return max_l
```