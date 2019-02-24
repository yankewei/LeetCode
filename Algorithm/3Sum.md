##### 描述
###### 给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。
##### 注意
###### 答案中不可以包含重复的三元组。
##### 示例
```go
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```
##### 解决方案
###### 首先想到的是遍历切片的时候，固定住一个数，然后再遍历剩下的值，就可以使用[Two Sum](./TwoSum.md)中的方法，但是到后来发现需要排重，就会很麻烦。所以这个题目的意义应该并不是让我们使用同样的方法。
###### 我们可以先把数组进行升序排序，第一个数 > 0,那么直接返回空切片。因为已经排序。我们可以对后边的元素进行迭代。这次迭代是首[j],尾[k]迭代。也就是说j和k对应的元素相加，如果 > 0。则k--。迭代的条件是j < k。
###### 需要注意的是，为了使结果不重复。当我们进行第一次遍历的时候，如果这一次遍历的数字和上一次的相等则直接跳过。还有就是进行首尾迭代的时候，如果 j++之后和对应的j相等，也应该直接抛弃。对应的k也是。
```go
func threeSum(nums []int) [][]int {
	r := [][]int{}
	sort.Ints(nums)
	length := len(nums)
	if length < 3 || nums[0] > 0 || nums[length-1] < 0 {
		return r
	}
	for i := 0; i < length; i++ {
		if nums[i] > 0 {
			break
		}
		if i > 0 && nums[i] == nums[i-1] {
			continue
		}
		target := 0 - nums[i]
		j := i + 1
		k := length - 1
		for j < k {
			if (nums[j] + nums[k]) == target {
				r = append(r, []int{nums[i], nums[j], nums[k]})
				j++
				for j < k && nums[j] == nums[j-1] {
					j++
				}
				k--
				for j < k && nums[k] == nums[k+1] {
					k--
				}
			} else if nums[j]+nums[k] > target {
				k--
			} else {
				j++
			}
		}
	}
	return r
}
```
###### 耗时：880 ms
###### 内存使用：205.9 MB
