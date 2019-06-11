Runtime: 0 ms, faster than 100.00% of Go online submissions for Pascal's Triangle II.

Memory Usage: 2.1 MB, less than 30.60% of Go online submissions for Pascal's Triangle II

想用数学公式算，但是溢出了

```
func getRow(rowIndex int) []int {
    res := make([][]int, 0)
    for i := 1; i <= rowIndex+1; i++ {
        temp := make([]int, i)
        temp[0], temp[i-1] = 1, 1
        if i >= 3 {
            for j := 0; j < len(res[i-2]) - 1; j++ {
                temp[j+1] = res[i-2][j] + res[i-2][j+1]
            }
        }
        res = append(res, temp)
    }
    return res[rowIndex]
}
```
