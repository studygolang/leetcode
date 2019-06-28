Runtime: 20 ms, faster than 93.71% of Go online submissions for Valid Palindrome II.

Memory Usage: 7.3 MB, less than 91.67% of Go online submissions for Valid Palindrome II.
```
func validPalindrome(s string) bool {
    if len(s) == 1 {
        return true
    }
    return is_palindrome(s, 0, len(s)-1, false)
}

func is_palindrome(s string, start int, end int, flag bool) bool {
    for start < end {
        if s[start] != s[end] {
            if flag {
                return false
            }
            if s[start + 1] == s[end] {
                if is_palindrome(s, start + 1, end, true) {
                    return true
                } 
            }    
            if s[start] == s[end - 1] {
                if is_palindrome(s, start, end - 1, true) {
                    return true
                }
            }  
            return false
       }
       start++
       end--
    }
    return true;
  }
  ```
  
  
