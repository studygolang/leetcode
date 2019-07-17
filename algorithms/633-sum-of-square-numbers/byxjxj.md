```golang
func judgeSquareSum(c int) bool {
    
    maxNum := int(math.Sqrt(float64(c)))
    
    for a := 0; a <= maxNum; a++ {
        b := int(math.Sqrt(float64(c-a*a)))
        if a*a + b*b == c {
            return true
        } 
    }
    
    return false
}
```
