### 697. 数组的度

### 代码
```
func findShortestSubArray(nums []int) int {
    m:=make(map[int]int)
    startIdx:=make(map[int]int)
    degree:=1
    res:=1<<32
    for i:=0;i<len(nums);i++{
        m[nums[i]]+=1
        if _, ok:=startIdx[nums[i]];!ok{
            startIdx[nums[i]]=i
        }
        if m[nums[i]]==degree{
            res = min(res, i - startIdx[nums[i]] + 1)
        }else if m[nums[i]]>degree{
            res= i - startIdx[nums[i]]+1
            degree = m[nums[i]]
        }
    }
    return res
}

func min(a, b int)int{
    if a<b{
        return a
    }
    return b
}
```