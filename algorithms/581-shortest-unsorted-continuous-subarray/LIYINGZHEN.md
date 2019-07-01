### 題目

[581. Shortest Unsorted Continuous Subarray](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)

### 解題思路

將排序過與尚未排序的數組作對比，找出不同的範圍，再計算長度即可

### 代碼

```go
func findUnsortedSubarray(nums []int) int {
	sorted := make([]int, len(nums))
	copy(sorted, nums)
	sort.Ints(sorted)

	start, end, length := -1, -1, 0

	for i, v := range nums {
		if v != sorted[i] {
			if start == -1 {
				start = i
			} else {
				end = i
			}
		}
	}

	if start == end {
		return 0
	} else {
		length = end - start + 1
	}

	return length
}
```
