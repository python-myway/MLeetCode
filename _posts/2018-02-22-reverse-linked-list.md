---
layout: post
title:  leetcode-206 reverse-linked-list
date:   2018-02-22 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Reverse a singly linked list.

## Hint :

A linked list can be reversed either iteratively or recursively. Could you implement both?

## Solution：

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        next = None
        while head:
            head.next, head, next = next, head.next, head
        return next
```