---
layout: post
title:  leetcode-863 all-nodes-distance-k-in-binary-tree
date:   2018-07-10 00:00:00
categories: LeetCode
tags: LeetCode-Medium Tree DFS BFS
---

* content
{:toc}

This is another LeetCode Day

## Difficulty

**Medium**

## Description

We are given a binary tree (with root node root), a target node, and an integer value K.
Return a list of the values of all nodes that have a distance K from the target node.  
The answer can be returned in any order.

## Example

Input: root = [3,5,1,6,2,0,8,null,null,7,4], target = 5, K = 2

Output: [7,4,1]

Explanation: 
The nodes that are a distance 2 from the target node (with value 5)
have values 7, 4, and 1.
![](/pic/leetcode-863-01.png)

Note that the inputs "root" and "target" are actually TreeNodes.
The descriptions of the inputs above are just serializations of these objects.

## Note

- The given tree is non-empty.
- Each node in the tree has unique values 0 <= node.val <= 500.
- The target node is a node in the tree.
- 0 <= K <= 1000.

## Solution
- 根据[discuss](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/discuss/146689/Python3-construct-graph-with-dfs-and-find-answer-with-bfs)修改得到，原来的回答返回的是值不是结点

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def distanceK(self, root, target, K):
        """
        :type root: TreeNode
        :type target: TreeNode
        :type K: int
        :rtype: List[int]
        """
        # 首先dfs整个树，得到一个字典，字典的键是当前结点，值是当前结点的父结点，左子结点，右子结点
        graph = {}
        def dfs(node, parent=None):
            graph[node] = set()
            graph[node].add(parent)
            if node.left:
                graph[node].add(node.left)    
                dfs(node.left, node)
            if node.right:
                graph[node].add(node.right)
                dfs(node.right, node)
        dfs(root)        
        # with the graph we can use BFS to get answers
        queue = collections.deque([(target, 0)])
        seen = set([target])
        ret = []
        while queue:
            node, dist = queue.pop()
            if dist == K:
                ret.append(node)
            if dist > K: 
                break    
            for next_node in graph[node]:
                if next_node not in seen:
                    seen.add(next_node)
                    queue.appendleft((next_node, dist+1))
        return ret
```

## [More](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/description/)