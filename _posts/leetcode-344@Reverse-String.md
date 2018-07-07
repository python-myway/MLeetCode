
---
layout: post
title:  leetcode-344 Reverse-String
date:   2018-04-25 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Write a function that takes a string as input and returns the string reversed.

## Example：

```
Given s = "hello", return "olleh". 
```

## Solution：

```
class Solution:
    """
    思路：参照#557大神的思路
    """
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        return s[::-1]
```