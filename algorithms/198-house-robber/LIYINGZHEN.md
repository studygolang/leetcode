## Question

https://leetcode.com/problems/house-robber/

## Solutions

```go
func rob(nums []int) int {
	// Handle edge cases.
	if len(nums) == 0 {
		return 0
	}

	// d stores the maximun value we can rob so far.
	d := make([]int, len(nums))

	// Formula: Max(d[i-1], d[i-2]+nums[i])
	// 1. If we don't rob the house then the max value will be the previous one (i-1).
	// 2. If we rob the house then the max value will be the current one (i) + the one before the previous (i-2).

	for i := 0; i < len(nums); i++ {
		// Fot the first house.
		if i == 0 {
			// d[i-1] set to 0
			d[i] = Max(0, 0+nums[i])
			continue
		}
		// Fot the second house.
		if i == 1 {
			// d[i-2] set to 0
			d[i] = Max(d[i-1], 0+nums[i])
			continue
		}
		// Fot the reset of the houses.
		d[i] = Max(d[i-1], d[i-2]+nums[i])
	}

	return d[len(nums)-1]
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
