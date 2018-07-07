
---
layout: post
title:  leetcode-217 contains-duplicate
date:   2018-03-24 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an array of integers, find if the array contains any duplicates. 
Your function should return true if any value appears at least twice 
in the array, and it should return false if every element is distinct.

## Solution：

```
class Solution:
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if len(set(nums)) == len(nums):
            return False
        return True

```