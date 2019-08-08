```golang
func numDecodings(s string) int {
    
    if len(s) == 0 || s[0] == '0' {
        return 0
    }
    
    pre, res := 1, 1
    for i := 1; i < len(s); i++ {
        tmp := 0
        if s[i] != '0' {
           tmp += res
        }
        if s[i-1] == '1' || (s[i-1] == '2' && s[i] <= '6') {
           tmp += pre 
        }
        pre, res = res, tmp
    }
    
    return res
}
```
