### 題目

[485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/submissions/)

### 解題思路

for loop counter

### 代碼

```go
func findMaxConsecutiveOnes(nums []int) int {
	max, counter := 0, 0
	for _, v := range nums {
		if v == 1 {
			counter++
			continue
		}
		if counter > max {
			max = counter
		}
		counter = 0
	}
	if counter > max {
		max = counter
	}
	return max
}
```
