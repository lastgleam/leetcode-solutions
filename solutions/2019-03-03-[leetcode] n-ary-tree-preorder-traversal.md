---
layout: post
title:  "[leetcode] N-ary Tree Preorder Traversal"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/n-ary-tree-preorder-traversal/](https://leetcode.com/problems/m-ary-tree-preorder-traversal/)

이 문제는 재귀함수를 이용하면 간단히 풀 수 있는 문제였으나 note에 "재귀함수로 푸는건 쉬우니깐 이터레이티브하게 풀 수 있음?"이라고 되어있었던 관계로 재귀함수의 콜스택을 array와 pop()함수로 스택을 구현하여 흉내내었다.
아예 다른 풀이를 원하는 줄 알았으나, 애초에 재귀란 무엇인가를 한번 더 곱씹게 해준 고마운 문제였다.

> Runtime: 624 ms, faster than 100.00% of JavaScript online submissions for N-ary Tree Preorder Traversal.

>
> Memory Usage: 81.2 MB, less than 38.00% of JavaScript online submissions for N-ary Tree Preorder Traversal.


```javascript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */
/**
 * @param {Node} root
 * @return {number[]}
 */
var preorder = function(root) {
    let result = [];
    let stack = [];
    if(!root) {
        return result;
    }
    result.push(root.val);
    if (root.children) {
       for (let i = root.children.length - 1; i >= 0; i--) {
            stack.push(root.children[i]);
        } 
    }
    console.log(stack);
    while (stack.length > 0) {
        const node = stack.pop();
        result.push(node.val);
        if(node.children) {
            for(let j = node.children.length - 1; j >= 0; j--) {
                stack.push(node.children[j]);
            }
        }
    }
    return result;
};
```
