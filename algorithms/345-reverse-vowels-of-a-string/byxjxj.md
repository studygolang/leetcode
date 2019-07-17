```golang
func reverseVowels(s string) string {
    
    vowel := map[byte]bool {
        'a': true, 'A': true,
        'e': true, 'E': true,
        'i': true, 'I': true,
        'o': true, 'O': true,
        'u': true, 'U': true,
    }
    
    i, j := 0, len(s)-1
    tmp := []byte(s)
    
    for i < j {
        for i < len(s) && !vowel[tmp[i]] {
            i++
        }
        for j >= 0 && !vowel[tmp[j]] {
            j--
        }
        if i >= j {
            break
        }
        
        tmp[i], tmp[j] = tmp[j], tmp[i]
        i++
        j--
    }
    
    return string(tmp)
}
```
