### 764. 最大加号标志


### 代码


#### 暴力
```
func orderOfLargestPlusSign(N int, mines [][]int) int {
    
    res:=0
    mat:=make([][]int, N)
    for i :=range mat{
        mat[i]=make([]int, N)
    }
    for _, mine:=range mines{
        mat[mine[0]][mine[1]]=1
    }
    for i:=0;i<N;i++{
        for j:=0;j<N;j++{
            k:=0
            for helper(&mat, N, i, j, k){
                k++
            }
            res=max(res, k)
        }
    }
    return res
}

func max(a, b int)int{
    if a>b{
        return a
    }
    return b
}

func helper(mat *[][]int, N int, i, j int, k int)bool{
    if i-k<0||j-k<0||i+k>=N||j+k>=N{
        return false
    }
    return (*mat)[i-k][j]==0&&(*mat)[i+k][j]==0&&(*mat)[i][j-k]==0&&(*mat)[i][j+k]==0
}
```


#### 非暴力
```
留空

```