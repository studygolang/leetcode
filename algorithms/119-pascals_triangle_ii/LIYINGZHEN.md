### 題目

[119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)

### 解題思路

跟 [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/) 解題思路一樣。
注意下標越界問題即可。

### 代碼

```go
func getRow(rowIndex int) []int {
	result := make([][]int, rowIndex+1)
	result[0] = []int{1}

	for row := 1; row <= rowIndex; row++ {
		result[row] = make([]int, row+1)
		for column := 0; column <= row; column++ {
			if column == 0 || column == row {
				result[row][column] = 1
			} else {
				result[row][column] = result[row-1][column-1] + result[row-1][column]
			}
		}
	}

	return result[rowIndex]
}
```
