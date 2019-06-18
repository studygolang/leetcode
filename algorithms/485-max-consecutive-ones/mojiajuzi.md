
Runtime: 40 ms, faster than 48.80% of Go online submissions for Max Consecutive Ones.
Memory Usage: 6.3 MB, less than 55.66% of Go online submissions for Max Consecutive Ones.


```go
func findMaxConsecutiveOnes(nums []int) int {
	max := 0
	curr := 0
	for i := 0; i < len(nums); i++ {
		if nums[i] != 0 {
			curr++
		} else {
			if max < curr {
				max = curr
			}
			curr = 0
		}
	}
	if max > curr {
		return max
	}
	return curr
}
```