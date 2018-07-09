Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.
> 给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

If the last word does not exist, return 0.
> 如果不存在最后一个单词，请返回 0 。

Note: A word is defined as a character sequence consists of non-space characters only.
> 说明：一个单词是指由字母组成，但不包含任何空格的字符串。

Example:
```
Input: "Hello World"
Output: 5
```

### Go
```go
/*
 * 因为是最后一个单词的长度，而且是以空格来区分一个单词。那么我们应该先把两端的空格去除掉。因为它不属于单词。然后在用字符串函数去切分字符串，转换为切片
 * 最后去除切片的最后一个元素即可。
 */
func lengthOfLastWord(s string) int {
    slice := strings.Split(strings.Trim(s, " "), " ")
    return len(slice[len(slice) - 1])
}
```
