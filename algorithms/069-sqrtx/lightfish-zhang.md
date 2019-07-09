# x 的平方根

## 解法

用二分法来猜测平均数的平方是否接近x，因为输出只有整数部分，所以最终结果偏向左边界

```golang
func mySqrt(x int) int {
	if x == 0 || x == 1 {
		return x
	}
	l, r, t := 1, x, 0
	m := (l + r) / 2
	for l != m {
		t = m * m
		if t == x {
			return m
		}
		if t < x {
			l = m
		} else {
			r = m
		}
		m = (l + r) / 2
	}
	return m
}
```