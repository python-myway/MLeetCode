---
layout: post
title:  leetcode-563 binary-tree-tilt
date:   2018-04-09 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a binary tree, return the tilt of the whole tree.

The tilt of a tree node is defined as the absolute difference between the sum 
of all left subtree node values and the sum of all right subtree node values. 
Null node has tilt 0.

The tilt of the whole tree is defined as the sum of all nodes' tilt.

## Example：

```
Input: 
         1
       /   \
      2     3
      
Output: 1

Explanation: 
Tilt of node 2 : 0
Tilt of node 3 : 0
Tilt of node 1 : |2-3| = 1
Tilt of binary tree : 0 + 0 + 1 = 1

```

## Note :

- The sum of node values in any subtree won't exceed the range of 32-bit integer.
- All the tilt values won't exceed the range of 32-bit integer.

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
    思路：要用self.total而不是total
    """
    def findTilt(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        self.total = 0
        def helper(node):
            if not node:
                return 0
            left = helper(node.left or None)
            right = helper(node.right or None)
            self.total += abs(left - right)
            return left + right + node.val
        helper(root)
        return self.total
```