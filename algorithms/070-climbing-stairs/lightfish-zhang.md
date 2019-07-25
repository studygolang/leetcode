# 70.爬楼梯

实际上是斐波那契数列

```golang
func climbStairs(n int) int {
	if n < 3 {
		return n
	}
	x, y := 1, 2
	for i := 2; i < n; i++ {
		x, y = y, x+y
	}
	return y
}
```