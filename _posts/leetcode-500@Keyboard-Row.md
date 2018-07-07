
---
layout: post
title:  leetcode-500 Keyboard-Row
date:   2018-04-08 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a List of words, return the words that can be typed using 
letters of alphabet on only one row's of American keyboard like the image below.

![keyboard](./src/keyboard.png)

## Example：

```
Input: ["Hello", "Alaska", "Dad", "Peace"]

Output: ["Alaska", "Dad"]
```

## Note :

- You may use one character in the keyboard more than once.
- You may assume the input string will only contain letters of alphabet.

## Solution：
```
class Solution:
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        r1 = 'qwertyuiop'
        r2 = 'asdfghjkl'
        r3 = 'zxcvbnm'
        temp = []
        while words:
            word = words.pop()
            if any((all(map(lambda x: x.lower() in r1, word)), all(map(lambda x: x.lower() in r2, word)), all(map(lambda x: x.lower() in r3, word)))):
                temp.append(word)
            else:
                continue
        return temp
        
# 大神解法
class Solution:
    def findWordsRe(self, words):
        return list(filter(re.compile('(?i)([qwertyuiop]*|[asdfghjkl]*|[zxcvbnm]*)$').match, words))
```