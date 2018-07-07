---
layout: post
title:  leetcode-696 count-binary-substrings
date:   2018-02-03 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Give a string **s**, count the number of non-empty (contiguous(连续)) substrings 
that have the same number of 0's and 1's, and all the 0's and all the 
1's in these substrings are grouped consecutively.

Substrings that occur multiple times are counted the number of times they occur.

## Example1：

```
Input: "00110011"

Output: 6

Explanation: There are 6 substrings that have equal number of consecutive 
1's and 0's: "0011", "01", "1100", "10", "0011", and "01".
Notice that some of these substrings repeat and are counted the number of times they occur.
Also, "00110011" is not a valid substring because all the 0's (and 1's) are not grouped together.
```

## Example2：

```
Input: "10101"

Output: 4

Explanation: There are 4 substrings: "10", "01", "10", "01" that have equal 
number of consecutive 1's and 0's.
```

## Note :

- s.length will be between 1 and 50,000.
- s will only consist of "0" or "1" characters.

## Solution：

```
# 大神的解法
# 思路：First, I count the number of 1 or 0 grouped consecutively.
# For example “0110001111” will be [1, 2, 3, 4].
# Second, for any possible substrings with 1 and 0 grouped consecutively, 
# the number of valid substring will be the minimum number of 0 and 1.
# For example “0001111”, will be min(3, 4) = 3, ("01", "0011", "000111")
class Solution:
    def countBinarySubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        s = map(len, s.replace('01', '0 1').replace('10', '1 0').split())
        return sum(min(a, b) for a, b in zip(s, s[1:]))

# 我的解法，时间测试没通过       
class Solution:
    def countBinarySubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        import re
        m = '10'
        n = '01'
        result = []
        while len(m) <= len(s):
            pattern_m = re.compile(m)
            pattern_n = re.compile(n)
            fm = pattern_m.findall(s)
            if fm:
                result.extend(fm)
            fn = pattern_n.findall(s)
            if fn:
                result.extend(fn)
            m = '1' + m + '0'
            m = 'n' + n + '1'
        return len(result)
```