---
title: Rotate Array
date: 2019-12-24 09:30:00 Z
solved: true
---

Given an array, rotate the array to the right by *k* steps, where *k* is non-negative.

**Example 1:**

    Input: [1,2,3,4,5,6,7] and k = 3
    Output: [5,6,7,1,2,3,4]
    Explanation:
    rotate 1 steps to the right: [7,1,2,3,4,5,6]
    rotate 2 steps to the right: [6,7,1,2,3,4,5]
    rotate 3 steps to the right: [5,6,7,1,2,3,4]
    

**Example 2:**

    Input: [-1,-100,3,99] and k = 2
    Output: [3,99,-1,-100]
    Explanation: 
    rotate 1 steps to the right: [99,-1,-100,3]
    rotate 2 steps to the right: [3,99,-1,-100]
    

**Note:**

* Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

* Could you do it in-place with O(1) extra space?

---

Startup code:

    var rotate = function(nums, k) {
    ...
    }

**What I learned** The question is asking to move k number in the back to the front, you can just move k number without using any loop.

The spread syntax convert an array into individual number, say:

    let sum = (x,y,z) => {
        return x+y+z;
    }
    
    sum(...[5,6,7])

**My solution**

    var rotate = function(nums, k) {
        for(let i = 0; i < k; i++) {
                 nums.unshift(nums.splice(-1,1));
            }
    };

**What I like about it** Straight to the point, understandable, readable code.

**What could be better** The for loop is unnecessary, I could've just cut the k number in the end and bring to front.

    var rotate = function(nums, k) {
        nums.unshift(...nums.splice(nums.length-k,k));
    };