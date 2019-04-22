---
layout: post
title:  "[leetcode] Unique Email Addresses"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/unique-email-addresses](https://leetcode.com/problems/unique-email-addresses)

> Runtime: 80 ms, faster than 80.94% of JavaScript online submissions for Unique Email Addresses.
>
> Memory Usage: 38.6 MB, less than 95.49% of JavaScript online submissions for Unique Email Addresses.

이메일 배열이 주어지면 그 안에 유니크한 이메일이 몇게가 들어있는지를 묻는 문제.
이메일은 로컬네임과 도메인으로 구성되어 있으며,`@`로 구분된다. 로컬네임은 `.`는 무시되고, `+` 이후는 생략된다는 게 이 문제의 전제조건이다.
유니크한 이메일을 찾을 때마다 배열에 push하여 그 길이를 리턴하면 된다.
그러기 위해 먼저 로컬네임과 도메인을 나눈다.
로컬네임에서 `+` 이 후를 지워주고, `.`부분을 지우기 위해 split한 이후에 다시 join해준다.
마지막으로 로컬네임과 도메인을 붙여주고, 유니크배열에 이미 들어있는지 아닌지 체크 후 넣어준다.

```javascript
/**
 * @param {string[]} emails
 * @return {number}
 */
var numUniqueEmails = function(emails) {
    const validMails = [];
    emails.forEach(email => {
        const domain = email.slice(email.lastIndexOf('@'));
        let localName = email.slice(0, email.lastIndexOf('@'));
        if (localName.includes('+')) {
           localName = localName.slice(0, localName.indexOf('+'));
        }
        while(localName.includes('.')) {
            localName = localName.split('.').join('');
        }
        const formed = localName.concat(domain);
        if(!validMails.includes(formed)) {
            validMails.push(formed);
        }
    });
    return validMails.length;
};
```
