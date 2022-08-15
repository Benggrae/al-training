# Isomorphic Strings

Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

> 두 문자열의 패턴이 맞는지를 검사한다.

```text
Example 1:

Input: s = "egg", t = "add"
Output: true
Example 2:

Input: s = "foo", t = "bar"
Output: false
Example 3:

Input: s = "paper", t = "title"
Output: true
 

Constraints:

1 <= s.length <= 5 * 104
t.length == s.length
s and t consist of any valid ascii character.
```

## 접근 방법

1. 길이가 다르면 이미 같은 패턴이 아니다.
2. 문자열 패턴의 키와 맵핑할 수 있는 오브젝트를 생성하여 맵핑 정보를 담는다.
3. 맵핑 정보와 다르면 해당 패턴은 틀린것으로 간주

### 코드

* 내가 작성한 코드

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
    //아이디어 
    // 1. 길이가 다르면 이미 틀림;
    // 2. 문자열 패턴 정보를 담은 인덱스 맵을 구현 
    // 3. 비교 하면서 해봄 
    if (s.length !== t.length) {
        return false;
    }
    
    
    let sMap = {};
    let tMap = {};
    let sc = 0;
    
    for (let i = 0; i < s.length; i++) {
        let skey = s.substring(i, i + 1);
        let tkey = t.substring(i, i + 1);
        if (sMap[skey] !== tMap[tkey]) {
            return false;
        }
        
        if (!sMap[skey]) {
            sMap[skey] = sc;
            tMap[tkey] = sc;
            sc++;
        }
     }
    
    return true;
};

```

* 빠른 방법

> 나와 조금 다른 점은 맵핑값을 타겟 값으로 설정했다는 것이다.

```javascript
var isIsomorphic = function(s, t) {
    let mapping = {}
    let mapped = new Set()
    if (s.length !== t.length) return false
    
    for (let i = 0; i < s.length; i++) {
        let s_char = s[i]
        let t_char = t[i]
        
        
        if (mapping[s_char] && mapping[s_char] !== t_char)
            return false
        
        if (!mapping[s_char]){
            if (mapped.has(t_char)) return false // already mapped
            mapping[s_char] = t_char
            mapped.add(t_char)
        }
    }
    return true
};
```

* indexOf를 활용한 고수

```javascript
  /**
   * @param {string} s
   * @param {string} t
   * @return {boolean}
   */
  var isIsomorphic = function(s, t) {
      for(i=0;i<s.length;i++){
          if(s.indexOf(s[i], i+1)!==t.indexOf(t[i],i+1)) return false;   
      }
      return true;
  };

```
