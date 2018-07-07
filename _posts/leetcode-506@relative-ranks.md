
---
layout: post
title:  leetcode-506 relative-ranks
date:   2018-04-06 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given scores of N athletes, find their relative ranks and the people with 
the top three highest scores, who will be awarded medals: "Gold Medal", 
"Silver Medal" and "Bronze Medal".

## Example：

```
Input: [5, 4, 3, 2, 1]

Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]

Explanation: The first three athletes got the top three highest scores, 
so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the left two athletes, you just need to output their relative ranks according to their scores.
```

## Note :

- N is a positive integer and won't exceed 10,000.
- All the scores of athletes are guaranteed to be unique.

## Solution：

```
class Solution:
    def findRelativeRanks(self, nums):
        """
        :type nums: List[int]
        :rtype: List[str]
        """
        dict_num = {}
        for j, num in enumerate(reversed(sorted(nums)), start=1):
            dict_num[num] = j
        for i in range(len(nums)):
            num = nums[i]
            if dict_num[num] == 1:
                nums[i] = 'Gold Medal'
            elif dict_num[num] == 2:
                nums[i] = 'Silver Medal'
            elif dict_num[num] == 3:
                nums[i] = 'Bronze Medal'
            else:
                nums[i] = str(dict_num[num])
        return nums
        
# 这个也是快了25%，map还能这样用的
class Solution:
    def findRelativeRanks(self, nums):
        """
        :type nums: List[int]
        :rtype: List[str]
        """
        sort = sorted(nums)[::-1]
        rank = ["Gold Medal", "Silver Medal", "Bronze Medal"] + list(map(str, range(4, len(nums) + 1)))
        return list(map(dict(zip(sort, rank)).get, nums))
```