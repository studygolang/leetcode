```golang
func canPlaceFlowers(flowerbed []int, n int) bool {
    
    length := len(flowerbed)
    
    for i, v := range flowerbed {
        if v == 0 && 
        (i == 0 || flowerbed[i-1] == 0) &&
        (i == length-1 || flowerbed[i+1] == 0) {
            flowerbed[i] = 1
            n--
            
            if n <= 0 {
                return true
            }
        }
    }
    
    return n <= 0
}
```
