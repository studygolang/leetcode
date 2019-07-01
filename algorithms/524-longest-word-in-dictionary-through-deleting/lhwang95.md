Runtime: 20 ms, faster than 77.92% of Go online submissions for Longest Word in Dictionary through Deleting.

Memory Usage: 7.2 MB, less than 94.00% of Go online submissions for Longest Word in Dictionary through Deleting.

```
func findLongestWord(s string, d []string) string {
    var res string
    for _, str := range d {
        index := 0
        for j:=0; j<len(s); j++ {
            if index<len(str)&&s[j]==str[index] {
                index++
            }
            if index == len(str) && len(str) > len(res) {
                res = str
                break
            } else if index == len(str) && len(str)==len(res) && str < res {
                res = str
                break
            }
        }
    }
    return res
}
```
