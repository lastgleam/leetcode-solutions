---
layout: post
title:  "[leetcode] Add To Array Form Of Integer"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/add-to-array-form-of-integer](https://leetcode.com/problems/add-to-array-form-of-integer)

자리수를 맞추어 덧셈을 유도하는 문제다.
주어지는 매개변수가 배열과 int형이기 때문에
int를 배열로 바꾼 후 길이가 짧은 배열에 0을 unshift하여 넣어주어 길이를 맞출 필요가 있다.
예를 들어, [1,2,0,0]과 34가 주어진 경우, 34를 [3,4]로 변환 후 `unshift()`로 [0,0,3,4]로 만들어준다.

> Runtime: 268 ms, faster than 5.45% of JavaScript online submissions for Add to Array-Form of Integer.
>
> Memory Usage: 42 MB, less than 29.31% of JavaScript online submissions for Add to Array-Form of Integer.

```javascript
/**
 * @param {number[]} A
 * @param {number} K
 * @return {number[]}
 */
var addToArrayForm = function(A, K) {
    K = K.toString().split("");
    let result = [];
    let carry = 0;
    let differ = A.length - K.length;
    if(differ > 0) {
        let count = 0;
        while (count < differ) {
            K.unshift(0);
            count++;
        }
    } else {
        let count = 0;
        while (count < Math.abs(differ)) {
            A.unshift(0);
            count++;
        }
    }
    for (let i = A.length - 1; i >= 0; i--) {
        let a = A[i];
        let k = Number.parseInt(K[i]);
        const now = a + k + carry;
        result.unshift(now % 10);
        carry = Math.floor(now / 10);
    }
    if (carry > 0) {
        result.unshift(carry);
    }
    return result;
};
```
