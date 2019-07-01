Runtime: 16 ms, faster than 95.65% of Go online submissions for Can Place Flowers.

Memory Usage: 5.9 MB, less than 30.56% of Go online submissions for Can Place Flowers.
```
func canPlaceFlowers(flowerbed []int, n int) bool {
    length := len(flowerbed)
    res, i := 0, 0
    for i<length {
        if (i == 0 || flowerbed[i-1] == 0) && flowerbed[i] == 0 && (i == length - 1 || flowerbed[i+1] == 0) {
            flowerbed[i] = 1
            res++
        }
        i++
        if res >= n {
            return true
        }
    }
    return false
}
```
