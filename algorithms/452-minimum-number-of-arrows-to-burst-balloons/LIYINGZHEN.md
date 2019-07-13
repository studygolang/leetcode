### 題目

[452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

### 解題思路

排序完之後只要新起點的頭大於前一個的尾巴就不會碰到，必須要用下一個飛鏢射

### 代碼

```go
import "sort"

func findMinArrowShots(points [][]int) int {
	if len(points) <= 1 {
		return len(points)
	}
	sort.Sort(Sorter(points))
	end := points[0][1]
	res := 0
	for i := 1; i < len(points); i++ {
		if points[i][0] > end {
			end = points[i][1]
			res++
		}
	}

	return res + 1
}

type Sorter [][]int

func (s Sorter) Len() int {
	return len(s)
}

func (s Sorter) Swap(i, j int) {
	s[i], s[j] = s[j], s[i]
}

func (s Sorter) Less(i, j int) bool {
	return s[i][1] < s[j][1]
}
```
