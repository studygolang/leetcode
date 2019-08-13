```golang
func ladderLength(beginWord string, endWord string, wordList []string) int {
    
    dict := make(map[string]bool)
    for _, word := range wordList {
            dict[word] = true
    }
    if !dict[endWord] {
        return 0
    }
    
    beginQue, endQue := []string{beginWord}, []string{endWord}
    res := 0
    
    for len(beginQue) > 0 && len(endQue) > 0 {
        res++
        if len(beginQue) > len(endQue) {
            beginQue, endQue = endQue, beginQue
        }
        queLen := len(beginQue)   
        for i := 0; i < queLen; i++ {
            word := beginQue[0]
            beginQue = beginQue[1:]
            byteWord := []byte(word)
            for j := range byteWord {
                tmp := byteWord[j]
                for k := 'a'; k <= 'z'; k++ {
                    byteWord[j] = byte(k)
                    tmpStr := string(byteWord)
                    for _, w := range endQue {
                        if w == tmpStr {
                            return res + 1
                        }
                    }
                    if dict[tmpStr] {
                        delete(dict, tmpStr)
                        beginQue = append(beginQue, tmpStr)
                    }
                }
                byteWord[j] = tmp
            }
        }
    }
    
    return 0
}
```
