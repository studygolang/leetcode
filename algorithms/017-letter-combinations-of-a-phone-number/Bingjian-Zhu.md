非递归方法，使用迭代，每次加一个字母

```golang
func letterCombinations(digits string) []string {
	var (
		lookup = map[byte][]string{
			'0': []string{"0"},
			'1': []string{"1"},
			'2': []string{"a", "b", "c"},
			'3': []string{"d", "e", "f"},
			'4': []string{"g", "h", "i"},
			'5': []string{"j", "k", "l"},
			'6': []string{"m", "n", "o"},
			'7': []string{"p", "q", "r", "s"},
			'8': []string{"t", "u", "v"},
			'9': []string{"w", "x", "y", "z"},
		}
		res = []string{""}
	)
	if digits == "" {
		return []string{}
	}
	for i := 0; i < len(digits); i++ {
		nextRes := []string{}
		for j := 0; j < len(lookup[digits[i]]); j++ {
			for _, tmp := range res {
				nextRes = append(nextRes, tmp+lookup[digits[i]][j])
			}
		}
		res = nextRes
	}
	return res
}
```