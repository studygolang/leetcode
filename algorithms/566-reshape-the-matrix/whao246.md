### 566. 重塑矩阵

### 代码
```
func matrixReshape(nums [][]int, r int, c int) [][]int {
    l1:=len(nums)
    l2:=len(nums[0])
    res:=make([][]int, r)
    for i, _:=range res{
        res[i]=make([]int, c)
    }
    if r*c!=l1*l2{
        return nums
    }
    for i:=0;i<r;i++{
        for j:=0;j<c;j++{
            k:=i*c+j
            res[i][j]=nums[k/l2][k%l2]
        }
    }
    return res
}
```