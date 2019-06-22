Runtime: 68 ms, faster than 77.78% of Go online submissions for Image Smoother.

Memory Usage: 7.6 MB, less than 75.00% of Go online submissions for Image Smoother.
```
func imageSmoother(M [][]int) [][]int {
    row, col := len(M), len(M[0])
    dx := []int{1,1,1,0,0,-1,-1,-1}
    dy := []int{-1,0,1,-1,1,-1,0,1}
    result := make([][]int, 0)
    for i:=0; i<row; i++ {
        temp := make([]int, 0)
        for j:=0; j<col; j++ {
            sum := M[i][j]
            count := 1
            for k:=0; k<8; k++ {
                x := i+dx[k]
                y := j+dy[k]
                if x>=0 && x<row && y>=0 && y<col {
                    count++
                    sum+=M[x][y] //这部分浪费太多时间，可以改进
                }
            }
            temp = append(temp, sum/count)
        }
        result = append(result, temp)
    }
    return result
}
```
