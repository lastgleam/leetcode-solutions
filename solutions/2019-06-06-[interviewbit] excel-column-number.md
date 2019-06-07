URL : https://www.interviewbit.com/problems/excel-column-number/

```javascript
module.exports = { 
 //param A : string
 //return an integer
    titleToNumber : function(A){
        var decimal = 0;
        for (var i = 0; i < A.length; i++) {
            var digit = (A.length - 1) - i;
            // A~Z is 65~90 in ascii table 
            var code = parseInt(A.charCodeAt(i), 10) - 64;
            decimal += (Math.pow(26, digit) * code);
        }
        return decimal;
    }
};
```

A to Z로 이루어진 26진수를 10진수로 변환한다.

먼저 알파벳을 10진수로 바꾸기 위해 `charCodeAt()` 을 이용하여 A일 때 1이 되도록 64를 빼주고

자리수를 계산하여 곱한 후 결과에 더해준다. O(N)의 시간복잡도를 갖는다.



A to Zの値を持つ２６進数の文字列を10進数に変換する。

まずアルファベットを`charCodeAt()`を用いてASCIIコード番号を得て64を引く。

forループのポインターで桁を計算し、戻り値に足していく。

O(N)の時間計算量を持つ。