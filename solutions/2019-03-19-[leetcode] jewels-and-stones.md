---
layout: post
title:  "[leetcode] 767.jewels-and-stones"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/jewels-and-stones](https://leetcode.com/problems/jewels-and-stones)

J로 주어진 문자들이 S에 몇번 들어있는 지 세는 문제이다.
J안의 문자들은 서로 다른 문자라고 제한이 걸려있는데다가, S의 길이도 50이다.
정말로 여러가지 방법이 있을 수 있으나, 첨엔 퓨어하게 for문을 돌려가며 하나하나 일치비교 하는 식으로 두가지를 짜보았다.
그 후, descriptions에 올라온 다른 풀이들을 보고 세번째 방법을 짰다.
세번째 방법이 속도가 제일 빠르다.
문자열을 탐색하는 문제 였다면 라빈-카프 알고리즘으로 풀어야 하나, 애초에 J의 문자 자체가 해시값이나 다름없기 때문에 비교 로직만 짜넣으면 된다.


```javascript
/**
* First answer using 2-loops
* 
 * @param {string} J
 * @param {string} S
 * @return {number}
 */
var numJewelsInStones = function(J, S) {
    const checked = [];
    let count = 0;
    for (let i = 0; i < J.length; i++) {
        for (let j = 0; j < S.length; j++) {
            if (checked.includes(j)) {
               continue; 
            }
            if (J[i] === S[j]) {
                count++;
                checked.push(j);
            }
        }
    }
    return count;
};

/**
* Second answer using only one loop
* 
 * @param {string} J
 * @param {string} S
 * @return {number}
 */
var numJewelsInStones = function(J, S) {
    let count = 0;
    for (let i = 0; i < S.length; i++) {
        if(J.includes(S[i])) {
            count++;
        }
    }
    return count;
};

/**
* Second answer using HashSet and reduce
* 
 * @param {string} J
 * @param {string} S
 * @return {number}
 */
var numJewelsInStones = function(J, S) {
    const set = new Set(J.split(''));
    return S.split('').reduce(
        (count, now) => count + set.has(now)
    ,0);
};
```
