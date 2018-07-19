---
layout: post
title:  leetcode-115 distinct-subsequences
date:   2018-07-19 00:00:00
categories: LeetCode
tags: LeetCode-Hard String DynamicProgramming
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Hard**

## Description

Given a string S and a string T, count the number of distinct 
subsequences of S which equals T.
A subsequence of a string is a new string which is formed from 
the original string by deleting some (can be none) of the characters 
without disturbing the relative positions of the remaining characters. 
(ie, "ACE" is a subsequence of "ABCDE" while "AEC" is not).

## Example1

```
Input: S = "rabbbit", T = "rabbit"
Output: 3
Explanation:

As shown below, there are 3 ways you can generate "rabbit" from S.
(The caret symbol ^ means the chosen letters)

rabbbit
^^^^ ^^
rabbbit
^^ ^^^^
rabbbit
^^^ ^^^
```

## Example2

```
Input: S = "babgbag", T = "bag"
Output: 5
Explanation:

As shown below, there are 5 ways you can generate "bag" from S.
(The caret symbol ^ means the chosen letters)

babgbag
^^ ^
babgbag
^^    ^
babgbag
^    ^^
babgbag
  ^  ^^
babgbag
    ^^^
```

## Solution

- 动态规划的题目跪了，盗用讨论区回答，[原址](https://leetcode.com/problems/distinct-subsequences/discuss/143506/36-ms-Python-solution-O(n)-space-and-O(m-*-n)-time-beat-100)

```
from collections import defaultdict

class Solution:
    def numDistinct(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: int
        """
        if not s or not t:
            return 0
        
        li = [0 for x in range(len(t))]
        d = defaultdict(list)
        
        for (i, ch) in enumerate(t):
            d[ch].append(i)
        
        for i in range(len(s)):
            if s[i] in t:
                for j in reversed(d[s[i]]):
                    if j == 0:
                        li[0] += 1
                    else:
                        li[j] += li[j - 1]
        return li[-1]
```

- 上面的解法不是用典型的动态规划写出来的，附上另一个解法，[原址](https://leetcode.com/problems/distinct-subsequences/discuss/143488/Python-DP-solution)

```
class Solution(object):
    def numDistinct(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: int
        """
        dp = [[0]*(len(t)+1) for i in range(len(s)+1)]
        for i in range(len(dp)):
            dp[i][0] = 1 
        for j in range(1,len(dp[0])):
            for i in range(1,len(dp)):
                if s[i-1] == t[j-1]:
                    dp[i][j] = dp[i-1][j-1] + dp[i-1][j] # 
                else:
                    dp[i][j] = dp[i-1][j] # 当s和t对应位置的字母不相同时，对结果没有影响
        return dp[-1][-1]
```

## [More](https://leetcode.com/problems/distinct-subsequences/description/)