
---
layout: post
title:  leetcode-21 merge-two-sorted-lists
date:   2018-03-07 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Merge two sorted linked lists and return it as a new list. 

The new list should be made by splicing together the nodes 

of the first two lists.

## Example：

```
Input: 1->2->4, 1->3->4

Output: 1->1->2->3->4->4

```

## Solution：

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        if a and b:
            if a.val > b.val:
                a, b = b, a
            a.next = self.mergeTwoLists(a.next, b)
        return a or b
```
