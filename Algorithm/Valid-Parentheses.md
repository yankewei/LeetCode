##### 描述
###### 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。有效字符串需满足：
###### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. 左括号必须用相同类型的右括号闭合。
###### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. 左括号必须以正确的顺序闭合。
###### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. 注意空字符串可被认为是有效字符串。
##### 示例
```
输入: "()"
输出: true
```
```
输入: "()[]{}"
输出: true
```
```
输入: "(]"
输出: false
```
```
输入: "([)]"
输出: false
```
```
输入: "{[]}"
输出: true
```
##### 解决方案
###### 可以用"栈"的概念来做。
```go
func isValid(s string) bool {
    dict := map[rune]rune{
		')':'(',
		']':'[',
		'}':'{',
	}
	stack := []rune{}
	for _, v := range s {
		if len(stack) == 0 {
			stack = append(stack, v)
			continue
		}
		if stack[len(stack) - 1] == dict[v] {
			stack = stack[:len(stack) - 1]
		} else {
			stack = append(stack, v)
		}
	}
	return len(stack) == 0
}
```
