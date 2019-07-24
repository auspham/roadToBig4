---
title: 'Leetcode PhoneInterview #1 (not solved)'
date: 2019-07-24 12:58:00 Z
author: System
layout: post
---

#### Question:
> Given an array  `A`  of integers, return the  **length**  of the longest arithmetic subsequence in  `A`.

Recall that a  _subsequence_  of  `A`  is a list  `A[i_1], A[i_2], ..., A[i_k]`  with  `0 <= i_1 < i_2 < ... < i_k <= A.length - 1`, and that a sequence  `B` is  _arithmetic_  if  `B[i+1] - B[i]`  are all the same value (for  `0 <= i < B.length - 1`).

**Examples:**
> **Input:** [3,6,9,12]
**Output:** 4
**Explanation:** 
The whole array is an arithmetic sequence with steps of length = 3.

> **Input:** [9,4,7,2,10]
**Output:** 3
**Explanation:** 
The longest arithmetic subsequence is [4,7,10].

> **Input:** [20,1,15,3,10,5,8]
**Output:** 4
**Explanation:** 
The longest arithmetic subsequence is [20,15,10,5].

Note:
1.  `2 <= A.length <= 2000`
2.  `0 <= A[i] <= 10000`

#### Solution:

