### 題目

[1. Two Sum](https://leetcode.com/problems/two-sum/)

### 解題思路

**利用 map**

1. key 是列表中的元素
2. value 是元素的下標

counterPart 是對應的元素，相加會等於 target

### 代碼

```go
func twoSum(nums []int, target int) []int {
	// m store value and index
	visited := make(map[int]int)

	for currentIndex, v := range nums {
		// 找對應的元素
		counterPart := target - v

		counterPartIndex, ok := visited[counterPart]
		if ok {
			// 在 map 找到直接回傳
			return []int{counterPartIndex, currentIndex}
		}
		// 找不到就把自己加入到 map 裡面
		visited[v] = currentIndex
	}

	return []int{-1, -1}
}
```
