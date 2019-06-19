Runtime: 56 ms, faster than 88.29% of Go online submissions for Reshape the Matrix.

Memory Usage: 93.7 MB, less than 46.81% of Go online submissions for Reshape the Matrix.

```
func matrixReshape(nums [][]int, r int, c int) [][]int {
    height,width := len(nums),len(nums[0])
    res := make([][]int, 0)
    if height <= 0 || width*height != r*c {
        return nums
    }
    curh, curw := 0, 0
    for i:=0; i<r; i++ {
        temp := make([]int, 0)
        for j:=0; j<c; j++ {
            temp = append(temp, nums[curh][curw])
            curw++
            if curw == width {
                curw = 0
                curh++
            }
        }
        res = append(res, temp)
    }
    return res
}
```

2、
