---
layout: post
title:  "[leetcode] Binary Subarrays With Sum"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/binary-subarrays-with-sum/](https://leetcode.com/problems/binary-subarrays-with-sum/)


> Runtime: 2092 ms, faster than 35.85% of JavaScript online submissions for Binary Subarrays With Sum.
> 
> Memory Usage: 37.2 MB, less than 100.00% of JavaScript online submissions for Binary Subarrays With Sum.

제출된 다른 유저들 코드를 보니 내께 너무 씸플해서 O(N^2)으로 푼게 잘못인가...하는 생각이 든다.

```javascript
/**
 * @param {number[]} A
 * @param {number} S
 * @return {number}
 */
var numSubarraysWithSum = function(A, S) {
    let count = 0;
    for (let i = 0; i < A.length; i++) {
        let sum = 0;
        for(let j = i; j < A.length; j++) {
            sum += A[j];
            if (sum === S) {
                 ++count;
            }
        }
    }
    return count;
};
```
