### 題目

[27. Remove Element](https://leetcode.com/problems/remove-element/)

### 解題思路

這題跟 26. Remove Duplicates from Sorted Array 很像。
基本上就是遍歷數組，並且不斷把不同的值往前挪動。

### 代碼

```go
func removeElement(nums []int, val int) int {
	replaceIndex := 0

	for i, v := range nums {
		if v != val {
			nums[replaceIndex] = nums[i]
			replaceIndex++
		}
	}

	return replaceIndex
}
```
