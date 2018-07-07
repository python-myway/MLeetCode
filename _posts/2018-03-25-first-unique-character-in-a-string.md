---
layout: post
title:  leetcode-387 first-unique-character-in-a-string
date:   2018-03-25 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a string, find the first non-repeating character in it and return it's index. 
If it doesn't exist, return -1. 

## Example：

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```

## Note :

- You may assume the string contain only lowercase letters. 

## Solution：

```
class Solution:
    """
    思路：找到第一个在整个字符串中不重复的字母，返回索引
    """
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        letters='abcdefghijklmnopqrstuvwxyz'
        index=[s.index(l) for l in letters if s.count(l) == 1]
        return min(index) if len(index) > 0 else -1
```