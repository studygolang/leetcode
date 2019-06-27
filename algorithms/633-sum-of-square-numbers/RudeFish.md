## 题目
[633. 平方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers)

## 代码
```go
func judgeSquareSum(c int) bool {
	s, e := 0, int(math.Sqrt(float64(c)))
	for s <= e {
		if r := s*s + e*e; r ==  c {
			return true
		} else if r > c {
			e--
		} else {
			s++
		}
	}
	return false
}
```
