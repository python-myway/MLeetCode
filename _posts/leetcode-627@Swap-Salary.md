
---
layout: post
title:  leetcode-627 Swap-Salary
date:   2018-03-27 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given a table **salary**, such as the one below, that has m=male and f=female values. Swap all f and m values (i.e., change all f values to m and vice versa) with a single update query and no intermediate temp table.

For example:

| id | name | sex | salary |
|----|------|-----|--------|
| 1  | A    | m   | 2500   |
| 2  | B    | f   | 1500   |
| 3  | C    | m   | 5500   |
| 4  | D    | f   | 500    |

After running your query, the above salary table should have the following rows:

| id | name | sex | salary |
|----|------|-----|--------|
| 1  | A    | f   | 2500   |
| 2  | B    | m   | 1500   |
| 3  | C    | f   | 5500   |
| 4  | D    | m   | 500    |

## Solution：

```

#1
UPDATE salary SET sex = IF(sex='m','f','m');

#2(这个想法好奇妙啊)
UPDATE salary SET sex= CHAR(ASCII('f') + ASCII('m') - ASCII(sex));

#3(炸裂)
UPDATE salary SET sex = CHAR(ASCII(sex) ^ 11);
# in ascii table, ‘f’ is 0x66, ‘m’ is 0x6D, and 0x66 xor 0x6D = 0x0B, which is 11 in decimal
```