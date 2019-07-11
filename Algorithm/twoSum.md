##### 问题描述：
###### 给定一个数组nums，返回两个值的索引，这两个值相加要等于给定的一个值target，假设只有一个解，并且这两个值不能重复

##### 例子：
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
##### 解决方法：
###### Go实现
```go
func twoSum(nums []int, target int) []int {
    var array []int
	var length = len(nums)
	for i := 0; i < length; i++ {
		k := target - nums[i]
		for j := i + 1; j < length; j++ {
			if ( nums[j] == k) {
				array = append(array, i, j)
			}
		}
	}
	return array
}
```