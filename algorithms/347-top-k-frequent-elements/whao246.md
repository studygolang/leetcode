### 347. 前K个高频元素
### 代码

```
func topKFrequent(nums []int, k int) []int {
    m:=make(map[int]int)
    out:=[]int{}
    res:=[]int{}
    if len(nums)==k{
        return nums
    }
    for _, v:=range nums{
        m[v]++
    }
    for _, v:=range m{
        out=append(out, v)
    }
    sort.Ints(out)
    for i:=0;i<k;i++{
        for x, v:=range m{
            if out[len(out)-1-i]==v{
                res=append(res, x)
                delete(m, x)
                
            }
        }
        
    }
    return res
}


```