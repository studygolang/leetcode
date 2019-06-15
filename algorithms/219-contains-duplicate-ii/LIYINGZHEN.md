### 題目

[219. Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)

### 解題思路

1. hashMap 儲存位置
2. 如果數字重複並且兩者距離小於 k 就回傳 true，不然的話就存最新的下標

### 代碼

```go
func containsNearbyDuplicate(nums []int, k int) bool {
	hashMap := make(map[int]int)

	for currentIndex, v := range nums {
		index, ok := hashMap[v]
		if ok {
			if (currentIndex - index) <= k {
				return true
			}
		}
		hashMap[v] = currentIndex
	}

	return false
}
```
