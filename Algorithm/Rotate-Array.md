#### 描述
给定一个数组，将数组向右旋转k步，其中k为非负数。
#### 示例1：
```
Input: [1,2,3,4,5,6,7] and k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```
#### 示例2：
```
Input: [-1,-100,3,99] and k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```
#### 备注：
* 尝试尽可能多地提出解决方案，至少有3种不同的方法来解决这个问题。
* 你能用O(1)额外空间就地做到吗？

#### 解决方案1：
强制转换，过程就是取最后一个元素和第一个元素交换，第一个和第二个交换...。这样的过程执行K次就可以了
```go
func rotate_one(nums []int, k int){
	tmp := 0;
	for i := 0; i < k; i++ {
		end := nums[len(nums) - 1]
		for j := 0; j < len(nums); j++ {
			tmp = nums[j]
			nums[j] = end
			end = tmp
			fmt.Printf("nums is %v\n", nums)
		}
	}
}
```
* 耗时: 216 ms
* 内存使用: 7.6 MB
#### 解决方案2：
