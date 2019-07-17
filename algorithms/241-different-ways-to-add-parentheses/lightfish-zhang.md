# 241. Different Ways to Add Parentheses 添加括号的不同方式

## 解法

题目一看起来似乎有些难度，其实使用分治法，就把大化小了

```golang
import "strconv"

func diffWaysToCompute(input string) []int {
	ret := []int{}
	for i, c := range input {
		if c == '+' || c == '-' || c == '*' {
			left_ret := diffWaysToCompute(input[0:i])
			right_ret := diffWaysToCompute(input[i+1:])
			for _, l_ret := range left_ret {
				for _, r_ret := range right_ret {
					if c == '+' {
						ret = append(ret, l_ret+r_ret)
					} else if c == '-' {
						ret = append(ret, l_ret-r_ret)
					} else {
						ret = append(ret, l_ret*r_ret)
					}
				}
			}
		}
	}
	if len(ret) == 0 {
		num, _ := strconv.Atoi(input)
		ret = append(ret, num)
	}
	return ret
}
```