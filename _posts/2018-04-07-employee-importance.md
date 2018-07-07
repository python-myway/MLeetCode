---
layout: post
title:  leetcode-690 employee-importance
date:   2018-04-07 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

You are given a data structure of employee information, which includes the 
employee's unique id, his importance value and his direct subordinates' id.

For example, employee 1 is the leader of employee 2, and employee 2 is the 
leader of employee 3. They have importance value 15, 10 and 5, respectively. 
Then employee 1 has a data structure like [1, 15, [2]], and employee 2 has 
[2, 10, [3]], and employee 3 has [3, 5, []]. Note that although employee 3 
is also a subordinate of employee 1, the relationship is not direct.

Now given the employee information of a company, and an employee id, 
you need to return the total importance value of this employee and all his subordinates.

## Example：

```
Input: [[1, 5, [2, 3]], [2, 3, []], [3, 3, []]], 1

Output: 11

Explanation:
Employee 1 has importance value 5, and he has two direct subordinates: 
employee 2 and employee 3. They both have importance value 3. So the total 
importance value of employee 1 is 5 + 3 + 3 = 11.
```

## Note:

- One employee has at most one direct leader and may have several subordinates.
- The maximum number of employees won't exceed 2000.

## Solution：

```
# 我的写法不能解决目标在后面的情况，唉，这是大神的
class Solution(object):
    def getImportance(self, employees, id):
        """
        :type employees: Employee
        :type id: int
        :rtype: int
        """
        # Time: O(n)
        # Space: O(n)
        emps = {employee.id: employee for employee in employees}
        dfs = lambda id: sum([dfs(sub_id) for sub_id in emps[id].subordinates]) + emps[id].importance
        return dfs(id)
```