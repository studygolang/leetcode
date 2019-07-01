### 題目

[674. Longest Continuous Increasing Subsequence](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)

### 解題思路

遍歷比大小

### 代碼

```go

func findLengthOfLCIS(nums []int) int {
	if len(nums) == 0 {
		return 0
	}

	right, count, max := 1, 1, 1

	for right < len(nums) {
		if nums[right-1] < nums[right] {
			count++
			if max < count {
				max = count
			}
		} else {
			count = 1
		}
		right++
	}

	return max
}
```
