问题描述：Given an array of integers, return indices of the two numbers such that they add up to a specific target.You may assume that each input would have exactly one solution, and you may not use the same element twice.

例子：
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
解决方法：
# Go实现
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

# Python实现
```Python
class Solution(object):
    def twoSum(self, nums, target):
        d = {}
        for i, n in enumerate(nums):
            m = target - n
            if m in d:
                return [d[m], i]
            else:
                d[n] = i
```
