```golang
func mySqrt(x int) int {
    
    left, right := 1, x
    
    for left <= right {
        mid := left + (right-left) >> 1
        if mid > x / mid {
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    
    return right
}
```
