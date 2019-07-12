```golang
func fib(N int) int {
    
    if N <= 1 {
        return N
    }
    
    num1, num2 := 0, 1
    res := 0
    
    for i := 2; i <= N; i++ {
        res = num1 + num2
        num1, num2 = num2, res
    }
    
    return res
}
```
