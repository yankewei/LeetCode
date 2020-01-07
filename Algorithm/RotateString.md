###### 给定两个字符串, `A`和`B`。

###### `A`的旋转操作就是将 A 最左边的字符移动到最右边。 例如, 若 `A='abcde'`，在移动一次之后结果就是`'bcdea'`。如果在若干次旋转操作之后，`A`能变成`B`，那么返回`True`。

```
Example 1:
Input: A = 'abcde', B = 'cdeab'
Output: true

Example 2:
Input: A = 'abcde', B = 'abced'
Output: false
```
###### `A`和`B`的长度不超过100。

# Go
```go
func rotateString(A string, B string) bool {
    return len(A) == len(B) && strings.Contains(A + A, B)
}
```
