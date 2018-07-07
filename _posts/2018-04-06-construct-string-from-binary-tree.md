---
layout: post
title:  leetcode-606 construct-string-from-binary-tree
date:   2018-04-06 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

You need to construct a string consists of parenthesis and integers 
from a binary tree with the preorder traversing way.

The null node needs to be represented by empty parenthesis pair "()". 
And you need to omit all the empty parenthesis pairs that don't affect 
the one-to-one mapping relationship between the string and the original binary tree.

## Example1：

```
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())", 
but you need to omit all the unnecessary empty parenthesis pairs. 
And it will be "1(2(4))(3)".
```

## Example2：
```
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example, 
except we can't omit the first parenthesis pair to break the one-to-one 
mapping relationship between the input and the output.
```

## Solution：

```
class Solution:
    def tree2str(self, t):
        """
        :type t: TreeNode
        :rtype: str
        """
        if not t: 
            return ''
        left = '({})'.format(self.tree2str(t.left)) if (t.left or t.right) else ''
        right = '({})'.format(self.tree2str(t.right)) if t.right else ''
        return '{}{}{}'.format(t.val, left, right)
```