```go
func generate(numRows int) [][]int {

	s := make([][]int, numRows)
	for i := 1; i <= numRows; i++ {
		if i == 1 {
			s[i-1] = []int{1}
			continue
		}

		if i == 2 {
			s[i-1] = []int{1, 1}
			continue
		}
		s[i-1] = make([]int, i)
		copy(s[i-1], s[i-2])
		for j := 0; j < (i - 2); j++ {
			s[i-1][j+1] = s[i-2][j] + s[i-2][j+1]
		}
		s[i-1][i-1] = 1
	}
	return s
}
```