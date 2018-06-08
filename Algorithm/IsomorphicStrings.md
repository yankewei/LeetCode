### Isomorphic Strings(同构字符串)

#### 描述
> Given two strings s and t, determine if they are isomorphic.  
给两个字符串，判断是否是同构

> Two strings are isomorphic if the characters in s can be replaced to get t.  
两个字符串是同构取决于`s`能够被`t`替换

#### 例如
```
Input: s = "egg", t = "add"
Output: true
```
```
Input: s = "foo", t = "bar"
Output: false
```
```
Input: s = "paper", t = "title"
Output: true
```
#### 注意:
> You may assume both s and t have the same length.  
你可以假设`s`和`t`长度相同

#### Go
```go
func isIsomorphic(s string, t string) bool {
	dict1 := make(map[byte]byte)
	dict2 := make(map[byte]byte)
    for i := 0; i < len(s); i++ {
        value, exist := dict1[s[i]]
        if !exist {
            dict1[s[i]] = t[i]
        } else if value != t[i] {
			return false
		}
		value, exist = dict2[t[i]]
		if !exist {
			dict2[t[i]] = s[i]
		} else if value != s[i] {
			return false
		}
	}
    return true
}
```
