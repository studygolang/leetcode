### 661. 图片平滑器


### 代码
```
func imageSmoother(M [][]int) [][]int {
    res:=make([][]int, len(M))
    for i:=range res{
        res[i]=make([]int, len(M[0]))
    }
    dict:=[][]int{{1,1}, {1,0},{1,-1},{0,1},{0,0},{0,-1},{-1,1},{-1,0},{-1,-1}}
    for i:=0;i<len(M);i++{
        for j:=0;j<len(M[0]);j++{
            res[i][j]=average(M, i, j, dict)
        }
    }
    return res
}

func average(nums [][]int, i, j int, dict [][]int)int{
    count:=0
    sum:=0
    for k:=0;k<len(dict);k++{
        x:=i+dict[k][0]
        y:=j+dict[k][1]
        if x>=0&&x<len(nums)&&y>=0&&y<len(nums[0]){
            sum+=nums[x][y]
            count++
        }
    }
    return sum/count
}
```