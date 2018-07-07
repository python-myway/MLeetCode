
---
layout: post
title:  leetcode-520 detect-capital
date:   2018-02-07 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:
- All letters in this word are capitals, like "USA".
- All letters in this word are not capitals, like "leetcode".
- Only the first letter in this word is capital if it has more than one letter, like "Google".

Otherwise, we define that this word doesn't use capitals in a right way. 

## Example1：

```
Input: "USA"

Output: True
```

## Example2：

```
Input: "FlaG"

Output: False
```

## Solution：

```
class Solution:
    def detectCapitalUse(self, word):
        """
        :type word: str
        :rtype: bool
        """
        return any((word.title() == word, word.upper() == word, word.lower() == word))
        
# 这样写的运行时间会比较少
class Solution:
    def detectCapitalUse(self, word):
        """
        :type word: str
        :rtype: bool
        """
        return True if word == word.upper() or word == word.lower() or word == word.title() else False
```