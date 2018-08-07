---
layout: post
title:  leetcode-104 maxumum-depth-of-binary-tree
date:   2018-08-07 00:00:00
categories: LeetCode
tags: LeetCode-Easy Tree DFS BFS
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Easy**

## Description

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path 
from the root node down to the farthest leaf node.

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

## Note

A leaf is a node with no children.

## Solution

- 我的解法没有通过时间测试，这是和我思路差不多的解法[原址](https://leetcode.com/problems/maximum-depth-of-binary-tree/discuss/155116/One-line-Python-Solution-beats-99)

```

class Solution(object):
    def maxDepth(self, root):
        return 0 if not root else max(self.maxDepth(root.left),self.maxDepth(root.right)) + 1
```

## [More](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)