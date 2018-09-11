---
layout: post
title:  leetcode-587 erect-the-fence
date:   2018-09-10 00:00:00
categories: LeetCode
tags: LeetCode-Hard geometry
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Hard**

## Description

There are some trees, where each tree is represented by (x,y) coordinate in a two-dimensional 
garden. Your job is to fence the entire garden using the **minimum length** of rope as it is 
expensive. The garden is well fenced only if all the trees are enclosed. Your task is to 
help find the coordinates of trees which are exactly located on the fence perimeter.

## Example1

```
Input: [[1,1],[2,2],[2,0],[2,4],[3,3],[4,2]]
Output: [[1,1],[2,0],[4,2],[3,3],[2,4]]
```

Explanation:
![](/pic/leetcode-587-01.png)

## Example2

```
Input: [[1,2],[2,2],[4,2]]
Output: [[1,2],[2,2],[4,2]]
```

Explanation:
![](/pic/leetcode-587-01.png)
## Note

- All trees should be enclosed together. You cannot cut the rope to enclose trees that will separate them in more than one group.
- All input integers will range from 0 to 100.
- The garden has at least one tree.
- All coordinates are distinct.
- Input points have NO order. No order required for output.

## Solution

- 完全没有思路:(
- 根据讨论区，被普及了一个知识，[Monotone Chain Convex Hull](http://www.algorithmist.com/index.php/Monotone_Chain_Convex_Hull)
- 又普及了另外一个知识，[Graham Scan](https://en.wikipedia.org/wiki/Graham_scan)
- 下面的答案也是搬运自评论区，[原址](https://leetcode.com/problems/erect-the-fence/discuss/118552/python3-beats-100-with-easy-detailed-explanation)

```
# Definition for a point.
# class Point(object):
#     def __init__(self, a=0, b=0):
#         self.x = a
#         self.y = b

class Solution:
    def outerTrees(self, A):
        """
        :type points: A[Point]
        :rtype: List[Point]
        """
        def comparator(p1,p2):
            if p1.x==p2.x: return p1.y-p2.y
            else: 
                return p1.x-p2.x
                
        def onleftside(p0,p1,p2):
            x1,x2=p1.x-p0.x,p2.x-p1.x
            y1,y2=p1.y-p0.y,p2.y-p1.y
            cross=x1*y2-x2*y1
            return cross>0
            
        def findHull(s,p):
            while len(s)>=2 and onleftside(s[-2],s[-1],p):
                s.pop()
            s.append(p)
        
        n= len(A)
        if n<4: return A
        A.sort(cmp=comparator)
        
        upHull,bottemHull=[A[0]],[A[-1]]
        for i in xrange(1,n):
            findHull(upHull,A[i])
        for i in xrange(n-2,-1,-1):
            findHull(bottemHull,A[i])

        for p in bottemHull:
            if p not in upHull:
                upHull.append(p)
        return upHull
        
class Solution:
    def outerTrees(self, points):
        """
        :type points: List[Point]
        :rtype: List[Point]
        """
        ret = set()
        
        dic = collections.defaultdict(list)
        for p in points:
            dic[p.x].append(p.y)

        xs = sorted(set([_.x for _ in points]))
        ret.update([(xs[0], y) for y in dic[xs[0]]])
        ret.update([(xs[-1], y) for y in dic[xs[-1]]])
        
        x = xs.pop(0)
        ys = dic[x]
        y = max(ys)        
        while xs:
            remain = [(a, b) for a in xs for b in dic[a]]
            ma_sin = [(b-y)/(a-x) for (a, b) in remain]
            tmp = -sys.maxsize
            cands = set()
            for i in range(len(ma_sin)):
                if ma_sin[i]>tmp:
                    tmp = ma_sin[i]
                    cands = set([remain[i]])
                elif ma_sin[i]==tmp:
                    cands.add(remain[i])
            x, y = -1, -1
            ret.update(cands)
            for c in cands:
                if c[0]>x:
                    x, y = c
            while xs and xs[0]<=x:
                xs.pop(0)
        
        xs = sorted(set([_.x for _ in points]))
        x = xs.pop(0)
        ys = dic[x]
        y = min(ys)        
        while xs:
            print
            remain = [(a, b) for a in xs for b in dic[a]]
            mi_sin = [(b-y)/(a-x) for (a, b) in remain]
            tmp = sys.maxsize
            cands = set()
            for i in range(len(mi_sin)):
                if mi_sin[i]<tmp:
                    tmp = mi_sin[i]
                    cands = set([remain[i]])
                elif mi_sin[i]==tmp:
                    cands.add(remain[i])
            x, y = -1, -1
            ret.update(cands)
            for c in cands:
                if c[0]>x:
                    x, y = c
            while xs and xs[0]<=x:
                xs.pop(0)
            
        # print(ret)
        return list(ret)
```

## [More](https://leetcode.com/problems/erect-the-fence/description/)