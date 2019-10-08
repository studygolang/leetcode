```golang
func longestCommonPrefix(strs []string) string {
	lenStr := len(strs)
	if lenStr == 0 {
		return ""
	}
	var res = []byte{}
	i := 0
	isExit := false
	var tmp byte
	for !isExit {
		if i >= len(strs[0]) {
			return string(res)
		}
		tmp = strs[0][i]
		for index, val := range strs {
			if i >= len(val) || tmp != val[i] {
				isExit = true
				break
			}
			if index >= lenStr-1 {
				i++
				res = append(res, tmp)
			}
		}
	}
	return string(res)
}
```