```golang
func frequencySort(s string) string {
    
    fre := make(map[rune]int, len(s))
    for _, v := range s {
        fre[v]++
    }
    
    ss := make([]string, 0, len(fre))
    for k, v := range fre {
        tmp := make([]rune, v)
        for i := range tmp {
            tmp[i] = k
        }
        ss = append(ss, string(tmp))
    }
    
    sort.Sort(str(ss))
    
    res := ""
    for _, v := range ss {
        res += v
    }
    
    return res
}

type str []string

func (s str) Len() int {
    return len(s)
}

func (s str) Less(i, j int) bool {
    return len(s[i]) > len(s[j])
}

func (s str) Swap(i, j int) {
    s[i], s[j] = s[j], s[i]
}
```
