```go
func generate(numRows int) [][]int {
	if numRows == 0 {
		return nil
	}
	if numRows == 1 {
		fmt.Println([][]int{{1}})
		return [][]int{{1}}
	}
	rut := [][]int{}
	for i := 0; i < numRows; i++ {
		a := []int{}
		for j := 0; j <= i; j++ {
			if j == 0 || j == i {
				//a[j] = 1
				a = append(a, 1)
			}else {
				//a[j] = rut[i][j-1] + rut[i][j]
				a = append(a, rut[i-1][j-1] + rut[i-1][j])
			}
		}
		rut = append(rut, [][]int{a}...)
	}
	fmt.Println(rut)
	return rut
}
