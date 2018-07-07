
---
layout: post
title:  leetcode-455 assign-cookies
date:   2018-04-24 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Assume you are an awesome parent and want to give your children some cookies. 
But, you should give each child at most one cookie. Each child i has a greed 
factor gi, which is the minimum size of a cookie that the child will be content 
with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j 
to the child i, and the child i will be content. Your goal is to maximize the 
number of your content children and output the maximum number. 

## Example1：

```
Input: [1,2,3], [1,1]

Output: 1

Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could 
only make the child whose greed factor is 1 content.You need to output 1.
```

## Example2：

```
Input: [1,2], [1,2,3]

Output: 2

Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```

## Note ：

- You may assume the greed factor is always positive.
- You cannot assign more than one cookie to one child. 

## Solution：

```
class Solution:
    """
    思路：太慢了
    """
    def findContentChildren(self, g, s):
        """
        :type g: List[int]
        :type s: List[int]
        :rtype: int
        """
        total = 0
        g.sort()
        s.sort()
        while g:
            item = g.pop(0)
            if not s:
                break
            for cookie in s:
                if item <= cookie:
                    total += 1
                    s.remove(cookie)
                    break
        return total
        
# heapq.heapify(g),将列表转换成堆，线性时间，原位修改，heap[0]总是返回堆中最小的元素，
# heapq.heappop(g)删除并返回堆中最小的元素    
class Solution:
    def findContentChildren(self, g, s):
        """
        :type g: List[int]
        :type s: List[int]
        :rtype: int
        """
        ans = 0
        heapq.heapify(g)
        s.sort()
        for i in s:
            if not len(g):
                break
            elif g[0] <= i:
                ans += 1
                heapq.heappop(g)
        return ans
        
# 这个和我的思路差不多，但是快了10倍，难过。。。        
class Solution:
    def findContentChildren(self, g, s):
        """
        :type g: List[int]
        :type s: List[int]
        :rtype: int
        """
        g = sorted(g)
        s = sorted(s)
        a = 0
        i, j = len(g) - 1, len(s) - 1
        while i >= 0 and j >= 0:
            if g[i] <= s[j]:
                a += 1
                j -= 1
            i -= 1
        return a
```