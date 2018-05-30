You are a professional robber planning to rob houses along a street. 
Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

##### Example 1:
```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```
##### Example 2:
```
Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
```

##### 解题思路:
其实对对于这个问题有两种选择，不同的选择会影响到后面的选择，就可以用动态规划的思想来解决问题
- 到第n个是，如果选择拿就是前边`n-2`的最大值 加上 `n`的值；
- 如果选择不拿就是前边`n-1`的最大值；
- 对这两个进行比较，选择最大的，也就是当前n个元素是的最优解，以此类推
声明一个函数`f(n)`来计算有n + 1个长度的数组是，应该如何选择：
```
f(0) = nums[0]
f(1) = max(f(0), nums[1])
f(2) = max(f(0) + nums[2], f(1)) //这里就是不同的选择时获取最大值
f(k) = max(f(k-2) + nums[k], f(k-1))
```
对这个题，我们只需要求得最大值，所以我们用只有两个元素的数组来保存`f(k-2)`和`f(k-1)`的值

### Go解法
```go
func rob(nums []int) int {
	d := [2]int{0, 0}
	for _,value := range nums {
		tmp := d[0]
		d[0] = d[1]
		d[1] = max(tmp + value, d[1])
	}
	return d[1]
}

func max(a int, b int) int {
    if a > b {
        return a
    }
    return b
}
```
