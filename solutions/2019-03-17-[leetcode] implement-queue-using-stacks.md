---
layout: post
title:  "[leetcode] 232.implement-queue-using-stacks"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/implement-queue-using-stacks](https://leetcode.com/problems/implement-queue-using-stacks)

Stack으로 Queue를 구현하는 문제이다.
pop()를 구현하기 위해 임시 스택을 만들어서 reverse한 후 마지막 엘리먼트를 pop하여 다시 queue에 push해준다.

```text
Runtime: 56 ms, faster than 83.81% of JavaScript online submissions for Implement Queue using Stacks.

Memory Usage: 33.8 MB, less than 9.09% of JavaScript online submissions for Implement Queue using Stacks.
```

```javascript
/**
 * Initialize your data structure here.
 */
var MyQueue = function() {
    this.queue = [];
};

/**
 * Push element x to the back of queue. 
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function(x) {
    this.queue.push(x);
};

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function() {
    var temp = [];
    while(this.queue.length > 0) {
        temp.push(this.queue.pop());
    }
    var result = temp.pop();
    while(temp.length > 0) {
        this.queue.push(temp.pop());
    }
    return result;
};

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function() {
    return this.queue[0];
};

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function() {
    if(this.queue.length < 1) {
        return true;
    }
    return false;
};

/** 
 * Your MyQueue object will be instantiated and called as such:
 * var obj = Object.create(MyQueue).createNew()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.peek()
 * var param_4 = obj.empty()
 */
```
