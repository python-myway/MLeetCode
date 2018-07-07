---
layout: post
title:  leetcode-2 add-two-numbers
date:   2018-03-15 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Example：

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807
```

## Solution：

```
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        l3 = l4 = ListNode(0)
        carry = 0
        while True:
            carry, total = divmod((l1.val+l2.val+carry), 10)
            l3.val = total
            n1 = l1.next
            n2 = l2.next
            l1 = n1
            l2 = n2
            if not n1:
                l1 = ListNode(0)
            if not n2:
                l2 = ListNode(0)
            if not n1 and not n2:
                if carry == 0:
                    break
                else:
                    l3.next= ListNode(carry)
                    break
            l3.next = ListNode(0)
            l3 = l3.next
        return l4
```