---
layout: post
title:  "[leetcode] Vaild Palindrome"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/valid-palindrome](https://leetcode.com/problems/valid-palindrome)

> Runtime: 80 ms, faster than 73.17% of JavaScript online submissions for Valid Palindrome.
>
> Memory Usage: 40.1 MB, less than 20.57% of JavaScript online submissions for Valid Palindrome.

회문인지 아닌지 판별하는 문제다. 공백문자, 특수문자제외, 대소문자 구별없이 판별한다.
`"A man, a plan, a canal: Panama"`는 `true`이고 `"race a car"`는 `false`다.

나는 지난 번 익힌 투 포인터 방식으로 풀었다.
투포인터 그런거 모르겠고, while문도 싫다면 for문으로 length의 반만큼 돌려도 된다. 대신 건너뛰기가 힘드므로 특수문자와 공백문자를 미리 제거해두어야 한다.

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
    const regex = /([a-z0-9])/;
    s = s.toLowerCase().split(" ").join("");
    let start = 0;
    let end = s.length - 1;
    while (start < end) {
        while (start < end && !s[start].match(regex)) {
            start++;
        }
        let front = s[start];
        while (start < end && !s[end].match(regex)) {
            end--;
        }
        let back = s[end];
        if (front !== back) {
            return false;
        }
        start++;
        end--;
    }
    return true;
};
```
