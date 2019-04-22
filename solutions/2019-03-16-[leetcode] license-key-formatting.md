---
layout: post
title:  "[leetcode] 482.License Key Formatting"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/license-key-formatting](https://leetcode.com/problems/license-key-formatting)

> Runtime: 72 ms, faster than 85.21% of JavaScript online submissions for License Key Formatting.
>
> Memory Usage: 38.2 MB, less than 76.09% of JavaScript online submissions for License Key Formatting.

```javascript
/**
 * @param {string} S
 * @param {number} K
 * @return {string}
 */
var licenseKeyFormatting = function(S, K) {
    S = S.split('-').join('').toUpperCase();
    var result = [];
    for (let i = S.length; i > 0; i -= K) {
        var temp = S.substr(i-K, K);
        if(i-K < 0) {
           temp = S.substr(0, S.length % K);
        }
        result.push(temp);
    }
    return result.reverse().join('-');
};
```
