# 93 restore ip addresses

## 解法

题目特性：从素材中得出所有合法的排序结果，最适合使用回溯法

回溯法(backtrack)，也就是推演分支+剪枝，从不同的分支开始推演，并设置好过滤条件，提前结束无解的分支（剪枝），最终保留正解的分支结果。


```golang
import (
	"strconv"
	"strings"
)

func restoreIpAddresses(s string) []string {
	l := len(s)
	if l < 4 || l > 12 {
		return []string{}
	}
	res := []string{}
	var backTrack func(string, []string)
	backTrack = func(sub string, part []string) {
		if len(sub) > (4-len(part))*3 {
			return
		}
		if len(sub) == 0 && len(part) == 4 {
			res = append(res, strings.Join(part, "."))
			return
		}
		k := min(3, len(sub))
		for i := 1; i <= k; i++ {
			curr := sub[:i]
			if (curr[0] == '0' && len(curr) >= 2) || atoi(curr) > 255 {
				continue
			}
			newpart := append([]string{}, part...)
			newpart = append(newpart, curr)
			backTrack(sub[i:], newpart)
		}
	}
	backTrack(s, []string{})
	return res
}

func atoi(s string) int {
	n, _ := strconv.Atoi(s)
	return n
}

func min(x, y int) int {
	if x < y {
		return x
	}
	return y
}
```