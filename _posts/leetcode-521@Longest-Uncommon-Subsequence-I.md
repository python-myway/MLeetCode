
---
layout: post
title:  leetcode-521 Longest-Uncommon-Subsequence-I
date:   2018-02-18 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a group of two strings, you need to find the longest uncommon subsequence 
of this group of two strings. The longest uncommon subsequence is defined as the 
longest subsequence of one of these strings and this subsequence should not be any 
subsequence of the other strings.
A **subsequence** is a sequence that can be derived from one sequence by deleting some 
characters without changing the order of the remaining elements. Trivially, any string 
is a subsequence of itself and an empty string is a subsequence of any string.
The input will be two strings, and the output needs to be the length of the longest 
uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1. 

## Example：

```
Input: "aba", "cdc"

Output: 3

Explanation: The longest uncommon subsequence is "aba" (or "cdc"), 
because "aba" is a subsequence of "aba", 
but not a subsequence of any other strings in the group of two strings. 
```

## Note :

- Both strings' lengths will not exceed 100.
- Only letters from a ~ z will appear in input strings.

## Solution：

```
class Solution:
    """
    思路：我是用正则，但其实并不需要，难过
    """
    def findLUSlength(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: int
        """
        import re
        pattern = re.compile(a)
        check = pattern.search(b)
        if check:
            m, n = check.span()
            if n - m == len(b):
                return -1
            return len(b)
        else:
            return max(len(a), len(b))
            
            
class Solution:
    def findLUSlength(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: int
        """
        if len(a) != len(b): 
            return max(len(a), len(b))
        elif a != b: 
            return len(a)
        else: 
            return -1
```