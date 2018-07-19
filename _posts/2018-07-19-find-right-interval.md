---
layout: post
title:  leetcode-436 find-right-interval
date:   2018-07-19 00:00:00
categories: LeetCode
tags: LeetCode-Medium BinarySearch
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Medium**

## Description

Given a set of intervals, for each of the interval i, check if there exists 
an interval j whose start point is bigger than or equal to the end point of 
the interval i, which can be called that j is on the "right" of i.
For any interval i, you need to store the minimum interval j's index, which 
means that the interval j has the minimum start point to build the "right" 
relationship for interval i. If the interval j doesn't exist, store -1 for 
the interval i. Finally, you need output the stored value of each interval 
as an array.

## Example1

```
Input: [ [1,2] ]
Output: [-1]
Explanation: There is only one interval in the collection, so it outputs -1.
```

## Example2

```
Input: [ [3,4], [2,3], [1,2] ]
Output: [-1, 0, 1]
Explanation: There is no satisfied "right" interval for [3,4].
For [2,3], the interval [3,4] has minimum-"right" start point;
For [1,2], the interval [2,3] has minimum-"right" start point.
```

## Example3

```
Input: [ [1,4], [2,3], [3,4] ]
Output: [-1, 2, -1]
Explanation: There is no satisfied "right" interval for [1,4] and [3,4].
For [2,3], the interval [3,4] has minimum-"right" start point.
```

## Note

- You may assume the interval's end point is always bigger than its start point.
- You may assume none of these intervals have the same start point.

## Solution

- 没有通过时间测试:(
```
# Definition for an interval.
# class Interval:
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution:
    def findRightInterval(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[int]
        """
        if len(intervals) <= 1:
            return [-1]
        index_ = 0
        ret_list = []
        cmp = None
        while index_ <= len(intervals) - 1:
            interval = intervals[index_]
            for item in intervals:
                if item.start >= interval.end:
                    if not cmp or item.start <= cmp.start:
                        cmp = item
            if cmp_list:
                ret_list.append(intervals.index(cmp))
            else:
                ret_list.append(-1)
            index_ += 1
        return ret_list
```

- 这个解法是大多数解法的思路，[原址](https://leetcode.com/problems/find-right-interval/discuss/148304/8-line-python-solution-with-bisect)
```
class Solution:
    def findRightInterval(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[int]
        """
        from bisect import bisect_left
        start2index = dict({ itv.start: i for (i, itv) in enumerate(intervals)})
        sorted_start = sorted([ itv.start for itv in intervals ])
        
        n = len(intervals)
        ans = []  
        for interval in intervals:
            i = bisect_left(sorted_start, interval.end)
            ans.append(start2index[sorted_start[i]] if i != n else -1)
        return ans
```

## [More](https://leetcode.com/problems/find-right-interval/description/)