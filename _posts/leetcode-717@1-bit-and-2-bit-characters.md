
---
layout: post
title:  leetcode-717 1-bit-and-2-bit-characters
date:   2018-04-28 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

We have two special characters. The first character can be represented by 
one bit 0. The second character can be represented by two bits (10 or 11).

Now given a string represented by several bits. Return whether the last 
character must be a one-bit character or not. The given string will always 
end with a zero.

## Example1：

```
Input: 
bits = [1, 0, 0]

Output: True

Explanation: 
The only way to decode it is two-bit character and one-bit character. 
So the last character is one-bit character.
```

## Example2：

```
Input: 
bits = [1, 1, 1, 0]

Output: False

Explanation: 
The only way to decode it is two-bit character and two-bit character. 
So the last character is NOT one-bit character.
```

## Note :

- 1 <= len(bits) <= 1000.
- bits[i] is always 0 or 1.

## Solution：

```
class Solution:
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        s = ''.join([str(bit) for bit in bits]).replace('11', '@').replace('10', '@').split('@')[-1]
        if s:
            return True
        return False
        
# 这个答案比我的快很多，但是我不懂这个思路
class Solution:
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        if len(bits) == 1: 
            return True 
        
        s = 0
        i = len(bits) - 2
        
        while bits[i] == 1 and i >= 0:
            s += 1
            i -= 1
        return s % 2 == 0
```