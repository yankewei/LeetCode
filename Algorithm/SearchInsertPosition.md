问题描述：
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

例子：
```go
Input: [1,3,5,6], 5
Output: 2

Input: [1,3,5,6], 2
Output: 1

Input: [1,3,5,6], 7
Output: 4

Input: [1,3,5,6], 0
Output: 0
```

解决方法：

# Go
```go
func searchInsert(nums []int, target int) int {
    i, j := 0, len(nums) - 1
    for i <= j {
        mid := (i + j) >> 1
        if nums[mid] == target {
            return mid
        }else if nums[mid] > target {
            j = mid - 1
        }else {
            i = mid + 1
        }
    }
    return i
}
```
