
---
layout: post
title:  leetcode-733 flood-fill
date:   2018-04-30 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

An **image** is represented by a 2-D array of integers, each integer 
representing the pixel value of the image (from 0 to 65535).

Given a coordinate **(sr, sc)** representing the starting pixel (row and column) 
of the flood fill, and a pixel value **newColor**, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 
4-directionally to the starting pixel of the same color as the starting pixel, 
plus any pixels connected 4-directionally to those pixels (also with the same 
color as the starting pixel), and so on. Replace the color of all of the aforementioned 
pixels with the newColor.

At the end, return the modified image. 

## Example：

```
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2

Output: [[2,2,2],[2,2,0],[2,0,1]]

Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

## Note :

- The length of image and image[0] will be in the range [1, 50].
- The given starting pixel will satisfy 0 <= sr < image.length and 0 <= sc < image[0].length.
- The value of each color in image[i][j] and newColor will be an integer in [0, 65535].

## Solution：

```
class Solution:
    """
    思路：同#695
    """
    def floodFill(self, image, sr, sc, newColor):
        """
        :type image: List[List[int]]
        :type sr: int
        :type sc: int
        :type newColor: int
        :rtype: List[List[int]]
        """
        m, n = len(image), len(image[0])
        s = image[sr][sc]
        def dfs(i, j):
            if 0 <= i < m and 0 <= j < n and image[i][j] == s:
                image[i][j] = newColor
                dfs(i - 1, j)
                dfs(i, j + 1)
                dfs(i + 1, j)
                dfs(i, j - 1)
        if s != newColor: # 一定要这一步，不然会陷入死循环：（
            dfs(sr, sc)
        return image
```