
---
layout: post
title:  leetcode-412 Fizz-Buzz
date:   2018-05-02 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Write a program that outputs the string representation of numbers from 1 to n.
But for multiples of three it should output “Fizz” instead of the number and 
for the multiples of five output “Buzz”. For numbers which are multiples of both three and 
five output “FizzBuzz”.

## Example：

```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

## Solution：
```
class Solution:
    """
    思路： 常规解法
    """
    def fizzBuzz(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        temp = []
        for i in range(1, n+1):
            if i % 15 == 0:
                temp.append('FizzBuzz')
            elif i % 3 == 0:
                temp.append('Fizz')
            elif i % 5 == 0:
                temp.append('Buzz')
            else:
                temp.append(str(i))
        return temp
        
# 大神解法1
def fizzBuzz(self, n):
    return ['Fizz' * (not i % 3) + 'Buzz' * (not i % 5) or str(i) for i in range(1, n+1)]
```