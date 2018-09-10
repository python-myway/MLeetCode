---
layout: post
title:  leetcode-289 game-of-life
date:   2018-09-09 00:00:00
categories: LeetCode
tags: LeetCode-Medium Array
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Medium**

## Description

According to the Wikipedia's article: "The Game of Life, also known simply as Life, 
is a cellular automaton devised by the British mathematician John Horton Conway in 1970."

Given a board with m by n cells, each cell has an initial state live (1) or dead (0). 
Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using 
the following four rules (taken from the above Wikipedia article):

    - Any live cell with fewer than two live neighbors dies, as if caused by under-population.
    - Any live cell with two or three live neighbors lives on to the next generation.
    - Any live cell with more than three live neighbors dies, as if by over-population..
    - Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.

Write a function to compute the next state (after one update) of the board given its current 
state. The next state is created by applying the above rules simultaneously to every cell 
in the current state, where births and deaths occur simultaneously.

## Example

```
Input: 
[
  [0,1,0],
  [0,0,1],
  [1,1,1],
  [0,0,0]
]
Output: 
[
  [0,0,0],
  [1,0,1],
  [0,1,1],
  [0,1,0]
]
```

## Follow Up

    - Could you solve it in-place? Remember that the board needs to be updated at the same time:
     You cannot update some cells first and then use their updated values to update other cells.
    - In this question, we represent the board using a 2D array. In principle, the board is 
    infinite, which would cause problems when the active area encroaches the border of the array.
     How would you address these problems?

## Solution

```
class Solution:
    def gameOfLife(self, board):
    # 和扫雷那类的题型类似，但是我的解法是复制了一份board数据，肯定不符合内存要求:(
        """
        :type board: List[List[int]]
        :rtype: void Do not return anything, modify board in-place instead.
        """
        rows = len(board)
        cols = len(board[0])
        import copy
        temp = copy.deepcopy(board)
        for i in range(rows):
            for j in range(cols):
                posi = [(i, j-1), (i, j+1), (i-1, j-1), (i-1, j+1), 
                    (i+1, j-1), (i+1, j+1), (i+1, j), (i-1, j)]
                counter = 0
                for pos in posi:
                    if (rows > pos[0] >= 0 and cols > pos[1] >= 0) and temp[pos[0]][pos[1]] == 1:
                        counter += 1
                if temp[i][j] == 1 and 2 <= counter <= 3:
                    board[i][j] = 1
                elif temp[i][j] == 1:
                    board[i][j] = 0
                elif temp[i][j] == 0 and counter == 3:
                    board[i][j] = 1
                else:
                    board[i][j] = temp[i][j]
```

## [More](https://leetcode.com/problems/game-of-life/description/)