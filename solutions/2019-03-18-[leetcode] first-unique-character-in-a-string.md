---
layout: post
title:  "[leetcode] 387.first-unique-character-in-a-string"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/first-unique-character-in-a-string](https://leetcode.com/problems/first-unique-character-in-a-string)

첫번째 유니크한 캐릭터의 인덱스를 찾는 문제다.

처음에 주어진 문자열의 길이만큼 돌면서 탐색하는 식으로 짰는데 무려 2760ms이나 걸렸다.

따라서 Map을 사용하여 처음 등장한 캐릭터는 true, 이미 같은 캐릭터가 등록되어 있다면 false를 주는 식으로하여 O(N)만큼 처리 후, 다시 문자열의 길이만큼 돌면서 true이면 인덱스를 리턴하는 식으로 짰다.

최대 0(2N)만큼 걸리는 로직이다.


> Runtime: 108 ms, faster than 61.74% of JavaScript online submissions for First Unique Character in a String.
>
> Memory Usage: 37.6 MB, less than 87.56% of JavaScript online submissions for First Unique Character in a String.

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function(s) {
    var checked = new Map();
    for (let i = 0; i < s.length; i++) {
        if(checked.has(s[i])) {
            checked.set(s[i], false);
        } else {
            checked.set(s[i], true);
        }
    }
    for (let j = 0; j < s.length; j++) {
        if(checked.has(s[j]) && checked.get(s[j])) {
            return j;
        }
    }
    return -1;
};
```
