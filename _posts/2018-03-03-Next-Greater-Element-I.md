---
layout: post
title:  leetcode-496 Next-Greater-Element-I
date:   2018-03-03 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

You are given two arrays (without duplicates) nums1 and nums2 where 
nums1’s elements are subset of nums2. Find all the next greater numbers 
for nums1's elements in the corresponding places of nums2.
The Next Greater Number of a number x in nums1 is the first greater number 
to its right in nums2. If it does not exist, output -1 for this number. 

## Example1：

```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].

Output: [-1,3,-1]

Explanation:
    For number 4 in the first array, you cannot find the next greater number 
    for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in 
    the second array is 3.
    For number 2 in the first array, there is no next greater number for 
    it in the second array, so output -1.
```

## Example2：

```
Input: nums1 = [2,4], nums2 = [1,2,3,4].

Output: [3,-1]

Explanation:
    For number 2 in the first array, the next greater number for 
    it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it 
    in the second array, so output -1.
```

## Note :

- All elements in nums1 and nums2 are unique.
- The length of both nums1 and nums2 would not exceed 1000.

## Solution：

```
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        temp = []
        for m in nums1:
            x = nums2.index(m)
            for n in nums2[x+1:]:
                if n > m:
                    temp.append(n)
                    break
            else:
                temp.append(-1)
        return temp
        
# 这个解法的效率高很多(非本人的)
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        stack = []
        precalculated = {}
        for num in nums2:
            if not stack:
                stack.append(num)
            elif stack[-1] >= num:
                stack.append(num)
            else:
                while stack and stack[-1] < num:
                    precalculated[stack.pop()] = num
                stack.append(num)
                
        return [ precalculated.get(val, -1) for val in nums1]
```