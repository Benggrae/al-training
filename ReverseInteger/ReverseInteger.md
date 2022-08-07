### 숫자를 뒤집어서 출력
  
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**

```text
  Example 1:

  Input: x = 123
  Output: 321
  Example 2:

  Input: x = -123
  Output: -321
  Example 3:

  Input: x = 120
  Output: 21
  

  Constraints:

  -231 <= x <= 231 - 1
  Accepted
  2,180,228
  Submissions
```
--- 

### 문제풀이 
> 각 숫자자리를 쪼게서 뒤에서 붙어 자리수를 이어 붙이는 아이디어 
```javascirpt
/**
 * @param {number} x
 * @return {number}
 */

//숫자 범위
const MIN_VALUE = Math.pow(2, 31) * -1;
const MAX_VALUE = Math.pow(2, 31) -1;

var reverse = function(x) {
    let isMinus = x < 0 ? true : false;
    x = Math.abs(x);
    
    let result = 0;
    let size = (x+"").length - 1;
    let count = 0;

    for (let i = 0; i <= size; i++) {
        let digitNumber = Math.pow(10, size - i);
        let div = parseInt(x / digitNumber);
        x = x - (div * digitNumber);
        result += div * Math.pow(10, count);
        count++;
    }
    
    if (isMinus) {
        result = result * -1;
    }
    
    if (result < MIN_VALUE || result > MAX_VALUE) {
        return 0;
    }
    
    return result;    
    
};


```

