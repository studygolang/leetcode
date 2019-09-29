滑动窗口，例如题中的abcabcbb，列表中有abc后，发现再放a就重复了，然后把左边的a去掉。
用map的原因是它查找元素是否存在的效率为O(1)
```golang
func lengthOfLongestSubstring(s string) int {
	res := 0
	lenS := len(s)
	if lenS == 0 {
		return res
	}
	strMap := make(map[byte]struct{}, 100)
	left := 0
	right := 0
	for left < lenS && right < lenS {
		if _, ok := strMap[s[right]]; !ok {
			strMap[s[right]] = struct{}{}
			right++
			res = maxInt(res, len(strMap))
		} else {
			delete(strMap, s[left])
            left++
            strMap[s[right]] = struct{}{}
            right++
		}
	}
	return res
}

func maxInt(x, y int) int {
	if x < y {
		return y
	}
	return x
}
```