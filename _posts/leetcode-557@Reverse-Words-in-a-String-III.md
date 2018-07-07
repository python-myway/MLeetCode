
---
layout: post
title:  leetcode-557 Reverse-Words-in-a-String-III
date:   2018-04-26 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a string, you need to reverse the order of characters in each word within 
a sentence while still preserving whitespace and initial word order.

## Example：

```
Input: "Let's take LeetCode contest"

Output: "s'teL ekat edoCteeL tsetnoc"
```

## Note :

- In the string, each word is separated by single space and there will 
not be any extra space in the string.

## Solution：

```
class Solution:
    """
    思路：将每个单词颠倒再连接
    """
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        temp = s.split(' ')
        temp2 = map(lambda x : ''.join(list(reversed(x))), temp)
        return ' '.join(temp2)

# 大神解法
class Solution:
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        return ' '.join([i[::-1] for i in s.split(' ')])
```