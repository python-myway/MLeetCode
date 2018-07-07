
---
layout: post
title:  leetcode-171 excel-sheet-column-number
date:   2018-02-19 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Related to question [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)
Given a column title as appear in an Excel sheet, return its corresponding column number.

## Example：

```
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28
```

## Solution：

```
class Solution:
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        temp = [chr(key).upper() for key in range(97,123)]
        z_dict = dict(zip(temp, range(1, 27)))
        r = 0
        i = 0
        rs = s[::-1]
        while i < len(s):
            r += 26 ** i * z_dict[rs[i]]
            i += 1
        return r
        
# 这个解法比我的快一半的时间
class Solution:
    """
    思路： 这个思路和我的差不多，都是get到每多一层，就是多乘26
    """
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        col = 0
        for letter in s:
            col = col * 26 + ord(letter) - 64
        return col
```