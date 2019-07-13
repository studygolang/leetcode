### 題目

[455. Assign Cookies](https://leetcode.com/problems/assign-cookies/description/)

### 解題思路

排序之後只要餅乾的大小，大於等於孩童所要的就給予不然就換下一個餅乾

### 代碼

```go
func findContentChildren(g []int, s []int) int {
	sort.Ints(g)
	sort.Ints(s)

	gi, si := 0, 0

	for gi < len(g) && si < len(s) {
		if g[gi] <= s[si] {
			gi++
		}
		si++
	}

	return gi
}
```
