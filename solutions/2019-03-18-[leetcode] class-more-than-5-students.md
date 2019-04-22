---
layout: post
title:  "[leetcode] 592.class-more-than-5-students"
author: "lastgleam"
---
URL : [https://leetcode.com/problems/class-more-than-5-students](https://leetcode.com/problems/class-more-than-5-students)

유니크한 값만 카운트 하는 것이 중요한 포인트였다.
때문에 COUNT()를 할 때 `DISTINCT`를 넣어주어야 한다.


> Runtime: 1179 ms, faster than 19.35% of Oracle online submissions for Classes More Than 5 Students.
>
>  Memory Usage: N/A


```sql
/* Write your PL/SQL query statement below */
select class as class from courses group by class having count(distinct student) >= 5;
```
