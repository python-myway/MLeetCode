---
layout: post
title:  leetcode-104 maximum-depth-of-binary-tree
date:   2019-03-18 00:00:00
categories: LeetCode
tags: LeetCode-Easy Tree DFS
---

* content
{:toc}

This is another LeetCode Day
中间断了一段时间，现在重拾起来啦

## Difficulty

**Easy**

## Description

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Note: A leaf is a node with no children.

## Example

```
Given binary tree [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
return its depth = 3.
```

## Solution

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        if (not root.left) and (not root.right):
            return 1
        left_length = max(1, self.maxDepth(root.left))
        right_length = max(1, self.maxDepth(root.right))
        return 1 + max(left_length, right_length)
```

## [More](https://leetcode.com/problems/maximum-depth-of-binary-tree/)