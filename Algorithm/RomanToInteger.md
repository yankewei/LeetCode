问题描述：
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

例子：
```
```
解决方法：
```go
func romanToInt(s string) int {
    dict := map[byte]int{
                'I': 1,
                'V': 5,
                'X': 10,
                'L': 50,
                'C': 100,
                'D': 500,
                'M': 1000,
        }
        length := len(s)
        sum := dict[s[0]]
        for i := 1; i < length; i++ {
                if dict[s[i]] <= dict[s[i-1]] {
                        sum += dict[s[i]]
                } else {
                        sum += (-2*dict[s[i-1]] + dict[s[i]])
                }
        }
        return sum
}
```
