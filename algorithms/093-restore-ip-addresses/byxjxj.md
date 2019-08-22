```golang
func restoreIpAddresses(s string) []string {
    
    if len(s) < 4 || len(s) > 12 {
        return []string{}
    }
    
    res := []string{}
    dfs(&res, []string{}, s, 0)
    
    return res
}

func dfs(res *[]string, subRes []string, s string, index int) {
    if len(subRes) == 4 && index == len(s) {
        *res = append(*res, strings.Join(subRes, "."))
        return
    }
    
    tmpArr := []string{}
    tmpStr := ""
    for i := index; i < len(s); i++ {
        tmpStr += string(s[i])
        num, _ := strconv.Atoi(tmpStr)
        if len(tmpStr) > 3 || num > 255 || len(tmpStr) >= 2 && tmpStr[0] == '0' {
            break
        }
        tmpArr = append(tmpArr, tmpStr)
    }
    
    for _, str := range tmpArr {
        subRes = append(subRes, str)
        dfs(res, subRes, s, index+len(str))
        subRes = subRes[:len(subRes)-1]
    }
}
```
