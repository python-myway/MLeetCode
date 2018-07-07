
---
layout: post
title:  leetcode-167 two-sum-ii-input-array-is-sorted
date:   2018-02-25 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an array of integers that is already sorted in ascending order, 
find two numbers such that they add up to a specific target number.
The function twoSum should return indices of the two numbers such that 
they add up to the target, where index1 must be less than index2. Please 
note that your returned answers (both index1 and index2) are not zero-based.
You may assume that each input would have exactly one solution and you may 
not use the same element twice.

## Example：

```
Input: numbers={2, 7, 11, 15}, target=9

Output: index1=1, index2=2 
```

## Solution：

```
class Solution:
    """
    这个超时了
    """
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        n = len(numbers)
        while numbers:
            num = numbers.pop(0)
            if target - num in numbers:
                return [n - len(numbers), n - len(numbers) + numbers.index(target - num) + 1]

# 比较喜欢这个思路
def twoSum1(self, numbers, target):
    l, r = 0, len(numbers)-1
    while l < r:
        s = numbers[l] + numbers[r]
        if s == target:
            return [l+1, r+1]
        elif s < target:
            l += 1
        else:
            r -= 1
 
# dictionary           
def twoSum2(self, numbers, target):
    dic = {}
    for i, num in enumerate(numbers):
        if target-num in dic:
            return [dic[target-num]+1, i+1]
        dic[num] = i
 
# binary search        
def twoSum(self, numbers, target):
    for i in xrange(len(numbers)):
        l, r = i+1, len(numbers)-1
        tmp = target - numbers[i]
        while l <= r:
            mid = l + (r-l)//2
            if numbers[mid] == tmp:
                return [i+1, mid+1]
            elif numbers[mid] < tmp:
                l = mid+1
            else:
                r = mid-1
```