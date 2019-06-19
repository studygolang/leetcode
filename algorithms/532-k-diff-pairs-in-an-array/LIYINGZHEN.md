### 題目

[532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/submissions/)

### 解題思路

Hash Map 記錄次數

### 代碼

```go
func findPairs(nums []int, k int) int {
    // edge cases
	if k < 0 {
		return 0
	}

	dict, count := make(map[int]int), 0

	for _, v := range nums {
		dict[v]++
	}

	for v, c := range dict {
		if k == 0 {
            // k == 0 ，算出現兩次的數字即可
			if c >= 2 {
				count++
			}
		} else {
			if dict[v+k] > 0 {
				count++
			}
		}
	}

	return count
}
```
