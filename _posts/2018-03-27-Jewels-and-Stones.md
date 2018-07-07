---
layout: post
title:  leetcode-771 Jewels-and-Stones
date:   2018-03-27 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

## Example1：

```
Input: J = "aA", S = "aAAbbbb"

Output: 3
```

## Example2：

```
Input: J = "z", S = "ZZ"

Output: 0
```

## Note:

- S and J will consist of letters and have length at most 50. 
- The characters in J are distinct.


## Solution：

```
class Solution:
    """
    思路：考查J中的元素在S中出现多少次
    """
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        list_j = list(J)
        list_s = list(S)
        count = 0
        while True:
            if not list_s:
                break
            item = list_s.pop()
            if item in list_j:
                count += 1
                continue
        return count
```