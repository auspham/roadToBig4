---
title: Amazon Merge Two Sorted Lists
date: 2019-12-24 09:23:00 Z
tags:
- Amazon
solved: true
---

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

    Input: 1->2->4, 1->3->4
    Output: 1->1->2->3->4->4
    

---

Company: Amazon

Startup code:

    var mergeTwoLists = function(l1, l2) {
    
    };

**What I learn?**

1. For link-list questions, just stop make a new node if it's the end. *Don't make a new node and then make it to null, it doesn't work like that*

2. When checking `l2.val <= l1.val` or accessing an attribute of an object, *always check if the object is null or not*.

**My solution**

    var mergeTwoLists = function(l1, l2) {
        let head = new ListNode(null);
        let curr = head;
    
        if(l1 == null && l2 == null) {
            return null;
        }
    
        while(l1 !== null || l2 !== null) {
            if(l1 !== null && (l2 == null || l1.val <= l2.val )) {
                curr.val = l1.val;
                l1 = l1.next;
            } else {
                curr.val = l2.val;
                l2 = l2.next;
            }
    
            if( l1 || l2 ) {
                /*To avoid to create new node*/
                curr.next = new ListNode(null);
            }
            curr = curr.next;
        }
        return head;
    };

Complexity: O(n) because you go through the list once. Space: O(n) it's just a combination of 2 lists

**What I like about my solution:** It's very intuitive, straight to the point of what the piece of code is doing. I generate the node on the fly of comparing between the 2 node `l1` and `l2`

**What I could do instead** The problem - which I don't like with my code is for every-time I create a new node, I'll have to check *if it is worth creating*. This checking is wrapped in a function

    if( l1 || l2 ) {
    ...
    }

which is really cumbersome.

*Solution* The question is asking about **merging 2 lists**. So *why do we create a new node?*, why don't we just reuse our node and merge them together?

One of the solution:

    var mergeTwoLists = function(l1, l2) {
        let head = new ListNode(0);
        let list = head;
    
        while (l1 && l2) {
            if (l1.val > l2.val) {
                list.next = l2;
                l2 = l2.next;
            } else {
                list.next = l1;
                l1 = l1.next
            }
    
            list = list.next;
        }
    
            /* It will by default pick l1, if l1 is null, it will then pick l2 */
        list.next = l1 || l2;
    
            /* Because the first one is 0 so you need to call next to start pointing to the first node.*/
        return head.next;
    };