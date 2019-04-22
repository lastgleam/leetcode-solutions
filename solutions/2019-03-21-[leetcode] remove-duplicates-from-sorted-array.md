---
layout: post
title:  "[leetcode] 26.Remove Duplicates From Sorted Array"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/remove-duplicates-from-sorted-array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)

공간 복잡도가 O(1)어야만 하고, 다른 배열은 선언할 수 없는 제한사항에 주의 하자.

> Runtime: 92 ms, faster than 57.79% of JavaScript online submissions for Remove Duplicates from Sorted Array.
>
> Memory Usage: 37.3 MB, less than 34.08% of JavaScript online submissions for Remove Duplicates from Sorted Array.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    let i = 0;
    while (i < nums.length) {
        if (nums[i] === nums[i+1]) {
           nums.splice(i+1, 1); 
        } else {
            i++;
        }
    }
    return nums.length;
};
```
