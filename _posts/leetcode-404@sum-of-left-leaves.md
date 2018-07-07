
---
layout: post
title:  leetcode-404 sum-of-left-leaves
date:   2018-02-23 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Find the sum of all left leaves in a given binary tree.

## Example：

```
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```

## Solution：

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def sumOfLeftLeaves(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        total = 0
        lr = [root]
        while lr:
            node = lr.pop(0)
            if not node:
                continue
            if node.left and not node.left.left and not node.left.right:
                total += node.left.val
            lr.append(node.left or None)
            lr.append(node.right or None)
        return total
  
# 这种方式快了一倍，思路和我的一样，都是用栈的概念
class Solution:
    def sumOfLeftLeaves(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root: 
            return 0
        stack = [root]
        res = 0
        while stack:
            tmp = stack.pop()
            if tmp.left:
                stack.append(tmp.left)
                if not tmp.left.left and not tmp.left.right:
                    res += tmp.left.val
            if tmp.right:
                stack.append(tmp.right)
        return res
```