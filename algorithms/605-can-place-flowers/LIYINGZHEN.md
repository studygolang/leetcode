### 題目

[605. Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)

### 解題思路

當前下標的左右兩邊是 0 就代表可以種花，記得的處理特殊例子

### 代碼

```go
func canPlaceFlowers(flowerbed []int, n int) bool {
	// [0]
	if len(flowerbed) == 1 && flowerbed[0] == 0 {
		flowerbed[0] = 1
		n--
	}

	// [0,0,1]
	if flowerbed[0] == 0 && flowerbed[1] == 0 {
		flowerbed[0] = 1
		n--
	}

	for i := 1; i < len(flowerbed); i++ {
		if flowerbed[i] == 0 {
            // 處理尾巴
			if flowerbed[i-1] == 0 && i == len(flowerbed)-1 {
				flowerbed[i] = 1
				n--
				continue
			}
			if flowerbed[i-1] == 0 && flowerbed[i+1] == 0 {
				flowerbed[i] = 1
				n--
			}
		}

	}
	return n <= 0
}
```
