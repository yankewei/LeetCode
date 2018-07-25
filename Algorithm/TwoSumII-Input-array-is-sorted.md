Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.
> 给定一个已经按照升序排好序的数组，找出两个值，使这两个值相加等于一个指定的值。

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.
> 函数`twoSum`应该返回两个值得索引，并且index1 的值必定小于index2。

**Note:**
- 返回的答案都不是从0开始的。
- 你可以假设输入的数组必定会有一个解，并且你不可以使用一个元素两次。

**Example:**
```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

#### Solution:
###### 这个主要考察的是双指针，因为是已经排好序了，那么我们就可以使用两个指针，一个从数组头部（L）开始，一个从数组尾部（R）开始，而且必定有一个解，我们就可以让头尾相加，如果比目标值大，我们可以让 R - 1， 反过来就是让 L + 1.

##### Go
```go
func twoSum(numbers []int, target int) []int {
    l, r := 0, len(numbers) -1
    response := []int{}
    for l <= r {
        if numbers[l] + numbers[r] == target {
			response = append(response, l + 1, r + 1)
			break
        } else if numbers[l] + numbers[r] > target {
            r--
        } else {
            l++
        }
    }
    return response
}
```
