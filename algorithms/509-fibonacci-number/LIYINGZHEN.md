### 題目

[509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)

### 解題思路

遞歸函數

### 代碼

```go
func fib(N int) int {
	if N < 0 {
		return 0
	}
	if N <= 1 {
		return N
	}
	return fib(N-1) + fib(N-2)
}
```
