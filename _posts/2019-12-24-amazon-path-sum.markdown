---
title: Amazon Path Sum
date: 2019-12-24 09:27:00 Z
---

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

**Note:** A leaf is a node with no children.

**Example:**

Given the below binary tree and `sum = 22`,

          5
         / \
        4   8
       /   / \
      11  13  4
     /  \      \
    7    2      1
    

return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.

---

Company: Amazon

Startup code:

    var hasPathSum = function(root, sum) {
        ...
    }

**What I learned** Again, why using

    if( root.val === sum ) {
        return true
    }

when you can just use:

    return root.val === sum

**My solution**

    var hasPathSum = function(root, sum) {
        let prev = {
            val: 0
        }
        return helper(root, prev, sum);
    };
    
    
    let helper = (root, prev, sum) => {
        if(root) {
            root.val += prev.val;
            if((!root.left && !root.right) && root.val === sum) {
                return true;
            } else {
                return helper(root.left, root, sum) || helper(root.right, root, sum);
            }
        } else {
            return false;
        }
    }

**What I like about my solution** From the previous lesson, I learned to check if an object is null before using its attributes. The code is very easy to understand and easy to code. I coded it in almost one go!

I guess the trick is really understand what you are doing, what is your strategy is to solve the problem instead of keep hacking it.

**What I can improve** First is to improve what I learn.

Second, is to not use a second function. The point of using a second function is to keep the original sum to compare and have another accumulated value to compare with sum.

However, this problem can be tackled by *keep minus until the sum reach to 0*. By using this, we don't even need to create another function at all!

    var hasPathSum = function(root, sum) {
        if(!root) return false;
    
        sum -= root.val;
    
        if(!root.left && !root.right) {
            return sum === 0;
        }
    
        return hasPathSum(root.left, sum) || hasPathSum(root.right, sum);
    }