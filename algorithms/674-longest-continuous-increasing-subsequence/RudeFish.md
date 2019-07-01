## 题目
[674. 最长连续递增序列](https://leetcode-cn.com/problems/longest-continuous-increasing-subsequence/)

## 思路
循环数组，增序加一，返回最大值

## 代码
```go
func findLengthOfLCIS(nums []int) int {
	if len(nums) == 0{
		return 0
	}
	n, r := 1, 1
	for i, v := range nums[1:] {
		if v > nums[i] {
			n++
			if n>r{
				r=n
			}
		}else {
			n=1
		}
	}

	return r
}
```
