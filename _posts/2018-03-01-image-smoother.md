---
layout: post
title:  leetcode-661 image-smoother
date:   2018-03-01 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a 2D integer matrix M representing the gray scale of an image, 
you need to design a smoother to make the gray scale of each cell 
becomes the average gray scale (rounding down) of all the 8 surrounding 
cells and itself. If a cell has less than 8 surrounding cells, then use as many as you can.

## Example：

```
Input:
[[1,1,1],
 [1,0,1],
 [1,1,1]]
 
Output:
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]
 
Explanation:
For the point (0,0), (0,2), (2,0), (2,2): floor(3/4) = floor(0.75) = 0
For the point (0,1), (1,0), (1,2), (2,1): floor(5/6) = floor(0.83333333) = 0
For the point (1,1): floor(8/9) = floor(0.88888889) = 0
```

## Note :

- The value in the given matrix is in the range of [0, 255].
- The length and width of the given matrix are in the range of [1, 150].

## Solution：

```
class Solution:
    """
    没有搞清楚这道题的意图
    """
    def imageSmoother(self, M):
        """
        :type M: List[List[int]]
        :rtype: List[List[int]]
        """
        x_len = len(M)
        y_len = len(M[0]) if x_len else 0
        res = copy(M)
        for x in range(x_len):
            for y in range(y_len):
                neighbors = [
                    M[_x][_y]
                    for _x in (x-1, x, x+1)
                    for _y in (y-1, y, y+1)
                    if 0 <= _x < x_len and 0 <= _y < y_len
                ]
                res[x][y] = sum(neighbors) // len(neighbors)
        return res
```