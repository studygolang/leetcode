把字符串进行排序
```golang
type sortRunes []rune

func (s sortRunes) Less(i, j int) bool {
	return s[i] < s[j]
}

func (s sortRunes) Swap(i, j int) {
	s[i], s[j] = s[j], s[i]
}

func (s sortRunes) Len() int {
	return len(s)
}

func groupAnagrams(strs []string) [][]string {
	record := make(map[string]int, 16)
	res := [][]string{}
	for _, str := range strs {
		sByte := []rune(str)
		sort.Sort(sortRunes(sByte))
		temp := string(sByte)
		if index, ok := record[temp]; ok {
			res[index] = append(res[index], str)
		} else {
			record[temp] = len(record)
			res = append(res, []string{str})
		}
	}
	return res
}
```

把字母异位单词转成一个key,然后放到map比较
```golang
func groupAnagrams(strs []string) [][]string {
	result := make([][]string, 0)
	strSum := make(map[int32]int, 16)
	for _, str := range strs {
		var mul int32 = 1
		var sum int32 = 0
		for _, v := range str {
			mul *= v
			sum += v
		}
		sum += mul
		if index, ok := strSum[sum]; ok {
			result[index] = append(result[index], str)
		} else {
			strSum[sum] = len(result)
			result = append(result, []string{str})
		}
	}
	return result
}
```

