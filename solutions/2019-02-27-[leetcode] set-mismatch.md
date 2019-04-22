---
layout: post
title:  "[leetcode] Set Mismatch"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/set-mismatch/](https://leetcode.com/problems/set-mismatch/)

미리 오름차순 정렬해놓고 현재값과 다음값을 비교해서 같을 경우 리턴하면 되는 문제였다.
하지만 처음에 정렬이 필요없다고 생각하여 먼저 두 번 들어있는 값을 구하고 들어있지 않은 값을 찾는 식으로 풀이했더니 런타임이 980ms에 육박하게 되었다.
정렬을 O(N)으로 하는 방법을 알아야할 것 같다. (물론 이 문제 안에서)

> Runtime: 980 ms, faster than 5.04% of JavaScript online submissions for Set Mismatch.
>
> Memory Usage: 50.8 MB, less than 12.50% of JavaScript online submissions for Set Mismatch.

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    for (let i = 0; i< nums.length; i++) {
        if(nums.slice(i+1).includes(nums[i])) {
            for (let j = 0; j < nums.length; j++) {
                if (nums[j] !== 1 && !nums.includes(nums[j] - 1)) {
                    return [nums[i], nums[j] - 1]; 
                } else if (nums[j] !== nums.length && !nums.includes(nums[j] + 1)) {
                    return [nums[i], nums[j] + 1];
                }
            }
        }
    }
};
```
