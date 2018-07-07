
---
layout: post
title:  leetcode-350 intersection-of-two-arrays-ii
date:   2018-03-29 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given two arrays, write a function to compute their intersection.

Follow up:
What if the given array is already sorted? How would you optimize your algorithm?
What if nums1's size is small compared to nums2's size? Which algorithm is better?
What if elements of nums2 are stored on disk, and the memory is limited such that 
you cannot load all elements into the memory at once?

## Example：

```
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].
```

## Note :

- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.

## Solution：

```
class Solution:
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        r = []
        from collections import Counter
        d_1 = Counter(nums1)
        d_2 = Counter(nums2)
        for key, value in d_1.items():
            value2 = d_2.get(key, 0)
            r.extend(min(value, value2) * [key])
        return r
        
# 思路差不多，速度快
class Solution:
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        dict1={}
        for i in range(len(nums1)):
            if nums1[i] in dict1:
                dict1[nums1[i]]+=1
            else:
                dict1[nums1[i]]=1
        
        res=[]
        for i in range(len(nums2)):
            if nums2[i] in dict1 and dict1[nums2[i]]>0:
                res.append(nums2[i])
                dict1[nums2[i]]-=1
        
        return res
```