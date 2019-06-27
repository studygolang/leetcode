Runtime: 4 ms, faster than 94.19% of Go online submissions for Reverse Vowels of a String.

Memory Usage: 4.1 MB, less than 71.43% of Go online submissions for Reverse Vowels of a String.
```
func reverseVowels(s string) string {
    if s == "" {
        return ""
    }
    begin, end := 0, len(s)-1
    res := make([]byte, len(s))
    for begin <= end {
        for begin < len(s) && s[begin] != 'a' && s[begin] != 'e' && s[begin] != 'i' && s[begin] != 'o' && s[begin] != 'u' && s[begin] != 'A' && s[begin] != 'E' && s[begin] != 'I' && s[begin] != 'O' && s[begin] != 'U' {
            res[begin] = s[begin]
            begin++
        }
        for end >= 0 && s[end] != 'a' && s[end] != 'e' && s[end] != 'i' && s[end] != 'o' && s[end] != 'u' && s[end] != 'A' && s[end] != 'E' && s[end] != 'I' && s[end] != 'O' && s[end] != 'U' {
            res[end] = s[end]
            end--
        }
        if begin < end {
            res[begin], res[end] = s[end], s[begin]
        } else if begin == end {
            res[begin] = s[begin]
        }
        begin++
        end--
    }
    return string(res)
}
```
