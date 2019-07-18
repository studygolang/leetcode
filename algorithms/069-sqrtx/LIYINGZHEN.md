### 題目

[69. Sqrt(x)](https://leetcode.com/problems/sqrtx/)

### 解題思路

簡單的二分法

### 代碼

```go
func mySqrt(x int) int {
  l, r := 0, x

  for l <= r {
    m := l + (r-l) / 2
    if (m*m < x) {
      l = m+1
    } else if (m*m > x) {
      r = m-1
    } else {
      return m
    }
  }

  return r
}
```
