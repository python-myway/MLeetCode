---
layout: post
title:  leetcode-760 Find-Anagram-Mappings
date:   2018-04-16 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given two lists Aand B, and B is an anagram(回文构词法) of A. B is an anagram of A means B is made by randomizing the order of the elements in A.

We want to find an index mapping P, from A to B. A mapping P[i] = j means the ith element in A appears in B at index j.

These lists A and B may contain duplicates. If there are multiple answers, output any of them.

## Example：

```
Input: A = [12, 28, 46, 32, 50],B = [50, 12, 32, 46, 28]

Output: [1, 4, 3, 2, 0]

# P[0] = 1 because the 0th element of A appears at B[1], and P[1] = 4 because the 1st element of A appears at B[4], and so on.
```

## Note:

- A, B have equal lengths in range [1, 100].
- A[i], B[i] are integers in range [0, 10^5].

## Solution：

```
class Solution:
    """
    思路：返回一个列表，列表中的元素表示B与A中相同的那个元素的索引
    """
    def anagramMappings(self, A, B):
        """
        :type A: List[int]
        :type B: List[int]
        :rtype: List[int]
        """
        list_r = []
        while A:
            item = A.pop(0)
            list_r.append(B.index(item))
        return list_r
```