```golang
func nextGreatestLetter(letters []byte, target byte) byte {
    
    if target < letters[0] || target > letters[len(letters)-1] {
        return letters[0]
    }
    
    left, right := 0, len(letters) - 1
    res := letters[0]
    for left <= right {
        mid := left + (right-left) >> 1
        if letters[mid] > target {
           res = letters[mid] 
           right = mid - 1
        } else {
            left = mid + 1
        }
    }
    
    return res
}
```
