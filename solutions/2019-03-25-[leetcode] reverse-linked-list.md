---
layout: post
title:  "[leetcode] 206.Reverse Linked List"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/reverse-linked-list](https://leetcode.com/problems/reverse-linked-list)

일단 iteratively하게 풀었다.

예를 들어 [1,2,3,4,5]일 경우, 선형으로 이동하면서 next값을 이전 노드로 바꿔주면 된다.
1일 때는 null, 2일 때는 1...5일 때 4를 next에 대입해주고 마지막 노드를 리턴한다.

> Runtime: 80 ms, faster than 20.13% of JavaScript online submissions for Reverse Linked List.
>
> Memory Usage: 35 MB, less than 49.80% of JavaScript online submissions for Reverse Linked List.

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
    let cur = head;
    let prev = null;
    while (cur !== null) {
        const next = cur.next;
        cur.next = prev;
        prev = cur;
        cur = next;
    }
    return prev;
};
```
