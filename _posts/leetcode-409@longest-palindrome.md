
---
layout: post
title:  leetcode-409 longest-palindrome
date:   2018-02-20 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a string which consists of lowercase or uppercase letters, 
find the length of the longest palindromes(回文) that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

## Example：

```
Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.
```

## Note :

- Assume the length of given string will not exceed 1,010.

## Solution：

```
class Solution:
    """
    思路：要明白奇数个数的字母，减去一个就可以用，整个字符串里最多一个奇数个数的字母，bool(m)是防止m为0,就不需加1
    """
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """
        from collections import Counter
        d = Counter(s)
        m = 0
        for key, value in d.items():
            if value % 2 == 1:
                m += 1
        return len(s) - m + bool(m)
        
# 思路一致，快了一倍        
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """       
        r = 2*sum(s.count(n)//2 for n in set(s))
        return r+1 if r < len(s) else r
```