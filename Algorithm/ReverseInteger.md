问题描述：Given a 32-bit signed integer, reverse digits of an integer.

例子：
```
Input: 123
Output:  321

Input: -123
Output: -321

Input: 120
Output: 21
```
备注：
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
（这里假设你的计算环境是32位的，当反转时，如果溢出则返回0）

解决方法：
```go
func reverse(x int) int {
    sum := 0
    for x != 0 {
        sum = sum*10 + x%10
        x = x/10
    }
    if sum > math.MaxInt32 || sum < math.MinInt32 {
        return 0
    }
    return sum
}
```
