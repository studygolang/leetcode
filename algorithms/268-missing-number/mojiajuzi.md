
Runtime: 16 ms, faster than 96.05% of Go online submissions for Missing Number.
Memory Usage: 5.9 MB, less than 100.00% of Go online submissions for Missing Number.

```go
func missingNumber(nums []int) int {
	for k, v := range nums {
		if k == 0 {
			nums[0] = k - v
		} else {
			nums[0] += k - v
		}
	}
	return len(nums) + nums[0]
}
```


