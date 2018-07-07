
---
layout: post
title:  leetcode-122 best-time-to-buy-and-sell-stock-ii
date:   2018-02-05 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions 
as you like (ie, buy one and sell one share of the stock multiple times). However, 
you may not engage in multiple transactions at the same time (ie, you must sell the 
stock before you buy again).

## Solution：

```
class Solution:
    """
    思路：看讨论，真的有人面试遇到了这个题目了
    """
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if not prices or len(prices) == 1:
            return 0
        total = 0
        for i in range(1, len(prices)):
            if prices[i] >= prices[i-1]:
                total += prices[i] -prices[i-1]
        return total

# 这种解法很有意思啊，错位相减
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        return sum(y-x for x, y in zip(prices[:-1], prices[1:]) if y > x)
```