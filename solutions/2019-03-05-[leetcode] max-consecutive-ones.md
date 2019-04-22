---
layout: post
title:  "[leetcode] Max Consecutive Ones"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/max-consecutive-ones](https://leetcode.com/problems/max-consecutive-ones)

주어진 배열에서 가장 길게 1이 연속된 값을 리턴하는 문제다.
O(n)으로 풀 수 있는 문제로, 1이 나올때마다 카운트하고 0이 나올때마다 max값과 비교하여 더 크면 max에 카운트된 값을 할당하는 방식으로 해결한다. 

> Runtime: 76 ms, faster than 54.71% of JavaScript online submissions for Max Consecutive Ones.
>
> Memory Usage: 37 MB, less than 56.06% of JavaScript online submissions for Max Consecutive Ones.


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    let max = 0;
    let temp = 0;
    for(let i = 0; i < nums.length; i++) {
        if(nums[i] === 1) {
            temp += 1;
        } else if (nums[i] === 0) {
            if(temp > max) {
                max = temp;
            }
            temp = 0;
        }
    }
    if(temp > max) {
        max = temp;
    }
    return max;
};
```
)
