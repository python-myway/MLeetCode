---
layout: post
title:  leetcode-383 ransom-note
date:   2018-04-15 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given an arbitrary ransom note string and another string containing letters 
from all the magazines, write a function that will return true if the ransom 
note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

## Example：

```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```

## Note :

- You may assume that both strings contain only lowercase letters. 

## Solution：

```
class Solution:
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        lr = list(ransomNote)
        lm = list(magazine)
        while lr:
            item = lr.pop()
            if item not in lm:
                return False
            lm.remove(item)
        else:
            return True
            
# 这个解法是我的一半时间，思维简直了，厉害
class Solution:
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        for t in 'qwertyuiopasdfghjklzxcvbnm':
            if magazine.count(t)<ransomNote.count(t):
                return False
        return True
```