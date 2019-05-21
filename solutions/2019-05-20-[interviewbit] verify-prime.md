URL : https://www.interviewbit.com/problems/verify-prime/

Given a number N, verify if N is prime or not.

Return 1 if N is prime, else return 0.



My first answer is:

```javascript
module.exports = { 
 //param A : integer
 //return an integer
	isPrime : function(A){
	  if(A === 1) return 0;
	  if(A === 2) return 1;
    for (var i = 2; i < A / 2; i++) {
      if(A % i === 0) return 0;
    }
    return 1;
	}
};
```

to make it more efficient, replace `A/2` with `Math.pow(A, 0.5)` or `Math.sqrt(A)` with equality in the end condition.
that would have time complexity of O(root of N).



Why? Because you don't have to check the numbers from `root of A` to `A/2` .

for example, When A is 14, root of 14 is 3.xx. 

so the numbers from `root of A` to `A/2`  would be `4,5,6,7,8,9,10,11,12,13`.

`4,6,8,9,10,12` are composite number. they have 2 or 3 as a factor.

As 2 and 3 are smaller than root of 14, they have been checked already. 

`5,7,11,13` are prime number, so they cannot be the factor of 14.

As a result, we can make it more efficiently by changing the end condition.



more efficient answer is:

```javascript
module.exports = { 
 //param A : integer
 //return an integer
	isPrime : function(A){
	  if(A === 1) return 0;
	  if(A === 2) return 1;
    for (var i = 2; i <= Math.sqrt(A); i++) {
      if(A % i === 0) return 0;
    }
    return 1;
	}
};
```



Ref: https://stackoverflow.com/questions/5811151/why-do-we-check-up-to-the-square-root-of-a-prime-number-to-determine-if-it-is-pr