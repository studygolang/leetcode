Runtime: 0 ms, faster than 100.00% of Go online submissions for Pascal's Triangle.

Memory Usage: 2.3 MB, less than 50.97% of Go online submissions for Pascal's Triangle

```
func generate(numRows int) [][]int {
    res := make([][]int, 0) // 声明空返回值
    for i := 1; i <= numRows; i++ {
        temp := make([]int, i)　// 声明每一行
        temp[0], temp[i-1] = 1, 1 //　每行首尾都是1
        if i >= 3 {
            for j := 0; j < len(res[i-2]) - 1; j++ {
                temp[j+1] = res[i-2][j] + res[i-2][j+1] //　每行第二个值起都等于前一行相邻加和
            }
        }
        res = append(res, temp)
    }
    return res
}
```
