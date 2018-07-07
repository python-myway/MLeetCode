
---
layout: post
title:  leetcode-637 Average-of-Levels-in-Binary-Tree
date:   2018-03-04 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array. 

## Example：

```
Input:
    3
   / \
  9  20
    /  \
   15   7
   
Output: [3, 14.5, 11]

Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, 
and on level 2 is 11. Hence return [3, 14.5, 11].
```

## Note :

- The range of node's value is in the range of 32-bit signed integer.

## Solution：

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    """
    大神的答案
    """
    def averageOfLevels(self, root):
        """
        :type root: TreeNode
        :rtype: List[float]
        """
        info = []
        def dfs(node, depth = 0):
            if node:
                if len(info) <= depth:
                    info.append([0, 0])
            info[depth][0] += node.val
            info[depth][1] += 1
            dfs(node.left, depth + 1)
            dfs(node.right, depth + 1)
        dfs(root)
        return [s/float(c) for s, c in info] 
```