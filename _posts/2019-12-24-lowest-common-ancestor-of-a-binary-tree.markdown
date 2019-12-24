---
title: Lowest Common Ancestor of a Binary Tree
date: 2019-12-24 09:31:00 Z
tags:
- Amazon
solved: true
---

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow **a node to be a descendant of itself**).”

Given the following binary tree: root = \[3,5,1,6,2,0,8,null,null,7,4\]

![](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)

**Example 1:**

    Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
    Output: 3
    Explanation: The LCA of nodes 5 and 1 is 3.
    

**Example 2:**

    Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
    Output: 5
    Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
    

**Note:**

* All of the nodes' values will be unique.

* p and q are different and both values will exist in the binary tree.

---

Company: Amazon

Starter code:

    var lowestCommonAncestor = function(root, p, q) {
    
    }

**What I learned** You cannot go reversely in a recursive function **but you can check if it's go able or not before going**.

Instead of

    if (root == p || root == q) {
            return root;
    }
    
    /* Checking before go to the left or right else return null */
    let left = root.left ? lowestCommonAncestor(root.left, p, q) : null;
    let right = root.right ? lowestCommonAncestor(root.right, p ,q) : null;
    ....
    return false;

Why if root is `null`, we don't just return root?

    if (!root || root == p || root == q) {
            return root;
    }
    let left = lowestCommonAncestor(root.left, p, q);
    let right = lowestCommonAncestor(root.right, p ,q);

a much cleaner code.

**My Solution**

    if (root == p || root == q) {
            return root;
    }
    
    let left = root.left ? lowestCommonAncestor(root.left, p, q) : null;
    let right = root.right ? lowestCommonAncestor(root.right, p ,q) : null;
    
    if (left && right) {
            return root;
    } else if (left) {
            return left
    } else if (right) {
            return right
    }
    
    return false;

**What I like about it** It's very readable and understandable

**What I don't like about it** Some of the part is redundant and can be much cleaner.

**What should I do instead**

    var lowestCommonAncestor = function(root, p, q) {
        if (!root || root == p || root == q) {
            return root;
        }
    
        let left = lowestCommonAncestor(root.left, p, q);
        let right = lowestCommonAncestor(root.right, p ,q);
    
        if (!left) {
            return right
        }
    
        if (!right) {
            return left
        }
    
        return root;
    };

Why `!left` and `!right` ? This is equivalant to

    if (left && right) {
        return root;
    } else if (left) {
        return left;
    } else {
        return right
    }

If you do `if(left)` and `if(right)` the condition of `left && right` won't be valid anymore since it will just return straight to either left or right.

**Complexity:**

* Time complexity: O(n) where n is the number of node.

* Space complexity: O(n) since it's the recursion stack