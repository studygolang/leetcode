Runtime: 0 ms, faster than 100.00% of Go online submissions for Fibonacci Number.

Memory Usage: 2 MB, less than 20.26% of Go online submissions for Fibonacci Number.

```
func fib(N int) int {
    res := make([]int, 31)
    res[0], res[1] = 0, 1
    if N < 2 {
        return res[N]
    }
    for i:=2; i<=N; i++ {
        res[i] = res[i-1] + res[i-2]
    }
    return res[N]
}
```
