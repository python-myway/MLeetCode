---
layout: post
title:  leetcode-529 minesweeper
date:   2018-07-11 00:00:00
categories: LeetCode
tags: LeetCode-Medium DFS BFS
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Medium**

## Description

Let's play the minesweeper game ([Wikipedia](https://en.wikipedia.org/wiki/Minesweeper_(video_game)), [online game](http://minesweeperonline.com/))!
You are given a 2D char matrix representing the game board. 'M' represents an unrevealed mine, 
'E' represents an unrevealed empty square, 'B' represents a revealed blank square that has no 
adjacent (above, below, left, right, and all 4 diagonals) mines, digit ('1' to '8') represents 
how many mines are adjacent to this revealed square, and finally 'X' represents a revealed mine.
Now given the next click position (row and column indices) among all the unrevealed squares 
('M' or 'E'), return the board after revealing this position according to the following rules:
    - If a mine ('M') is revealed, then the game is over - change it to 'X'.
    - If an empty square ('E') with no adjacent mines is revealed, then change it to revealed 
    blank ('B') and all of its adjacent unrevealed squares should be revealed recursively.
    - If an empty square ('E') with at least one adjacent mine is revealed, then change it to 
    a digit ('1' to '8') representing the number of adjacent mines.
    - Return the board when no more squares will be revealed.

## Example1

```markdown
Input: 
[['E', 'E', 'E', 'E', 'E'],
 ['E', 'E', 'M', 'E', 'E'],
 ['E', 'E', 'E', 'E', 'E'],
 ['E', 'E', 'E', 'E', 'E']]
Click : [3,0]

Output: 
[['B', '1', 'E', '1', 'B'],
 ['B', '1', 'M', '1', 'B'],
 ['B', '1', '1', '1', 'B'],
 ['B', 'B', 'B', 'B', 'B']]
 
Explanation:
![](/pic/leetcode-539-01.png)
```

## Example2

```markdown
Input: 

[['B', '1', 'E', '1', 'B'],
 ['B', '1', 'M', '1', 'B'],
 ['B', '1', '1', '1', 'B'],
 ['B', 'B', 'B', 'B', 'B']]
Click : [1,2]

Output: 
[['B', '1', 'E', '1', 'B'],
 ['B', '1', 'X', '1', 'B'],
 ['B', '1', '1', '1', 'B'],
 ['B', 'B', 'B', 'B', 'B']]

Explanation:
![](/pic/leetcode-539-02.png)
```

## Note

- The range of the input matrix's height and width is [1,50].
- The click position will only be an unrevealed square ('M' or 'E'), which also means the 
input board contains at least one clickable square.
- The input board won't be a stage when game is over (some mines have been revealed).
- For simplicity, not mentioned rules should be ignored in this problem. For example, you 
don't need to reveal all the unrevealed mines when the game is over, consider any cases that you will win the game or flag any squares.

## Solution

```python
class Solution:
    # 这就是扫雷啊
    # dfs和bfs的差别就是一个用栈一个用队列
    # 这道题其实挺有意思的，不知道为什么挺多不喜欢的
    
    directions = [(-1, 0), (-1, -1), (-1, 1), (0,-1), (0, 1), (1, -1), (1, 0), (1, 1)]
    
    def updateBoard(self, board, click):
        """
        :type board: List[List[str]]
        :type click: List[int]
        :rtype: List[List[str]]
        """
        # return self.bfs(board, click)
        return self.dfs(board, click)
    
    def dfs(self, board, click):
        stack = [(click[0], click[1])]
        m, n = len(board), len(board[0])
        while stack:
            r, c = stack.pop() 
            if board[r][c] == 'M':
                board[r][c] = 'X'
                break
            # 查看周围九宫格的雷的情况
            mines = 0
            for i, j in self.directions:
                dr = r + i
                dc = c + j
                if 0 <= dr < m and 0 <= dc < n and board[dr][dc] == 'M':
                    mines += 1
            board[r][c] = str(mines) if mines else 'B'
            
            for i, j in self.directions:
                dr = r + i
                dc = c + j
                if 0 <= dr < m and 0 <= dc < n and board[r][c] == 'B' and board[dr][dc] == 'E':
                    stack.append((dr, dc))
            
        return board
        
    
    def bfs(self, board, click):
        queue = [(click[0], click[1])]
        m, n = len(board), len(board[0])
        while queue:
            r, c = queue.pop(0)
            
            if board[r][c] == 'M':
                board[r][c] = 'X'
                break

            mines = 0
            for i, j in self.directions:
                dr = r + i
                dc = c + j
                if 0 <= dr < m and 0 <= dc < n and board[dr][dc] == 'M':
                    mines += 1
            board[r][c] = str(mines) if mines else 'B'

            for i, j in self.directions:
                dr = r + i
                dc = c + j
                if 0 <= dr < m and 0 <= dc < n and (dr,dc) not in queue and board[r][c] == 'B' and board[dr][dc] == 'E':
                    queue.append((dr, dc))
                
        return board
```

## [More](https://leetcode.com/problems/minesweeper/description/)