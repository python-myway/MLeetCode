---
layout: post
title:  leetcode-669 trim-a-binary-search-tree
date:   2018-09-10 00:00:00
categories: LeetCode
tags: LeetCode-Easy Tree
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Easy**

## Description

Given a binary search tree and the lowest and highest boundaries as L and R, 
trim the tree so that all its elements lies in [L, R] (R >= L). You might need to 
change the root of the tree, so the result should return the new root of the 
trimmed binary search tree.

## Example1

```
Input: 
    1
   / \
  0   2

  L = 1
  R = 2

Output: 
    1
      \
       2
```

## Example2

```
Input: 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

Output: 
      3
     / 
   2   
  /
 1
```

## Solution
- 我对这种题目还是思路有问题，这时借鉴大佬的解法，[原址](https://leetcode.com/problems/trim-a-binary-search-tree/discuss/158631/Python-DFS-tm) 

```
# 分成三种情况，root的值小于L，就去掉左树，大于R，就去掉右树，介于之间的话就对左右树分别递归
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def trimBST(self, root, L, R):
        """
        :type root: TreeNode
        :type L: int
        :type R: int
        :rtype: TreeNode
        """
        if not root: 
            return root
        if root.val > R: 
            return self.trimBST(root.left, L, R)
        if root.val < L: 
            return self.trimBST(root.right, L, R)

        root.left = self.trimBST(root.left, L, R)
        root.right = self.trimBST(root.right, L, R)

        return root
```

## [More](https://leetcode.com/problems/trim-a-binary-search-tree/description/)