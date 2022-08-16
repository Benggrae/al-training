# Is Subsequence

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

> 문자열이 특정 문자열이 포함될 경우를 찾는다.

```text
Example 1:

Input: s = "abc", t = "ahbgdc"
Output: true
Example 2:

Input: s = "axc", t = "ahbgdc"
Output: false
 

Constraints:

0 <= s.length <= 100
0 <= t.length <= 104
s and t consist only of lowercase English letters.
```

## 접근 방법

1. 순회하면서 문자를 찾는다.

### 코드

* 내가 푼 풀이

```javascript
  var isSubsequence = function(s, t) {
    if (s.length === 0 && t.length === 0) {
        return true;
    }
    
    const colectCount = s.length;
    let findIndex = 0;
    
    for (let i = 0; i < t.length; i++) {
        const findChar = s[findIndex];
        
        if (findChar === t[i]) {
            findIndex++;
        }
        if (findIndex === colectCount) {
            return true;
        }
    }
    
    return false;
```

* 최적화 풀이

```javascript
    let curIdx = 0;
    
    for(let i = 0; i < t.length; i++) {
        const letter = t[i];

        if (letter === s[curIdx]) {
            curIdx += 1;
        }
    }

    return curIdx === s.length;
```
