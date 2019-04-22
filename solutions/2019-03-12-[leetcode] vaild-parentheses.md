---
layout: post
title:  "[leetcode] Vaild Parentheses"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/valid-parentheses](https://leetcode.com/problems/valid-parentheses)

> Runtime: 72 ms, faster than 45.23% of JavaScript online submissions for Valid Parentheses.
>
> Memory Usage: 34.8 MB, less than 28.15% of JavaScript online submissions for Valid Parentheses.

소중대괄호로만 이루어진 스트링의 안에서 괄호끼리 쌍이 맞으면 true, 아니면 false를 리턴한다.

for문으로 스트링의 한 캐릭터씩 돌리는데 닫는 괄호일 경우 직전의 캐릭터와 비교하여 쌍이 맞는지 확인한다.
맞지 않으면 그 즉시 false를 리턴한다.
마지막까지 다 돌렸는데도 임시 배열의 길이가 0이 아니면 쌍이 안맞는 괄호가 남아있는 것이므로 false를 리턴한다.

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const map = new Map([
        [")","("],
        ["}","{"],
        ["]","["]
    ]);
    const array = [];
    for (let i = 0; i < s.length; i++) {
        let char = s.charAt(i);
        if (char === "(" || char === "{" || char === "[") {
            array.push(char);
        } else {
            if (array.length > 0 && array[array.length - 1] === map.get(char)) {
                array.pop();
            } else {
                return false;
            }
        }
    }
    if (array.length > 0) {
       return false;
    }
    return true;
};
```
