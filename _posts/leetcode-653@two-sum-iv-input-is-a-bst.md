
---
layout: post
title:  leetcode-653 two-sum-iv-input-is-a-bst
date:   2018-04-02 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a Binary Search Tree and a target number, return true if 
there exist two elements in the BST such that their sum is equal to the given target.

## Example1：

```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

## Example2：

```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False
```
## Solution：

```
class Solution:
    """
    思路：这个解法是借鉴了大神的想法，但是我用了while循环
    """
    def findTarget(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: bool
        """
        if not root:
            return False
        l = [root]
        s = set()
        while l:
            node = l.pop(0)
            if k - node.val in s:
                return True
            s.add(node.val)
            if node.left:
                l.append(node.left)
            if node.right:
                l.append(node.right)
        else:
            return False
```