## 题目
[643. 子数组最大平均数 I](https://leetcode-cn.com/problems/maximum-average-subarray-i/submissions/)

## 代码
```go
func findMaxAverage(nums []int, k int) float64 {
    temp := 0
	// 算出第一轮k个数和
	for _, v := range nums[:k] {
		temp += v
	}
	max := temp

	for i, v := range nums[k:] {
		// 减去前一个，加上后一个
		temp = temp - nums[i] + v
		if temp > max {
			max = temp
		}
	}

	return float64(max)/float64(k)
}
```
