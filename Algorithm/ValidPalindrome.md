Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.
> 给一个字符串，判断是否是一个回文，仅考虑英文字符和数字，不区分大小写

Note: For the purpose of this problem, we define empty string as valid palindrome.
> 对于这个问题，空字符串也认为是回文

Example 1:
```
Input: "A man, a plan, a canal: Panama"
Output: true
```
Example 2:
```
Input: "race a car"
Output: false
```
### 版本1
```go
/**
 * 首先想到的是使用正则表达式，把所有需要的字符匹配出来，返回一个切片，然后再用strings.Join()函数转换为字符串，在统一转换为小写，对字符串进行遍历，
 * 使用双指针，一个从头开始遍历，一个从末尾开始遍历
**/
func isPalindrome(s string) bool {
    regexp := regexp.MustCompile("[a-zA-Z0-9]+")
    slice := regexp.FindAllString(s, -1)
    if len(slice) == 0 {
        return true
    }
    str := strings.ToLower(strings.Join(slice, ""))
    for i, j := 0, len(str) - 1; i < j; i, j = i + 1, j -1 {
        if str[i] != str[j] {
            return false
        }
    }
    return true
}
```
