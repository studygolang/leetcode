```golang
func maximumProduct(nums []int) int {
    
    max1, max2, max3 := -1<<31, -1<<31, -1<<31
    min1, min2 := 1>>31, 1>>31
    
    for _, v := range nums {
        if v > max1 {
            max3, max2, max1 = max2, max1, v
        } else if v > max2 {
            max3, max2 = max2, v
        } else if v > max3 {
            max3 = v
        }
        
        if v < min1 {
            min2, min1 = min1, v
        } else if v < min2 {
            min2 = v
        }
    }
    
    return max(max1*max2*max3, max1*min1*min2)
}

func max(a, b int) int {
    if a > b {
        return a 
    }
    
    return b
}
```
