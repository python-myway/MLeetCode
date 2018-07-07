
---
layout: post
title:  leetcode-485 max-consecutive-ones
date:   2018-04-16 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a binary array, find the maximum number of consecutive 1s in this array.

## Example：

```
Example 1:

Input: [1,1,0,1,1,1]

Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3. 
```

## Note:

- The input array will only contain 0 and 1.
- The length of input array is a positive integer and will not exceed 10,000.

## Solution：

```
class Solution:
    """
    思路：虽然运行时间长，但还是觉得我写的很好玩
    """
    def findMaxConsecutiveOnes(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        temp = [str(item) for item in nums]
        return len(max(''.join(temp).split('0'), key=len))

# 这种写法的运行时间是我的1/3,可怕
class Solution:
    def findMaxConsecutiveOnes(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = 0
        max_ones = -float('inf')
        for i in nums:
            if i == 1:
                count += 1
            else:
                if count > max_ones:
                    max_ones = count
                count = 0
        max_ones = count if count > max_ones else max_ones
        return max_ones
```

