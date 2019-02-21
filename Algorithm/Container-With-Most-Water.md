#### 描述
给定 n 个非负整数 a1，a2，...，an ，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。
#### 说明
你不能倾斜容器，且 n 的值至少为 2。
![图示](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg "图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。")
#### 示例
```
输入: [1,8,6,2,5,4,8,3,7]
输出: 49
```
#### 解决方案
##### 暴力解决
###### 两次循环，设一个X，一个Y，求一个面积即可
```go
func maxArea(height []int) int {
    area := 0
	len := len(height)
	areaTemp := 0
	for i := 0; i <= len; i++ {
		for j := i + 1; j < len; j++ {
			x := j - i
			y := compare(height[i], height[j])
			areaTemp = x * y
			if areaTemp > area {
				area = areaTemp
			}
		}
	}
	return area
}

func compare(a int, b int) int {
	if a >= b {
		return b
	}
	return a
}
```
* 耗时：372 ms **时间复杂度O(n<sup>2</sup>)**
* 内存使用: 5.6 MB **空间复杂度O(1)**
##### 双指针
###### 我们知道面积公式 `底 * 高`,底我们知道最长就是数组长度，高是按最小的值来计算的，这样我们就可以从两端开始算，哪一端的值小，就移动它，左端值小就++，右边值小就--。
```go
func maxArea(s []int) int {
	maxArea := 0
	length := len(s)
	l := 0
	r := length - 1
	for l < r {
		x := r - l
		y := compare(s[l], s[r])
		if x * y > maxArea {
			maxArea = x * y
		}
		if s[l] > s[r] {
			r--;
		} else {
			l++;
		}
	}
	return maxArea
}

func compare(a int, b int) int {
	if a >= b {
		return b
	}
	return a
}
```
* 耗时 16 ms **时间复杂度O(n)**
* 内存使用 5.6MB **空间复杂度O(1)**
