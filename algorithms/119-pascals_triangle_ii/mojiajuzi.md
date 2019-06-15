```go
func getRow(rowIndex int) []int {
	rowIndex++
	s := make([][]int, rowIndex)
	for i := 1; i <= rowIndex; i++ {
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
	return s[rowIndex-1]

}
```