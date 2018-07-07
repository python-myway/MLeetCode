
---
layout: post
title:  leetcode-657 Judge-Route-Circle
date:   2018-03-28 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to **the original place**.

The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are **R** (Right), **L** (Left), **U** (Up) and **D** (down). The output should be true or false representing whether the robot makes a circle. 

## Example1：

```
Input: "UD"

Output: true
```

## Example2：

```
Input: "LL"

Output: false
```

## Solution：

```
class Solution:
    """
    思路：在水平方向和垂直方向上的向量和为0
    """
    def judgeCircle(self, moves):
        """
        :type moves: str
        :rtype: bool
        """
        list_moves = list(moves)
        temp = {'R': 0, 'L': 0, 'U': 0, 'D': 0}
        dict_moves = {'R': 1, 'L': -1, 'U': 1, 'D': -1}
        while list_moves:
            item = list_moves.pop(0)
            temp[item] += dict_moves[item]
        if temp['R'] + temp['L'] == 0 and temp['U'] + temp['D'] == 0:
            return True
        else:
            return False
```
