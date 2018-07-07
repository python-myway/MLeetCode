---
layout: post
title:  leetcode-575 Distribute-Candies
date:   2018-02-14 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given an integer array with even length, where different numbers in this array 
represent different kinds of candies. Each number means one candy of the corresponding kind. 
You need to distribute these candies equally in number to brother and sister. 
Return the maximum number of kinds of candies the sister could gain.


## Example1：

```
Input: candies = [1,1,2,2,3,3]

Output: 3

Explanation:
There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too. 
The sister has three different kinds of candies.
```

## Example2：

```
Input: candies = [1,1,2,3]

Output: 2

Explanation: For example, the sister has candies [2,3] and the brother has candies [1,1]. 
The sister has two different kinds of candies, the brother has only one kind of candies.
```

## Note :

- The length of the given array is in range [2, 10,000], and will be even.
- The number in given array is in range [-100,000, 100,000].

## Solution：

```
class Solution:
    """
    思路：min(len(candies)/2, len(set(candies))),我的解法罗嗦了
    """
    def distributeCandies(self, candies):
        """
        :type candies: List[int]
        :rtype: int
        """
        temp = list(set(candies))
        max_kind = int(len(candies) / 2)
        return len(temp) - max((len(temp) - max_kind), 0)
```