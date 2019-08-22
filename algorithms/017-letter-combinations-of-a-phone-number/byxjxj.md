```golang
func letterCombinations(digits string) []string {
    
    if len(digits) == 0 {
        return []string{}
    }
    
    charMap := map[byte]string{'2': "abc", '3': "def", '4': "ghi", '5': "jkl", '6': "mno", '7': "pqrs", '8': "tuv", '9': "wxyz"}
    res := []string{}
    
    var dfs func(int, string)
    dfs = func(index int, com string) {
        if index == len(digits) {
            res = append(res, com)
            return
        }
        
        for _, c := range charMap[digits[index]] {
            dfs(index+1, com+string(c))
        }
    }
   
    dfs(0, "")
    
    return res
}
```
