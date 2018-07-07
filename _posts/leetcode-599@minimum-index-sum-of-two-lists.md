
---
layout: post
title:  leetcode-599 minimum-index-sum-of-two-lists
date:   2018-03-11 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Suppose Andy and Doris want to choose a restaurant for dinner, 
and they both have a list of favorite restaurants represented by strings.

You need to help them find out their common interest with the least list 
index sum. If there is a choice tie between answers, output all of them 
with no order requirement. You could assume there always exists an answer.

## Example1：

```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["Piatti", "The Grill at Torrey Pines", "Hungry Hunter Steakhouse", "Shogun"]

Output: ["Shogun"]

Explanation: The only restaurant they both like is "Shogun".
```

## Example2：

```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["KFC", "Shogun", "Burger King"]

Output: ["Shogun"]

Explanation: The restaurant they both like and have the least index sum is 
"Shogun" with index sum 1 (0+1).
```

## Note :

- The length of both lists will be in the range of [1, 1000].
- The length of strings in both lists will be in the range of [1, 30].
- The index is starting from 0 to the list length minus 1.
- No duplicates in both lists.

## Solution：

```
class Solution:
    def findRestaurant(self, list1, list2):
        """
        :type list1: List[str]
        :type list2: List[str]
        :rtype: List[str]
        """
        d = dict(zip(list1, range(len(list1))))
        r = []
        m = 2000
        for item in list2:
            try:
                d[item] += list2.index(item)
                if d[item] < m:
                    r.clear()
                    r.append(item)
                    m = d[item]
                elif d[item] == m:
                    r.append(item)
            except KeyError:
                continue
        return r
        
# 思路和我的差不多，但是速度快了近1倍，try...except真的很耗时间
class Solution:
    def findRestaurant(self, list1, list2):
        """
        :type list1: List[str]
        :type list2: List[str]
        :rtype: List[str]
        """
        H = { string: idx for (idx, string) in enumerate(list1) }
        m, items = len(list2) + len(list1), []
        for i, string in enumerate(list2):
            if string in H:
                if i + H[string] < m:
                    m = i + H[string]
                    items = [string]
                elif i + H[string] == m:
                    items.append(string)
        return items
```