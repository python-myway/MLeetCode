
---
layout: post
title:  leetcode-566 Reshape-the-Matrix
date:   2018-03-21 00:00:00

categories: LeetCode
tags: LeetCode-Easy
---

* content
{:toc}

正经的分界线





## Difficulty:

**Easy**

## Description：

In MATLAB, there is a very useful function called 'reshape', which can reshape 
a matrix into a new one with different size but keep its original data.

You're given a matrix represented by a two-dimensional array, and two positive 
integers r and c representing the row number and column number of the wanted 
reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix 
in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new 
reshaped matrix; Otherwise, output the original matrix. 

## Example1：

```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4

Output: 
[[1,2,3,4]]

Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, 
fill it row by row by using the previous list.
```

## Example2：

```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 2, c = 4

Output: 
[[1,2],
 [3,4]]
 
Explanation:
There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.
```

## Note :

- The height and width of the given matrix is in range [1, 100].
- The given r and c are all positive.

## Solution：

```
class Solution:
    """
    思路：看了大神的答案，感觉思路差不多，都是先将nums的所有元素放到一个列表里，然后再进行分割
    """
    def matrixReshape(self, nums, r, c):
        """
        :type nums: List[List[int]]
        :type r: int
        :type c: int
        :rtype: List[List[int]]
        """
        from itertools import chain
        l = len(nums[0])
        if not len(nums) * l / r == c:
            return nums
        temp = list(chain.from_iterable(nums))
        temp2 = []
        while temp:
            temp2.append(temp[:c])
            temp = temp[c:]
        return temp2
        
        
# 还有这种解法，考虑转换后元素的位置关系
public class Solution {
    public int[][] matrixReshape(int[][] nums, int r, int c) {
        int[][] res = new int[r][c];
        if (nums.length == 0 || r * c != nums.length * nums[0].length)
            return nums;
        int rows = 0, cols = 0;
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums[0].length; j++) {
                res[rows][cols] = nums[i][j];
                cols++;
                if (cols == c) {
                    rows++;
                    cols = 0;
                }
            }
        }
        return res;
    }
}
```