---
layout: post
title:  leetcode-13 roman-to-integer
date:   2018-04-17 00:00:00
categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

This is another LeetCode Day

## Difficulty:

**Easy**

## Description：

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

## Solution：

```
class Solution:
    """
    思路：搞清楚罗马数字的规则
    
    罗马数字共有7个，即I（1）、V（5）、X（10）、L（50）、C（100）、D（500）和M（1000）。
    1、重复数次：一个罗马数字重复几次，就表示这个数的几倍。
    2、右加左减：
        2.1 在较大的罗马数字的右边记上较小的罗马数字，表示大数字加小数字。
        2.2 在较大的罗马数字的左边记上较小的罗马数字，表示大数字减小数字。
        2.3 左减的数字有限制，仅限于I、X、C。比如45不可以写成VL，只能是XLV
        2.4 但是，左减时不可跨越一个位数。比如，99不可以用IC（100 - 1）表示，
        而是用XCIX（[100 - 10] + [10 - 1]）表示。（等同于阿拉伯数字每位数字分别表示。）
        2.5 左减数字必须为一位，比如8写成VIII，而非IIX。
        2.6 右加数字不可连续超过三位，比如14写成XIV，而非XIIII。（见下方“数码限制”一项。）
    3、加线乘千：
        3.1 在罗马数字的上方加上一条横线或者加上下标的Ⅿ，表示将这个数乘以1000，即是原数的1000倍。
        3.2 同理，如果上方有两条横线，即是原数的1000000（1000^{2}）倍。
    4、数码限制：
        4.1 同一数码最多只能出现三次，如40不可表示为XXXX，而要表示为XL。
        4.2 例外：由于IV是古罗马神话主神朱庇特（即IVPITER，古罗马字母里没有J和U）的首字，
        因此有时用IIII代替Ⅳ。
    """
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        dr = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D':500, 'M': 1000}
        # dp中的值的由来：IV本来应该减1,但是计算的时候加1了，所以应该减2,以此类推
        dp = {'IV': 2, 'IX': 2, 'XL': 20, 'XC': 20, 'CD': 200, 'CM': 200}
        total = 0
        for item in s:
            total += dr[item]
        sp = s[:2]
        for key, value in dp.items():
            try:
                if s.index(key) != -1:
                    total -= value
            except ValueError:
                continue
        return total
        
# 这个解法的速度快很多
class Solution:
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        value = 0
        roman = {'M': 1000,'D': 500 ,'C': 100,'L': 50,'X': 10,'V': 5,'I': 1}
        for i in range(len(s)-1):
            if roman[s[i]] < roman[s[i+1]]:
                value -= roman[s[i]]
            else:
                value += roman[s[i]]

        value += roman[s[-1]]
        return value
```