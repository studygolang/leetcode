## 题目
[661 图片平滑器](https://leetcode-cn.com/problems/image-smoother)

## 思路
先列出所有可能，超过边界的去掉，符合要求的加到数组后面(思路看的大佬的

## 代码

```go
func imageSmoother(M [][]int) [][]int {
	l, e := len(M), len(M[0])
	if l == 0 {
		return M
	}
	// 列出所有可能
	smooth := [][]int{{-1, 1}, {0, 1}, {1, 1}, {-1, 0}, {1, 0}, {-1, -1}, {0, -1}, {1, -1}}
	N := []int{}
	for x, v := range M {
		for y, a := range v {
			total, count := a, 1
			for _, s := range smooth {
				// 超过界限的去掉
				if x+s[0] < 0 || x+s[0] > l-1 || y+s[1] < 0 || y+s[1] > e-1 {
					continue
				} else {
					total += M[x+s[0]][y+s[1]]
					count++
				}
			}
			// 将算出来的值加到数组中
			N = append(N, total/count)
		}
		// 将第一条加到M后面将数组清零
		M = append(M, N)
		N = []int{}
	}
	// 返回新加的数组
	return M[l:][:]
}
```
