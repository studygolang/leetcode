### 643. 子数组最大平均数 I

### 代码
```
func findMaxAverage(nums []int, k int) float64 {
    var res float64
    res=-10000
    if k>=len(nums){
        return average(nums, 0, len(nums))
    }
    for i:=0;i<=len(nums)-k;i++{
        temp:= average(nums, i, i+k)
        if res<temp{
            res=temp
        }
    }
    return res
}

func average(nums []int,  l, r int)float64{
    sum:=0
    for i:=l;i<r;i++{
        sum+=nums[i]
    }
    return float64(sum)/float64(r-l)
}

```