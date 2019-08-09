### 題目

[300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

### 解題思路

Dynamic Programming

### 代碼

```go
func lengthOfLIS(nums []int) int {
	if nums == nil || len(nums) == 0 {
		return 0
	}

	n, max := len(nums), 1
	d := make([]int, n)
	d[0] = 1

	for i := 1; i < n; i++ {
		for j := 0; j < i; j++ {
			cur := 1
			if nums[i] > nums[j] {
				cur = d[j] + 1
			}
			d[i] = Max(d[i], cur)
		}
		max = Max(max, d[i])
	}

	return max
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
