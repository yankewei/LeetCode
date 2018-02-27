问题描述：Determine whether an integer is a palindrome. Do this without extra space.

例子：
```

```

解决方法：
```go
func isPalindrome(x int) bool {
    if x < 0 {
        return false
    }
    sum := 0
    tmp := x
    for tmp != 0 {
        sum = sum*10 + tmp%10
        tmp = tmp/10
    }
    if sum > math.MaxInt32 || sum < math.MinInt32 {
        return false
    }
    if sum == x {
        return true
    }
    return false
}
```
