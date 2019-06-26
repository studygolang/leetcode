###633. Sum of Square Numbers

### 代码

```
func judgeSquareSum(c int) bool {
    i:=0
    j:=int(math.Sqrt(float64(c)))
    for i<=j{
        if i*i+j*j==c{
            return true
        }else if i*i+j*j>c{
            j--
        }else{
            i++
        }
    }
    return false
}
```