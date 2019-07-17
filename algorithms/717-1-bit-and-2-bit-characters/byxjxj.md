```golang
func isOneBitCharacter(bits []int) bool {
    
    i := 0
    
    for i < len(bits) {
        if bits[i] == 1 {
            i += 2
        } else {
            if i == len(bits)-1 {
                return true
            }
            i++
        }
    }
    
    return false
}
```
