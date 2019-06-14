### 題目

[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

### 解題思路

hashMap 遇到存在直接返回 true

### 代碼

```go
func containsDuplicate(nums []int) bool {
	hashMap := make(map[int]int)

	for _, v := range nums {
		_, ok := hashMap[v]
		if ok {
			return true
		}
		hashMap[v] = v
	}

	return false
}
```
