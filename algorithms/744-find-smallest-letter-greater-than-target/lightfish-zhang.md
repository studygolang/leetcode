# 744. 寻找比目标字母大的最小字

```golang
func nextGreatestLetter(letters []byte, target byte) byte {
	l, m, r := 0, 0, len(letters)
	for l < r {
		m = (r + l) / 2
		if letters[m] <= target {
			l = m + 1
		} else {
			r = m
		}
	}
	return letters[l%len(letters)]
}
```