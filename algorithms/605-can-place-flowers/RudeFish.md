## 题目
[605. 种花问题](https://leetcode-cn.com/problems/can-place-flowers/submissions/)

## 思路
当前面、后面和自己都是0时将自己变成1，在0位置时忽略前面的，在最后位置时同理

想不出来，借鉴别人写的:sweat_smile:

## 代码
```go
func canPlaceFlowers(flowerbed []int, n int) bool {
	l := len(flowerbed)
	for i:= 0; i < l; i++ {
		if flowerbed[i] == 0 && // 必须当前为0
			(i+1 >= l || flowerbed[i+1] == 0 && i+1 <= l-1) && // 后一个数为0，或者当前数为最后一个
			(i-1 < 0 || flowerbed[i-1] == 0 && i-1 >= 0){	   // 前一个数为0，或者当前数在最前面
				flowerbed[i] = 1
				n--
				// 种完n朵即可
				if n <= 0 {
					return true
				}
		}
	}

	return n <= 0
}
```
