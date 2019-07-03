Runtime: 4 ms, faster than 96.34% of Go online submissions for Sort Characters By Frequency.

Memory Usage: 5.8 MB, less than 52.38% of Go online submissions for Sort Characters By Frequency.
```
func frequencySort(s string) string {
    temp := make([]byte, len(s))
	copy(temp, s)
	data := make([]string, 0)
	for i := 0; i < len(s); {
		begin := i
		for j := i + 1; j < len(s); j++ {
			if temp[j] == temp[i] {
				i++
				temp[i], temp[j] = temp[j], temp[i]
			}
		}
		i++
		data = append(data, string(temp[begin:i]))
	}
    sort.Slice(data, func (i, j int) bool {
        return len(data[i]) > len(data[j])
    })
    var res string
    for i:=0; i<len(data); i++ {
        res += data[i]
    }
    return res
}
```
