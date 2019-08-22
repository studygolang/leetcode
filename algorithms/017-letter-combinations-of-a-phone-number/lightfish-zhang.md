# 17.letter combinations of a phone number

```golang
func letterCombinations(digits string) []string {
	res := []string{}
	if len(digits) == 0 {
		return res
	}
	m := map[byte][]string{
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
	res = m[digits[0]]
	for i := 1; i < len(digits); i++ {
		reslen := len(res)
		for j := 0; j < reslen; j++ {
			for _, ch := range m[digits[i]] {
				res = append(res, res[j]+ch)
			}
		}
		res = res[reslen:]
	}
	return res
}
```