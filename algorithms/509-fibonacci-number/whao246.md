### 509-fibonacci-number
### 代码
```
func fib(N int) int {
    first:=0
    second:=1
    sum:=0
    if N<=1{
        return N
    }
    for i:=2;i<=N;i++{
        sum=second+first
        first = second
        second = sum
    }
    return sum
    
}
```