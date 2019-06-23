### 題目

[661. Image Smoother](https://leetcode.com/problems/image-smoother/)

### 解題思路

遍歷實現即可

### 代碼

```go
func imageSmoother(M [][]int) [][]int {
	m, n := len(M), len(M[0])
	out := make([][]int, m)
	for r := range M {
		out[r] = make([]int, n)
	}

	for i := range out {
		for j := range out[i] {
			out[i][j] = getValue(M, i, j)
		}
	}

	return out
}

func getValue(M [][]int, r, c int) int {
	value, count := 0, 0
	for i := r - 1; i < r+2; i++ {
		for j := c - 1; j < c+2; j++ {
			if 0 <= i && i < len(M) && 0 <= j && j < len(M[0]) {
				value += M[i][j]
				count++
			}
		}
	}
	return value / count
}
```
