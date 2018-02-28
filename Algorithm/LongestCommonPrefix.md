问题描述：
Write a function to find the longest common prefix string amongst an array of strings.

例子：
```
```

解决方法：
```go
func longestCommonPrefix(strs []string) string {
        var prefix string
        if (len(strs) == 0) {
                prefix = ""
        } else {
                prefix = strs[0]
                for i := 1; i < len(strs); i++ {
                        for strings.HasPrefix(strs[i], prefix) == false {
                                prefix = string([]rune(prefix)[:len(prefix) - 1])
                        }
                }
        }
        return prefix
}
```
