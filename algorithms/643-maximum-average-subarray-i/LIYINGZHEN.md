### 題目

[643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)

### 解題思路

Sliding window algorithm.

### 代碼

```go
func findMaxAverage(nums []int, k int) float64 {
	sum := 0

	for _, v := range nums[:k] {
		sum += v
	}

	maxSum, windowSum := sum, sum

	for i := 0; i < len(nums)-k; i++ {
		windowSum += nums[k+i] - nums[i]
		if windowSum > maxSum {
			maxSum = windowSum
		}
	}

	return float64(maxSum) / float64(k)
}
```
