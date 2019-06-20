### 題目

[566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)

### 解題思路

建立好新的二維數組之後遍歷，把值從舊的數組對應到新的數組中

```go
x := i % n
y := i / n
newX := i % c
newY := i / c
// 数组第一维是 y，第二维是 x
ans[newY][newX] = nums[y][x]
```

### 代碼

```go
func matrixReshape(nums [][]int, r int, c int) [][]int {
	if len(nums) == 0 {
		return nums
	}

	m := len(nums)
	n := len(nums[0])

	if m*n != r*c {
		return nums
	}

	ans := make([][]int, r)
	for i := 0; i < len(ans); i++ {
		ans[i] = make([]int, c)
	}

	for i := 0; i < m*n; i++ {
		x := i % n
		y := i / n
		newX := i % c
        newY := i / c
        // 数组第一维是 y，第二维是 x
		ans[newY][newX] = nums[y][x]
	}

	return ans
}
```
