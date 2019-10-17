回溯法
```golang
func generateParenthesis(n int) []string {
	res := []string{}
	backTrack(&res, "", 0, 0, n)
	return res
}

func backTrack(res *[]string, s string, open int, close int, max int) {
	if len(s) == max*2 {
		*res = append(*res, s)
		return
	}
	if open < max {
		backTrack(res, s+"(", open+1, close, max)
	}
	if close < open {
		backTrack(res, s+")", open, close+1, max)
	}
}
```