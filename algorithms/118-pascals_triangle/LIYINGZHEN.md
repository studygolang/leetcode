### 題目

[118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

### 解題思路

1. 最左與最右邊都是 1
2. 剩下的值是左上 ([row-1][column-1]) 跟右上 ([row-1][column]) 的和

### 代碼

```go
func generate(numRows int) [][]int {
    // 處理極端情況
	if numRows < 1 {
		return [][]int{}
	}

	result := make([][]int, numRows)
	// 第一行一定是 [1]
	result[0] = []int{1}

	for row := 1; row < numRows; row++ {
		// 建立空間
		result[row] = make([]int, row+1)

		for column := 0; column <= row; column++ {
			// 最左，最右邊都是 1
			if column == 0 || column == row {
				result[row][column] = 1
			} else {
				// 剩下的值是 左上跟右上的和
				result[row][column] = result[row-1][column-1] + result[row-1][column]
			}
		}
	}

	return result
}
```
