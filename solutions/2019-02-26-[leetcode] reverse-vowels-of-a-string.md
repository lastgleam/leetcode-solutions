---
layout: post
title:  "[leetcode] Reverse Vowels of a String"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/reverse-vowels-of-a-string/](https://leetcode.com/problems/reverse-vowels-of-a-string/)

양쪽 끝에서 동시에 탐색하는 투 포인터 문제였다.
일단 처음 작성한 답안은 다음과 같다.

> Runtime: 3260 ms, faster than 5.13% of JavaScript online submissions for Reverse Vowels of a String.
> 
> Memory Usage: 43.9 MB, less than 31.03% of JavaScript online submissions for Reverse Vowels of a String.

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
    const indexes = [];
    let mid = 0;
    for(let i = 0; i < s.length; i++) {
        if (s.charAt(i).match(/(a|e|i|o|u)/i)) {
            indexes.push(i);
        } 
    }
    if (indexes % 2 !== 0) {
        mid = (s.length - 1) / 2;
    } else {
        mid = (s.length /2 - 1);
    }
    let result = "";
    let count = 0;
    for(i = 0; i < s.length; i++) {
        if (indexes.includes(i)) {
            if (count <= mid) {
                result += s.charAt(indexes[indexes.length - 1 - count]);
            } else {
                result += s.charAt(indexes[count - 1 - indexes.length]);
            }
            count++;
        } else {
            result += s.charAt(i);
        }
    }
    return result;
};
```

두번째 풀이는 two-pointer에 따라서
첫 지점과 끝 지점에서 각각 출발해서 모음인 부분의 인덱스에서 멈춰세우고, 얻게된 두가지 캐릭터의 위치를 바꿔나갔다.
또 상위 while문을 `start < end`로 비교하여 연산을 끝내고 자리바꿈을 끝낸 배열을 `join("")`으로 string으로 만들어 리턴했다.
string값도`split("")`로 캐릭터를 가진 배열로 분할할 수 있기 때문에 한결 쉽게 자리바꿈 로직을 짤 수 있었다.

>Runtime: 80 ms, faster than 89.74% of JavaScript online submissions for Reverse Vowels of a String.
Memory Usage: 38.3 MB, less than 89.66% of JavaScript online submissions for Reverse Vowels of a String.

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
    if(s && s.length < 2) {
        return s;
    }
    const vowels = ["a","e","i","o","u","A","E","I","O","U"];
    let splitted = s.split("");
    let mid = 0;
    let start = 0;
    let end = s.length - 1;
    while (start < end) {
        while(start < s.length) {
            if(vowels.includes(s.charAt(start))) {
                break;    
            }
            start++;
        }
        while(end > -1) {
            if(vowels.includes(s.charAt(end))) {
                break;    
            }
            end--;
        }
        if (start < end) {
            const temp = splitted[start];
            splitted[start] = splitted[end];
            splitted[end] = temp;
            start++;
            end--;
        }
    }
    return splitted.join("");
};
```
