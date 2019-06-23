### 674-longest-continuous-increasing-subsequence
### 代码
```
func findLengthOfLCIS(nums []int) int {
    start:=-1
    res:=1
    if len(nums)==0{
        return 0
    }
    for i:=1;i<len(nums);i++{
        if nums[i]>nums[i-1]{
            res=max(res, i-start)
        }else{
            start=i-1
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
```