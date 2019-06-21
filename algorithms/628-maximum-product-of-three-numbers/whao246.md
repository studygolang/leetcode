### 628. 三个数的最大乘积

### 解析
找最大三个数和最小2个数
### 代码
```
func maximumProduct(nums []int) int {
    mn1, mn2, mn3 := -1000,  -1000, -1000
    mx1, mx2 := 1000, 1000
    for _, num :=range nums{
        if num>=mn1{
            mn3=mn2
            mn2=mn1
            mn1=num
        }else if num>=mn2{
            mn3=mn2
            mn2=num
        }else if num>=mn3{
            mn3=num
        }
        
        if num<=mx1{
            mx2=mx1
            mx1=num
        }else if num<=mx2{
            mx2=num
        }
    }
    return max(mx1*mx2*mn1, mn1*mn2*mn3)
    
}

func max(a, b int)int{
    if a>b{
        return a
    }
    return b
}
```