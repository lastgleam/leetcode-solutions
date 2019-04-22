---
layout: post
title:  "[leetcode] 944.Largest Time For Given Digits"
author: "lastgleam"
---

URL : [https://leetcode.com/problems/largest-time-for-given-digits](https://leetcode.com/problems/largest-time-for-given-digits)

 [2,0,6,6] 일 때 20:66이 나와서 풀이실패.

추후 재도전 예정.  

```javascript
/**
 * @param {number[]} A
 * @return {string}
 */
var largestTimeFromDigits = function(A) {
    let hour = -1;
    let min = -1;
    let first = 0;
    let second = 0;
    
    for (let i = 0; i < A.length; i++) {
        for (let j = 0; j < A.length; j++) {
            if(i === j) {
                continue;
            }
            const temp = Number.parseInt(A[i] + "" + A[j]);
            if(temp < 24 && temp > hour) {
                hour = temp;
                first = i;
                second = j;
            }
        }
    }
    if(hour === -1) {
        return "";
    }
    A[first] = null;
    A[second] = null;
    console.log(hour);
    A = A.filter(cur => cur !== null);
    for (i = 0; i < A.length; i++) {
        for (j = 0; j < A.length; j++) {
            if(i === j) {
                continue;
            }
            const temp = Number.parseInt(A[i] + "" + A[j]);
            if(temp < 60 && temp > min) {
                min = temp;
            }
        }
    }
    if(min === -1) {
        return "";
    }
    hour = hour.length < 2 ? "0" + hour : hour;
    min = min.length < 2 ? "0" + min : min;
    return hour + ":" + min;
};
```