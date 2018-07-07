---
layout: post
title:  leetcode-242 valid-anagram
date:   2018-02-11 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given two strings s and t, write a function to determine if t is an anagram(相同字母异序词) of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

Follow up:
What if the inputs contain unicode characters? How would you adapt your solution to such case?

## Solution：

```
class Solution:
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if not s and not t:
            return True
        elif not s or not t:
            return False
        letters='abcdefghijklmnopqrstuvwxyz'
        if all(map(lambda l: s.count(l) == t.count(l), letters)):
            return True
        return False
```