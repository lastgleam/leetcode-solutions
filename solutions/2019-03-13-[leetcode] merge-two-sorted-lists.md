---
layout: post
title:  "[leetcode] Merge Two Sorted Lists"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/merge-two-sorted-lists](https://leetcode.com/problems/merge-two-sorted-lists)

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if (!l1 && !l2) {
       return null; 
    }
    let nextNode;
    const first = new ListNode(0);
    let l1val = l1 ? l1.val : 0;
    let l2val = l2 ? l2.val : 0;
    if (l1val <= l2val) {
        first.next = new ListNode(l1val);
        first.next.next = new ListNode(l2val);   
    } else {
        first.next = new ListNode(l2val);
        first.next.next = new ListNode(l1val);            
    }
    nextNode = first.next.next;
    if(l1) {
       l1 = l1.next; 
    }
    if(l2) {
       l2 = l2.next; 
    }    
    while (l1 || l2) {
        l1val = l1 ? l1.val : 0;
        l2val = l2 ? l2.val : 0;
        if (l1val <= l2val) {
            nextNode.next = new ListNode(l1val);
            nextNode.next.next = new ListNode(l2val);   
        } else {
            nextNode.next = new ListNode(l2val);
            nextNode.next.next = new ListNode(l1val);            
        }
        nextNode = nextNode.next.next;
        if(l1) {
           l1 = l1.next; 
        }
        if(l2) {
           l2 = l2.next; 
        }
    }
    return first.next;
};
```
