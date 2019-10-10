```golang
func strStr(haystack string, needle string) int {
	lenHaystack := len(haystack)
	lenNeedle := len(needle)
	if needle == "" {
		return 0
	}
	if lenHaystack < lenNeedle {
		return -1
	}
	for i := 0; i < lenHaystack; i++ {
		if haystack[i] == needle[0] {
			temp := i
			if lenNeedle == 1 {
				return i
			} else {
				for j := 1; j < lenNeedle; j++ {
					temp++
					if temp > lenHaystack-1 {
						return -1
					}
					if haystack[temp] != needle[j] {
						break
					}
					if j >= lenNeedle-1 {
						return i
					}
				}
			}
		}
	}
	return -1
}
```