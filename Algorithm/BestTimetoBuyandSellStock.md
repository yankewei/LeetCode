##### 描述
###### 给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。
###### 如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。
###### 注意你不能在买入股票前卖出股票。

##### 示例
###### 示例1
```
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
```
###### 示例2
```
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```

##### 暴力破解
###### 循环两遍，第`i`的元素的值认为是买的价格，第`j`的元素的值认为是卖的价格。`prices[j] - prices[i]`即为最大值
```go
func maxProfit(prices []int) int {
    max := 0
	length := len(prices)
	for i := 0; i < length; i++ {
		buy := prices[i]
		for j := i; j < length; j++ {
			seller := prices[j]
			if (seller - buy) > max {
				max = (seller - buy)
			}
		}
	}
	return max
}
```
- 时间复杂度 O(n<sup>2</sup>)
- 空间复杂度 O(1)
##### 动态规划（个人认为不太像）
###### 股票的趋势其实是一个折线图
![示例](https://leetcode.com/media/original_images/121_profit_graph.png)
###### 那么我们就是找到最低点和最高点就可以了，做一个减法，就是收益最大值
```go
func maxProfit(prices []int) int {
    minProfit := math.MaxInt64
	maxProfit := 0
	for i := 0; i < len(prices); i++ {
		if prices[i] < minProfit {
			minProfit = prices[i]
		} else if (prices[i] - minProfit) > maxProfit {
			maxProfit = prices[i] - minProfit
		}
	}
	return maxProfit
}
```
- 时间复杂度 O(n)
- 空间复杂度 O(1)
