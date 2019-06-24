## 题目
[509. 斐波那契数](https://leetcode-cn.com/problems/fibonacci-number/submissions/)

## 思路


## 代码
```go
func fib(N int) int {
	a, b := 0, 1
	for i:=0; i<N; i++ {
		a, b = b, a+b
	}
	return a
}
```
