### 題目

[283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

### 解題思路

1. replaceIndex 記錄 0 值的位置，遍歷數組將非 0 值往 replaceIndex 寫入
2. 最後再將 0 值補齊即可

### 代碼

```go
func moveZeroes(nums []int) {
	replaceIndex := 0

	for _, v := range nums {
		if v != 0 {
			nums[replaceIndex] = v
			replaceIndex++
		}
	}

	for i := replaceIndex; i < len(nums); i++ {
		nums[i] = 0
	}
}
```
