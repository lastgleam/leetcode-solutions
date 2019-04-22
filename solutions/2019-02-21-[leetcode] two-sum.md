---
layout: post
title:  "[leetcode] Two Sum"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

투썸이라니
한국의 투썸플레이스라는 카페가 생각난다...

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for (let i=0; i < nums.length- 1; i++) {
        for(let j = i+1; j < nums.length; j++ ){
            if(nums[i]+nums[j] == target) {
                return [i,j];
            }
        }
    }
};
```
