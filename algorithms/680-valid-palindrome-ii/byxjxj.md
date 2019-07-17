```golang
func validPalindrome(s string) bool {
    
    i, j := 0, len(s)-1
    
    for i < j {
        if s[i] != s[j] {
            return isPalindrome(s, i+1, j) ||
            isPalindrome(s, i, j-1)
        } else {
            i++
            j--
        }
    }
    
    return true
}

func isPalindrome(s string, i, j int) bool {
    for i < j {
        if s[i] != s[j] {
            return false
        }
        i++
        j--
    }
    
    return true
}
```
