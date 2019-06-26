### 題目

[633. Sum of Square Numbers](https://leetcode.com/problems/sum-of-square-numbers/)

### 解題思路

雙指針

### 代碼

```go
func judgeSquareSum(c int) bool {
	if c == 0 {
		return true
	}

	left, right := 0, int(math.Sqrt(float64(c)))

	for left < right {
		sum := left*left + right*right
		if sum == c {
			return true
		} else if sum > c {
			right--
		} else {
			left--
		}
	}

	return false
}
```
