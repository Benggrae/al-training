# Longest Palindrome

Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

```text
Example 1:

Input: s = "abccccdd"
Output: 7
Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.
Example 2:

Input: s = "a"
Output: 1
Explanation: The longest palindrome that can be built is "a", whose length is 1.
 

Constraints:

1 <= s.length <= 2000
s consists of lowercase and/or uppercase English letters only. 

```

> 요약 : 주어진 문자열에서 대칭되는 문자열의 길이 구한다.

## 아이디어

1. 문자열이 2개가 되면 대칭이 된다.
2. 2개이외의 하나의 문자열이 있는 경우 해당 값도 랭스에 포함이된다.
3. Set을 활용하여 값을 만나면 길이를 2 증가 하고 키가 남으면 +1 을 한다.

### Code

```javascirpt
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
    let set = new Set();
    let length = 0; 
    
    for (let i = 0; i < s.length; i++) {
        const data = s[i];
        if (set.has(data)) {
            set.delete(data);
            length += 2;
        } else {
            set.add(data);
        }
    }

    
    return set.size > 0 ? length + 1 : length;
    
};
```
