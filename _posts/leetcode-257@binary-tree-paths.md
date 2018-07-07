
---
layout: post
title:  leetcode-257 binary-tree-paths
date:   2018-02-01 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a binary tree, return all root-to-leaf paths.

Note: A leaf is a node with no children.

## Example：

```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
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
    def binaryTreePaths(self, root):
        """
        :type root: TreeNode
        :rtype: List[str]
        """
        if not root:
            return []
        
        ansList = [] 
        def dfs(root, ans = ''):
            ans += str(root.val)
            if not (root.left or root.right):
                ansList.append(ans)
                return
            ans += '->'
            if root.left:
                dfs(root.left, ans)
            if root.right:
                dfs(root.right, ans)
        dfs(root)
        return ansList
```