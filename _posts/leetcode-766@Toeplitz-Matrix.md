
---
layout: post
title:  leetcode-766 Toeplitz-Matrix
date:   2018-03-15 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

A matrix is Toeplitz if every diagonal(对角线) from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.

## Example1：

```
Input: matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]

Output: True

Explanation:
1234
5123
9512

In the above grid, the diagonals are "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", 
"[4]", and in each diagonal all elements are the same, so the answer is True.
```

## Example2：

```
Input: matrix = [[1,2],[2,2]]

Output: False

Explanation:
The diagonal "[1, 2]" has different elements.
```

## Note :

- matrix will be a 2D array of integers.
- matrix will have a number of rows and columns in range [1, 20].
- matrix[i][j] will be integers in range [0, 99].

## Solution：

```
# 思路：找出对角线相等的元素的下标的联系，即matrix[r-1][c-1] == matrix[r][c]，这个也变化出另一种r1-c1=r2-c2
class Solution(object):
    def isToeplitzMatrix(self, matrix):
        groups = {}
        for r, row in enumerate(matrix):
            for c, val in enumerate(row):
                if r-c not in groups:
                    groups[r-c] = val
                elif groups[r-c] != val:
                    return False
        return True
        
class Solution(object):
    def isToeplitzMatrix(self, matrix):
        return all(r == 0 or c == 0 or matrix[r-1][c-1] == val
                   for r, row in enumerate(matrix)
                   for c, val in enumerate(row))
```