
---
layout: post
title:  leetcode-405 convert-a-number-to-hexadecimal
date:   2018-05-01 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

Given an integer, write an algorithm to convert it to hexadecimal. 
For negative integer, two’s complement method is used.

## Example1：

```
Input:
26

Output:
"1a"
```

## Example2：

```
Input:
-1

Output:
"ffffffff"
```

## Note:

```
- All letters in hexadecimal (a-f) must be in lowercase.

- The hexadecimal string must not contain extra leading 0s. 
If the number is zero, it is represented by a single zero 
character '0'; otherwise, the first character in the hexadecimal 
string will not be the zero character.

- The given number is guaranteed to fit within the range of a 
32-bit signed integer.

- You must not use any method provided by the library which 
converts/formats the number to hex directly.

```

## Solution：

```
# 这个解法很厉害
def toHex(self, num):
    if num==0: 
        return '0'
    mp = '0123456789abcdef'  # like a map
    ans = ''
    for i in range(8):
        n = num & 15       # this means num & 1111b
        c = mp[n]          # get the hex char 
        ans = c + ans
        num = num >> 4
    return ans.lstrip('0')  #strip leading zeroes
```