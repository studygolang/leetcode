
直接遍历切片，如果满足要求则进位，否则直接跳出执行,

```go
func plusOne(digits []int) []int {
	l := len(digits) - 1

	for i := l; i >= 0; i-- {
		if digits[i] == 9 {
			digits[i] = 0
		} else {
			digits[i]++
			break
		}
	}

	if digits[0] > 0 {
		return digits
	}

	return append([]int{1}, digits...)
}
```

扩展: 添加切片元素到特定的