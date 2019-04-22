---
layout: post
title:  "[leetcode] Multiply Strings"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/multiply-strings/](https://leetcode.com/problems/multiply-strings/)

３時間くらい頑張っても解けず、諦めた。

```javascript
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var multiply = function(num1, num2) {
    const map = new Map([
       ["0",0],["1",1],["2",2],["3",3],["4",4],["5",5],["6",6],["7",7],["8",8],["9",9]
    ]);
    const result = new Map();
    num1Array = [];
    num2Array = [];
    
    for (let i = 0; i < num1.length; i++) {
        num1Array.push(num1.charAt(i));
    }
    for (i = 0; i < num2.length; i++) {
        num2Array.push(num2.charAt(i));
    }
    
    num1Array.reduce((prev1, now1, index1) => {
        const x = map.get(now1);
        const xC = (num1Array.length - index1 - 1);
        num2Array.reduce((prev2, now2, index2) => {
            const y = map.get(now2);
            const yC = (num2Array.length - index2 - 1);
            let temp = (x * y * (10 ** yC));
            temp = Number(temp).toString();
            tempArray = [];
            for (i = 0; i < temp.length; i++) {
                tempC = temp.length - i - 1;
                if(result.get(tempC)) {
                    result.get(tempC).push(temp.charAt(i));
                    continue;
                }
                result.set(tempC, [temp.charAt(i)]);
            }
        }, 0);
    }, 0);
    console.log(result);
    
    i = 0;
    let carry = 0;
    let str = "";
    while(result.get(i)) {
        console.log(i);
        let plus = result.get(i).reduce((prev, now) => (map.get(prev) || prev) + map.get(now), 0);
        plus += carry;
        console.log(plus);
        carry = Math.floor(plus / 10);
        plus %= 10;
        str = plus + str;
        i++;
    }

    return str;
};
```
