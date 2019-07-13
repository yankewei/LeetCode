##### 问题描述：
###### Determine whether an integer is a palindrome. Do this without extra space.

##### 示例：
###### 示例1：
```
输入: 121
输出: true
```
###### 示例2：
```
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
```
###### 示例3：
```
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```

##### 解决方法：
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
