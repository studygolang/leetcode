### 680. 验证回文字符串 Ⅱ

### 代码

```
func validPalindrome(s string) bool {
    i:=0
    j:=len(s)-1
    for i<j{
        if s[i]==s[j]{
            i++
            j--
        }else{
            return helper(s, i, j-1)||helper(s, i+1, j)
        }
    }
    return true
    
}

func helper(s string, l, r int)bool{
    for l<r{
        if s[l]!=s[r]{
            return false
        }
        l++
        r--
    }
    return true
}
```