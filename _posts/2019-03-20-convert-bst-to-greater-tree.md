---
layout: post
title:  leetcode-538 convert-bst-to-greater-tree
date:   2019-03-20 00:00:00
categories: LeetCode
tags: LeetCode-Easy Tree
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Easy**

## Description

Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

## Example

```
Input: The root of a Binary Search Tree like this:
              5
            /   \
           2     13

Output: The root of a Greater Tree like this:
             18
            /   \
          20     13
```

## Solution

```
# 我总是get不到这类问题的解决思路，这是偷了讨论里的思路
class Solution:
    def convertBST(self, root: TreeNode) -> TreeNode:
        self.res = 0
        self.dfs(root)
        return root
    def dfs(self,root):
        if not root: 
            return     
        self.dfs(root.right)
        self.res += root.val
        root.val = self.res  
        self.dfs(root.left)
```

## [More](https://leetcode.com/problems/convert-bst-to-greater-tree/)